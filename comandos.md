# Comandos Básicos de Git

<a href="https://education.github.com/git-cheat-sheet-education.pdf">Manual de bolsillo de comandos de git</a>

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