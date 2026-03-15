# m👀agents

<div align="center">

[![Made with ❤️ by Copilot](https://img.shields.io/badge/Made%20with%20%E2%9D%A4%EF%B8%8F%20by-Copilot-ff69b4?style=flat-square)](https://github.com/github/copilot-docs)
![Beginner Friendly](https://img.shields.io/badge/Beginner-Friendly-brightgreen?style=flat-square)

**Uma coleção de agentes personalizados do GitHub Copilot amigáveis para iniciantes para começar com desenvolvimento auxiliado por IA.**

</div>

## 🎯 O que é m👀agents?

m👀agents é um kit de ferramentas iniciais de agentes personalizados projetados para desenvolvedores novos no GitHub Copilot. Fornece agentes prontos para usar que aumentam as capacidades do Copilot para tarefas comuns, como criar documentação e modelos de código.

Quer você esteja explorando agentes personalizados pela primeira vez ou construindo sobre habilidades existentes, esta coleção demonstra como criar e usar personas de IA especializadas em seu fluxo de trabalho.

## 🚀 Guia de Início Rápido

### Obtenha os Agentes

**Opção 1: Clone para experimentação local**
```bash
git clone https://github.com/m00sp/m00agents.git
cd m00agents
```

**Opção 2: Faça um fork em sua conta do GitHub**
```bash
# Visite: https://github.com/m00sp/m00agents/fork
# Em seguida, clone seu fork
git clone https://github.com/YOUR-USERNAME/m00agents.git
cd m00agents
```

### Instale os Agentes Localmente

Copie os agentes para sua configuração local do Copilot:

```bash
# Copiar para agentes no nível do usuário (disponíveis em todos os projetos)
cp agents/*.agent.md ~/.copilot/agents/
```

Ou para uso específico do repositório:
```bash
# Copiar para agentes no nível do repositório (disponíveis apenas neste projeto)
mkdir -p .github/agents
cp agents/*.agent.md .github/agents/
```

### Use um Agente no Copilot CLI

```bash
# Listar agentes disponíveis
copilot /agent

# Ou especificar um agente diretamente
copilot --agent=docs-creator --prompt "Create documentation for..."
copilot --agent=readme-creator --prompt "Generate a README..."
```

## 📦 Agentes Disponíveis

Este repositório inclui agentes especializados organizados por domínio:

### 📝 Agentes de Documentação
| Agente | Propósito |
|--------|----------|
| **m👀readme-creator** | Cria e melhora arquivos README com estrutura clara, guias de instalação e visão geral do projeto |
| **docs-creator** | Gera documentação técnica clara e amigável |

### 💻 Agentes de Engenharia de Software
| Agente | Propósito |
|--------|----------|
| **C++ Expert** | Fornece orientação especializada em engenharia de software C++ usando C++ moderno e práticas recomendadas da indústria |
| **m👀Rust Expert for Beginners** | Orientação especializada em Rust para iniciantes, enfatizando propriedade, segurança e padrões idiomáticos |
| **Custom Agent Foundry** | Especialista em projetar, criar e melhorar agentes personalizados com configurações ideais |

### 🐧 Agentes de Administração de Sistemas Linux
| Agente | Propósito |
|--------|----------|
| **Arch Linux Expert** | Especialista em Arch Linux focado em pacman, manutenção de versão móvel e administração de sistemas |
| **m👀Alpine Linux Expert** | Especialista em Alpine Linux focado em apk, sistemas leves e administração mínima de sistemas |
| **m👀Artix Linux Expert** | Especialista em Artix Linux focado em pacman, manutenção de versão móvel e fluxos de trabalho OpenRC |
| **CentOS Linux Expert** | Especialista em CentOS (Stream/Legacy) focado em administração compatível com RHEL e fluxos de trabalho yum/dnf |
| **Debian Linux Expert** | Especialista em Debian focado em administração de sistemas estável e gerenciamento de pacotes baseado em apt |
| **Fedora Linux Expert** | Especialista em Fedora (família Red Hat) focado em dnf, SELinux e fluxos de trabalho baseados em systemd |
| **m👀Gentoo Linux Expert** | Especialista em Gentoo focado em portage, compilação a partir da fonte e USE flags |

### ♿ Agentes de Acessibilidade e Qualidade
| Agente | Propósito |
|--------|----------|
| **Accessibility Expert** | Assistente especializado para acessibilidade na web (WCAG 2.1/2.2), UX inclusiva e testes de a11y |

### 📋 Agentes de Planejamento e Estratégia
| Agente | Propósito |
|--------|----------|
| **Plan Mode - Strategic Planning & Architecture** | Assistente de planejamento e arquitetura estratégica focado em análise reflexiva antes da implementação |
| **Planning mode** | Gerar um plano de implementação para novos recursos ou refatoração de código existente |

Cada agente é adaptado para ajudá-lo a produzir rapidamente resultados profissionais com configuração mínima.

## 📚 Saiba Mais

- **[Tutorial de Início Rápido](docs/quick-start-tutorial.md)** - Guia passo a passo para entender e usar agentes do Copilot
- **[Guia Detalhado de Agentes](docs/README.m00agents.md)** - Documentação detalhada sobre agentes personalizados e como criar os seus
- **[Modelo de Agente](agents/starter-template.md)** - Modelo de referência para construir seus próprios agentes personalizados

## 🎓 Sobre Agentes Personalizados

Agentes personalizados são personas de IA especializadas que você pode criar para melhorar o Copilot para fluxos de trabalho específicos. Você pode:

- Defini-los no nível de **usuário** (todos os seus projetos)
- Defini-los no nível de **repositório** (um projeto específico)
- Defini-los no nível de **organização** (para equipes)

Saiba mais na [documentação oficial do GitHub Copilot](https://docs.github.com/en/copilot/customizing-copilot).

## 📖 Estrutura do Repositório

```plaintext
m00agents/
├── agents/              # Agentes personalizados do Copilot (arquivos .agent.md)
├── skills/              # Habilidades para capacidades aprimoradas do Copilot (novo!)
├── docs/                # Guias e tutoriais
├── assets/              # Ícones e ativos visuais
├── instructions/        # Diretrizes do projeto
└── README.md            # Este arquivo
```

**Novidade:** O diretório `skills/` contém módulos de habilidades adicionais para estender os recursos do Copilot além dos agentes base.

## 🔗 Créditos e Inspiração

Este projeto foi inspirado por:

- 📖 [How to write a great agents.md](https://github.blog/ai-and-ml/github-copilot/how-to-write-a-great-agents-md-lessons-from-over-2500-repositories/) por Matt Nigh - Leitura essencial para criadores de agentes
- ⭐ [Awesome GitHub Copilot](https://github.com/github/awesome-copilot) - Coleção comunitária de recursos do Copilot

## ℹ️ Aviso Legal

Os agentes neste repositório são exemplos criados para aprendizado e experimentação. O GitHub não verifica, endossa nem garante sua funcionalidade ou segurança. Sempre inspecione os agentes e sua documentação antes de usá-los.

---

<div align="center">

**Feito com ❤️ e Copilot**

![Copilot Icon](assets/icons8-github-copilot-48.png)

</div>

*Traduzido usando GitHub Copilot e GPT-4o.*
