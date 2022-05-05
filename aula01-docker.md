# Docker

### O que é docker?

Docker é uma ferramenta para criar e manter containers, responsável por isolar o container do Host do SO. Desenvolvido em Go.

O docker utiliza o Cgroups do Kernel para isolar o uso de CPU, memória, disco e rede.

E utiliza o recuso de namespaces para isolar o componente criando uma camada, isolando os grupos de processos:

> - pid - isolamento de processos (PID)
> - net - controle de interfaces de rede
> - ipc - comunicação entre processos e memória compartilhada
> - mnt - sistema de arquivos e pontos de montagem
> - uts - age como se o container fosse outro host

### Por que usar Docker?

Com o docker conseguimos configurar ambientes de forma rápida, diminuindo problemas de compatibilidade.

#### No que o Docker pode ajudar?

- O Docker tem como objetivo criar, testar e implementar aplicações de uma forma padronizada, separadamente de configurações da máquina original.
- O repositório de imagens docker pode ser acessado para conseguir modelos de aplicações e serviços prontos para integrações complexas.
- Economia significativa de recursos, quando comparado a soluções tradicionais de virtualização.
- Implantação rápida.

### Docker hub
Lugar público várias empresas e pessoas publicam imagens pré-compiladas de soluções. Então, lá você vai poder, por exemplo, encontrar uma imagem pronta para servidores Java e diversas outras soluções.
