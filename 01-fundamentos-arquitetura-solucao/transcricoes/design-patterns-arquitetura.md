# Design Patterns de Arquitetura de Solução

## N-tier / N-layer

N-tier/N-layer é um padrão de arquitetura que divide uma aplicação em camadas lógicas ou físicas distintas, onde cada camada tem responsabilidades específicas e se comunica apenas com camadas adjacentes.

- Presentation
- Application
- Data

## Multi-tenant

Um único sistema que pode ser utilizado por vários tipos de usuário. Muito comum quando temos sistemas tipo SaaS. Podemos separar os dados de diferentes clientes em bancos de dados diferentes.

O mais comum é ter tabelas com chaves primárias compostas, onde é possível dar um "select" utilizando um "where" que seja daquele cliente específico.

É possível que algum cliente muito grande (ex Coca-Cola) tenha compliance que não permita que dados de outros clientes estejam em seu banco de dados, e que tenhamos uma regra específica para este cliente acabar acessando um banco de dados específico ao invés de ser separado por chaves primárias.

## Stateless vs Stateful

- **Stateful**: São aplicações que armazenam dados do usuário em um servidor
- **Stateless**: Aplicações que não guardam estado. Neste caso, a sessão pode ficar em um Redis ou Banco de Dados. Os Assets podem ficar num Amazon S3. Os logs podem ficar armazenados em um Crashlytics da vida. AGS = Auto Scaling Group

## Serverless

Uma aplicação Serverless é paga somente quando é utilizada, funciona 24/7. Engloba vários tipos de serviços.

Serverless é um modelo de computação em nuvem onde o provedor gerencia automaticamente a infraestrutura, permitindo que desenvolvedores foquem apenas no código. As principais características são:

- Execução baseada em eventos
- Cobrança por uso real (pay-per-use)
- Escalabilidade automática
- Sem necessidade de gerenciar servidores

Exemplos incluem AWS Lambda, Azure Functions e Google Cloud Functions.

**Limitações:**
- Cold starts
- Tempo máximo de execução
- Vendor lock-in
- Complexidade no debugging

É ideal para cargas de trabalho variáveis e microserviços, mas pode não ser adequado para aplicações que exigem baixa latência ou processamento contínuo.

## Microsserviços

São sistemas com funcionalidades específicas. Um microsserviço pode depender diretamente de outro, mas o correto é fazer com que eles não sejam acoplados para não gerar um efeito dominó quando um dos microsserviços está indisponível.

### Como evitar esse tipo de acoplamento?

Ter bancos de dados independentes e trabalhar de maneira assíncrona, comunicando-se com o "broker". Neste caso, o funcionamento de um MS não impacta o outro.

**Vantagens dos Microsserviços vs Monolito:**
- Principal motivação: Organizacional. Equipes. Uma equipe que cuida de um Microsserviço não vai impactar a outra
- Escalabilidade
- Separação de responsabilidades
- Diferentes tecnologias
- Baixo acoplamento

### Microsserviços vs Complexidades

- Maturidade da organização
- Maturidade dos times
- Deployment
- Observabilidade
- Troubleshooting

## CQRS (Command Query Responsibility Segregation)

CQRS separa operações de leitura (Queries) e escrita (Commands) em modelos diferentes.

Para uma gravação de dados, normalmente você vai precisar passar por mais regras de domínio do que se estivesse fazendo apenas uma consulta. Você pode ter um banco de dados de escrita e outro de leitura — o mais importante nesse caso é a performance.

**Command Stack:**
- Alteram estado
- Validam regras de negócio
- São assíncronos
- Otimizados para escrita

**Query Stack:**
- Apenas leem dados
- Não alteram estado
- São síncronos
- Otimizados para leitura

**Benefícios:**
- Performance otimizada
- Escalabilidade independente
- Melhor adequação a diferentes casos de uso

**Desafios:**
- Complexidade aumentada
- Consistência eventual
- Manutenção de dois modelos

Ideal para sistemas complexos com muitas leituras, mas pode ser overhead para aplicações simples.

## Caching

**Estratégias de invalidação:**
- **Time-based invalidation**: Limpa o cache depois de um tempo específico
- **Least Recently Used (LRU)**: O cache persiste para os dados mais novos
- **Most Recently Used (MRU)**: Joga fora a versão mais recente do dado, substituindo por uma mais recente ainda
- **Least Frequently Used (LFU)**: Joga fora a versão que tem menos acessos
- **TTL-based invalidation**
- **Write-through invalidation**: Sempre quando há alteração no disco, o cache é atualizado junto. Funciona bem quando o sistema não tem muita escrita
- **Write-back invalidation**: Pouco utilizado. Quando há alteração, o cache primeiramente é atualizado e depois o dado em disco é atualizado. Muitas vezes o dado em disco é atualizado quando o cache já está para expirar de alguma forma

## Distributed Locking

Serve para evitar problemas de concorrência. Bloqueia operação para evitar que dois sistemas façam a mesma requisição.

- Consistência de dados
- Contenção de recursos
- Evita dead locks
- Garante mais eficiência dos recursos
- **Ferramentas**: Apache Zookeeper, ETCD, Redis (favorito), Consul

## Configuration

- Configurações de uma aplicação mudam a qualquer momento
- Como mudar uma senha de banco de dados, credenciais de email, etc… Sem ter que reiniciar totalmente a aplicação ou refazer o deploy?

## Secret Management

- Credenciais não podem ficar "voando" na empresa
- Processos para rotacionar credenciais são importantes
- Serviços gerenciados e soluções ajudam nessa tarefa:
  - **Hashicorp Vault**
  - **AWS Secret Manager**
    - Armazenamento de secrets
    - Faz rotacionamento automático de secrets nos serviços como RDS
    - SDK para recuperação dos secrets em tempo de execução

## Circuit Breaker

O Circuit Breaker é um padrão de design que previne falhas em cascata em sistemas distribuídos, funcionando de forma similar a um disjuntor elétrico.

**Estados do Circuit Breaker:**

1. **CLOSED (Fechado)**
   - Estado normal de operação
   - Requisições passam normalmente
   - Monitora falhas

2. **OPEN (Aberto)**
   - Ativado quando número de falhas excede limite
   - Rejeita requisições imediatamente
   - Previne sobrecarga do sistema
   - Tem timeout para tentar recuperação

3. **HALF-OPEN (Semi-aberto)**
   - Estado intermediário após timeout
   - Permite algumas requisições para testar
   - Decide se volta ao CLOSED ou OPEN

**Principais benefícios:**
- Falha rápida (fail-fast)
- Previne sobrecarga de recursos
- Permite recuperação gradual
- Melhora resiliência do sistema

## Sequencing

Sequencing é um padrão para ordenar execução de operações em sistemas distribuídos.

**Implementações comuns:**
1. Auto-incremento em banco de dados
2. Serviço centralizado de sequência
3. Timestamps com algoritmos como Lamport ou vetores de versão

**Usos:**
- Ordenação de transações
- Controle de concorrência
- Geração de IDs únicos
- Consistência em mensageria

**Desafios:**
- Gargalo de performance
- Single point of failure
- Sincronização de relógios
- Escalabilidade

## API Gateway

- Centralização de requisições
- Roteamento
- Autenticação
- Conversão de dados
- Cabeçalhos
- Throttling
- Rate Limit

## Event Driven Architecture

- Eventos acontecem no passado
  - **Event Notification** (Não são importantes, apenas notificações dispensáveis)
  - **Event Carried State Transfer** (Eventos com informações importantes e que não podem ser perdidos)
  - **Event Sourcing** (Grava todas as mudanças de estado da sua aplicação, sendo possível reproduzir tudo o que você fez)
- Um evento emitido pode ser o gatilho de entrada para outro sistema
- Coreografia vs Orquestração

## Pub-Sub (Public-Subscribe)

É um sistema de observable sobre um Topic. O Sistema A manda mensagem para o Topic, que é lido pelo sistema B, C e D. Na prática são producers e consumers.

## BFF — Backend for Frontend

Criar um Backend para o Frontend, que fornece somente informações que serão utilizadas pelo frontend. A quantidade de informações para cada plataforma é diferente. O GraphQL consegue seguir a mesma ideia.

## Sidecars Applications

- Aplicação auxiliar na aplicação principal
- Coleta de logs
- mTLS

## Service Mesh

"Uma malha de serviço é uma camada de infraestrutura dedicada que você pode adicionar às suas aplicações. Ele permite adicionar recursos de forma transparente, como observabilidade, gerenciamento de tráfego e segurança, sem adicioná-los ao seu próprio código."

- **Istio**
  - Gerenciamento de Tráfego
  - Segurança
  - Policy Enforcement
  - Observabilidade
  - Extensibilidade (Circuit Breaker)
