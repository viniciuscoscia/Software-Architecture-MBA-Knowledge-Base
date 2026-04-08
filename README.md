# MBA Full Cycle — Knowledge Base

Repositório de anotações e resumos do MBA em Arquitetura de Software da Full Cycle.

## Progresso dos Módulos

| # | Módulo | Progresso | Status |
|---|--------|-----------|--------|
| 01 | [Fundamentos de Arquitetura de Solução](./01-fundamentos-arquitetura-solucao/) | 100% | ✅ Concluído |
| 02 | [System Design e Design Docs](./02-system-design/) | 100% | ✅ Concluído |
| 03 | [Fundamentos de Arquitetura de Software](./03-fundamentos-arquitetura-software/) | 98% | 🔄 Em andamento |
| 04 | [SOLID e Design Patterns](./04-solid-design-patterns/) | 100% | ✅ Concluído |
| 05 | [DDD (Domain Driven Design)](./05-ddd/) | 52% | 🔄 Em andamento |
| 06 | [Arquitetura Hexagonal & Clean Architecture](./06-hexagonal-clean-architecture/) | 47% | 🔄 Em andamento |
| 07 | [Microsserviços e Arquitetura baseada a eventos](./07-microsservicos-eda/) | 100% | ✅ Concluído |
| 08 | [Docker & Kubernetes](./08-docker-kubernetes/) | 24% | 🔄 Em andamento |
| 09 | [Prompt Engineering para Devs](./09-prompt-engineering/) | — | 🎁 Bônus |
| 10 | [Encontros Ao Vivo](./10-encontros-ao-vivo/) | — | 📅 Contínuo |

## Estrutura de cada módulo

```
XX-nome-do-modulo/
├── README.md          # Índice do módulo + objetivos + conceitos-chave
├── transcricoes/      # Transcrições brutas das aulas (referência)
│   └── nome-da-aula.md
└── resumos/           # Resumos estruturados gerados com Claude Code
    └── nome-da-aula.md
```

## Como usar este repositório com Claude Code

```bash
# Gerar resumo de uma transcrição
# Abra o Claude Code na raiz do projeto e peça:
# "Leia a transcrição em 07-microsservicos-eda/transcricoes/introducao.md
#  e gere um resumo estruturado em 07-microsservicos-eda/resumos/introducao.md"
```

## Referências externas

- [Building Microservices — Sam Newman](https://www.oreilly.com/library/view/building-microservices-2nd/9781492034018/)
- [Domain-Driven Design — Eric Evans](https://www.domainlanguage.com/ddd/)
- [The Twelve-Factor App](https://12factor.net/)
- [Clean Architecture — Robert C. Martin](https://www.oreilly.com/library/view/clean-architecture-a/9780134494272/)

## Setup

Este repositório é usado com **Claude Code** como tutor interativo.
Os arquivos de transcrição são a fonte primária; os resumos são gerados via Claude Code e podem ser exportados para o NotebookLM.
