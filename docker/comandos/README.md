# Comandos docker

## Docker hub

- Para o docker run funcionar, ele precisa encontrar a imagem do container:
    - Existe um grande repositório de imagens, que é o Docker hub, e dentro dele podemos encontrar diversas imagens.
```
tetzner@pop-os:~/learning-devops$ sudo docker run --help

Usage:  docker run [OPTIONS] IMAGE [COMMAND] [ARG...]
```
   - Hell World é o nome de uma imagem
- Imagem oficial do docker hub, é um grupo confiável que cuida da imagem.

- Podemos ter um container que contém um Sistema Operacional
    - Exemplo: Ubuntu

```
$ sudo docker run ubuntu
```
## RUN

- Ele executa uma imagem no docker.
- O comando docker run é responsável por executar um container em nosso host.

## Fluxo da criação de containers

- De primeira com comando docker run ubuntu, ele não roda

```
$ sudo docker run ubuntu
```

- Existe comandos que vão ajudar:
    - docker ps (Quais containers estão em execução no atual momento).
    - docker container ls
    - Para ver os containers que não estão mais em execução
        - docker ps -a
        - docker container ls -a

- O container foi executado, subiu e rodou um bash, mas foi encerrado.
- Para um container ficar em execução, precisa de no minímo 1 processo dentro dele.

- Para fazer de uma forma mais clara, podemos passar um comando para esse container como flag do docker run

```
Usage:  docker run [OPTIONS] IMAGE [COMMAND] [ARG...]
```

Então podemos executar, dentro do container ubuntu:

```
tetzner@pop-os:~$ sudo docker run ubuntu sleep 1d
```

Verificando com docker ps:

```
CONTAINER ID   IMAGE     COMMAND      CREATED          STATUS             NAMES
d5ce0c82eb20   ubuntu    "sleep 1d"   53 seconds ago   Up 52 seconds    relaxed_lamarr
```

### O docker run, o host foi no docker hub buscar a imagem do ubuntu, depois faz uma validação com sha-256, e executa o nosso container, que vai ter um comando básico a ser executado.

### Se não tiver um processo, vamos criar container's zumbi, que vão subir e morrer depois.

