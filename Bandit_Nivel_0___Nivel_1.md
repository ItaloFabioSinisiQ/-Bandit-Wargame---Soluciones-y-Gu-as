# 🔐 Bandit Level 0 → Level 1

<div align="center">

![Nivel](https://img.shields.io/badge/Nivel-0_→_1-blue?style=for-the-badge)
![Dificultad](https://img.shields.io/badge/Dificultad-Muy_Fácil-success?style=for-the-badge)

**Objetivo:** Leer un archivo llamado `readme` en el directorio home

[🌐 Desafío Original](https://overthewire.org/wargames/bandit/bandit1.html) | [📺 Video Tutorial](#)

</div>

---

## 🎯 Objetivo del Nivel

La contraseña para **bandit1** está almacenada en un archivo llamado **readme** ubicado en el directorio home.

---

## 🛠️ Solución Paso a Paso

### Paso 1️⃣: Ver los archivos en el directorio

Ejecuta el siguiente comando para ver los archivos en tu directorio actual:

```bash
ls
```

**Salida esperada:**
```
readme
```

Deberías ver un archivo llamado `readme`.

---

### Paso 2️⃣: Leer el contenido del archivo

Para ver la contraseña dentro del archivo `readme`, usa:

```bash
cat readme
```

**Esto mostrará la contraseña que necesitas para acceder al Nivel 1.**

---

### Paso 3️⃣: Guardar la contraseña

**Anótala en un lugar seguro** porque la necesitarás en el siguiente nivel.

---

## 🔑 Contraseña para Nivel 1

```
ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If
```

---

## 🚀 Cómo conectarte correctamente al Nivel 1

### 1️⃣ Sal del servidor Bandit (vuelve a tu máquina local)

En la terminal, escribe:

```bash
exit
```

Esto te devolverá a tu máquina local.

---

### 2️⃣ Conéctate a Bandit 1 desde tu máquina local

Ejecuta este comando desde tu terminal local:

```bash
ssh bandit1@bandit.labs.overthewire.org -p 2220
```

Cuando te pida la contraseña, introduce:

```
ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If
```

> 💡 **Tip:** Copiar y pegar funciona, pero asegúrate de que no haya espacios adicionales.

---

## 📚 Conceptos Aprendidos

- ✅ Comando `ls` para listar archivos
- ✅ Comando `cat` para leer contenido de archivos
- ✅ Comando `exit` para cerrar conexión SSH
- ✅ Cambio de usuario en SSH

---

## 🔧 Comandos Utilizados

| Comando | Descripción |
|---------|-------------|
| `ls` | Lista los archivos en el directorio actual |
| `cat readme` | Muestra el contenido del archivo readme |
| `exit` | Sale de la sesión SSH actual |
| `ssh bandit1@...` | Conecta al usuario bandit1 |

---

<div align="center">

**[⬅️ Nivel Anterior](./Bandit_0.md)** | **[🏠 Volver al README](./README.md)** | **[➡️ Siguiente Nivel](./Bandit_Nivel_1___Nivel_2.md)**

</div>
