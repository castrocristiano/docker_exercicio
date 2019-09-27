
# Criar a imagem do docker 
## -t define o nome da imagem 
## -f define onde está o arquivo
> docker build -t mysql-image -f db/Dockerfile .


# Comando para listar as imagens
> docker image ls 

## -d libera o terminal para a execução de outros comandos
## --rm remove o container caso já exista um com o mesmo nome
## --name define o nome do container
> docker run -d --rm --name mysql-container mysql-image

# Comando para exibir os containers que estão de pé
> docker ps

# Comando dentro do container
## -i significa que é comando interativo
> docker exec -i mysql-container mysql -uroot -pK@r@mb@ < db/script.sql

# Comandos utilizando o terminal 
## -it comando interativo e t de terminal
> docker exec -it mysql-container /bin/bash

# Acessar o mysql dentro do container
> mysql -uroot -pK@r@mb@ 

# Comando para parar o container
## Se não utilizar volumes, ao parar o container tudo será perdido.
> docker stop mysql-container

# Volumes
## -v define o volume
## $() para executar um comando dentro da linha de comando, no nosso caso o comando pwd que mostra a pasta atual. $(pwd)
> docker run -d -v $(pwd)/db/data:/var/lib/mysql --rm --name mysql-container mysql-image