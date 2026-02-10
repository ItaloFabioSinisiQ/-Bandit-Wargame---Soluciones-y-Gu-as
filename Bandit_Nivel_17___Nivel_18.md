# 🔐 Bandit Level 17 → 18

<div align="center">

![Nivel](https://img.shields.io/badge/Nivel-17_→_18-blue?style=for-the-badge)
![Dificultad](https://img.shields.io/badge/Dificultad-Fácil-yellowgreen?style=for-the-badge)

**Objetivo:** Comparar archivos con diff

[🌐 Desafío Original](https://overthewire.org/wargames/bandit/bandit18.html) | [📺 Video Tutorial](#)

</div>

---


### 🎯 **Objetivo del nivel:**

Hay **2 archivos** en el directorio home: `passwords.old` y `passwords.new`.

> La contraseña para el **siguiente nivel** está en `passwords.new` y es la **única línea que ha cambiado** entre `passwords.old` y `passwords.new`.

---

### ⚠️ **NOTA:**

Si ya resolviste este nivel y ves el mensaje **"Byebye!"** al intentar iniciar sesión en `bandit18`, eso está relacionado con el siguiente nivel: `bandit19`.

---

### 🛠️ **Comandos que podrías necesitar para resolver este nivel:**

- `cat` → Para ver el contenido de un archivo
    
- `grep` → Para buscar texto dentro de archivos
    
- `ls` → Para listar archivos y carpetas
    
- `diff` → Para comparar diferencias entre archivos
    

---

## ✅ **Paso 1: Inicia sesión en el nivel 17**

Desde tu WSL o Ubuntu, conéctate con la clave privada:

```bash
cd /mnt/c/Users/SARLLA/Downloads
chmod 600 bandit17_key.private

Pueden conectarse tambien desde PowerShell
ssh -i bandit17_key.private bandit17@bandit.labs.overthewire.org -p 2220
```

> Esto te conectará al servidor de Bandit, como el usuario `bandit17`.

---

## ✅ **Paso 2: Lista los archivos disponibles**

Ya dentro del servidor:

```bash
ls
```

Verás algo como:

```
passwords.old  passwords.new
```

---

## ✅ **Paso 3: Compara los archivos para ver la línea diferente**

Usamos el comando `diff`, que compara dos archivos línea por línea:

```bash
diff passwords.old passwords.new
```

Verás una salida parecida a esta:

```
42c42
< C6XNBdYOkgt5ARXESMKWWOUwBeaIQZ0Y
---
> x2gLTTjFwMOhQ8oWNbMN362QKxfRqGlO
```

### 🔍 ¿Qué significa eso?

- `42c42`: la **línea 42** cambió.
    
- `<` es lo que estaba antes (en `passwords.old`).
    
- `>` es lo nuevo (en `passwords.new`).
    

💡 Entonces, **la línea del `>` es la contraseña del nivel 18**.

---

## ✅ **Paso 4: Conéctate al siguiente nivel**

Copias la contraseña que viste después del `>` y sales del nivel actual con:

```bash
exit
```

Luego te conectas como `bandit18`:

```bash
ssh bandit18@bandit.labs.overthewire.org -p 2220
```

Y cuando te pida la contraseña, **pegas la que obtuviste**.

---

## ✅ **¡Listo! Ya estás en Bandit 18 🎉**


---

## 🧠 ¿Qué significa esta salida del comando `diff`?

Cuando ejecutas este comando:

```bash
diff passwords.old passwords.new
```

Estás pidiéndole a Linux que **compare ambos archivos línea por línea** y te diga si hay alguna diferencia.

Supongamos que el resultado que aparece es este:

```
42c42
< qwertyuiopasdfghjklzxcvbnm
---
> myS3cr3tP@ssword!
```

### ¿Cómo se interpreta?

|Parte|Significado|
|---|---|
|`42c42`|Esto dice que la **línea 42** del primer archivo fue **cambiada** en la línea 42 del segundo archivo. La `c` viene de "change" (cambio).|
|`< texto`|Este símbolo muestra el **contenido anterior**, o sea, lo que había en la línea 42 del archivo `passwords.old`.|
|`>` texto|Este símbolo muestra el **nuevo contenido**, es decir, lo que está ahora en la línea 42 del archivo `passwords.new`.|

---

### 💡 ¿Y por qué eso es importante?

Porque el reto dice que **solo una línea ha sido modificada**, y que la **nueva contraseña está en `passwords.new`**.

Entonces, de toda esa salida del comando `diff`, lo que nos importa es **lo que aparece después del `>`**, porque **esa es la nueva línea con la contraseña del nivel 18**.


> “Mira, este comando `diff` nos dice exactamente en qué parte cambiaron los archivos. Solo tenemos que buscar el símbolo `>`, y lo que esté al costado es la nueva línea. Como solo una línea cambió, eso es nuestra clave para entrar al siguiente nivel.”

---



---

## 🔑 Contraseña para Nivel 18

```
x2gLTTjFwMOhQ8oWNbMN362QKxfRqGlO
```

---

## 🚀 Conectarse al Siguiente Nivel

```bash
ssh bandit18@bandit.labs.overthewire.org -p 2220
```

---

<div align="center">

**[⬅️ Nivel Anterior](./Bandit_Nivel_16___Nivel_18.md)** | **[🏠 Volver al README](./README.md)** | **[➡️ Siguiente Nivel](./Bandit_Nivel_18___Nivel_19.md)**

</div>
