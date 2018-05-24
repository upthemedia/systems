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
