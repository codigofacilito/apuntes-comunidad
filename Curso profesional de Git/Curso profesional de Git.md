# Curso profesional de Git

# Índice
[¿Qué es Git?](#¿qué-es-git?)

[GitHub & GitLab](#GitHub-y-GitLab)

[Instalación](#instalación)

[Identificación en Git](#personalización)

[Crear repositorio y agregar archivos](#crear-repositorio-y-agregar-archivos)

[Crear commits](#crear-commits)

[¿Qué es RESET?](#¿Qué-es-RESET?)

[Crear ramas y cómo fusionar](#crear-ramas-y-cómo-fusionar)

[¿Cómo gestionar GitHub/GitLab con Git?](#¿Cómo-gestionar-GitHub/GitLab-con-Git)


<br>
<br>

# ¿Qué es Git? 
Es un sistema de control de versiones `SCV`, fue creado por **Linus Torvalds** el propósito de tener eficiencia en el mantenimiento de versiones en proyectos de desarrollo de software. 
Ayuda a gestionar lo trabajado a lo largo del tiempo con distintas colaboraciones de manera simultánea. 
Dicho esto y ante la eficiencia del SCV, es y ha sido factible en proyecto de índole ajena como la _escritura_, _diseño_, _programación gráfica_, etcétera.

<br>

[Regresa a índice.](#índice)

<br>


# GitHub y GitLab
Están ligados a Git por algo más que el nombre. 
Son sitios que te permiten tener la accesibilidad de un sistema de control de versiones, pero en internet. Lo que proporciona la ventaja de trabajo colaborativo. Cuentan con un componente social con el hecho de compartir trabajo en conjunto, de esta manera se han convertido en  “redes sociales” para programadores, y vea el trabajo de otro (dadas las propiedades configuradas del usuario). 

<br>

[Regresa a índice.](#índice)

<br>


# Instalación

### Mac
Ir al [link](https://git-scm.com/) para descargar el ejecutable. La página automáticamente detecta el S.O. que emplea el equipo.
* Preferencias del sistema
* Seguridad y privacidad
	- Abrir la instalación. Instalación sencilla.

<br>

### Windows
Click en el [link](https://git-scm.com/) para descargar el ejecutable.
Instalación sencilla de Git Bash.

<br>

### GNU/Linux
Abriremos nuestra terminal y actualizamos la lista de paquetes en caso de que el S.O. lo necesite:
* ``` sudo apt-get update ```
* ``` sudo apt-get upgrade ```
 
Enseguida, instalamos Git:
* ``` apt-get install git ```
<br>

[Regresa a índice.](#índice)

<br>


# Identificación en Git
### Ingreso de datos personales
Podría no parecer relevante, pero esta información será útil en el momento de creación de commits y dado en futuro que otros los visualicen/consulten todo de ellos.

### Configurar nombre
```ssh
	git config --global user.name "Loremp Impsum"
```
> Para verificar ```  git config --global user.name ```
           
### Configurar email
```ssh
    git config --global user.email "example@email.com"
```
> Para verificar ```  git config --global user.email ```

### Color en consola
```ssh
    git config --global color.ui true
```
<br>

Git tiene tres estados o secciones, los cuales se identifican como árboles: 
* Directorio de trabajo (Working area).
* Índice de archivos (Staging area). 
* Head (Head area).
<br>

[Regresa a índice.](#índice)

<br>

# Crear repositorio y agregar archivos
Una vez que ya se tiene una carpeta o directorio de trabajo establecido, se mapea ``` cd <Folder Name> ```

### Repositorio
Se inicializa el directorio
```ssh
    git init
```

Revisar el estado del repositorio
```ssh
    git status
```

### Add files

##### Únicamente un archivo 
```      git add "example.txt" ```

##### Todos el contenido de la carpeta
```      git add . ```

```     git add -A ```
<br>

#### Borrar de Staging
> __Catched__ significa que el archivo se encuentra en memoria ram, no en database histórico del proyecto, el comando lo extrae de ahí o deshace el _add_.

```ssh 
    git rm --cached example.txt 
```

<br>

[Regresa a índice.](#índice)

<br>

# Crear commits

Una vez gestionados en _staging_ se crean los commits para marcar el registro en el repositorio.
```ssh 
    git commit -m "Mensaje de ejemplo"
```

Para visualizar los cambios después de los commits
```ssh 
    git log
```

Para volver a un commit
```ssh 
    git checkout <581ea1bf08afe8c>  => ejemplo de id de commit
```

Para regresar el último commit realizado antes del comando anterior
```ssh 
    git checkout master
```

<br>

[Regresa a índice.](#índice)

<br>


# ¿Qué es RESET?
> 🚩 COMANDOS DE ALTO IMPACTO 🚩

Los reset con saltos como los _checkout_ pero que borran todo a su paso: 
* **Reset Soft**. Te lleva a un commit borrando los posteriores pero mantiene intacto el directorio de trabajo.
* **Reset Midset**. Borra los commits a su paso y todo lo que se encuentra en staging, pero no las borra del directorio local.
* **Reset Hard**. Borra todo lo que haya sucedido después del commit al que se dirige y convierte al commit en el que se está viajando en el nuevo máster.

__Soft__
```ssh 
    git reset --soft <581ea1bf08afe8c>
```

__Hard__
```ssh 
    git reset --hard <581ea1bf08afe8c>
```
<br>

[Regresa a índice.](#índice)

<br>

# Crear ramas y cómo fusionar
Todos los commit se trabajan sobre una rama por default _master_. Crear una rama es copiar todo lo trabajado desde una determinada, pasar esa info a otra y continuar trabajando sin afectar el flujo de trabajo principal. 

Para crear una rama
```ssh 
    git branch <branchname>
```
> Para verificar ramas  ``` git branch ``` 

Para viajar a otra rama 
```ssh 
    git checkout <branchname>
```
> Cuando se viaja a otra rama, se lleva a sí misma todos los commit realizados antes.

Para regresar a la rama máster
```ssh 
    git checkout master
```

Para fusionar ramas
```ssh 
    git merge <branchname>
```

Borrar ramas
```ssh 
    git branch <branchname> -d
```
> Cuando se escriben las cosas con mayúscula es similar a ejecutar tareas en privilegio admin, solo realiza la acción sin preguntar si deseas realizarla o no. 

<br>

[Regresa a índice.](#índice)

<br>


# ¿Cómo gestionar GitHub/GitLab con Git?
:octocat: Github/GitLab son sistemas que permiten arrojar proyectos de manera remota, usando la gestión de `Git`.

Estructura del repositorio:
 - Watch
 - Star
 - Fork
 - Documentación README
 - Commits
 - Branches
 - Contribuciones
 - Issues
 - Pull request
 - etc...

## Git clone
Para obtener de manera local un repositorio de GitHub/GitLab
> Copiamos a portapapeles el link https del repositorio y hacemos uso de ello en el siguiente comando:
```ssh 
    git clone <linkhttps>
```

Para subir/sincronizar un repositorio local hacia un repositorio en GitHub/GitLab
* Se crea un repositorio del mismo nombre al local.
* Se vincula el proyecto local 
```ssh 
    git remote add origin <linkhttps>
```
> Verificar ``` git remote -v ```

Para remover conexión
```ssh 
    git remote remove origin
```

Para sincronizar cambios de manera remota
```ssh 
    git push -u origin master
```

Para sincronizar en otra rama
```ssh 
    git push origin <branchname>
```

<br>

[Regresa a índice.](#índice)

<br>