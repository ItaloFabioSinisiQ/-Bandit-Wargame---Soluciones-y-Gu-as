# 🔐 Bandit Level 0

<div align="center">

![Nivel](https://img.shields.io/badge/Nivel-0-blue?style=for-the-badge)
![Dificultad](https://img.shields.io/badge/Dificultad-Muy_Fácil-success?style=for-the-badge)

**Objetivo:** Conectarse al servidor mediante SSH

[🌐 Desafío Original](https://overthewire.org/wargames/bandit/bandit0.html) | [📺 Video Tutorial](#)

</div>

---

## 📋 Información del Servidor

| Parámetro | Valor |
|-----------|-------|
| **Host** | `bandit.labs.overthewire.org` |
| **Puerto** | `2220` |
| **Usuario** | `bandit0` |
| **Contraseña** | `bandit0` |

---

## 🎯 Solución Paso a Paso

### Paso 1️⃣: Conectar al servidor con SSH

En la terminal, ejecuta el siguiente comando:

```bash
ssh bandit0@bandit.labs.overthewire.org -p 2220
```

**Desglose del comando:**
- `ssh` → Comando para conectarse a través de SSH.
- `bandit0@bandit.labs.overthewire.org` → Usuario y dirección del servidor.
- `-p 2220` → Indica que debes usar el puerto 2220 en lugar del predeterminado (22).

---

### Paso 2️⃣: Ingresar la contraseña

Cuando se te pida la contraseña, ingresa:

```
bandit0
```

> ⚠️ **Nota:** No se mostrará nada en la pantalla mientras escribes la contraseña, pero sigue escribiendo y presiona **Enter**.

---

### Paso 3️⃣: Confirmar que estás dentro

Si la conexión fue exitosa, deberías ver un mensaje de bienvenida y la línea de comandos cambiará a algo como:

```bash
bandit0@bandit:~$
```

---

## ✅ ¡Completado!

Ahora ya estás dentro y puedes seguir con **Bandit Level 1**. 

---

## 🔜 Siguiente Nivel

Para continuar, revisa las instrucciones del siguiente nivel:

**🔗 [Bandit Level 0 → Level 1](https://overthewire.org/wargames/bandit/bandit1.html)**

---

## 📚 Conceptos Aprendidos

- ✅ Conexión SSH básica
- ✅ Uso de puertos personalizados
- ✅ Autenticación con contraseña
- ✅ Navegación básica en terminal

---

<div align="center">

**[⬅️ Volver al README](./README.md)** | **[➡️ Siguiente Nivel](./Bandit_Nivel_0___Nivel_1.md)**

</div>
