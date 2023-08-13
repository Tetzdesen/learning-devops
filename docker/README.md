# Docker learning

Documentação e resumo de curso de docker.

# Instalação e configuração do docker

###  Linux

- O docker roda de uma forma bem tranquila em uma distribuição linux.

- Seguindo a documentação do https://docs.docker.com/engine/install/ubuntu/

```
$ sudo apt-get update
$ sudo apt-get install ca-certificates curl gnupg
```

```
$ sudo install -m 0755 -d /etc/apt/keyrings curl -fsSL https://download.docker.com/linux/ubuntu gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg

$ sudo chmod a+r /etc/apt/keyrings/docker.gpg
```

```
$ echo \
  "deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  "$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

```
$ sudo apt-get update
```

```
$ sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

```
$ sudo docker run hello-world
```

```
Unable to find image 'hello-world:latest' locally
latest: Pulling from library/hello-world
719385e32844: Pull complete 
Digest: sha256:dcba6daec718f547568c562956fa47e1b03673dd010fe6ee58ca806767031d1c
Status: Downloaded newer image for hello-world:latest

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/get-started/

```


# Problema
  Imagina nosso software/aplicação que contém:
  - Uma aplicação nginx.
  - Uma aplicação Java.
  - Uma aplicação Dotnet (C#).

  - Precisamos que as aplicações estejam em execução, isso pode gerar problemas entre:

    ### O docker tenta resolver:
    - Conflitos de portas;
    - Podemos alterar as versões de maneira prática?

# Container

 - São mais leves em relação a uma máquina virtual, dentro de um SO, cada container vai funcionar como um processo dentro do SO, VM tem uma parte de virtualização dentro do nosso Sistema Operacional.

 - A nível de consumo de recursos dentro do nosso SO, container se sobressai em relação a VM.

 - A fim de garantir o isolamento entre os container's e o Sistema Operacional, existe o conceito de namespace, que vai garantir o isolamento de container a nível.

  - Graças o namespace de UTS, o nosso container vai ter um pedaço do kernel do nosso SO embutido, só que isolado.
  - Não precisamos instalar um SO dentro do container, já que ele vai usar um namespace para isolar e utilizar um pedaço do kernel do SO padrão em que o ambiente docker é utilizado.

- Outro conceito é cgroups que garantem a divisão de recursos, como memória e CPU.

- Ele vai funcionar como processos do nosso SO.
