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
