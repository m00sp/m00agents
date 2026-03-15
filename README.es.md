# m👀agents

<div align="center">

[![Made with ❤️ by Copilot](https://img.shields.io/badge/Made%20with%20%E2%9D%A4%EF%B8%8F%20by-Copilot-ff69b4?style=flat-square)](https://github.com/github/copilot-docs)
![Beginner Friendly](https://img.shields.io/badge/Beginner-Friendly-brightgreen?style=flat-square)

**Una colección de agentes personalizados de GitHub Copilot amigables para principiantes para comenzar con el desarrollo asistido por IA.**

</div>

## 🎯 ¿Qué es m👀agents?

m👀agents es un kit de herramientas de inicio con agentes personalizados diseñados para desarrolladores nuevos en GitHub Copilot. Proporciona agentes listos para usar que mejoran las capacidades de Copilot para tareas comunes como crear documentación y plantillas de código.

Si estás explorando agentes personalizados por primera vez o creando sobre habilidades existentes, esta colección demuestra cómo crear y usar personas de IA especializadas en tu flujo de trabajo.

## 🚀 Inicio Rápido

### Obtener los Agentes

**Opción 1: Clonar para experimentación local**
```bash
git clone https://github.com/m00sp/m00agents.git
cd m00agents
```

**Opción 2: Hacer fork en tu cuenta de GitHub**
```bash
# Visita: https://github.com/m00sp/m00agents/fork
# Luego clona tu fork
git clone https://github.com/YOUR-USERNAME/m00agents.git
cd m00agents
```

### Instalar Agentes Localmente

Copia los agentes a tu configuración local de Copilot:

```bash
# Copiar a agentes a nivel de usuario (disponibles en todos los proyectos)
cp agents/*.agent.md ~/.copilot/agents/
```

O para uso específico del repositorio:
```bash
# Copiar a agentes a nivel de repositorio (disponibles solo en este proyecto)
mkdir -p .github/agents
cp agents/*.agent.md .github/agents/
```

### Usar un Agente en Copilot CLI

```bash
# Listar agentes disponibles
copilot /agent

# O especificar un agente directamente
copilot --agent=docs-creator --prompt "Create documentation for..."
copilot --agent=readme-creator --prompt "Generate a README..."
```

## 📦 Agentes Disponibles

Este repositorio incluye agentes especializados organizados por dominio:

### 📝 Agentes de Documentación
| Agente | Propósito |
|--------|-----------|
| **m👀readme-creator** | Crea y mejora archivos README con estructura clara, guías de instalación y descripción general del proyecto |
| **docs-creator** | Genera documentación técnica clara y amigable |

### 💻 Agentes de Ingeniería de Software
| Agente | Propósito |
|--------|-----------|
| **C++ Expert** | Proporciona orientación experta en ingeniería de software C++ utilizando C++ moderno y mejores prácticas de la industria |
| **m👀Rust Expert for Beginners** | Orientación experta en Rust para principiantes, enfatizando propiedad, seguridad y patrones idiomáticos |
| **Custom Agent Foundry** | Experto en diseñar, crear y mejorar agentes personalizados con configuraciones óptimas |

### 🐧 Agentes de Administración de Sistemas Linux
| Agente | Propósito |
|--------|-----------|
| **Arch Linux Expert** | Especialista en Arch Linux enfocado en pacman, mantenimiento de versión móvil y administración de sistemas |
| **m👀Alpine Linux Expert** | Especialista en Alpine Linux enfocado en apk, sistemas ligeros y administración mínima de sistemas |
| **m👀Artix Linux Expert** | Especialista en Artix Linux enfocado en pacman, mantenimiento de versión móvil y flujos de trabajo OpenRC |
| **CentOS Linux Expert** | Especialista en CentOS (Stream/Legacy) enfocado en administración compatible con RHEL y flujos de trabajo yum/dnf |
| **Debian Linux Expert** | Especialista en Debian enfocado en administración de sistemas estable y gestión de paquetes basada en apt |
| **Fedora Linux Expert** | Especialista en Fedora (familia Red Hat) enfocado en dnf, SELinux y flujos de trabajo basados en systemd |
| **m👀Gentoo Linux Expert** | Especialista en Gentoo enfocado en portage, compilación desde fuente y USE flags |

### ♿ Agentes de Accesibilidad y Calidad
| Agente | Propósito |
|--------|-----------|
| **Accessibility Expert** | Asistente experto para accesibilidad web (WCAG 2.1/2.2), UX inclusiva y pruebas de a11y |

### 📋 Agentes de Planificación y Estrategia
| Agente | Propósito |
|--------|-----------|
| **Plan Mode - Strategic Planning & Architecture** | Asistente de planificación y arquitectura estratégica enfocado en análisis reflexivo antes de la implementación |
| **Planning mode** | Generar un plan de implementación para nuevas características o refactorización de código existente |

Cada agente está diseñado para ayudarte a producir rápidamente resultados profesionales con configuración mínima.

## 📚 Aprender Más

- **[Tutorial de Inicio Rápido](docs/quick-start-tutorial.md)** - Guía paso a paso para entender y usar agentes de Copilot
- **[Guía Detallada de Agentes](docs/README.m00agents.md)** - Documentación exhaustiva sobre agentes personalizados y cómo crear los tuyos
- **[Plantilla de Agente](agents/starter-template.md)** - Plantilla de referencia para construir tus propios agentes personalizados

## 🎓 Acerca de Agentes Personalizados

Los agentes personalizados son personas de IA especializadas que puedes crear para mejorar Copilot para flujos de trabajo específicos. Puedes:

- Definirlos a nivel de **usuario** (todos tus proyectos)
- Definirlos a nivel de **repositorio** (un proyecto específico)
- Definirlos a nivel de **organización** (para equipos)

Aprende más en la [documentación oficial de GitHub Copilot](https://docs.github.com/en/copilot/customizing-copilot).

## 📖 Estructura del Repositorio

```plaintext
m00agents/
├── agents/              # Agentes personalizados de Copilot (.agent.md files)
├── skills/              # Habilidades para capacidades mejoradas de Copilot (¡nuevo!)
├── docs/                # Guías y tutoriales
├── assets/              # Iconos y activos visuales
├── instructions/        # Directrices del proyecto
└── README.md            # Este archivo
```

**Novedad:** El directorio `skills/` contiene módulos de habilidades adicionales para ampliar las capacidades de Copilot más allá de los agentes base.

## 🔗 Créditos e Inspiración

Este proyecto fue inspirado por:

- 📖 [How to write a great agents.md](https://github.blog/ai-and-ml/github-copilot/how-to-write-a-great-agents-md-lessons-from-over-2500-repositories/) por Matt Nigh - Lectura esencial para creadores de agentes
- ⭐ [Awesome GitHub Copilot](https://github.com/github/awesome-copilot) - Colección comunitaria de recursos de Copilot

## ℹ️ Descargo de Responsabilidad

Los agentes en este repositorio son ejemplos creados para aprendizaje y experimentación. GitHub no verifica, respalda ni garantiza su funcionalidad o seguridad. Siempre inspecciona los agentes y su documentación antes de usarlos.

---

<div align="center">

**Hecho con ❤️ y Copilot**

![Copilot Icon](assets/icons8-github-copilot-48.png)

</div>

*Traducido usando GitHub Copilot y GPT-4o.*
