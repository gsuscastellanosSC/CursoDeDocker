**Curso De Docker**
   https://platzi.com/clases/docker/
**1. Introducción**
    **Class#1**
        **Bienvenida al curso**
    **Class#2**
        **Las tres áreas en el desarrollo de software profesional**
            1. Construir:
                ➔ Entorno de desarrollo
                ➔ Dependencias
                ➔ Entorno de ejecución
                ➔ Equivalencia con entorno productivo
                ➔ Servicios externos
            2. Distribuir:
                ➔ Divergencia de repositorios
                ➔ Divergencia de artefactos
                ➔ Versionado
                ➔ Equivalencia con entorno productivo
                ➔ Servicios externos
         3. Ejecutar:
                ➔ Dependencias de aplicación
                ➔ Compatibilidad del entorno productivo
                ➔ Disponibilidad de servicios externos
                ➔ Recursos de hardware
    **Class#3**
        **Virtualización**
            **Problemas de las VMs**
                Peso:
                    En el orden de los GBs. Repiten archivos en común. Inicio lento.
                Costo de administración:
                    Necesita mantenimiento igual que cualquier otra computadora.
                Múltiples de formatos:
                    VDI, VMDK, VHD, raw, etc.
            **Containerización**
                ➔ Flexibles
                ➔ Livianos
                ➔ Portables
                ➔ Bajo acoplamiento
                ➔ Escalables
                ➔ Seguros
    **Class#4**
        **Preparando tu entorno de trabajo**
            docker run hello-world;
            docker info;
    **Class#5**
        **[Bonus] Play with Docker**
    **Class#6**
        **Qué es y cómo funciona Docker**
***2. Contenedores**
    **Class#7**
        **Primeros pasos: hola mundo**
            ➔ docker run hello-world;
    **Class#8**
        **Conceptos fundamentales de Docker: contenedores**
    **Class#9**
        **Comprendiendo el estado de Docker**
            ➔ docker inspect CONTAINER ID;
            ➔ docker inspect NAME;
            ➔ docker run --name hello-sc hello-world;
            ➔ docker rename hello-sc helo;
            ➔ docker container prune;<!-- Remove all containers. -->
    **Class#10**
        **El modo interactivo**
            ➔ docker run ubuntu;<!-- Create docker with Ubuntu. -->
            ➔ docker run -it ubuntu; <!-- Running container in interactive mode-->
    **Class#11**
        **Ciclo de vida de un contenedor**
            ➔ docker run --name SO -d ubuntu tail -f /dev/null;
            ➔ docker exec -ti ${nameContainer} bash;
            ➔ docker inspect --format '{{.State.Pid}}' ${nameContainer};
    **Class#12**
        **Exponiendo contenedores**
            ➔ docker run -d --name proxy nginx;      
            ➔ docker run --name proxy -p 8080:80 nginx;
                                           |   |__
                                       Local Port | 
                                            Container port
            ➔ docker logs -f proxy;
            ➔ docker logs --tail -f proxy;
**3. Datos en Docke**
    **Class#13**
        **Bind mounts**
            ➔ docker rm -f ${nameContainer};
            ➔ docker run -d --name dataBaseMongo -v ~/Documents/github/CursoDeDocker/dockerData:/data/db mongo;
    **Class#14**
        **Volúmenes**
            ➔ docker volume ls;
            ➔ docker volume create ${nameContainer};
            ➔ docker run -d --name db --mount src=${nameVolume},dst=/data/db mongo
    **Class#15**
        **Insertar y extraer archivos de un contenedor**
            ➔ docker run -d --name ${nameContainer} ubuntu tail -f /dev/null;
            ➔ docker cp ${LocalNameFile} copytest:/${DirRempteName}/${RemoteFileName};
            ➔ docker cp copytest:/${DirRemoteName} ${DirLocalName};
**4. Imágenes**
    **Class#16**
        **Conceptos fundamentales de Docker: imágenes**
            ➔ docker image ls;
            ➔ docker pull ubuntu:${tag};
    **Class#17**
        **Construyendo una imagen propia**
            ➔ docker build -t ubuntu:platzi ~/Documents/github/CursoDeDocker/dockerFiles;
            ➔ docker run -it ubuntu:${tag};
            ➔ docker tag ${REPOSITORY}:${TAG} ${propietario}/${so}:${tag};
            ➔ docker push gsuscastelsc/ubuntu:platzi;
    **Class#18**
        **El sistema de capas**
            ➔ docker history ubuntu:platzi;
            ➔ dive ubuntu:platzi;
**5. Docker como herramienta de desarrollo**    
    **Class#19**
        **Usando Docker para desarrollar aplicaciones**
            ➔ git clone https://github.com/platzi/docker;
            ➔ docker build -t platziapp .; 
            ➔ docker run --rm -p 3000:3000 platziapp
    **Class#20**
        **Aprovechando el caché de capas para estructurar correctamente tus imágenes**
            ➔ docker run --rm -p 3000:3000 -v /home/sc/Documents/github/CursoDeDocker/index.js:/usr/src/index.js platziapp
    **Class#21**
        **Docker networking: colaboración entre contenedores**
            ➔ docker network ls;
            ➔ docker network create --attachable platziNet;
            ➔ docker network inspect platziNet;
            ➔ docker run -d --name db mongo;
            ➔ docker network connect platziNet db;
            ➔ docker run -d --name app -p 3000:3000 --env MONGO_URL=mongodb://db:27017/test platziapp;
            ➔ docker network connect platziNet app;
**6. Docker Compose: la herramienta todo en uno**
    **Class#22**
        **Docker Compose: la herramienta todo en uno**
            Install dockerCompose:
                ➔  sudo curl -L "https://github.com/docker/compose/releases/download/1.27.4/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose;
                ➔ sudo chmod +x /usr/local/bin/docker-compose;
                ➔ docker-compose --version;
            Up docker compose:
                ➔ docker-compose up;
                ➔ docker-compose up -d;
        **Class#23**
            **Subcomandos de Docker Compose**
                ➔ docker-compose logs -f ${nameContainer};
                ➔ docker-compose exec ${nameContainer} bash;
                ➔ docker-compose down;
        **Class#24**
            **Docker Compose como herramienta de desarrollo**
                ➔ docker-compose build;
        **Class#25**
           **Compose en equipo: override**
                ➔ touch docker-compose.override.yml;
                ➔ docker-compose down;
                ➔ docker-compose up -d --scale app=2;
**Links**
    Install dockerCompose:
        https://docs.docker.com/compose/install/
    Wagoodman:
        https://github.com/wagoodman/dive
    Hub Docker:
        https://hub.docker.com/
    Play with Docker:
        https://labs.play-with-docker.com/
    Slides Curso Docker:
        https://static.platzi.com/media/public/uploads/slides-curso-docker_d04a71e1-4aa5-4b52-9dea-ba3ad2724202.pdf