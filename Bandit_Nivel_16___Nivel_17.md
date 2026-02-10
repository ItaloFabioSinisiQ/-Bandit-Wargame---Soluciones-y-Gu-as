# 🔐 Bandit Level 16 → 17

<div align="center">

![Nivel](https://img.shields.io/badge/Nivel-16_→_17-blue?style=for-the-badge)
![Dificultad](https://img.shields.io/badge/Dificultad-Medio-orange?style=for-the-badge)

**Objetivo:** Escanear puertos y usar clave privada SSH

[🌐 Desafío Original](https://overthewire.org/wargames/bandit/bandit17.html) | [📺 Video Tutorial](#)

</div>

---

Aquí tienes una guía paso a paso, muy detallada, de cómo pasar de Bandit Level 16 a Bandit Level 17, usando la contraseña actual:

---

### **Paso 1: Verifica tu contraseña actual (Bandit 16)**

La contraseña que te permite avanzar a Bandit 17 se obtiene enviando la contraseña actual de Bandit 16.  
Para verla, ejecuta:

```bash
cat /etc/bandit_pass/bandit16
```

- **Nota:**
    
    - El archivo oculto `.bandit15.password` que viste en tu directorio de Bandit 16 corresponde a la contraseña que usaste para ingresar a este nivel (Bandit 15 → 16).
        
    - Ahora debes usar la contraseña de Bandit 16, la cual se encuentra en `/etc/bandit_pass/bandit16`.
        

---

### **Paso 2: Verifica que el puerto donde enviarás la contraseña esté abierto**

Según el enunciado, el servicio que acepta la contraseña se encuentra en un puerto dentro del rango 31000 a 32000. Para saber qué puertos están abiertos en tu máquina (Bandit 16), puedes usar `nmap`. Por ejemplo:

```bash
nmap -p31000-32000 localhost
```

- Esto te mostrará los puertos abiertos. En algunos walkthroughs se usa un puerto específico (por ejemplo, 31790) pero la idea es confirmar que hay un servicio escuchando.
    

---

### **Paso 3: Enviar la contraseña de Bandit 16 al puerto correcto usando SSL/TLS**

Debido a que el servicio utiliza SSL/TLS, usaremos `openssl s_client`. El comando general es:

```bash
echo "<CONTRASEÑA_BANDIT16>" | openssl s_client -connect localhost:<PUERTO> -quiet
```

- **Reemplaza `<CONTRASEÑA_BANDIT16>`** con el valor obtenido en el Paso 1.
    
- **Reemplaza `<PUERTO>`** con el número del puerto que hayas identificado (por ejemplo, 31790 o el que funcione según tu escaneo).
    

**Ejemplo:**

Si tu contraseña de Bandit 16 es `abcDEF123...` (obtenida del archivo `/etc/bandit_pass/bandit16`) y el puerto correcto es 31790, el comando sería:

```bash
echo "abcDEF123..." | openssl s_client -connect localhost:31790 -quiet
```

- **`echo`** envía la contraseña a la salida estándar.
    
- **El pipe (`|`)** la redirige como entrada a `openssl s_client`.
    
- **`openssl s_client -connect localhost:31790 -quiet`** establece una conexión SSL/TLS al puerto indicado y, con la opción `-quiet`, reduce la verbosidad para que puedas ver la respuesta esencial.
    

---

### **Paso 4: Recibe la respuesta**

El servicio, al verificar la contraseña enviada, responderá con las credenciales del siguiente nivel (Bandit 17).  
La salida debería incluir un mensaje de "Correct!" y la clave privada (o la contraseña) para Bandit 17.

- **Copia esa respuesta** (la contraseña o la clave privada) que te dé el servicio.
    

---

### **Paso 5: Conéctate al nivel Bandit 17**

Utiliza la credencial obtenida para iniciar sesión en Bandit 17. Por ejemplo, si recibiste una contraseña:

```bash
ssh bandit17@bandit.labs.overthewire.org -p 2220
```

- Cuando te pida la contraseña, pega la que obtuviste en el Paso 4.
    

O, si la respuesta es una clave privada, guárdala en un archivo (con permisos 600) y úsala para conectar mediante el parámetro `-i`.

---

### **Resumen Completo de los Comandos:**

1. **Obtener la contraseña actual (Bandit 16):**
    
    ```bash
    cat /etc/bandit_pass/bandit16
    ```
    
2. **Escanear puertos abiertos en el rango (opcional):**
    
    ```bash
    nmap -p31000-32000 localhost
    ```
    
3. **Enviar la contraseña a través de SSL/TLS (ejemplo en puerto 31790):**
    
    ```bash
    echo "TU_CONTRASEÑA_BANDIT16" | openssl s_client -connect localhost:31790 -quiet
    ```
    
4. **Recibir y copiar la respuesta (la contraseña o clave privada de Bandit 17).**
    
5. **Conectarse al siguiente nivel:**
    
    ```bash
    ssh bandit17@bandit.labs.overthewire.org -p 2220
    ```
    
    Ingresa la nueva contraseña cuando se te solicite.
    

---

La ruta `/etc/bandit_pass/bandit16` se usa porque **OverTheWire Bandit** almacena las contraseñas de cada nivel en archivos dentro del directorio `/etc/bandit_pass/`.

### **Explicación detallada de la ruta**

📌 **`/etc/`** → Es un directorio estándar en Linux donde se guardan archivos de configuración y datos del sistema.  
📌 **`/etc/bandit_pass/`** → Es un subdirectorio donde Bandit guarda las contraseñas de cada nivel.  
📌 **`/etc/bandit_pass/bandit16`** → Es el archivo que contiene la contraseña para el nivel 16.

---

### **Ejemplo visual de los archivos de contraseñas**

Si listamos los archivos en `/etc/bandit_pass/` con:

```bash
ls /etc/bandit_pass/
```

Veremos algo así:

```
bandit0  bandit1  bandit2  bandit3  bandit4  ... bandit16  bandit17  ...
```

Cada archivo tiene la contraseña del siguiente nivel.

- **Ejemplo:**
    
    - `bandit16` → Contiene la contraseña para acceder a **bandit17**.
        
    - `bandit17` → Contiene la contraseña para **bandit18**.
        

Por eso, al ejecutar:

```bash
cat /etc/bandit_pass/bandit16
```

El sistema muestra la contraseña que necesitas para acceder a `bandit17`.

---

### **📌 ¿Por qué no todos pueden ver estos archivos?**

Solo el usuario correcto puede leer su contraseña porque los permisos están configurados así:

```bash
ls -l /etc/bandit_pass/
```

Salida típica:

```
-r-------- 1 bandit16 bandit16 33 Mar 31  2024 bandit16
-r-------- 1 bandit17 bandit17 33 Mar 31  2024 bandit17
```

📌 **Significado de los permisos `-r--------`**:

- **El usuario propietario (bandit16) puede leer (`r--`)**
    
- **Nadie más tiene permiso de lectura (`--------`)**
    

Por eso, si intentas ver la contraseña de otro nivel (por ejemplo, `bandit17`) antes de tiempo, recibirás un error de "Permission denied".

---

### **📌 Resumen final**

- **Las contraseñas están en `/etc/bandit_pass/`** por diseño del juego.
    
- **Cada usuario solo puede leer la contraseña de su nivel.**
    
- **La ruta completa `/etc/bandit_pass/bandit16` contiene la clave para entrar a `bandit17`**.
    



---

## 🔑 Contraseña para Nivel 17

```
EReVavePLFHtFlFsjn3hyzMlvSuSAcRD
```

---

## 🚀 Conectarse al Siguiente Nivel

```bash
ssh bandit17@bandit.labs.overthewire.org -p 2220
```

---

<div align="center">

**[⬅️ Nivel Anterior](./Bandit_Nivel_15___Nivel_17.md)** | **[🏠 Volver al README](./README.md)** | **[➡️ Siguiente Nivel](./Bandit_Nivel_17___Nivel_18.md)**

</div>
