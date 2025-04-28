# Comandos Básicos de Git

## Configuración Inicial
```bash
git config --global user.name "Tu Nombre"
git config --global user.email "tuemail@example.com"
```

## Crear un Repositorio
```bash
git init
```

## Clonar un Repositorio
```bash
git clone <url-del-repositorio>
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