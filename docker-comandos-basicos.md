#### Comandos Básicos
Recentemente iniciei os estudos em Docker e com isso compartilho com todos a lista de alguns comandos básicos para quem esta iniciando no mundo dos containers.

**Para quem desejar iniciar os estudos, indico a criação de laborátorios com maquinas virtuais ou com Vagrant.**

```bash

Instalação: curl -fsSL https://get.docker.com | bash

#VERIFICAR VERSÃO DO DOCKER INSTALADO
docker --version
Docker version 20.10.7, build f0df350

# LISTAR CONTAINER
docker container ls
CONTAINER ID   IMAGE COMMAND CREATED STATUS PORTS NAMES

# LISTAR TODOS OS CONTAINERS
docker container ls -a
CONTAINER ID   IMAGE   COMMAND CREATED     STATUS  PORTS NAMES
1ad404b620da   ubuntu  "bash"  1 hours ago Exited        mccarthy

# LISTAR IMAGENS
docker image ls

REPOSITORY    TAG       IMAGE ID       CREATED             SIZE
ubuntu        latest    c29284518f49   6 days ago          72.8MB
nginx         latest    4cdc5dd7eaad   13 days ago         133MB
debian        latest    7a4951775d15   3 weeks ago         114MB
hello-world   latest    d1165f221234   4 months ago        13.3kB

#LISTAR ENDEREÇOS DE REDE
docker network ls

NETWORK ID     NAME      DRIVER    SCOPE
5df1ea620210   bridge    bridge    local

#LISTAR VOLUMES
docker volume ls

DRIVER    VOLUME NAME
local     rosemary
local     tyler

# EXECUTAR CONTAINER
docker container run -ti hello-world

docker run -it ubuntu bash (container com terminal interativo)
<CTRL> + <P> + <Q> (sair do container sem matar processo)

#VOLTAR PARA O CONTAINER EM EXECUÇÃO
docker container attach [ID/NOME/CONTAINER]

# # Comando Exec: execução de comandos no container
docker container exec -ti [ID CONTAINER] ls /
docker container exec -ti [ID CONTAINER] bash

# START CONTAINER
docker container start [ID CONTAINER]

# PARAR EXECUÇÃO CONTAINER
docker container stop [ID CONTAINER]

# RESTART CONTAINER
docker container restart [ID CONTAINER]

# PAUSE / UNPAUSE CONTAINER
docker container pause [ID CONTAINER]
docker container unpause [ID CONTAINER]

# INSPECT: DETALHES DO CONTAINER
docker container inspect ID_CONTAINER

# LOGS CONTAINER
docker container logs -f [ID CONTAINER]

# REMOVER CONTAINER
docker container rm ID_CONTAINER

# REMOVER CONTAINER FORÇADAMENTE
docker container rm -f ID_CONTAINER
```
#### Configurações de CPU e Memória
```bash

# INFORMARÇÕES EM TEMPO REAL, CPU, MEMORIA ETC.
docker container stats [ID CONTAINER]

# INFORMAÇÕES DE PROCESSOS EM EXECUÇÃO
docker container top [ID CONTAINER]

UID   PID   PPID C STIME TTY    TIME     CMD
root  2286  2257 1 02:32 pts/0  00:00:00 bash

# ESTABELECER LIMITE DE MEMORIA
docker container run -d -m 128MB nginx

# ESTABELECER LIMITE DE CPU
docker container run -d -m 128MB --cpus 1 nginx

# ATUALIZAR CPUS e MEMORIA
docker container update --cpus [valores] ID_CONTAINER
docker container update --cpus [valores] --memory [valores] ID_CONTAINER
```
