# Instalando prometheus

Primeiro, precisaremos do __spring boot actuator__ um subprojeto do Spring boot, que fornece recursos de monitoramento, auditoria e _healthcheck_ entre outras propriedades, sem que o desenvolvedor precise configurar.

#### Reference:
[Jean Morais - Medium](https://medium.com/@jeanmorais/monitorando-aplica%C3%A7%C3%B5es-spring-boot-de-forma-escal%C3%A1vel-no-kubernetes-com-prometheus-operator-e-326f63bb5b00)

#### Adicionando Actuator no projeto

1. Primeiro passo a ser realizado é a inclusão da dependência no `pom.xml` do projeto a ser monitorado.

```sh
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-actuator</artifactId>
</dependency>
```

Ele habilita alguns endpoints por _default_, onde é possível consumir algumas informações. Alguns exemplos de endpoints disponibilizados pelo Actuator:
* __/env__ - retorna as variáveis de ambiente;
* __/metrics__ - métricas detalhadas da aplicação
* __/loggers__ - consultar e modificar nível de log da aplicação
* __/health__ - resumo da saúde da aplicação

> é possível habilitar e desabilitar estes endpoints atraés do arquivo de configuração da aplicação, no nosso caso o properties

#### Adicionando Micrometer no projeto

O Micrometer fornece uma camada para exibição de métricas baseada em bibliotecas clientes dos mais populares sistemas de monitoramento. Através de poucas configurações, é possível selecionar um ou vários sistemas de monitoramento para exportar as métricas de sua aplicação: Prometheus, New Relic, Atlas e Datadog são alguns deles.

```sh
<dependency>
    <groupId>io.micrometer</groupId>
    <artifactId>micrometer-registry-prometheus</artifactId>
</dependency>
```

##### habilitar os endpoints para exibição das métricas

```yml
management:
  endpoints:
    web:
      exposure:
        include: '*'
  metrics:
    export:
      prometheus:
        enabled: true
  endpoint:
    metrics:
      enabled: false
    prometheus:
      enabled: true
```

Se tudo foi configurado corretamente deve ser possível chamar o endpoint _/actuator/prometheus_
