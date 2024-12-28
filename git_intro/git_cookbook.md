# Guía Completa de Git para Repositorios en GitHub

Este documento te guiará a través de los comandos y flujos más comunes de Git, desde inicializar un repositorio hasta trabajar con ramas, commits y colaborar en un entorno basado en GitHub. Está estructurado para servir como referencia práctica.

---

## **1. Configuración Inicial de Git**

### Configura tus credenciales
Antes de empezar a trabajar con Git, configura tu nombre y correo electrónico:
```bash
git config --global user.name "Tu Nombre"
git config --global user.email "tuemail@dominio.com"
```

Verifica la configuración:
```bash
git config --list
```

---

## **2. Crear o Clonar un Repositorio**

### Crear un nuevo repositorio en GitHub
Si el repositorio no existe:
1. Ve a [GitHub](https://github.com) y crea un nuevo repositorio.
   - Elige un nombre para tu repositorio.
   - Decide si incluir un archivo `README.md` inicial o un `.gitignore`.

2. Copia la URL del repositorio remoto (HTTPS o SSH).

3. En tu máquina local, ejecuta los siguientes pasos:
   ```bash
   mkdir nombre-repositorio
   cd nombre-repositorio
   git init
   git remote add origin https://github.com/usuario/nombre-repositorio.git
   ```

### Crear un nuevo repositorio local
1. Crea una carpeta:
   ```bash
   mkdir nombre-repositorio
   cd nombre-repositorio
   ```

2. Inicializa un repositorio:
   ```bash
   git init
   ```

3. Crea un archivo de ejemplo:
   ```bash
   echo "# Mi Proyecto" > README.md
   ```

4. Haz commit de los cambios iniciales:
   ```bash
   git add .
   git commit -m "Primer commit"
   ```

5. Conecta tu repositorio local al remoto en GitHub:
   ```bash
   git remote add origin https://github.com/usuario/nombre-repositorio.git
   git branch -M main
   git push -u origin main
   ```

### Clonar un repositorio existente
Si el repositorio ya existe en GitHub:
```bash
git clone https://github.com/usuario/nombre-repositorio.git
```

---

## **3. Ciclo Básico de Git**

### Agregar cambios al repositorio
1. Verifica el estado actual:
   ```bash
   git status
   ```

2. Agrega archivos al área de preparación (staging):
   ```bash
   git add archivo.txt
   # o para agregar todos los archivos:
   git add .
   ```

3. Haz un commit con un mensaje:
   ```bash
   git commit -m "Mensaje descriptivo del cambio"
   ```

### Enviar cambios a GitHub
1. Sube los cambios:
   ```bash
   git push origin main
   ```

---

## **4. Ramas (Branches)**

### Crear y cambiar de rama
1. Crea una nueva rama:
   ```bash
   git branch nombre-rama
   ```

2. Cambia a esa rama:
   ```bash
   git checkout nombre-rama
   ```

3. Crea y cambia de rama al mismo tiempo:
   ```bash
   git checkout -b nombre-rama
   ```

### Ver y administrar ramas
1. Lista todas las ramas:
   ```bash
   git branch
   ```

2. Elimina una rama (que no estés usando):
   ```bash
   git branch -d nombre-rama
   ```

3. Elimina una rama remota:
   ```bash
   git push origin --delete nombre-rama
   ```

---

## **5. Colaboración en GitHub**

### Traer cambios del repositorio remoto
1. Actualiza la rama actual con cambios remotos:
   ```bash
   git pull origin main
   ```

2. Trae los cambios remotos sin aplicarlos automáticamente:
   ```bash
   git fetch origin
   ```

### Fusionar ramas (merge)
1. Cambia a la rama principal:
   ```bash
   git checkout main
   ```

2. Fusiona una rama en la rama actual:
   ```bash
   git merge nombre-rama
   ```

### Resolver conflictos
Si hay conflictos al fusionar, Git mostrará los archivos problemáticos. Edítalos para resolver los conflictos y luego:
```bash
git add archivo-conflictivo
git commit -m "Conflictos resueltos"
```

---

## **6. Revertir y Corregir Cambios**

### Revertir un archivo al último commit
```bash
git checkout -- archivo.txt
```

### Deshacer el último commit (manteniendo los cambios en staging)
```bash
git reset --soft HEAD~1
```

### Deshacer cambios no registrados en staging
```bash
git reset archivo.txt
```

### Eliminar cambios no guardados permanentemente
```bash
git checkout .
```

---

## **7. Comandos Avanzados**

### Ver historial de commits
```bash
git log
# Con detalles más compactos:
git log --oneline
```

### Ver diferencias entre commits
```bash
git diff
```

### Cambiar el mensaje de un commit (si es el más reciente)
```bash
git commit --amend -m "Nuevo mensaje"
```

---

## **8. Trabajando con Tags**

### Crear un tag
```bash
git tag -a v1.0 -m "Versión 1.0"
```

### Subir tags a GitHub
```bash
git push origin v1.0
```

---

## **9. Configuración Avanzada**

### Ignorar archivos no deseados
1. Crea un archivo `.gitignore`:
   ```
   node_modules/
   *.log
   .env
   ```

2. Agrega y haz commit del archivo `.gitignore`:
   ```bash
   git add .gitignore
   git commit -m "Agregar .gitignore"
   ```

---

## **10. Ejemplo Completo**

### Flujo típico de trabajo
1. Clona el repositorio:
   ```bash
   git clone https://github.com/usuario/nombre-repositorio.git
   cd nombre-repositorio
   ```

2. Crea una rama para tu nueva funcionalidad:
   ```bash
   git checkout -b feature-nueva
   ```

3. Haz cambios y confirma:
   ```bash
   echo "Cambio importante" >> archivo.txt
   git add archivo.txt
   git commit -m "Agregar cambio importante"
   ```

4. Sube la rama al repositorio remoto:
   ```bash
   git push origin feature-nueva
   ```

5. Haz un pull request en GitHub para fusionar tu rama.

---