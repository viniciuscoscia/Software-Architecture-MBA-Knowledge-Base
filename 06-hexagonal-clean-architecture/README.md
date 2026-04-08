# Arquitetura Hexagonal & Clean Architecture

**Progresso:** 47% 🔄

> Módulo em andamento. Conteúdo será exportado conforme o curso avançar.

## Conceitos a cobrir

### Arquitetura Hexagonal (Ports & Adapters)
- Ports (interfaces) vs Adapters (implementações)
- Domain isolado de infraestrutura
- Facilita testes — adapters podem ser substituídos por mocks

### Clean Architecture (Robert C. Martin)
- Dependency Rule — dependências sempre apontam para dentro
- Entities → Use Cases → Interface Adapters → Frameworks & Drivers
- Independente de frameworks, UI, banco de dados

## Conexão com experiência mobile

Você já usa Clean Architecture no Android (domain → data → presentation). A Arquitetura Hexagonal é o mesmo conceito — os "ports" são as interfaces do seu `domain`, os "adapters" são as implementações em `data`.
