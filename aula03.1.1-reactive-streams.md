# Api de cadastro

#### Primeiro Passo

Crie o projeto utilizando o **[Spring Initializr](https://start.spring.io/)**.

1. Adicione a dependência do *"WEB"*, *"LOMBOK"*, *"JPA"*, *"Java Mail Sender"*

#### Segundo Passo

Criar os objetos de cliente e emailDTO como sugerido.

```java

@Entity
@Data
public class Cliente {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;
    private String name;
    private String cpf;

}

```

```java

@Data
@AllArgsConstructor
public class EmailDTO {
    private String para;
    private String titulo;
    private String conteudo;
}


```

#### Terceiro Passo

Definir um simples método REST

```java

@RestController
@RequestMapping("/clientes")
@RequiredArgsConstructor
public class ClienteController {

    private final ClienteService clienteService;

    @PostMapping
    public ResponseEntity<Void> efetuarCadastro(@RequestBody Cliente novoCliente) {
        clienteService.efetuarCadastro(novoCliente);
        return ResponseEntity.created(null).build();
    }
}
```

#### Quarto Passo

Configurar as credenciais do email no *application.properties* como sugerido

```sh

spring.mail.host=smtp.gmail.com
spring.mail.port=587
spring.mail.protocol=smtp
spring.mail.username=teste.api.03@gmail.com
spring.mail.password=<senha>
spring.mail.properties.mail.smtp.auth=true
spring.mail.properties.mail.smtp.starttls.enable=true
spring.mail.properties.mail.smtp.starttls.required=true
spring.mail.properties.mail.smtp.quitwait=false


```
  
#### Quarto Passo
 
 Crie os services de *Cliente* e de *Email* conforme sugerido
 
 - Cliente service
 
 ```java
 @Service
@RequiredArgsConstructor
public class ClienteService {

    private final ClienteRepository clienteRepository;
    private final EmailService emailService;

    public Cliente efetuarCadastro(Cliente novoCliente) {
        enviarEmailDeConfirmacao();
        enviarEmailDeBoasVindas();
        return clienteRepository.save(novoCliente);
    }

    public List<Cliente> listarTodos() {
        return clienteRepository.findAll();
    }

    private void enviarEmailDeBoasVindas() {
        var para = "teste.api.03@gmail.com";
        var titulo = "Email de BOAS VINDAS";
        var conteudo = "Enviei esse email pela minha api spring EMAIL DE BOAS VINDAS";
        emailService.enviarEmailSincrono(para, titulo, conteudo);
    }

    private void enviarEmailDeConfirmacao() {
        var para = "teste.api.03@gmail.com";
        var titulo = "Email de CONFIRMACAO";
        var conteudo = "Enviei esse email pela minha api spring EMAIL DE CONFIRMACAO";
        emailService.enviarEmailSincrono(para, titulo, conteudo);
    }

}
 ```
 
 - Email service

```java
@Service
@RequiredArgsConstructor
public class EmailService {

    private final JavaMailSender mailSender;

    public void enviarEmailSincrono(String para, String titulo, String conteudo) {
        this.efetuarEnvioDeEmail(new EmailDTO(para, titulo, conteudo));
    }

    public void enviarEmailAsincrono(String para, String titulo, String conteudo) {

        // O PUBLISHER ENVIA O EMAIL PARA O SUBSCRIBER
        SubmissionPublisher<EmailDTO> publisher = new SubmissionPublisher<>();

        publisher.consume(this::efetuarEnvioDeEmail);

        // Enviando para o subscriber o email
        publisher.submit(new EmailDTO(para, titulo, conteudo));

        publisher.close();
    }

    private void efetuarEnvioDeEmail(EmailDTO emailDTO) {
        SimpleMailMessage email = new SimpleMailMessage();
        email.setTo(emailDTO.getPara());
        email.setSubject(emailDTO.getTitulo());
        email.setText(emailDTO.getConteudo());
        mailSender.send(email);
    }
}
```

#### Testes e amostragem

Para testar envie um `POST` para http://localhost:8080/clientes com o seguinte conteúdo

```json
{
    "name":"Joao da silva",
    "cpf": "123456"
}
```

> Uma vez que os dados do email estão mockados não precisamos passar destinatário.

Após isso verifique o tempo de resposta no seu cliente rest, então altere, no cliente service, de:
```java
emailService.enviarEmailSincrono(para, titulo, conteudo);
```
para
```java
emailService.enviarEmailAsincrono(para, titulo, conteudo);
```

E verifique novamente o tempo de resposta!

