# Comandos Básicos de Git

<a href="https://education.github.com/git-cheat-sheet-education.pdf">Manual de bolsillo de comandos de git</a>
<a href="https://learn.microsoft.com/en-us/training/courses/gh-900t00#course-syllabus">Curso de Microsoft: GitHub Foundations</a>

## Configuración Inicial
```bash
git config --global user.name "Tu Nombre"
git config --global user.email "tuemail@example.com"
#cambiar el nombre de tu rama por default
git config --global init.defaultBranch <nombre-rama>


## Crear un Repositorio
bash
git init


## Clonar un Repositorio
```bash
git clone <url-del-repositorio>
```

## Descartar Cambios en un Archivo
```bash
git checkout -- <archivo>
```

## Ver el Estado del Repositorio
```bash
git status
```

## Añadir Cambios al Área de Staging
```bash
git add <archivo>
git add .
```

## Eliminar un Archivo del Área de Staging
```bash

git reset <archivo> 
Este comando elimina un archivo del área de staging, pero mantiene el archivo en el directorio de trabajo. Es decir, el archivo sigue existiendo en tu proyecto, pero ya no está preparado para ser confirmado (commit).

git rm --cached <archivo> 
Este comando también elimina un archivo del área de staging, pero se utiliza principalmente cuando deseas eliminar el archivo del repositorio sin eliminarlo del sistema de archivos local. Es útil, por ejemplo, cuando accidentalmente agregaste un archivo que no debería estar en el repositorio (como un archivo grande o confidencial).

Ambos comandos eliminan el archivo del área de staging, pero git reset es más general y no implica necesariamente que el archivo sea eliminado del repositorio, mientras que git rm --cached está más orientado a eliminar el archivo del control de versiones.
```

## Confirmar Cambios
```bash
git commit -m "Mensaje del commit"
```

## Ver el Historial de Cambios
```bash
git log
```

## Ver el Historial de Cambios de una Rama
```bash
git log <branch>..origin/branch
```

## Subir Cambios al Repositorio Remoto
```bash
git push origin <rama>
```

## Descargar Cambios del Repositorio Remoto
```bash
git pull
```

## Crear una Nueva Rama
```bash
git branch <nombre-rama>
```

## Cambiar de Rama
```bash
git checkout <nombre-rama>
```

## Fusionar Ramas
```bash
git merge <nombre-rama>
```

## Eliminar una Rama
```bash
git branch -d <nombre-rama>
```

## Ver Ramas Disponibles
```bash
git branch
```

## Explicación del Comando `git revert` y Diferencias con `git reset`

### `git revert`
El comando `git revert` se utiliza para deshacer un commit específico creando un nuevo commit que invierte los cambios realizados por el commit original. Es una forma segura de deshacer cambios porque no altera el historial del repositorio.

**Uso:**
```bash
git revert <commit>
```

### `git reset`
El comando `git reset` se utiliza para mover el puntero de la rama actual a un commit específico y, opcionalmente, modificar el área de staging y el directorio de trabajo dependiendo del flag utilizado:

- **`--soft`:** Solo mueve el puntero de la rama actual al commit especificado. Los cambios permanecen en el área de staging.
- **`--mixed` (por defecto):** Mueve el puntero de la rama actual al commit especificado y elimina los cambios del área de staging, pero los mantiene en el directorio de trabajo.
- **`--hard`:** Mueve el puntero de la rama actual al commit especificado y elimina los cambios tanto del área de staging como del directorio de trabajo.

**Uso:**
```bash
git reset --soft <commit>
git reset --mixed <commit>
git reset --hard <commit>
```

### Diferencias Principales
- `git revert` no altera el historial del repositorio y es ideal para revertir cambios en repositorios compartidos.
- `git reset` puede reescribir el historial, lo que lo hace más adecuado para repositorios locales o ramas privadas.

### Cuándo Usar Cada Uno
- Usa `git revert` cuando trabajes en un repositorio compartido y necesites deshacer un commit sin alterar el historial.
- Usa `git reset`:
  - Con `--soft` si deseas mantener los cambios en el área de staging para un nuevo commit.
  - Con `--mixed` si deseas mantener los cambios en el directorio de trabajo pero no en el área de staging.
  - Con `--hard` si deseas descartar completamente los cambios del área de staging y del directorio de trabajo.

## `git tag` y `git checkout`

### `git tag`
El comando `git tag` se utiliza para crear **etiquetas** en un repositorio Git. Las etiquetas son referencias que apuntan a un commit específico, generalmente utilizadas para marcar versiones importantes (por ejemplo, versiones de lanzamiento).

**Uso común:**
- Crear una etiqueta ligera:
  ```bash
  git tag <nombre-etiqueta>
  ```
- Crear una etiqueta anotada (con mensaje y metadatos):
  ```bash
  git tag -a <nombre-etiqueta> -m "Mensaje de la etiqueta"
  ```
- Listar etiquetas existentes:
  ```bash
  git tag
  ```
- Subir etiquetas al repositorio remoto:
  ```bash
  git push origin <nombre-etiqueta>
  ```
- Subir todas las etiquetas:
  ```bash
  git push origin --tags
  ```

### `git checkout`
El comando `git checkout` se utiliza para cambiar entre ramas o restaurar archivos en el directorio de trabajo. Es una herramienta versátil que permite moverse dentro del historial del repositorio o deshacer cambios en archivos específicos.

**Uso común:**
- Cambiar a una rama:
  ```bash
  git checkout <nombre-rama>
  ```
- Restaurar un archivo al estado del último commit:
  ```bash
  git checkout -- <archivo>
  ```
- Cambiar a un commit específico (modo "detached HEAD"):
  ```bash
  git checkout <hash-del-commit>
  ```
- regresar a la rama actual:
  ```bash
  git checkout -
  ```
- crear una rama nueva y cambiar a ella:
  ```bash
  git checkout -b <nombre-rama>
  ```


### Diferencias entre `git tag` y `git checkout`
1. **Propósito:**
   - `git tag` se utiliza para marcar un commit específico con una etiqueta, generalmente para identificar versiones importantes.
   - `git checkout` se utiliza para cambiar entre ramas, commits o restaurar archivos.

2. **Persistencia:**
   - Las etiquetas creadas con `git tag` son permanentes y se pueden compartir con otros colaboradores.
   - `git checkout` no crea nada permanente; simplemente cambia el estado del directorio de trabajo o la rama activa.

3. **Contexto de uso:**
   - Usa `git tag` para marcar puntos importantes en el historial del proyecto.
   - Usa `git checkout` para navegar por el historial, cambiar de rama o deshacer cambios en archivos.

## Cómo Eliminar Etiquetas en Git

### Eliminar una Etiqueta Localmente
Para eliminar una etiqueta en tu repositorio local, usa el siguiente comando:
```bash
git tag -d <nombre-etiqueta>
```

### Eliminar una Etiqueta en el Repositorio Remoto
Primero, elimina la etiqueta localmente con el comando anterior. Luego, para eliminarla del repositorio remoto, usa:
```bash
git push origin --delete <nombre-etiqueta>
```

Este proceso asegura que la etiqueta sea eliminada tanto localmente como en el repositorio remoto.

## `Git show` 

El comando `git show` se utiliza para mostrar el contenido de un archivo en el repositorio remoto.
pero tambien puede ver tags, commits, diffs, etc.

**Uso:**
```bash
git show <commit>:<archivo>
```

Ejemplo:
```bash
git show HEAD:README.md
```
