# docker



## Comandos utilizados exemplo 1

FROM nginx:latest

RUN apt-get update
RUN apt-get install vim -y

Criar imagem com dockerfile: docker build -t alineassuncao/nginx-com-vim:latest . 

## Comandos utilizados exemplo 2

FROM nginx:latest

WORKDIR /app

RUN apt-get update && \
    apt-get install vim -y

COPY html/ /usr/share/nginx/html/

Criar imagem com dockerfile: docker build -t alineassuncao/nginx-com-vim:latest . 

## Comandos utilizados exemplo 3
FROM ubuntu:latest

CMD [ "echo", "Hello, World!" ]

Criar imagem com dockerfile: docker build -t alineassuncao/hello . 
Rodando:
docker run --rm alineassuncao/hello:latest 
docker run --rm alineassuncao/hello echo "oi"


## Comandos utilizados exemplo 4
FROM ubuntu:latest

ENTRYPOINT [ "echo", "Hello " ]

CMD [ "world" ]

Criar imagem com dockerfile: docker build -t alineassuncao/hello . 
Rodando:
docker run --rm alineassuncao/hello
docker run --rm alineassuncao/hello "Aline"

## Comandos network Bridge
docker network
docker network ls
docker network create --driver bridge minharede

EXEMPLO 1
docker run -dit --name ubuntu1 --network minharede bash
docker run -dit --name ubuntu2 --network minharede bash
docker exec -it ubuntu1 bash
ping ubuntu2

EXEMPLO 2
docker run -dit --name ubuntu3 bash
docker network connect minharede ubuntu3
docker inspect minharede

## Comandos network host
docker network
docker network ls
docker run --rm -d --name nginx --network host nginx