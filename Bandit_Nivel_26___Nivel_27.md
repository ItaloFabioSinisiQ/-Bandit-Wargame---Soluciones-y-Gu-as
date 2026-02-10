# 🔐 Bandit Level 26 → 27

<div align="center">

![Nivel](https://img.shields.io/badge/Nivel-26_→_27-blue?style=for-the-badge)
![Dificultad](https://img.shields.io/badge/Dificultad-Medio-orange?style=for-the-badge)

**Objetivo:** Usar binario setuid desde shell escapado

[🌐 Desafío Original](https://overthewire.org/wargames/bandit/bandit27.html) | [📺 Video Tutorial](#)

</div>

---


---

### **Explicación Detallada Paso a Paso**

#### **1. Conexión al servidor**
- **Comando**:  
  ```sh
  ssh bandit26@bandit.labs.overthewire.org -p 2220
  ```
- **Propósito**:  
  Conectarse al juego OverTheWire como el usuario `bandit26` (usando el puerto `2220`).  
- **Detalle**:  
  - Requiere la contraseña del nivel anterior (`bandit25` → `bandit26`).  
  - Al ingresar, el sistema muestra un mensaje de bienvenida y reglas del juego.  

---

#### **2. Exploración del directorio home**
- **Comando**:  
  ```sh
  ls
  ```
- **Resultado**:  
  ```
  bandit27-do  text.txt
  ```
- **Propósito**:  
  Listar archivos en el directorio home de `bandit26`.  
- **Importante**:  
  - `bandit27-do` es un binario especial con permisos `setuid`.  
  - `text.txt` es un archivo de texto (no relevante para este nivel).  

---

#### **3. Análisis del binario `bandit27-do`**
- **Comando**:  
  ```sh
  file bandit27-do
  ```
- **Resultado**:  
  ```
  bandit27-do: setuid ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked, interpreter /lib/ld-linux.so.2, BuildID[sha1]=35d353cf6d732f515a73f50ed205265fe1e68f90, for GNU/Linux 3.2.0, not stripped
  ```
- **Explicación**:  
  - **`setuid`**: Indica que el binario se ejecuta con los permisos de su propietario (`bandit27`), no del usuario que lo ejecuta (`bandit26`).  
  - **`ELF 32-bit`**: Es un ejecutable para Linux.  

---

#### **4. Ejecución del binario sin argumentos**
- **Comando**:  
  ```sh
  ./bandit27-do
  ```
- **Resultado**:  
  ```
  Run a command as another user.
  Example: ./bandit27-do id
  ```
- **Propósito**:  
  - El binario está diseñado para **ejecutar comandos como `bandit27`**.  
  - Muestra un mensaje de ayuda indicando cómo usarlo.  

---

#### **5. Verificación de permisos con `id`**
- **Comando**:  
  ```sh
  ./bandit27-do id
  ```
- **Resultado**:  
  ```
  uid=11026(bandit26) gid=11026(bandit26) euid=11027(bandit27) groups=11026(bandit26)
  ```
- **Explicación**:  
  - **`uid` y `gid`**: Tu usuario real sigue siendo `bandit26`.  
  - **`euid=11027(bandit27)`**: El binario se ejecuta con **privilegios de `bandit27`** (debido a `setuid`).  

---

#### **6. Lectura de la contraseña de `bandit27`**
- **Primer intento (error)**:  
  ```sh
  ./bandit27-do cat /etc/bandit_pas/bandit27
  ```
  - **Error**: `No such file or directory` (typo en `/etc/bandit_pas`).  
- **Segundo intento (éxito)**:  
  ```sh
  ./bandit27-do cat /etc/bandit_pass/bandit27
  ```
  - **Resultado**:  
    ```
    upsNCc7vzaRDx6oZC6GiR6ERwe1MowGB
    ```
- **Clave del nivel**:  
  - El archivo `/etc/bandit_pass/bandit27` solo puede ser leído por `bandit27`.  
  - Gracias al `setuid`, el binario `bandit27-do` te permitió leerlo.  

---

### **¿Por qué funciona?**
- **Mecanismo `setuid`**:  
  - Permite que un binario se ejecute con los permisos de su **dueño** (en este caso, `bandit27`).  
  - Sin esto, `bandit26` no podría leer `/etc/bandit_pass/bandit27`.  
- **Aplicación en seguridad**:  
  - Es una técnica común en sistemas Linux para delegar permisos elevados de forma controlada.  

---

### **Visualización para Alumnos**
Puedes resumirlo así:  

1. **`setuid`**:  
   - "Este binario actúa como `bandit27` aunque lo ejecute `bandit26`".  
2. **Uso del binario**:  
   - "`./bandit27-do <comando>` ejecuta `<comando>` como si fueras `bandit27`".  
3. **Lectura del password**:  
   - "Como `bandit27` puede leer su propio password, usamos el binario para hacerlo".  

---

### **Siguiente Nivel**
- **Comando para conectarse a `bandit27`**:  
  ```sh
  ssh bandit27@bandit.labs.overthewire.org -p 2220
  ```
- **Password**: `upsNCc7vzaRDx6oZC6GiR6ERwe1MowGB`.  

---

### **Resumen en Tabla**
| Comando | Acción | Importancia |
|---------|--------|-------------|
| `ls` | Listar archivos | Encontrar `bandit27-do`. |
| `file bandit27-do` | Ver tipo de archivo | Confirmar que es `setuid`. |
| `./bandit27-do id` | Ver permisos | Mostrar `euid=bandit27`. |
| `./bandit27-do cat /etc/bandit_pass/bandit27` | Leer password | Obtener la flag. |

### **¿Por qué es necesario achicar la terminal y usar `:set shell=/bin/bash` + `:shell` en Bandit Level 26?**  

En el **Bandit Level 26**, cuando intentas conectarte normalmente con:  
```sh
ssh bandit26@bandit.labs.overthewire.org -p 2220
```  
sucede algo inusual: **la sesión se cierra inmediatamente** después de ingresar la contraseña.  

Esto ocurre porque el **shell asignado a `bandit26` no es `/bin/bash`**, sino un programa especial que termina la conexión.  

---

## **Solución: Reducir la ventana y usar `:set shell=/bin/bash` + `:shell`**  

### **1. ¿Por qué achicar la terminal?**  
- Al conectarte como `bandit26`, el sistema ejecuta un **"shell de conexión"** configurado en:  
  ```sh
  /etc/passwd
  ```
- Si revisas el archivo (en niveles posteriores), verás que `bandit26` tiene asignado:  
  ```sh
  bandit26:x:11026:11026:bandit level 26:/home/bandit26:/usr/bin/showtext
  ```
  - **`/usr/bin/showtext`** es un script que **cierra la conexión si la terminal es demasiado grande**.  
  - Si la terminal es **pequeña** (ej: menos de 15 líneas), el script **no fuerza el cierre** y permite entrar en modo **"more"** (un visualizador de texto).  

### **2. ¿Qué hace `:set shell=/bin/bash`?**  
Cuando estás en el visualizador `more`:  
1. Presiona `v` para entrar en el editor **`vi`** (basado en `more`).  
2. Luego, ejecuta en modo comando de `vi`:  
   ```vim
   :set shell=/bin/bash
   ```
   - Esto **cambia el shell temporalmente** a `/bin/bash` (en lugar del shell restringido).  

### **3. ¿Qué hace `:shell`?**  
- Después de configurar el shell, ejecutas:  
  ```vim
  :shell
  ```
  - Esto **lanza una shell (`/bin/bash`)** dentro de la sesión de `vi`.  
  - Ahora tienes una terminal funcional como `bandit26`.  

---

## **¿Por qué funciona esto?**  
- El truco aprovecha que:  
  - `more` permite entrar en `vi` (con `v`).  
  - `vi` permite cambiar el shell y ejecutarlo.  
  - Al achicar la terminal, evitas que `/usr/bin/showtext` cierre la sesión.  

---

### **Explicación para Alumnos**  
🔹 **Problema**:  
- `bandit26` no te deja usar una shell normal.  
- Su configuración cierra la conexión automáticamente.  

🔹 **Solución**:  
1. **Achicar la terminal** → Engaña al sistema para que no cierre la sesión.  
2. **Entrar en `vi`** → Usar `:set shell=/bin/bash` para cambiar a una shell útil.  
3. **Ejecutar `:shell`** → Obtener una terminal funcional.  

🔹 **Conclusión**:  
- Es un **bypass ingenioso** que aprovecha el comportamiento de `more` y `vi`.  
- Sin esto, no podrías ejecutar `./bandit27-do` para avanzar al siguiente nivel.  

---

### **Comandos Clave**  
| Comando | Explicación |
|---------|------------|
| `:set shell=/bin/bash` | Cambia el shell a `/bin/bash` en `vi`. |
| `:shell` | Abre una nueva shell con los permisos actuales. |
| `./bandit27-do cat /etc/bandit_pass/bandit27` | Lee la contraseña de `bandit27`. |



---

## 🔑 Contraseña para Nivel 27

```
upsNCc7vzaRDx6oZC6GiR6ERwe1MowGB
```

---

## 🚀 Conectarse al Siguiente Nivel

```bash
ssh bandit27@bandit.labs.overthewire.org -p 2220
```

---

<div align="center">

**[⬅️ Nivel Anterior](./Bandit_Nivel_25___Nivel_25.md)** | **[🏠 Volver al README](./README.md)** | **[➡️ Siguiente Nivel](./Bandit_Nivel_27___Nivel_28.md)**

</div>
