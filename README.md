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
**Links**
    Play with Docker:
        https://labs.play-with-docker.com/
    Slides Curso Docker:
        https://static.platzi.com/media/public/uploads/slides-curso-docker_d04a71e1-4aa5-4b52-9dea-ba3ad2724202.pdf