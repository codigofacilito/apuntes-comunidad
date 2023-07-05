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

Manejo básico de contenedores con el cliente de Docker (desde terminal)

- docker container ls: Enlista los contenedores
- Sólo aparecen los contenedores "encendidos"
- docker container ls -a Enlista contenedores ejecutándose y no ejecutándose
   - container id: Identificador único de docker
   - name: Lo asigna aleatorio docker
   - Podemos hacer referencia a un contenedor por su id o su nombre

- Un contenedor se apaga si no tiene servicios ejecutándose
- docker container rm, elimina uno o más contenedores. Ej: docker container rm db74e4eaea8c
- docker container run es igual a ejecutar docker container create y docker container start
- docker container create, crea el contenedor pero no lo ejecuta
- docker container ls incluye una columna STATUS que, cuando indica Created, quiere decir que el contenedor fue creado, pero no ejecutado
- docker container start  ejecuta el contenedor para el ID especificado
- STATUS en docker container ls indica cuándo finalizó la ejecución de un contenedor

## Modo interactivo de Docker

El modo interactivo nos permite abrir una terminal en el contenedor para ejecutar comandos, puede abrirse en la terminal que estamos usando, o en segundo plano.

- En el Docker Hub, tags nos permiten diferenciar entre distintas versiones de la imagen, latest es la última soportada, se usa por defecto latest.
- docker image pull : para descargar un tag específico
- docker container ls incluye una columna TAG donde se indica el tag usado para descargar la imagen
- docker container run : nos permite ejecutar una imagen en un tag específico
- Cuando un contenedor ejecuta un servicio, la terminal queda en ejecución del contenedor
- docker container ls debería enlistar un contenedor con procesos en ejecución
- docker container ls incluye una columna STATUS que si está up, significa que el contenedor se está ejecutando
- Ctrl + C para finalizar un contenedor con un proceso ejecutándose
- Modo interactivo: Una forma de ejecutar una terminal dentro del contenedor
- La bandera -i mantiene la entrada estándar abierta, -t genera una nueva terminal. La combinación de -i, -t genera un proceso dentro del contenedor y agrega una terminal
- docker container run -it  para habilitar la terminal en el contenedor (Modo interactivo)
- exit para salir de la terminal del contenedor
- docker container run -d Ejecuta el contenedor en segundo plano e imprime el ID. Ejemplo: docker container run -d 
- docker container run -itd  habilita el modo interactivo en segundo plano
- docker container ls

## Ejecutar comandos dentro de un contenedor

- docker container attach nos "agrega" a la entrada y salida estándar del contenedor, en términos prácticos esto significa que nos ingresa a la terminal de un contenedor ejecutándose en segundo plano. Ej: docker container attach 
- exit dentro de attach también cierra el proceso y apaga el contenedor cuando el proceso que lo mantiene disponible es la terminal
- docker container exec nos permite ejecutar comandos directamente en la terminal. Ejemplo: docker container exec   : `docker container exec f778423aac8f ls -lh``
- La flag -i en exec nos permite abrir una entrada estándar al contenedor, sin que al finalizarlo se finalice la ejecución del proceso de entrada estándar del contenedor mismo `docker container exec -it f778423aac8f bash` (presuntamente es como abrir una nueva terminal en el contenedor de Ubuntu)
- exit sobre la terminal abierta con exec no cierra el proceso estándar del contenedor y por tanto lo mantiene abierto.
- docker container top  enlista los procesos ejecutándose dentro de un contenedor

## Puertos

Los puertos nos permiten exponer servicios de un contenedor hacia el host.

- Mapean el puerto del contenedor hacia la máquina local
- `docker container ls -q` obtiene solos los IDs de los contenedores ejecutándose
- docker container stop $(docker container ls -q) detiene todos los contenedores activos
- docker container prune - Elimina todos los contenedores detenidos
- La bandera -p del comando docker container -run, publica los puertos del contenedor al host.
- La sintaxis de -p es :, ejemplo: `docker container run -d -p 3030:80 nginx`, en este caso el puerto 80 del contenedor se accede con el 3030 en el host.
- `docker container port <id-contenedor>` Enlista los puertos mapeados del contenedor al host
- El flag -P de docker container run delega a docker el mapeo de puertos para que asigne uno aleatorio en el host para los puertos del contenedor `docker container run -d -P nginx`, puedes saber a qué puerto mapeo con docker container port
- `docker container ls` también contiene una columna PORT para los puertos enlistados
- Múltiples puertos se mapean concatenando el flag -p `docker container run -d -p 3030:80 -p 2020:81 nginx`

## Logs

Los logs nos permiten visualizar la salida estándar o el error estándar del contenedor.

- docker container logs  imprime los logs del contenedor
- Bastante útil cuando no sabemos por qué un contenedor se apagó, ya que imprime las entradas al error estándar del contenedor

## Commits

Un commit es una forma de tomar a un contenedor con todos sus recursos y transformarlo en una imagen.

- En términos prácticos: Si has hecho modificaciones en el contenedor, como crear archivos, instalar o desinstalar, entre otros, puedes convertir eso en una imagen para regenerar contenedores con los mismos cambios.
- `docker container commit <id-contenedor> <nombre-imagen>`
- El comando docker container commit genera una nueva imagen que puedes ver con `docker image ls`
- Puedes generar un nuevo contenedor para la imagen generada con `docker container run <nombre-imagen>`

## Volúmenes

Compartir archivos entre el host y el contenedor o entre contenedores. Almacenar información sensible que no debería estar en el contenedor. Es como un espacio de archivos compartidos.

- docker volume es el comando para controlar los volúmenes
- Podemos usar drivers para configurar los volúmenes, por defecto es el disco local, pero puedes usar drivers para almacenar los archivos en cloud (AWS, Docker, etc)
- `docker volume create` sirve para crear nuevos volúmenes
- La bandera -d de opciones nos permite configurar el driver para el volumen
- `docker volume create <nombre-volumen>` crea un nuevo volúmen
- `docker volume ls` enlista los volúmenes en nuestra computadora
- `docker volume inspect <nombre-volumen>` entrega info del volumen como fecha de creación, driver y dónde ubicarlo en el host. El path puede no encontrarse en Mac o Windows porque se ejecutan en máquinas virtuales
- Para montar un volumen en un contenedor usamos la opcion -v al ejecutar el contenedor: `docker container run -dit -v local:/app ubuntu`
- La sintaxis de la opción -v es :, el path del contenedor define en qué ubicación estará el volumen.
- Los archivos de un volumen persisten incluso aunque el contenedor haya sido eliminado.

## Terminología

- **Host**: El sistema operativo en el que se está ejecutando el contenedor
- **Contenedor**: Instancia de una imagen que ejecutamos con Docker

## Notas importantes

- Si un contenedor no ejecuta un proceso, se apaga automáticamente
- Aunqueno se pueden eliminar contenedores ejecutándose, podemos usar el flag -f para forzarlo: `docker container rm -f <id-contenedor>`

comprobando que me funciona pull request