## Docker compose
Docker compose é uma ferramenta para ajudar na definição e no execução de multiplos containeres.

Com ela é possível configurar todos os parâmetros necessários para executar cada container a partir de um arquivo de definição. Dentro desse arquivo, definimos cada container como serviço, ou seja, sempre que esse texto citar serviço de agora em diante, imagine que é a definição que será usada para iniciar um container, tal como portas expostas, variáveis de ambiente e afins.

Com o Docker Compose podemos também especificar quais volumes e rede serão criados para serem utilizados nos parâmetros dos serviços, ou seja, isso quer dizer que não preciso criá-los manualmente para que os serviços utilizem recursos adicionais de rede e volume.