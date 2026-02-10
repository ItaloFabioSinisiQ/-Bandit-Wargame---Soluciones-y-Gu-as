# 🔐 Bandit Level 29 → 30

<div align="center">

![Nivel](https://img.shields.io/badge/Nivel-29_→_30-blue?style=for-the-badge)
![Dificultad](https://img.shields.io/badge/Dificultad-Medio-orange?style=for-the-badge)

**Objetivo:** Explorar ramas Git (dev branch)

[🌐 Desafío Original](https://overthewire.org/wargames/bandit/bandit30.html) | [📺 Video Tutorial](#)

</div>

---


## Objetivo del Nivel
Hay un repositorio git en `ssh://bandit29-git@localhost/home/bandit29-git/repo` a través del puerto 2220. La contraseña para el usuario `bandit29-git` es la misma que para el usuario `bandit29`.

Clona el repositorio y encuentra la contraseña para el siguiente nivel.

## **1. Entendiendo el problema**
- **Objetivo**: Encontrar la contraseña de **bandit30** en un repositorio Git.
- **Datos proporcionados**:
  - Repositorio: `ssh://bandit29-git@localhost:2220/home/bandit29-git/repo`
  - Usuario: `bandit29-git` (misma contraseña que `bandit29`)
- **Posibles pistas**:
  - Git guarda historial de cambios, ramas y archivos ocultos.
  - La contraseña puede estar en un commit antiguo, una rama diferente o en metadata.

---

## **2. Pasos

### **Paso 1: Crear un directorio temporal**
Como no tenemos permisos de escritura en `/home/bandit29`, usamos `/tmp` para clonar el repositorio.
```bash
bandit29@bandit:~$ mkdir -p /tmp/mi_repo  # -p evita errores si ya existe
bandit29@bandit:~$ cd /tmp/mi_repo
```
- **Explicación**:
  - `/tmp` es un directorio temporal donde cualquier usuario puede escribir.
  - `mkdir -p` crea el directorio solo si no existe.

---

### **Paso 2: Clonar el repositorio Git**
```bash
bandit29@bandit:/tmp/mi_repo$ git clone ssh://bandit29-git@localhost:2220/home/bandit29-git/repo
```
- **Respuesta esperada**:
  - Git pedirá confirmación de conexión SSH (escribimos `yes`).
  - Luego pedirá la contraseña de `bandit29-git` (la misma que para `bandit29`).

- **Posibles errores**:
  - **Error en la URL**: Si escribes mal la URL (como `ss h://`), fallará.
  - **Permiso denegado**: Si no usas `/tmp`, Git no podrá clonar.

---

### **Paso 3: Entrar al repositorio clonado**
```bash
bandit29@bandit:/tmp/mi_repo$ cd repo
```
- **Explicación**:
  - `git clone` crea una carpeta llamada `repo` (por defecto, el nombre del repositorio).

---

### **Paso 4: Ver archivos en el repositorio**
```bash
bandit29@bandit:/tmp/mi_repo/repo$ ls
README.md
```
- **Contenido de `README.md`**:
```md
# Bandit Notes
Some notes for bandit30 of bandit.

## credentials

- username: bandit30
- password: <no passwords in production!>
```
- **Análisis**:
  - El archivo principal no contiene la contraseña real.
  - Git guarda historial de cambios, así que debemos revisar commits o ramas alternativas.

---

### **Paso 5: Ver el historial de commits**
```bash
bandit29@bandit:/tmp/mi_repo/repo$ git log
```
- **Salida**:
```
commit 3b8b91fc3c... (HEAD -> master)
  Author: Ben Dover
  Message: fix username

commit 8d2ffeb5e4...
  Author: Ben Dover
  Message: initial commit of README.md
```
- **Explicación**:
  - Hay dos commits, pero ninguno parece tener la contraseña.
  - Debemos buscar en otras ramas.

---

### **Paso 6: Listar todas las ramas disponibles**
```bash
bandit29@bandit:/tmp/mi_repo/repo$ git branch -a
```
- **Salida**:
```
* master
  remotes/origin/HEAD -> origin/master
  remotes/origin/dev
  remotes/origin/master
  remotes/origin/sploits-dev
```
- **Análisis**:
  - Hay una rama remota llamada `dev` que podría contener información útil.

---

### **Paso 7: Cambiar a la rama `dev`**
```bash
bandit29@bandit:/tmp/mi_repo/repo$ git checkout dev
```
- **Explicación**:
  - `git checkout dev` cambia a la rama `dev`.
  - Las ramas de desarrollo (`dev`) a veces contienen información no publicada en `master`.

---

### **Paso 8: Ver el README.md actualizado**
```bash
bandit29@bandit:/tmp/mi_repo/repo$ cat README.md
```
- **Contenido**:
```md
# Bandit Notes
Some notes for bandit30 of bandit.

## credentials

- username: bandit30
- password: qp30ex3VLz5MDG1n91YowTv4Q8l7CDZL
```
- **¡Éxito!** La contraseña está aquí.

---

## **3. ¿Por qué funcionó esto?**
- **Rama `dev` vs `master`**:
  - En Git, `master` suele ser la versión estable, mientras que `dev` contiene cambios en desarrollo.
  - Alguien olvidó quitar la contraseña antes de fusionar a `master`.

- **Lección aprendida**:
  - Siempre revisa **todas las ramas** en un repositorio Git.
  - Usa `git branch -a` para listar ramas ocultas.

---

## **4. Posibles errores y soluciones**
| **Error**                     | **Causa**               | **Solución**                                                   |
| ----------------------------- | ----------------------- | -------------------------------------------------------------- |
| `Permission denied` al clonar | No estás en `/tmp`      | Usa `mkdir /tmp/mi_repo && cd /tmp/mi_repo`                    |
| `Could not resolve host`      | URL mal escrita         | Usa `ssh://bandit29-git@localhost:2220/home/bandit29-git/repo` |
| Contraseña incorrecta         | Usaste la de otro nivel | Verifica la contraseña actual de `bandit29`                    |

---

## **5. Conclusión**
- **Contraseña encontrada**: `qp30ex3VLz5MDG1n91YowTv4Q8l7CDZL`
- **Método correcto**:
  1. Clonar el repo en `/tmp`.
  2. Cambiar a la rama `dev`.
  3. Leer `README.md` en esa rama.



---

## 🔑 Contraseña para Nivel 30

```
qp30ex3VLz5MDG1n91YowTv4Q8l7CDZL
```

---

## 🚀 Conectarse al Siguiente Nivel

```bash
ssh bandit30@bandit.labs.overthewire.org -p 2220
```

---

<div align="center">

**[⬅️ Nivel Anterior](./Bandit_Nivel_28___Nivel_28.md)** | **[🏠 Volver al README](./README.md)** | **[➡️ Siguiente Nivel](./Bandit_Nivel_30___Nivel_31.md)**

</div>
