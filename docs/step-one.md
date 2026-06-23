Step One — Implementación en contenedores (Docker) para Android mobile apps (Play Store)

Resumen
- Objetivo: desplegar el framework de agentes y la cadena de desarrollo en contenedores Docker reproducibles, siguiendo la adopción "usar dev-containers (Docker + devcontainer.json)" marcada en draft.md.
- Público objetivo: desarrolladores y equipos que quieren CI reproducible y agentes aislados por repo.

Prerequisitos
- Docker instalado en máquina local/CI
- Docker Compose (opcional)
- Java JDK 11+ o el requerido por el proyecto
- Android SDK/NDK (se instalará en imagen o se montará cache)
- Acceso a repositorios de agentes (p. ej. m00sp/m00agents) y gists referenciados

Guía completa paso a paso

1) Crear repositorio esqueleto
   - Crear estructura básica:
     - README.md, LICENSE, CONTRIBUTING.md
     - .github/workflows/
     - .github/ISSUE_TEMPLATE/
     - devcontainer.json
     - Dockerfile
     - docs/
   - Añadir CODEOWNERS, ISSUE_TEMPLATE y PR template.

2) Definir devcontainer.json (archivo reproducible para VS Code)
   - Objetivo: permitir abrir el proyecto en un entorno idéntico.
   - Ejemplo completo (copiar como .devcontainer/devcontainer.json):

```
{
  "name": "Android Dev",
  "build": { "dockerfile": "../Dockerfile", "context": ".." },
  "workspaceFolder": "/workspace",
  "customizations": {
    "vscode": {
      "extensions": [
        "redhat.java",
        "vscjava.vscode-java-pack",
        "ms-vscode.cpptools",
        "ms-vscode.vscode-typescript-tslint-plugin"
      ]
    }
  },
  "mounts": [
    "source=${localEnv:HOME}/.gradle,target=/home/vscode/.gradle,type=bind,consistency=cached",
    "source=${localEnv:HOME}/.android,target=/home/vscode/.android,type=bind,consistency=cached"
  ],
  "postCreateCommand": "./scripts/setup-android-sdk.sh",
  "settings": {
    "terminal.integrated.shell.linux": "/bin/bash"
  }
}
```

- Crear el script scripts/setup-android-sdk.sh con pasos de instalación del SDK (se detalla en el Dockerfile/e.j.).

3) Dockerfile (imagen base reproducible)
   - Crear Dockerfile en la raíz (ejemplo listo para usar):

```
# Dockerfile - imagen base para desarrollo Android
FROM openjdk:11-jdk-slim

ENV ANDROID_SDK_ROOT=/opt/android-sdk
ENV PATH=${PATH}:${ANDROID_SDK_ROOT}/cmdline-tools/latest/bin:${ANDROID_SDK_ROOT}/platform-tools

RUN apt-get update && apt-get install -y --no-install-recommends \
    wget unzip git curl gradle ca-certificates bash && \
    rm -rf /var/lib/apt/lists/*

# Crear directorios
RUN mkdir -p ${ANDROID_SDK_ROOT}/cmdline-tools && mkdir -p /workspace
WORKDIR /workspace

# Instalar commandline-tools (sdkmanager)
RUN mkdir -p /tmp/sdk && \
    cd /tmp/sdk && \
    wget -q https://dl.google.com/android/repository/commandlinetools-linux-8512546_latest.zip -O cmdline.zip && \
    unzip cmdline.zip -d cmdline && \
    rm cmdline.zip && \
    mv cmdline/cmdline-tools ${ANDROID_SDK_ROOT}/cmdline-tools/latest

# Aceptar licencias y descargar plataformas básicas
RUN yes | ${ANDROID_SDK_ROOT}/cmdline-tools/latest/bin/sdkmanager --sdk_root=${ANDROID_SDK_ROOT} "platform-tools" "platforms;android-33" "build-tools;33.0.0" "ndk;25.2.9519653"

# Crear usuario no-root para desarrollo
RUN useradd -m -s /bin/bash devuser && chown -R devuser:devuser /workspace ${ANDROID_SDK_ROOT}
USER devuser

# Gradle wrapper preferido: usar wrapper presente en proyecto
ENV GRADLE_USER_HOME=/home/devuser/.gradle

CMD ["/bin/bash"]
```

Notas Dockerfile:
- Ajusta versiones (android-33, build-tools) según proyecto.
- Para imágenes más pequeñas, limpiar caches y combinar capas.

4) scripts/setup-android-sdk.sh (para devcontainer)
- Ejemplo (colocar en .devcontainer/scripts/setup-android-sdk.sh):

```
#!/bin/bash
set -e
ANDROID_SDK_ROOT=/opt/android-sdk
# Si el SDK está montado por el host, no re-instalar
if [ -d "$ANDROID_SDK_ROOT/cmdline-tools" ]; then
  echo "Android SDK already present"
  exit 0
fi
# Aquí podría descargarse e instalar cmdline-tools si no está montado
# Para el devcontainer asumimos que Dockerfile ya instaló herramientas base
```

5) Caching y rendimiento
   - Local: montar ${HOME}/.gradle y ${HOME}/.android al devcontainer para persistencia.
   - CI: usar actions/cache para ~/.gradle y caches de SDK.

6) GitHub Actions workflow (ejemplo: .github/workflows/android-build.yml)

```
name: Android CI
on:
  push:
    branches: [ main, 'agent/*' ]
  pull_request:
    branches: [ main ]

jobs:
  build:
    runs-on: ubuntu-latest
    env:
      JAVA_TOOL_OPTIONS: -Dfile.encoding=UTF8
    steps:
      - name: Checkout
        uses: actions/checkout@v4

      - name: Set up JDK
        uses: actions/setup-java@v4
        with:
          distribution: temurin
          java-version: '11'

      - name: Cache Gradle
        uses: actions/cache@v4
        with:
          path: |
            ~/.gradle/caches
            ~/.gradle/wrapper
          key: ${{ runner.os }}-gradle-${{ hashFiles('**/gradle-wrapper.properties') }}

      - name: Install Android SDK tools
        run: |
          sudo apt-get update && sudo apt-get install -y wget unzip
          wget -q https://dl.google.com/android/repository/commandlinetools-linux-8512546_latest.zip -O /tmp/cmdline.zip
          sudo unzip -q /tmp/cmdline.zip -d /opt/android-sdk
          sudo chown -R $USER:$USER /opt/android-sdk
          yes | /opt/android-sdk/cmdline-tools/latest/bin/sdkmanager --sdk_root=/opt/android-sdk "platform-tools" "platforms;android-33" "build-tools;33.0.0"

      - name: Build
        run: ./gradlew --no-daemon assembleRelease

      - name: Upload artifacts
        uses: actions/upload-artifact@v4
        with:
          name: apk
          path: app/build/outputs/**/*.apk
```

Notas workflow:
- Para signing y deploy, usar secrets (KEYSTORE_PASSWORD, KEYSTORE_BASE64) y acciones como r0adkll/sign-android-release or fastlane.

7) Firma de APK en CI (breve)
   - Guardar keystore como secret en base64 y decodificar en CI:

```
- name: Decode keystore
  run: echo "$KEYSTORE_BASE64" | base64 --decode > release.keystore
  env:
    KEYSTORE_BASE64: ${{ secrets.KEYSTORE_BASE64 }}
```

- Usar variables de entorno para passwords y firmar con jarsigner o gradle signingConfig.

8) Integración de agentes y orquestación
   - Mantener manifiesto de agentes en repo (agents.yaml) con campos: name, repo, gist_examples, ci_required.
   - Orquestador debe validar CI status de repos de agentes antes de permitir acciones que afecten al repo principal.

Ejemplo agents.yaml (sencillo):

```
- name: jp-agent-flow-fleet
  repo: https://github.com/m00sp/jp-agent-flow-fleet
  gist: https://gist.github.com/m00sp/615b515ebf3421455ba9ae1d576ac579
  ci_required: true
- name: ultralight-orchestration
  repo: https://github.com/m00sp/ultralight-orchestration
  gist: https://gist.github.com/m00sp/4b8025c073b2ea2b9104aa8b86371454
  ci_required: true
```

9) Pruebas en emuladores / device labs
   - Para instrumented tests en CI, usar Firebase Test Lab o servicios similares.
   - Evitar emuladores dentro de runners salvo que la infraestructura lo soporte.

10) Despliegue piloto y validación
   - Crear agente "hello-world" que abra un PR con un change trivial (README update).
   - Verificar: pipeline corre, artefactos generados, notificaciones y revisión humana.

11) Seguridad y permisos (resumen)
   - Tokens con scopes mínimos
   - Secretos sólo en gestores (GitHub Secrets)
   - Auditoría y registro de acciones de agentes

12) Documentación y onboarding
   - Añadir guías:
     - Cómo abrir devcontainer
     - Cómo ejecutar build local
     - Cómo crear y usar keystore localmente
     - Cómo añadir un nuevo agente al agents.yaml

Apéndice — Checklist rápido
- [ ] Dockerfile añadido y probado localmente
- [ ] .devcontainer/devcontainer.json y scripts añadidos
- [ ] .github/workflows/android-build.yml añadido y probado en PR
- [ ] agents.yaml con referencias a gists/repos
- [ ] Secrets configurados en CI (keystore, API tokens)
- [ ] Prueba piloto con agente hello-world completada

Notas finales
- Si "Tocker" era un término diferente a Docker, indicarlo y adapto la guía.
- Puedo generar archivos individuales (Dockerfile, devcontainer.json, workflow) como archivos en el repo si quieres.

Instrucciones paso a paso (comandos)
A continuación los comandos exactos para crear los archivos y validar localmente. Ejecuta desde la raíz del repo.

1) Crear directorios y archivos (si no existen)

```bash
mkdir -p .devcontainer/scripts .github/workflows docs
```

2) (Opcional) Inicializar git y crear rama principal

```bash
git init
git checkout -b main
```

3) Construir la imagen Docker localmente

```bash
docker build -t android-dev .
```

4) Ejecutar el contenedor para desarrollar y probar builds (montar caches)

```bash
docker run --rm -it \
  -v ${HOME}/.gradle:/home/devuser/.gradle \
  -v ${HOME}/.android:/home/devuser/.android \
  -v "$(pwd)":/workspace \
  android-dev /bin/bash
```
Dentro del contenedor:
```bash
# Compilar app (debug o release según necesidad)
./gradlew assembleDebug
# o
./gradlew assembleRelease
```

5) Abrir en VS Code con devcontainer
- En VS Code: Remote-Containers (Open Folder in Container) apuntando al repo.

6) Probar workflow con PR de agente (hello-world)

```bash
git checkout -b agent/hello-world
echo "PR generated by hello-world agent" >> README.md
git add README.md && git commit -m "test: hello-world agent PR"
git push -u origin agent/hello-world
# Crear PR en GitHub desde la rama; verificar que .github/workflows/android-build.yml se ejecute
```

7) Decodificar keystore (ejemplo CI)

```bash
# En CI: KEYSTORE_BASE64 es secreto en GitHub
echo "$KEYSTORE_BASE64" | base64 --decode > release.keystore
```

8) Limpieza y verificación
- Verifica que los artefactos (APK/AAB) aparecen en app/build/outputs/ después de la compilación.
- Comprueba que caches (~/.gradle) se hayan poblado para acelerar builds posteriores.

Comentarios finales
- Estos pasos son suficientes para un primer despliegue piloto. Tras validar, procede a configurar secrets en el repositorio (KEYSTORE, tokens) y a crear la tarea piloto del agente.

