# Deploy

Cria um deploy de uma aplicação Go.

## .Dockerfile.prod

```bash
# as build: cria um nome de etapa chamada builder, poderia ser outro nome
FROM golang:latest as builder
WORKDIR /app
# Copia todos os arquivos para o workdir
COPY . .
# GOOS: seta o sistema operacional linux
# GO_ENABLED: desabilita a utilização de pacotes do C
# -o: nomeia o binário
# -ldflags="-w -s": Remove o DWARF (Opções de debugging e etc.)
RUN GOOS=linux CGO_ENABLED=0 go build -ldflags="-w -s" -o server .
# scratch: cria uma imagem docker sem nada dentro
FROM scratch
# Copia o binário server da etapa builder para workdir
COPY --from=builder /app/server .
# Executa o binário
CMD ["./server"]
```

## Criar a imagem e subir container

```bash
# Cria
docker build -t venzel/deploy:latest -f Dockerfile.prod .

# Verifica o tamanho da imagem gerada
docker images | grep deploy

# Roda o container na porta 3000
# --rm: mata o container quando para de rodar
docker run --rm -p 3000:3000 venzel/deploy
```

## Subir o container no docker hub

```bash
# Vai pedir o user e o password
docker login

docker push venzel/deploy:latest
# https://hub.docker.com/repository/docker/venzel/deploy/general
```

## Makefile

```bash
# Sobe o container
make up

# Mata o container
make down

# Executa o programa
make run

# Entra no container
make exec

# Cria o binário com nome server
make build
```

<div>
  <img align="left" src="https://imgur.com/k8HFd0F.png" width=35 alt="Profile"/>
  <sub>Made with 💙 by <a href="https://github.com/venzel">Enéas Almeida</a></sub>
</div>
