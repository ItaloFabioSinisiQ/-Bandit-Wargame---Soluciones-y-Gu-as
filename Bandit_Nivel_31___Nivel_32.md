# 🔐 Bandit Level 31 → 32

<div align="center">

![Nivel](https://img.shields.io/badge/Nivel-31_→_32-blue?style=for-the-badge)
![Dificultad](https://img.shields.io/badge/Dificultad-Medio-orange?style=for-the-badge)

**Objetivo:** Git push con .gitignore bypass

[🌐 Desafío Original](https://overthewire.org/wargames/bandit/bandit32.html) | [📺 Video Tutorial](#)

</div>

---

Traducción al español:

**Bandit Nivel 31 → Nivel 32**

**Objetivo del Nivel**  
Hay un repositorio git en `ssh://bandit31-git@localhost/home/bandit31-git/repo` a través del puerto 2220. La contraseña para el usuario `bandit31-git` es la misma que para el usuario `bandit31`.

Clona el repositorio y encuentra la contraseña para el siguiente nivel.

**Comandos que podrías necesitar para resolver este nivel**  
`git`

---

## **🔍 Comandos Usados y su Explicación**

### **1. `git clone` (Clonar el repositorio)**
```bash
git clone ssh://bandit31-git@localhost:2220/home/bandit31-git/repo
```
- **¿Para qué sirve?**  
  - Descarga una copia del repositorio remoto a tu máquina local.  
- **Detalles importantes:**  
  - Usa el usuario `bandit31-git` (no `bandit31`).  
  - El puerto es `2220` (no el default `22`).  
  - Te pedirá la contraseña de `bandit31` (es la misma que usaste para entrar al servidor).  

---

### **2. `ls -a` (Listar archivos ocultos)**
```bash
ls -a
```
- **¿Para qué sirve?**  
  - Muestra todos los archivos, incluidos los ocultos (como `.gitignore`).  
- **¿Qué encontraste?**  
  - `README.md`: Instrucciones del nivel.  
  - `.gitignore`: Define qué archivos Git debe ignorar.  

---

### **3. `cat .gitignore` (Ver contenido de .gitignore)**
```bash
cat .gitignore
```
- **Salida:**  
  ```
  *.txt
  ```
- **¿Qué significa?**  
  - Git **ignorará cualquier archivo con extensión `.txt`**, por lo que no los subirá al repositorio.  
  - **Problema:** El reto te pide subir un `key.txt`, pero Git lo ignorará.  

---

### **4. `echo "'May I come in?'" > key.txt` (Crear el archivo con el contenido exacto)**
```bash
echo "'May I come in?'" > key.txt
```
- **¿Para qué sirve?**  
  - Crea un archivo `key.txt` con el contenido exacto que pide el reto (incluyendo las comillas simples).  
- **Error común:**  
  - Si no pones las comillas (`'May I come in?'`), el servidor rechazará el archivo.  

---

### **5. `git add -f key.txt` (Forzar la inclusión del archivo ignorado)**
```bash
git add -f key.txt
```
- **¿Para qué sirve?**  
  - El `-f` (**force**) obliga a Git a incluir el archivo **aunque esté en `.gitignore`**.  
- **¿Por qué es necesario?**  
  - Sin `-f`, Git ignoraría `key.txt` y no lo subiría.  

---

### **6. `git commit -m "Mensaje"` (Confirmar cambios)**
```bash
git commit -m "Added key.txt"
```
- **¿Para qué sirve?**  
  - Guarda los cambios en el historial local del repositorio.  
- **Importante:**  
  - Si no haces `commit`, el `push` no tendrá nada que enviar.  

---

### **7. `git push origin master` (Enviar cambios al servidor)**
```bash
git push origin master
```
- **¿Para qué sirve?**  
  - Sube tus cambios al repositorio remoto.  
- **¿Qué pasó en este nivel?**  
  - El servidor tiene un **"pre-receive hook"** (un script que verifica el archivo antes de aceptarlo).  
  - Si `key.txt` tiene el contenido correcto, **te dará la contraseña**, pero **rechazará el push** (es parte del juego).  

---

## **💡 ¿Por Qué el Push Falló pero el Nivel se Completó?**
- El servidor está configurado para:  
  1. **Verificar** que `key.txt` existe y tiene el contenido correcto.  
  2. **Mostrar la contraseña** (`3O9RfhqyAlVBEZpVb6LYStshZoqoSx5K`).  
  3. **Rechazar el push** (para evitar que modifiques el repositorio permanentemente).  

---

## **🔑 Contraseña del Siguiente Nivel (Bandit32)**
```
3O9RfhqyAlVBEZpVb6LYStshZoqoSx5K
```

---

## **📌 Resumen de lo Aprendido**
✅ **Git clone** → Descargar repositorios remotos.  
✅ **.gitignore** → Archivos que Git debe ignorar (usamos `-f` para forzar).  
✅ **git add -f** → Incluir archivos ignorados.  
✅ **git commit** → Guardar cambios localmente.  
✅ **git push** → Enviar cambios al servidor (aunque a veces falle por diseño).  

---




---

## 🔑 Contraseña para Nivel 32

```
3O9RfhqyAlVBEZpVb6LYStshZoqoSx5K
```

---

## 🚀 Conectarse al Siguiente Nivel

```bash
ssh bandit32@bandit.labs.overthewire.org -p 2220
```

---

<div align="center">

**[⬅️ Nivel Anterior](./Bandit_Nivel_30___Nivel_30.md)** | **[🏠 Volver al README](./README.md)** | **[➡️ Siguiente Nivel](./Bandit_Nivel_32___Nivel_33.md)**

</div>
