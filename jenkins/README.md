# Jenkins
[16/03/2018] La última versión LTS de Jenkins es la 2.107.1

## Prerequisitos
* Se debe instalar Docker y Docker Compose: https://docs.docker.com/compose/install/
* Configurar poder ejecutar Docker sin ser root: https://docs.docker.com/install/linux/linux-postinstall/


## Cómo construir la imagen y arrancarlo
1. Construye la imagen: `docker build -t jenkins-upthemedia .`
2. Para arrancarla puedes hacerlo:
    * Con Docker Compose (preferiblemente): `docker-compse up -d`
    * Manualmente: `docker run -p 8080:8080 --rm --name jenkins-upthemedia jenkins-upthemedia:latest`, donde:
        * `jenkins-upthemedia:latest` es el nombre de la imagen a partir de la cual crear un contenedor
        * `jenkins-upthemedia` es el nombre que damos al contenedor


## How to access local Jenkins from the outside
* In case you're running Jenkins from a local server (without a public URI), you can still turn you Jenkins URI externally available using ngrok:
https://dashboard.ngrok.com/get-started
* This could be useful, for example, for configuring the GitHub webhook to tell Jenkins about new commits, or just to access Jenkins from anywhere.
* Steps:
    * Install ngrok:        `npm i -g ngrok`
    * Connect your account: `./ngrok authtoken 4UaNif16MrTTzG6v1NpUs_5nzBdUBtmuddu9rMpYwC7`
    * To start a HTTP tunnel on port 80, run: `ngrok http 80`
        * You get an accesible public URI
    * To access ngrok inspector: `http://localhost:4040`
    * Status page: `https://dashboard.ngrok.com/status`


## Integración Jenkins-GitHub
* En GitHub:
    * Bajo "Settings -> Webhooks", configurar la URI del webhook de Jenkins, e.g. https://408ef008.ngrok.io/github-webhook/
* En el job de Jenkins:
    * marcar "GitHub project" y configurar la URI del repo
    * marcar "Git", configurando la URI, branch y subfolder (si se necesita)
    * marcar "GitHub hook trigger for GITScm polling"

## Pendiente
* https://trello.com/c/WCThfX8P/29-montar-ci-jenkins-dockerizado-en-local
* Memory settings: https://live-rg-engineering.pantheon.io/news/putting-jenkins-docker-container

## Links de interés
* Dockerización de Jenkins
    * https://dzone.com/articles/dockerizing-jenkins-2-setup-and-using-it-along-wit
    * https://hub.docker.com/_/jenkins/
    * https://github.com/Jenkinsci/docker
    * https://engineering.riotgames.com/news/putting-jenkins-docker-container
* PHP en Jenkins:
    * * http://jenkins-php.org/