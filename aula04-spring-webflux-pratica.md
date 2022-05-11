## Desenvolvendo na prática


#### Primeiro Passo

Crie o projeto utilizando o **[Spring Initializr](https://start.spring.io/)**.

1. Adicione a dependência do *"Reactive Web"*

#### Segundo Passo

Criar um simples POJO.

```sh

public class Mensageiro {
    private String msg;
    // Constructors, getters and setters
}

```

#### Terceiro Passo

Definir um simples método REST

```sh

@RestController
public class MensageriaController {
    @GetMapping("/mensageria")
    public Publisher<Mensageiro> getMensagem() {
        Flux<Mensageiro> mensagemFlux = Flux.<Mensageiro>generate(sink -> sink.next(new Mensageiro("Olá, boa noite!"))).take(50);
        return mensagemFlux;
    }
}

```

- No Flux.generate() vai criar e nunca terminar o stream do objeto de Mensagem.

- O método take(), como o nome é bem sugestivo, ele vai somente pegar 50 valores do stream.

#### Quarto Passo

Agora vamos testar o endpoint, iremos acessar o endpoint http://localhost:8080/mensageiro


#### Dúvida

Fizemos o processo para exibir 50 mensagens, mas isso não seria resolvido apenas com um único List<>?

#### Referência
[Spring reactor](https://stackabuse.com/spring-reactor-tutorial/)
[Programação Reativa](https://medium.com/nstech/programa%C3%A7%C3%A3o-reativa-com-spring-boot-webflux-e-mongodb-chega-de-sofrer-f92fb64517c3)