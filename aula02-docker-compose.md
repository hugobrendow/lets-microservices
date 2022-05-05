## Docker compose

#### O que é?

O **Docker Compose** é uma ferramenta de administração de containers. No mundo de micro-serviços é comum que uma aplicação tenha mais de uma API, com mais de uma linguagem de programação, mais de um banco de dados. Por causa dessa separação você precisaria de mais de 1 container para ter sua aplicação em produção.

Mesmo se sua aplicação não for um micro-serviço, o Docker Compose ajuda no gerenciamento da sua aplicação, para subir um banco de dados relacional, um banco de dados não relacional, um serviço de cache.

#### Por que usar?

Nós podemos criar um ambiente através de um arquivo com todas as ferramentas necessárias e logo em seguida subir esse arquivo com apenas um comando, ao invés de repetir o comando de docker run mais de uma vez.

#### Como funciona?

- Precisamos fazer o download do Docker Compose
- Nós iremos criar um arquivo yml, aquela extensão yml ou yaml.
  - É um tipo de arquivo que montamos uma estrutura com um tipo de identação.

#### Comandos

- **build**
  - Usado para construir todas as imagens dos serviços com a definição de build em seu bloco de código.
- **up**
  - Inicia todos os serviços que estão no arquivo
- **stop**
  - Para todos os serviços que estão no arquivo
- **ps**
  - Listar todos os serviços que foram iniciados no arquivo

#### Exemplo de arquivo
```sh
version: '2'
services:
web:
    build: .
    context: ./dir
    dockerfile: Dockerfile-alternate
    args:
        versao: 1
    ports:
    - "5000:5000"
redis:
    image: redis
```