# Git-Github
Fundamentals of Git &amp; Github

## Git
### Para ver que version tenemos de git y/o tener ayuda:

- `git -v`
- `git --version`
- `git -h`
- `git --help`

### Comandos Básicos de la Terminal

- `ls`: listados de todos los directorios que hay en el espacio actual.
- `cd`: para movernos hacia donde queremos (con tabulación o escribiendo directaqmente el nombre).
- `cd..`: volver hacia atras.
- flechas: nos movemos en los comandos que ya hemos usado.
- `pwd`: la ruta donde me encuentro.
- `mkdir` "nombre de la carpeta": para crear una carpeta
- `code .`: abre carpeta con visual studio code si este se encuentra instalado

### Configuración de Git

- `git config --global user.name "nombreUsuario"`
- `git config --global user.email "correo@example.com"`

### Git init

- `New-Item -Path "hello_git.py" -ItemType File`: crea fichero de cualquier tipo .py, .java, etc
- `git init`: Indica que queremos trabajar con git.

### Ramas en Git

- `git branch -m main`: cambia de master a main.
- `git config --global init.defaultBranch "nombre"`: configuaración para cambiar el nombre por defecto de la rama principal

### Git add y commit

- `git add nombrefichero.example`: agrega un fichero en especifico.
- `git add .`: agraga todos los ficheros.
- `git commit -m "comentario"`: se sube el cambio al repositorio de git.

### Git log y status

- `git status`: muestra el estado de los archivos
- `git log`: muestra la información de los commits.
- `git log --graph`: mas visual.
- `git log --graph --pretty=oneline`: muestra solo los mensajes.
- `git log --graph --decorate --all --oneline`: recorta el id.

### Git checkout y reset

- `git checkout nombreFichero.example`: para situarse en un punto de los cambios (mover el HEAD). Es como un rollback donde no he guardado
- `git checkout .`: todos los ficheros.
- `git reset`: resetea el archivo sin importar lo que se hizo despues.

### Git alias

- `git config --global alias.tree "log --graph --decorate --all --oneline"`: da un alias para un comando para ser más rapido (en este caso tree es el alias).
- `git tree`: acceder a ese alias

### Gitignore

- `New-Item -Path ".gitignore" -ItemType File`: crea el archivo necesario para poder ingnorar ficheros.

### Git diff

- `git diff`: ver que se ha modificado, sin haber guardado.

### Desplazamiento 

- `git checkout idCopia`: para moverse en los cambios del proyecto

### Git reset hard y reflog

- `git reset --hard idCommit`: va hacia un punto de la linea del tiempo, para atras o hacia adelante.
- `git reflog`: muestra el historial completo. 

### Git tag

- `git tag nombre_del_tag`: para puntos importantes por ejemplo versiones de la app. Nos movemos a este lugar con checkout (git checkout main para regresar donde estabamos).
- `git revert`: borra un commit (peligroso)

### Git branch y switch

- `git branch nombre_rama`: crea una nueva rama.
- `git switch nombre_rama`: para movernos a otra rama.

### Git merge

- `git merge main`: juntar con los cambios hechos en otra. rama (en este caso la principal)

### Conflictos en git

- Se elimina lo que no va en el editor, se agrega y se hace commit.

### Git stash

- cuando tenemos que salir de emergencia a otra rama, y tenemos codigo con errores.
- `git stash`: commit temporal y no afecta el arbol.
- `git stash list`: muestra lo que est pendiente.
- `git stash pop`: recupera lo que estabamos haciendo.
- `git stash drop`: borra los stash.

### Reintegración en git

- se integra al main haciendo un switch haciendo:
- `git diff login`: verificamos
- `git merge login`; agregamos al main lo hecho en la rama login

### Eliminación de ramas

- `git branch -d nombre_rama`: elimina la rama pero queda en memoria.

## Github
### Introducción a Github

Git funciona de manera local, por otro lado github funciona de manera remota.





