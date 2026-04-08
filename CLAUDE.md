# MBA Knowledge Base — Instruções para Claude Code

Este repositório contém anotações e transcrições do MBA em Arquitetura de Software (Full Cycle).

## Quem é o Vini

Senior Mobile Engineer (7+ anos Android/iOS), trabalhando remotamente para TeamUp/PayPal. Está fazendo MBA em Arquitetura de Software na Full Cycle (2025-2026). Iniciante nos tópicos de arquitetura backend/distribuída — experiência forte em mobile (Kotlin, Swift, Clean Architecture, MVI/MVVM).

## Estrutura do Repositório

```
XX-nome-do-modulo/
├── README.md              # Índice do módulo + conceitos-chave
├── transcricoes/          # Transcrições brutas por capítulo (não editar)
│   ├── 1 - Nome do capítulo.md
│   ├── 2 - Nome do capítulo.md
│   └── ...
└── resumos/               # Resumos estruturados gerados com Claude Code
    ├── 1 - Nome do capítulo.md
    └── ...
```

### Convenção de nomenclatura

- **Transcrições**: `N - Nome do Capítulo.md` — numeradas na mesma ordem do curso
- **Resumos**: mesmo nome do arquivo de transcrição correspondente, em `resumos/`
- Módulos com arquivo único legado (`completo.md`) serão migrados para capítulos conforme o uso

## Como trabalhar neste repositório

### Gerar um resumo

1. Leia a transcrição: `XX-modulo/transcricoes/N - Capítulo.md`
2. Gere o resumo estruturado e salve em: `XX-modulo/resumos/N - Capítulo.md`
3. Nunca modifique os arquivos em `transcricoes/`

### Formato dos resumos

- **Conceitos-chave** com definições claras e concisas
- **Trade-offs** — quando usar vs quando não usar
- **Conexões com experiência mobile** — Android/Kotlin/PayPal quando relevante
- **Termos técnicos** em PT e EN (ex: "degradação graciosa / graceful degradation")
- Linguagem direta, sem repetição, sem enrolação

### Exportar para NotebookLM

Os arquivos em `resumos/` são o input principal para o NotebookLM. Quanto mais estruturado e conciso, melhor o resultado dos podcasts e Q&A.

## Módulos

| # | Módulo | Progresso |
|---|--------|-----------|
| 01 | Fundamentos de Arquitetura de Solução | ✅ 100% |
| 02 | System Design e Design Docs | ✅ 100% |
| 03 | Fundamentos de Arquitetura de Software | 🔄 98% |
| 04 | SOLID e Design Patterns | ✅ 100% |
| 05 | DDD (Domain Driven Design) | 🔄 52% |
| 06 | Arquitetura Hexagonal & Clean Architecture | 🔄 47% |
| 07 | Microsserviços e Arquitetura baseada a eventos | ✅ 100% |
| 08 | Docker & Kubernetes | 🔄 24% |
| 09 | Prompt Engineering para Devs | 🎁 Bônus |
| 10 | Encontros Ao Vivo | 📅 Contínuo |

## Preferências

- Responder em **português**
- Direto e técnico, sem enrolação
- Corrigir entendimentos errados — honestidade > validação
- Conectar conceitos com o mundo mobile/Android quando fizer sentido
- Vini é iniciante nos tópicos de backend/distribuída — explicar com clareza sem ser condescendente
