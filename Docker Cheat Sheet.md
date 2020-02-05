## Executar um container
docker run hello-world

## Executar um container com terminal interativo
docker run -ti ubuntu /bin/bash #<-comando

## Executar um container em background
docker run -d ubuntu

## Finalizar o shell e o container
	Ctrl+d

## Sair do container e mantê-lo em execução
	Ctrl + P + Q

## Mostrar images disponíveis
sudo docker images
sudo docker image list

## Mostrar containers em execução
sudo docker ps

## Mostrar todos os containers
sudo docker ps -a

## Voltar para o container
docker attach <containerID>

## Apenas cria o container sem executá-lo
docker create ubuntu

## Parar o container
docker stop <containerID>
docker kill <containerID>

## Iniciar o container
docker start <coontainerID>

## Pausar o container
docker pause <containerID>

## Despausar o container
docker unpause <containerID>

## Informações de consumo do container
docker stats <containerID>

## quais processos estão consumindo os recursos do container
docker top <containerID>

## verificar logs do container
docker logs <containerID>

## remover container que já está parado
docker rm <containerID>

## remover container em execução 
docker rm -f <containerID>

## remover todos os containers parados
docker rm $(docker ps -a -q)


# Configurar os limites de utilização de recursos

## Visualzar detalhes do container em execução
docker inspect <containerID>

## iniciar container com nome
docker run -ti --name teste debian

## Verificar limite de memoria do container
docker inspect <containerID> <containerID> | grep -i mem

## Fixar um limite de mémoria na criação do container
docker run -ti --memory 512m --name novo_teste debian

## Alterar o limite de memória de um container já criado
docker update -m 256m <containerID>

## Atribuir limite de utilização de CPU
docker run -ti --cpu-shares 2014 --name container1 debian

## Atuaizar limite de utilização de CPU
docker update --cpu-shares 512 container1


# Utilização de volumes no docker

## Subir container com volume
docker run -ti -v /volume ubuntu /bin/bash
# container: df -h

## Obter localização de volumes no Host
docker inspect -f {{.Mounts}} <containerID>

## Mapear volume na criação do volume
docker run -ti -v /diretorioHost:/volumeContainer debian

## Subir container com volume (read-only)
docker run -ti -v $HOME:/volume:ro ubuntu /bin/bash

#Container data-only: armazena conteúdo para outros containers, e não precisa estar em execução
## Criar container Data-only
docker create -v /data --name dbdados centos

## Importar volume  de outro container na criação
docker run -d -p 5432:5432 --name pgsql1 --volumes-from dbdados -e POSTGRESQL_USER=docker -e POSTGRESQL_PASS=docker -e POSTGRESQL=docker kamui/postgresql

---------------------------------------------------
*docker volume create <nameVolume>
*docker volume inspect <nameVolume>
*docker volume ls 
*docker volume prune <--force>
*docker volume rm <nameVolume>


# Docker network

* docker network 
* docker network ls
* docker network inspect bridge
* docker network create database
* docker network inspect database

## Conectado a rede database
docker run -d --network database --name mysql -p 3306:3306 -e MYSQL_ROOT_PASSWORD=dontusethisinprod mysql
docker logs -f mysql

## Conectado a rede bridge
docker run -d --name adminer -p 8080:8080 adminer
docker network connect database adminer

## Conectando container adminer a rede database
docker network connect database adminer

## Desconectando o container adminer da rede bridge
docker network disconnect bridge adminer


# Dockerfile

	nano Dockerfile
	FROM debian #define a imagem que será utilizada
	ADD file.txt /diretorio/
	CMD ["sh", "-c", "echo","$HOME"] #parâmetros do entrypoint
	LABEL Description='versão Bla bla bla' # Metadata
	COPY texto.txt /diretorio #funciona apenas p/ arquivos e diretórios
	ENTRYPOINT ["/usr/bin/apache2ctl", "-D", "FOREGROUND"]
	ENV variavelDeAmbiente="PASSWORD"
	EXPOSE 80 #define  a porta do container que deve estar disponível
	RUN apt-get update && apt-get install apache2
	USER luan #define o usuario padrao
	WORKDIR /code #diretório default
	VOLUME /diretorio
	MANTAINER Luan Silva da Silva luansstkd@gmail.com

## Executar container apartir do Dockerfile
docker build . #Lê o Dockerfile na pasta

## Listar images
docker images

## buildar imagem
docker build -t nomeDaImagem:1.0 . # O ponto significa o diretório atual

## Criar imagem
mkdir /dockerfile/apache
nano Dockerfile

	FROM debian
	RUN apt-get update && apt-get install -y apache2 && apt-get clean
	ENV APACHE_LOCK_DIR="/var/lock"
	ENV APACHE_PID_FILE="/var/run/apache2.pid"
	ENV APACHE_RUN_USER="www-data"
	ENV APACHE_RUN_GROUP="www-data"
	ENV APACHE_LOG_DIR="/var/log/apache2"

	LABEL Description="Webserver"

	VOLUME /var/www/html

	EXPOSE 80

* Criar a imagem: docker build -t webserver:1.0 .
* Executar a imagem: docker run -ti webserver:1.0
* Verificar se o apache está em execução: ps -ef
* Iniciar o apache: /etc/init.d/apache2 start
* Verificar as portas ativas: ss -s
* Verificar o ip: ip addr
* Sair do container: Ctrl + P + Q
* Testar porta do container: curl <ip:porta>

## historico da imagem
docker history <imageid>

## mudar o nome da imagem
docker tag <imageid> userDockerHub/webserver:1.0

## Upload da imagem
docker push userDockerHub/webserver:1.0

## Pesquisar no terminal
docker search nameUser

## Apagar imagem
docker rmi -f userDockerHub/webserver:1.0 <ou imageid>

## Baixar imagem
docker pull userDockerHub/webserver:1.0


# Montar o distribuidor de imagens local

docker run -d -p 5000:5000 --restart=always --name registry registry:2

docker tag <imageid> localhost:5000/webserver:1.0

docker push localhost:5000/webserver:1.0

* Opcionalmente pesquisar por docker registry

## Verificar images do registry
curl localhost:5000/v2/_catalog

# Parâmetros de rede

docker run -ti --dns 8.8.8.8 debian ## servidor de dns 

docker run -ti --hostname webweb debian ## configura o hostname

docker run -ti --link container1 --name container2 ## cat /etc/hosts >> coloca os containers em comunicação

docker run -ti --expose 80 debian ## Faz o mesmo que o comando EXPOSE do Dockerfile

docker run -ti --publish 8080:80 debian ## redireciona o acesso da porta 8080 do Host para a porta 80 do container

docker run -ti --mac-address <mac personalizado> debian

docker run -ti --net=host debian ## Configura o container para utilizar as mesmas variaveis de rede do host

# Docker Machine

* Fazer a instalação

docker-machine --version

* Instalar o virtualbox

## Criar VM = HostDocker
docker-machine create --driver virtualbox nameHostDocker

## Conectar ao HostDocker
docker-machine env nameHostDocker
eval $(docker-machine env nameHostDocker)

## Listar Hosts Docker com seus estados (ativo/parado)
docker-machine ls 

## Mostrar ip do host docker
docker-machine ip nameHostDocker

## Conectar ao hostDocker via ssh
docker-machine ssh nameHostDocker

## Informações do Host Docker
docker-machine inspect nameHostDocker

## Parar Host Docker
docker-machine stop nameHostDockker

## Iniciar
docker-machine start nameHostDocker

## Remover
docker-machine rm nameHostDocker

# Docker Compose

## Criar imagem
build: . #caminho do Dockerfile

## Enviar comando para o container
command: bundle exec thin -p 3000

#nome do container
container_name: my-web-container

#indica o dns server
dns: 8.8.8.8

#dns_search = especifica um search domain
dns_search: example.com

#dockerfile = especifica um Dockerfile alternativo
dockerfile: Dockerfile-alternate

#env_file = Especifica um arquivo com variaveis de ambiente
env_file: .env

#enviroment = Adiciona variaveis de ambiente
env_file:
	RACK_ENV: development

#expose = expõe a porta do container
expose:
	- "3000"
	- "8000"

#external_links = linka containers que não fazem parte do docker-compose atual
external_links:
	- redis_1
	- project_db_1:mysql

#extra_hosts = Adiciona uma entrada no /etc/hosts do container
extra_hosts:
	- "somehost:ip"
	- "otherhost:ip"
#image = Indica uma imagem
image: ubuntu:14.04

#labels = Adiciona metadata ao container
labels:
	com.example.description: "Accounting webapp"
	com.example.description: "Finance"

#links  = linka containers dentro do mesmo docker-compose
links:
	- db
	- db:databse

#log_driver = indica o formato de log a ser gerado, por ex: syslog, json-file, etc
log_driver: syslog

OU

logging:
	driver: syslog

#log_opt = Indica onde mandar os logs, pode ser um local ou remoto
log_opt:
	syslog-address: "tcp:## ip:porta"
OU
logging:
	driver:syslog
	options:
		syslog-address: "tcp:## ip:porta"

#net = modo de uso da rede
net: "bridge"
net: "host"

#volumes, volume_driver = Monta volumes dentro do container
volumes:
	simple path
	- /var/lib/mysql
	absolute =path mapping
	- /opt/data:/var/lib/mysql
	path on the host, relative to the compose file
	- ./cache:/tmp/cache

#volumes_from = monta volumes através de outro container
volumes_from:
	-service_name
	-service_name.ro

#################################################################
Projeto Docker-Compose com PostgreSQL
#################################################################
mkdir project

nano docker-compose.yml

db:
	image: postgres
web:
	build: .
	command: python manage.py runserver 0.0.0.0:8000
	volumes:
		- .:/code
	ports:
		- 8000:8000
	links:
		- db

nano Dockerfile

FROM python:2.7
ENV PYTHONUNBEFFERED 1
RUN mkdir /code
WORKDIR /code
ADD requirements.txt /code/
RUN pip install -r requirements.txt
ADD . /code/

nano requirements.txt
Django
psycopg2

## executar no serviço web
docker-compose run web django-admin.py startproject composeexample .

editar o arquivo settings para o db postgres
...

## Subir o ambiente
docker-compose up -d

## testar
curl localhost:8000

## verificar instancias do compose
docker-compose ps

## escalar
docker-compose scale db=2

## Parar todos os containers
docker-compose stop

## Iniciar containers
docker-compose start

## Verificar logs 
docker-compose logs < -f [optional]> <--tail=n , [optional]>

## Para e remover containers, redes e volumes associados
docker-compose down

## Criar imagens, <service is optional>
docker-compose build <service>

## Recriar imagens mesmo que não tenham sofrido alterações
docker-compose up --build

## Executar comandos em um container 
docker-compose exec <service> <command>

## Validar o arquivo docker-compose.yml
docker-compose config


--------------------------------------------------------------

#################################################################
Orquestração de containers
#################################################################
video 21 : https:## www.youtube.com/watch?v=KfH1cJErGb0&list=PLf-O3X2-mxDkiUH0r_BadgtELJ_qyrFJ_&index=21

