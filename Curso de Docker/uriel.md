# Apuntes de Docker 🐳

## Qué es Docker
- Lugar virtual para almacenar dependencias
    - Dependencias que las apps necesitan
- Empaquetar la aplicación: Runtimes, bibliotecas y otros componentes
- Local o remoto en un servidor
- Se ejecuta bien en cualquier SO
- Isolar procesos dentro de un contenedor y ejecutarlo donde Docker esté funcionando
- build once, run anywhere
- Son similares a las máquinas virtuales, pero con propósitos diferentes.
    - Virtualización: Simular todos los componentes de un SO, sobre todo el Kernel (intermediario entre el SO y el Hardware)
    - Contenedor: No hay simulación del SO, se ejecutan directamente en el SO, y comparten el kernel. El kernel es el Docker engine.
    - Docker más veloz
    - Isolación: Un contenedor puede isolar entre procesos y contenedores, pero no está 100% isolado. Una máquina virtual 100% isolado, porque usa sus propios recursos
- Docker: Tecnología para la manipulación de contenedores
- Se ejecuta de igual forma en desarrollo como en producción

## Conceptos

- 3 conceptos: Imágenes, Contenedores, Docker Hub
- Imágenes: Una imagen es como una clase donde definimos las configuraciones del objeto.
    - Ej. Que tenga instalado nginx
    - Las instancias serían los contenedores
- Un contenedor es una instancia de una imagen que ejecuta las instrucciones de la imagen
- Docker Hub: Es un registro donde podemos descargar y subir imágenes, como GItHub pero de imágenes.
- Arquitectura: Cliente Servidor
    - Servidor: Docker Engine, encargado de la administración de imágenes y contenedores
    - Cliente: De línea de comandos o gráfico, se conecta al servidor vía una API
    - Flujo
        - Desde el cliente pedimos que se ejecute la imagen
        - El servidor irá al registro público (Docker Hub), descargará la imagen y la ejecutará en el host.

## Instalación

- Sólo funciona en Linux
- Revisar requisitos del sistema para Windows o Mac
- Seguir el proceso de instalación
- Reiniciar de ser necesario
- En Mac, sabes que está instalado cuando ves el icono de Docker en la barra de status
- Puedes ejecutar docker version en una nueva terminal para corroborar la instalación.

## Hola mundo

- docker image: Comando para manejar y administrar imágenes
- Docker Hub es el registro por defecto
- pull es el argumento de docker image para descargar imágenes del registro
- docker image pull fernando93d/hello sirve para descargar la imagen generada para el curso
- docker image ls Enlista las imágenes descargadas localmente
- docker container para manejar contenedores
- El argumento run de docker container ejecuta un contenedor dada una imagen
- Agregar el flag —help nos da ayuda del comando, estructura y flags
- La imagen fernando93d/hello contiene un script de Python que imprime Hola mundo, así se tiene que ver si todo salió bien:

## Comandos básicos de contenedores

- docker container ls: Enlista los contenedores
- Sólo aparecen los contenedores "encendidos"
- docker container ls -a Enlista contenedores ejecutándose y no ejecutándose
    - container id: Identificador único de docker
    - name: Lo asigna aleatorio docker
    - Podemos hacer referencia a un contenedor por su id o su nombre
- Un contenedor se apaga si no tiene servicios ejecutándose
- docker container dm, elimina uno o más contenedores