# Prometheus e grafana

### Importancia dos logs

    Os log são essenciais hoje em dia porque as aplicações estão cada vez mais sofisticadas e mais distribuídas.

- a partir dos logs que você consegue monitorar as aplicações
- Log parece coisa chata
- Logs nunca foram tão importantes quanto nos dias de hoje
    -   Corrigir bugs, rastrear
    -   Monitorar as aplicações (o sistema caiu existe algum log mostrando o motivo)
    -   Insights técnicos e de negócios (você começa verificar onde deve performar mais, onde seu sistema está precisando de mais recursos)
    -   Alertar (avisam quando qualquer métrica sair do lugar)
- Quem não mede não gerencia

### Logs e sua carreira

Quando você tem um log você consegue ter uma visão de tudo que acontece na sua aplicação mesmo sem você ter que ficar olhando, um dos grandes requisitos hoje para os profissionais de tecnologia é conhecer de logs ou pelo menos entender de logs, e definir métricas importantes, é o famoso profissional 'Data Driven', um profissional movido a dados, consegue tomar decisões e tirar insights dos dados e esses dados são os logs e os monitoramentos das aplicações

### Prometheus

<center><img src="https://miro.medium.com/max/1400/0*csYPaelLV7aKGtjj.png">

Temos a ferramenta (Prometheus) que faz um pull via http na sua aplicação pegando metricas e monitorando, ele acessa a url _/metrics_ que serve o prometheus igualmente a gente fazia com o actuator e o spring boot admin, sempre que ver o /metrics pode saber que por convensão ele ta servindo um serviço do prometheus - isso da uma liberdade de escolher o que realmente é importante e o que você vai precisar como logs como por exemplo: 
    * Quantidade de compras
    * Tempo de resposta no processo de compras
    * Quantos usuários acessam nossa aplicação
    
Você pode fazer a configuração do tempo que o prometheus faz essas requisições.

    -   Uma ferramenta de monitoramento de alerta de sistema open source
    -   Criado pela SoundCloud
    -   Atualmente é mantido de forma independente
    -   Hoje faz parte da Cloud _native computing foundation_

##### Conceitos iniciais de PULL vs PUSH

* PULL

    A aplicação tem um agent, que normalmente fica instalado na aplicação, no cluster ou em algum lugar estratégico, e ele começa dar um push, das métricas, para o serviço de monitoramento.
    > Ex.: Elastic search, new relic

* PUSH

    O serviço monitor que busca a informação na aplicação, faz um pull na aplicação, neste caso não precisaremos de _agent_ instalado.
    > Ex.: Prometheus
