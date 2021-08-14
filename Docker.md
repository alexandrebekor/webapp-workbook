# Docker Container

```
docker container run hello-world
```
Nesse mesmo comando temos:
- docker image pull
- docker container create
- docker container start
- docker container exec

```
docker container ps
# Retorna os containers ativos
```

```
docker container ps -a
# Retorna todos os containers independente do status
```

```
docker container rm nome-do-container
# Remove o container
```

O comando `run` cria sempre um novo container.

Para acessar o terminal do container criado:
```
docker container run -it nome-do-container bash
# -it aciona o container no modo interativo
```

Dentro do container é possível utilizar todos os comandos do próprio sistema do container:
```
touch arquivo.txt
# cria um novo arquivo
```

# Nomear Containers
```
docker container run --name nome-do-container -it nome-da-imagem bash
```

Nomear o container possibilita reutilizá-lo mais facilmente.
```
docker container ls -a
# Equivale ao ps: lista todos os containers
```

```
docker container start -ai nome-do-container
# Abre o terminal do container já criado
```

```
docker container stop nome-do-container
# Finaliza o container em execução
```

# Mapear Portas
```
docker container run -p 8080:80 nginx
# 8080 será a porta exposta do container e 80 a porta correspondente internamente
```

Significa que o nginx será inicializado pela porta 80 e os recursos externos acessarão essa porta por meio da 8080.

Para testar:
```
curl http://localhost:8080
```

# Mapeamento de Volumes
```
docker container run -p 8080:80 -v $(pwd):/usr/share/nginx/html nginx
```

O `$(pwd)` pode ser substituido pelo caminho absoluto da pasta atual.

```
docker container run -d --name nome-do-container -p 8080:80 -v ./:/usr/share/nginx/html nginx
# -d é o modo daemon que é quando o container será executado em background
```

# Gerenciar container em Background
```
docker container start nome-do-container
```

```
docker container stop nome-do-container
```

```
docker container restart nome-do-container
```

```
docker container logs nome-do-container
```

```
docker container exe nome-do-container comando
```

```
docker image ls
```

```
docker volume ls
```

```
docker image rm nome-da-container
```

```
docker container rm nome-do-container
```

```
docker volume rm nome-do-container
```

# Container vs Imagem
A imagem é como a receita e o container o prato construído por meio dessa receita.

```
docker image pull redis:latest
# Faz o download da útlima versão do redis
```

## Gerenciamento das Imagens
```
docker image
- ... pull nome-da-imagem
- ... ls
- ... rm nome-da-tag
- ... inspect nome-da-tag
- ... tag imagem-origem nome-da-nova-tag
- ... build
- ... push
```

O build é gerado por meio de um arquivo nomeado como: `Dockerfile`.

```
docker image build -t nome-da-imagem .
# -t indica que a próxima palavar é o nome
# . indica que o documento Dockerfile está na pasta raiz
```

```
docker container run -p 80:80 nome-da-imagem
# Executa a imagem
```

# Docker Compose
```
docker-compose [comando]
```

## Controlar o ambiente
- up
- down
- stop
- start

## Monitorar/ Auditar
- ps
- logs
- top
- kill

## Execitar Comandos
- exec [service-name] [command]