# Observability

Na teoria de controle, a observabilidade é definida como uma medida de quão bem os estados internos de um sistema podem ser inferidos a partir do conhecimento das saídas externas desse sistema. Simplificando, observabilidade é o quão bem você pode entender seu sistema complexo.

- Monitoramento nos mostra o que há de errado
- Monitoramento se baseia em saber com antecedência quais sinais você deseja monitorar
- Observabilidade nos permite perguntar o **porquê**

## Ferramentas Populares

- **Elastic Stack** (Grátis / Open Source) - Meio complicado, cada serviço é um servidor
- **Datadog** - Ótima ferramenta
- **New Relic** - Muito boa também
- **Splunk** - Busca por logs
- **Dynatrace**
- **Prometheus / Grafana** - Open Source, com diversas ferramentas de monitoramento, triggers de eventos, dashboards criados pela comunidade. Estudar mais sobre!
- **Jaeger** - Focado em microsserviços
- **Zipkin**
- **Kiali** - Usado em sistemas de Service Mesh

## OTEL (Open Telemetry)

Nova tecnologia, extremamente promissor, segue padrões, especificações e tem vários SDKs disponíveis para diferentes linguagens.

- CNCF Project
- Baseado no Open Tracing e Open Census
- Baseado em:
  - Especificações
  - Protocolos
  - SDKs
  - Ferramentas de Integração
