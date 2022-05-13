## Project Reactor

## Programação reativa

- assíncrona e não bloqueante (nonBlocking).
- baseado a eventos/mensagens
- Tudo é _data stream_
- Backpressure
- Programação funcional/declarativa

### Reactive streams

Componentes da reactive streams API
  - Publisher
  - Subscriber
  - Subscription
  - Processor

## O que é Project Reactor

É uma biblioteca reativa para construção de aplicações não-bloqueantes na JVM. O project reactor é a base da stack da programação reativa no ecossistema Spring. O Project reactor implementa as interfaces do __reactive streams api_.

Um sistema reativo prega os seguintes conceitos:

1. **Responsivo** - capacidade de responder no menor tempo possível.
2. **Resiliente** - em caso de falhas o sistema como um todo deve continuar respondendo e se recuperar.
3. **Elástico** - capacidade de escalar conforme a demanda, seja ela aumentando ou diminuindo, é excelente para economia e melhor performance da aplicação.
4. **Orientado a mensagens** - comunicação com outros serviços via mensagens assíncronas

Temos algumas interfaces importantes quando falamos sobre programação reativa.

**Publisher** - Um publisher é um provedor de um número de elementos, que irá prover os dados para um ou mais *Subscribers*.

**Subscriber** - Um subscriber escuta publicadores, pedindo novos dados. Ele pode ser conhecido também como *Consumer*.

**Backpressure** - É uma forma de lidar com o fluxo de dados que pode ser muito grande para processar de forma confiável.


#### **Conceitos**
**Não reativo**
Síncrona e Bloqueante

**Reativo**
Assincrona e não bloqueante

#### Tipos de Publishers

**Mono** - Se eu quiser buscar apenas um usuário no banco, eu utilizo este tipo. (0 ou 1)


**Flux** - Se eu quiser trazer uma lista de usuários eu preciso trazer no tipo Flux, pois eu espero 0 ou N.


## Por que usar Spring WebFlux

Spring WebFlux possui mais eficiência para aproveitamento de CPU e recursos de rede, provendo maior escalabilidade arquitetural e maior experiência de resposta com o usuário.

## Paradigmas

O Spring WebFlux possuí 2 paradigmas para criação:

- **Annotation baseado em spring controllers (Similar ao SpringMVC)**
- **Endpoints funcionais**
