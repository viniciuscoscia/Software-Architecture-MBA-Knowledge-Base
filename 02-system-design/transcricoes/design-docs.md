# Design Docs

São documentos relativamente informais que o autor principal ou autores de um sistema de software ou aplicativo criam antes de embarcar no projeto de codificação.

O documento de design documenta a estratégia de implementação de alto nível e as principais decisões de design com ênfase nas compensações que foram consideradas durante essas decisões.

Documento feito pelo time com o objetivo de tornar claro e compartilhável todo o processo de desenvolvimento de uma solução. É documentado o racional da solução adotada, alternativas, objetivos, arquitetura entre outros pontos.

## Objetivos

- A identificação precoce de problemas de design ao fazer alterações ainda é barata.
- Alcançar consenso em torno de um projeto na organização.
- Assegurar a consideração de preocupações transversais
- Escalar o conhecimento dos engenheiros seniores na organização
- Forme a base de uma memória organizacional em torno das decisões de design
- Atua como um artefato resumido no portifólio técnico do(s) designer(es) de software

# Exemplo de Estrutura de Design Doc

## Cabeçalhos

Contém o nome das pessoas autoras do documento, nome das pessoas que revisaram o documento, o estado atual do documento (rascunho, em revisão, proposto, aprovado, rejeitado), datas de criação.

**Dicas:**
- Não deixe de atualizar o estado do documento
- Envolva e peça revisão para pessoas com maior senioridade de áreas relevantes (segurança, infraestrutura, plataforma, etc) ou times envolvidos e impactados
- Adicionar rótulos (tags) podem ajudar na busca e classificação

**Exemplo:**

> **Design Doc:** Sistema de Gerenciamento de Tarefas
> **Autores:** João Silva, Maria Souza
> **Revisores:** Pedro Santos, Ana Oliveira
> **Data de criação:** 2022-08-15
> **Status:** Proposto
> **Tags:** Design Doc, Gerenciamento de Tarefas

## Visão Geral

Texto breve e de alto nível sobre o que este documento se trata. Visa trazer o que esperar na leitura do documento.

**Dicas:**
- Tipicamente será um parágrafo ou no máximo dois
- Não deve conter detalhes
- Alguém sem contexto deve conseguir entender

**Exemplo:**
> Este Design Doc apresenta a criação de um novo backend for frontend para um sistema de vendas online que agora irá oferecer um aplicativo móvel.

## Escopo e Contexto

Descreve o cenário o qual o sistema está inserido, os motivadores da escrita do documento e outras informações para entendimento do contexto onde o problema está inserido (tipicamente contém informações de tecnologia atual, dívidas técnicas, etc).

**Dicas:**
- Seja sucinto!
- Não coloque objetivos e soluções propostas
- Encare como um plano de fundo

## Objetivos e Fora de Escopo

- **Objetivos**: requisitos de negócio ou técnicos que serão alcançados
- **Fora de escopo**: pontos que **não** serão contemplados

**Dicas:**
- Dê preferência a objetivos metrificáveis
- Em "Fora de Escopo" não negue apenas os objetivos
- Seja sucinto, porém objetivo. Ao invés de escrever "Reduzir custos" escreva "Reduzir custos através da redução do tráfego"

## O Design

- Dado o contexto (fatos), objetivos e não objetivos (requisitos), mostre por que uma determinada solução atende melhor a esses objetivos
- Comece por dar uma visão geral e depois entre em detalhes
- Pode conter diagramas, API design, dados que serão manipulados, e se necessário, pseudocódigos
- Dê foco nas compensações para produzir um documento útil com valor a longo prazo

**Dicas:**
- Utilize fatos e dados para trazerem valor ao seu design
- Evite copiar e colar todo um schema ou API
- Elementos visuais são complementares e não substitutos de explicações

## Alternativas consideradas

Os sistemas ou soluções alternativas que foram consideradas para a resolução do problema, explicando compensações e motivações da escolha.

**Dicas:**
- Uma alternativa sempre a ser considerada é **não fazer nada**
- O foco deve estar nas compensações que cada design faz
- Seja sucinto, mas destaque por que a solução escolhida é a melhor opção

## Preocupações Transversais

Descreva o que pode impactar outras pessoas. Pode ser uma preocupação de segurança, quebra de compatibilidade de API, aumento de fluxo em outros sistemas ou questões relacionadas a infraestrutura.

## Outros

### Testabilidade e Observabilidade
Descreva como a solução será testada e como métricas serão criadas para garantir o atingimento do sucesso.

### Plano de Implantação
Segmentação das entregas e passos necessários para entrega de valor da solução.

### Perguntas em aberto
Pontos que ainda não foram definidos ou ainda não são conhecidos.

## Ferramentas

- **Confluence** — Wiki corporativo, integração com Jira e Bitbucket
- **Google Docs** — Edição colaborativa em tempo real
- **GitHub** — Markdown, versionamento, edição colaborativa
- **PlantUML** — Diagramas de sequência, C4, casos de uso
- **Web Sequence** — Diagramas de sequência de maneira textual
- **Structurizr** — "Diagramas como código", vários diagramas a partir de um único modelo

## Ciclo de Vida do Design Doc

Rascunho → Em Revisão → Proposto → Aprovado / Rejeitado

## Quando NÃO fazer um Design Doc

- **A cultura organizacional é patológica** — Há pouco benefício em escrever documentos sem alternativas, compensações e explicações
- **A sobrecarga no processo é um problema** — Sem o entendimento dos benefícios, pode gerar ruído
- **Quando não há complexidade** — Quando a complexidade da tarefa é inferior à compensação da escrita de um documento
