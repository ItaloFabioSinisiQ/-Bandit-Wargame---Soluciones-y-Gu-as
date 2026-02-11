# 🔐 Bandit Wargame - Soluciones y Guías

<div align="center">

![Bandit](https://img.shields.io/badge/OverTheWire-Bandit-brightgreen?style=for-the-badge)
![Levels](https://img.shields.io/badge/Niveles-0--34-blue?style=for-the-badge)
![Linux](https://img.shields.io/badge/Linux-FCC624?style=for-the-badge&logo=linux&logoColor=black)
![SSH](https://img.shields.io/badge/SSH-4D4D4D?style=for-the-badge&logo=openssh&logoColor=white)

**Soluciones paso a paso del wargame Bandit de OverTheWire**

[🌐 Sitio Oficial](https://overthewire.org/wargames/bandit/) | [📺 Playlist Completa](#-playlist-completa) | [📖 Documentación](#-niveles-resueltos)

</div>

---

## 📋 Tabla de Contenidos

- [Sobre Bandit](#-sobre-bandit)
- [¿Qué aprenderás?](#-qué-aprenderás)
- [Requisitos](#-requisitos)
- [Playlist Completa](#-playlist-completa)
- [Niveles Resueltos](#-niveles-resueltos)
- [Comandos Útiles](#-comandos-útiles)
- [Contribuir](#-contribuir)

---

## 🎯 Sobre Bandit

**Bandit** es un wargame diseñado para principiantes en seguridad informática. Te enseña los fundamentos de Linux y la línea de comandos a través de desafíos progresivos donde debes encontrar contraseñas para avanzar al siguiente nivel.

Este repositorio contiene:
- ✅ Soluciones detalladas de cada nivel
- 🎥 Videos explicativos en YouTube
- 📝 Comandos y conceptos clave
- 💡 Tips y mejores prácticas

---

## 🚀 ¿Qué aprenderás?

A través de estos desafíos desarrollarás habilidades en:

- 🔧 Navegación en sistemas Linux
- 📁 Manipulación de archivos y directorios
- 🔐 Conceptos básicos de SSH
- 🔍 Búsqueda y filtrado de información
- 📜 Permisos y propiedad de archivos
- 🛠️ Herramientas de línea de comandos
- 🔑 Fundamentos de ciberseguridad

---

## 💻 Requisitos

Para seguir estos desafíos necesitas:

- Un terminal o cliente SSH (Linux, macOS, Windows con WSL/PowerShell)
- Conexión a Internet
- Ganas de aprender 🚀

### Conexión Inicial

```bash
ssh bandit0@bandit.labs.overthewire.org -p 2220
# Contraseña: bandit0
```

---

## 📺 Playlist Completa

### 🎬 Video Completo - Todos los Niveles

[![Video Completo Bandit](https://img.youtube.com/vi/VIDEO_ID_COMPLETO/maxresdefault.jpg)](https://www.youtube.com/watch?v=55ZRou76d-U)

---

## 📖 Niveles Resueltos

### 🔰 Nivel 0 - Conexión Inicial

<table>
<tr>
<td width="70%">

**Objetivo:** Conectarse al servidor mediante SSH

**Conceptos clave:** SSH, autenticación, puertos personalizados

</td>
<td width="30%" align="center">

📄 **[Ver Guía Completa](./Bandit_0.md)**

🎥 **[Ver Video](#https://youtu.be/toa8Ik1HEIs?si=9dfD4NoMf-xhL1Yy)**

</td>
</tr>
</table>

<details>
<summary>💡 <b>Ver Solución Rápida</b></summary>

```bash
ssh bandit0@bandit.labs.overthewire.org -p 2220
# Contraseña: bandit0
```

</details>

---

### 🔐 Nivel 0 → Nivel 1

<table>
<tr>
<td width="70%">

**Objetivo:** Leer un archivo llamado `readme`

**Conceptos clave:** `ls`, `cat`, lectura de archivos

**Contraseña:** `ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If`

</td>
<td width="30%" align="center">

📄 **[Ver Guía Completa](./Bandit_Nivel_0___Nivel_1.md)**

🎥 **[Ver Video](https://www.youtube.com/watch?v=qI9vrU2C9HU)**

</td>
</tr>
</table>

<details>
<summary>💡 <b>Ver Solución Rápida</b></summary>

```bash
ls
cat readme
```

</details>

---

### 📝 Nivel 1 → Nivel 2

<table>
<tr>
<td width="70%">

**Objetivo:** Leer un archivo llamado `-`

**Conceptos clave:** Caracteres especiales, rutas relativas

**Contraseña:** `263JGJPfgU6LtdEvgfWU1XP5yac29mFx`

</td>
<td width="30%" align="center">

📄 **[Ver Guía Completa](./Bandit_Nivel_1___Nivel_2.md)**

🎥 **[Ver Video](https://www.youtube.com/watch?v=3F2V0pH3UH0)**

</td>
</tr>
</table>

<details>
<summary>💡 <b>Ver Solución Rápida</b></summary>

```bash
cat ./-
# o
cat -- -
```

</details>

---

### 📁 Nivel 2 → Nivel 3

<table>
<tr>
<td width="70%">

**Objetivo:** Leer un archivo con espacios en el nombre

**Conceptos clave:** Espacios en nombres de archivos, escape de caracteres

**Contraseña:** `MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx`

</td>
<td width="30%" align="center">

📄 **[Ver Guía Completa](./Bandit_Nivel_2___Nivel_3.md)**

🎥 **[Ver Video](#)**

</td>
</tr>
</table>

<details>
<summary>💡 <b>Ver Solución Rápida</b></summary>

```bash
cat "spaces in this filename"
# o
cat spaces\ in\ this\ filename
```

</details>

---

### 🔍 Nivel 3 → Nivel 4

<table>
<tr>
<td width="70%">

**Objetivo:** Encontrar un archivo oculto en el directorio `inhere`

**Conceptos clave:** Archivos ocultos, `ls -la`, navegación de directorios

**Contraseña:** `2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ`

</td>
<td width="30%" align="center">

📄 **[Ver Guía Completa](./Bandit_Nivel_3___Nivel_4.md)**

🎥 **[Ver Video](#)**

</td>
</tr>
</table>

<details>
<summary>💡 <b>Ver Solución Rápida</b></summary>

```bash
cd inhere
ls -la
cat .hidden
```

</details>

---

### 🔎 Nivel 4 → Nivel 5

<table>
<tr>
<td width="70%">

**Objetivo:** Encontrar el único archivo legible por humanos

**Conceptos clave:** Comando `file`, tipos de archivo

**Contraseña:** `4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw`

</td>
<td width="30%" align="center">

📄 **[Ver Guía Completa](./Bandit_Nivel_4___Nivel_5.md)**

🎥 **[Ver Video](#)**

</td>
</tr>
</table>

<details>
<summary>💡 <b>Ver Solución Rápida</b></summary>

```bash
cd inhere
file ./*
cat ./-file07
```

</details>

---

### 📏 Nivel 5 → Nivel 6

<table>
<tr>
<td width="70%">

**Objetivo:** Buscar archivo de 1033 bytes, legible, no ejecutable

**Conceptos clave:** `find`, filtrado por tamaño y propiedades

**Contraseña:** `HWasnPhtq9AVKe0dmk45nxy20cvUa6EG`

</td>
<td width="30%" align="center">

📄 **[Ver Guía Completa](./Bandit_Nivel_5___Nivel_6.md)**

🎥 **[Ver Video](#)**

</td>
</tr>
</table>

<details>
<summary>💡 <b>Ver Solución Rápida</b></summary>

```bash
find inhere -type f -size 1033c ! -executable
cat inhere/maybehere07/.file2
```

</details>

---

### 🌐 Nivel 6 → Nivel 7

<table>
<tr>
<td width="70%">

**Objetivo:** Buscar archivo en todo el servidor con usuario, grupo y tamaño específicos

**Conceptos clave:** Búsqueda global, `find`, permisos

**Contraseña:** `morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj`

</td>
<td width="30%" align="center">

📄 **[Ver Guía Completa](./Bandit_Nivel_6___Nivel_7.md)**

🎥 **[Ver Video](#)**

</td>
</tr>
</table>

<details>
<summary>💡 <b>Ver Solución Rápida</b></summary>

```bash
find / -type f -user bandit7 -group bandit6 -size 33c 2>/dev/null
cat /var/lib/dpkg/info/bandit7.password
```

</details>

---

### 🔤 Nivel 7 → Nivel 8

<table>
<tr>
<td width="70%">

**Objetivo:** Buscar contraseña junto a la palabra "millionth"

**Conceptos clave:** `grep`, búsqueda de patrones

**Contraseña:** `dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc`

</td>
<td width="30%" align="center">

📄 **[Ver Guía Completa](./Bandit_Nivel_7___Nivel_8.md)**

🎥 **[Ver Video](#)**

</td>
</tr>
</table>

<details>
<summary>💡 <b>Ver Solución Rápida</b></summary>

```bash
grep millionth data.txt
```

</details>

---

### 🔢 Nivel 8 → Nivel 9

<table>
<tr>
<td width="70%">

**Objetivo:** Encontrar la única línea que aparece solo una vez

**Conceptos clave:** `sort`, `uniq`, duplicados

**Contraseña:** `4CKMh1JI91bUIZZPXDqGanal4xvAg0JM`

</td>
<td width="30%" align="center">

📄 **[Ver Guía Completa](./Bandit_Nivel_8___Nivel_9.md)**

🎥 **[Ver Video](#)**

</td>
</tr>
</table>

<details>
<summary>💡 <b>Ver Solución Rápida</b></summary>

```bash
sort data.txt | uniq -u
```

</details>

---

### ⚡ Nivel 9 → Nivel 10

<table>
<tr>
<td width="70%">

**Objetivo:** Buscar contraseña precedida por caracteres "="

**Conceptos clave:** `strings`, archivos binarios, `grep`

**Contraseña:** `FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey`

</td>
<td width="30%" align="center">

📄 **[Ver Guía Completa](./Bandit_Nivel_9___Nivel_10.md)**

🎥 **[Ver Video](#)**

</td>
</tr>
</table>

<details>
<summary>💡 <b>Ver Solución Rápida</b></summary>

```bash
strings data.txt | grep "="
```

</details>

---

### 🔐 Nivel 10 → Nivel 11

<table>
<tr>
<td width="70%">

**Objetivo:** Decodificar datos en Base64

**Conceptos clave:** Base64, codificación

**Contraseña:** `dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr`

</td>
<td width="30%" align="center">

📄 **[Ver Guía Completa](./Bandit_Nivel_10___Nivel_11.md)**

🎥 **[Ver Video](#)**

</td>
</tr>
</table>

<details>
<summary>💡 <b>Ver Solución Rápida</b></summary>

```bash
base64 -d data.txt
```

</details>

---

### 🔄 Nivel 11 → Nivel 12

<table>
<tr>
<td width="70%">

**Objetivo:** Decodificar texto con cifrado ROT13

**Conceptos clave:** ROT13, cifrado César, `tr`

**Contraseña:** `7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4`

</td>
<td width="30%" align="center">

📄 **[Ver Guía Completa](./Bandit_Nivel_11___Nivel_12.md)**

🎥 **[Ver Video](#)**

</td>
</tr>
</table>

<details>
<summary>💡 <b>Ver Solución Rápida</b></summary>

```bash
cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
```

</details>

---

### 📦 Nivel 12 → Nivel 13

<table>
<tr>
<td width="70%">

**Objetivo:** Descomprimir archivo hexdump múltiples veces

**Conceptos clave:** `xxd`, `gzip`, `bzip2`, `tar`, descompresión

**Contraseña:** `FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn`

</td>
<td width="30%" align="center">

📄 **[Ver Guía Completa](./Bandit_Nivel_12___Nivel_13.md)**

🎥 **[Ver Video](#)**

</td>
</tr>
</table>

<details>
<summary>💡 <b>Ver Solución Rápida</b></summary>

```bash
mktemp -d
xxd -r data.txt data.bin
# Descomprimir iterativamente...
```

</details>

---

### 🔑 Nivel 13 → Nivel 14

<table>
<tr>
<td width="70%">

**Objetivo:** Usar clave SSH privada para conectarse

**Conceptos clave:** SSH keys, autenticación por clave pública

**Contraseña:** `MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS`

</td>
<td width="30%" align="center">

📄 **[Ver Guía Completa](./Bandit_Nivel_13___Nivel_14.md)**

🎥 **[Ver Video](#)**

</td>
</tr>
</table>

<details>
<summary>💡 <b>Ver Solución Rápida</b></summary>

```bash
ssh -i sshkey.private bandit14@localhost
cat /etc/bandit_pass/bandit14
```

</details>

---

### 🌐 Nivel 14 → Nivel 15

<table>
<tr>
<td width="70%">

**Objetivo:** Enviar contraseña a puerto 30000 usando netcat

**Conceptos clave:** `nc`, `telnet`, puertos, red

**Contraseña:** `8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo`

</td>
<td width="30%" align="center">

📄 **[Ver Guía Completa](./Bandit_Nivel_14___Nivel_15.md)**

🎥 **[Ver Video](#)**

</td>
</tr>
</table>

<details>
<summary>💡 <b>Ver Solución Rápida</b></summary>

```bash
echo "MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS" | nc localhost 30000
```

</details>

---

### 🔜 Más Niveles Próximamente...

<div align="center">

🚧 **Actualmente trabajando en los siguientes niveles** 🚧

_¡Mantente atento para más actualizaciones!_

</div>

## 🛠️ Comandos Útiles

Aquí hay una referencia rápida de los comandos más utilizados en Bandit:

| Comando | Descripción | Ejemplo |
|---------|-------------|---------|
| `ls` | Listar archivos | `ls -la` |
| `cd` | Cambiar directorio | `cd inhere` |
| `cat` | Mostrar contenido de archivo | `cat readme` |
| `pwd` | Mostrar directorio actual | `pwd` |
| `file` | Identificar tipo de archivo | `file *` |
| `find` | Buscar archivos | `find / -name readme` |
| `grep` | Buscar texto | `grep password file.txt` |
| `strings` | Extraer texto de binarios | `strings data.bin` |
| `base64` | Decodificar base64 | `base64 -d file` |
| `ssh` | Conectar por SSH | `ssh user@host -p port` |

---

## 📚 Recursos Adicionales

- 📖 [Documentación Oficial de Bandit](https://overthewire.org/wargames/bandit/)
- 🐧 [Guía de Linux para principiantes](https://linuxjourney.com/)
- 🔐 [OverTheWire - Otros Wargames](https://overthewire.org/wargames/)
- 📘 [Cheat Sheet de Bash](https://devhints.io/bash)

---

## 🤝 Contribuir

¿Encontraste una mejor solución o quieres añadir más niveles?

1. 🍴 Fork este repositorio
2. 🔨 Crea una rama con tu feature (`git checkout -b feature/nuevo-nivel`)
3. 💾 Commit tus cambios (`git commit -m 'Añadir nivel X'`)
4. 📤 Push a la rama (`git push origin feature/nuevo-nivel`)
5. 🎉 Abre un Pull Request

---

## ⚠️ Disclaimer

Este repositorio tiene fines **educativos únicamente**. Se recomienda intentar resolver los desafíos por tu cuenta antes de consultar las soluciones. El aprendizaje real viene de enfrentar y superar los obstáculos.

---

## 📧 Contacto

¿Preguntas o sugerencias?

- 📺 YouTube: [Tu Canal](https://www.youtube.com/channel/TU_CANAL)
- 💼 LinkedIn: [Tu Perfil](https://www.linkedin.com/in/tu-perfil)
- 🐦 Twitter: [@TuUsuario](https://twitter.com/TuUsuario)

---

<div align="center">

**⭐ Si este repositorio te fue útil, considera darle una estrella ⭐**

![Hecho con ❤️](https://img.shields.io/badge/Hecho%20con-❤️-red?style=for-the-badge)

</div>

### 🔐 Nivel 15 → Nivel 16

<table>
<tr>
<td width="70%">

**Objetivo:** Conectarse con SSL/TLS al puerto 30001

**Conceptos clave:** SSL/TLS, `openssl s_client`, cifrado

**Contraseña:** `kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx`

</td>
<td width="30%" align="center">

📄 **[Ver Guía Completa](./Bandit_Nivel_15___Nivel_16.md)**

🎥 **[Ver Video](#)**

</td>
</tr>
</table>

<details>
<summary>💡 <b>Ver Solución Rápida</b></summary>

```bash
echo "MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS" | openssl s_client -connect localhost:30001 -ign_eof
```

</details>

---

### 🔍 Nivel 16 → Nivel 17

<table>
<tr>
<td width="70%">

**Objetivo:** Escanear puertos y usar clave privada SSH

**Conceptos clave:** `nmap`, escaneo de puertos, claves SSH

**Contraseña:** `EReVavePLFHtFlFsjn3hyzMlvSuSAcRD`

</td>
<td width="30%" align="center">

📄 **[Ver Guía Completa](./Bandit_Nivel_16___Nivel_17.md)**

🎥 **[Ver Video](#)**

</td>
</tr>
</table>

<details>
<summary>💡 <b>Ver Solución Rápida</b></summary>

```bash
nmap -p31000-32000 localhost
echo "PASSWORD" | openssl s_client -connect localhost:31790 -quiet
```

</details>

---

### 📊 Nivel 17 → Nivel 18

<table>
<tr>
<td width="70%">

**Objetivo:** Comparar archivos con diff

**Conceptos clave:** `diff`, comparación de archivos

**Contraseña:** `x2gLTTjFwMOhQ8oWNbMN362QKxfRqGlO`

</td>
<td width="30%" align="center">

📄 **[Ver Guía Completa](./Bandit_Nivel_17___Nivel_18.md)**

🎥 **[Ver Video](#)**

</td>
</tr>
</table>

<details>
<summary>💡 <b>Ver Solución Rápida</b></summary>

```bash
diff passwords.old passwords.new
```

</details>

---

### 🚫 Nivel 18 → Nivel 19

<table>
<tr>
<td width="70%">

**Objetivo:** Bypass de .bashrc con SSH

**Conceptos clave:** SSH, ejecución remota, `.bashrc`

**Contraseña:** `cGWpMaKXVwDUNgPAVJbWYuGHVn9zl3j8`

</td>
<td width="30%" align="center">

📄 **[Ver Guía Completa](./Bandit_Nivel_18___Nivel_19.md)**

🎥 **[Ver Video](#)**

</td>
</tr>
</table>

<details>
<summary>💡 <b>Ver Solución Rápida</b></summary>

```bash
ssh bandit18@bandit.labs.overthewire.org -p 2220 "cat readme"
```

</details>

---

### 🔓 Nivel 19 → Nivel 20

<table>
<tr>
<td width="70%">

**Objetivo:** Usar binario con setuid

**Conceptos clave:** setuid, escalación de privilegios

**Contraseña:** `0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO`

</td>
<td width="30%" align="center">

📄 **[Ver Guía Completa](./Bandit_Nivel_19___Nivel_20.md)**

🎥 **[Ver Video](#)**

</td>
</tr>
</table>

<details>
<summary>💡 <b>Ver Solución Rápida</b></summary>

```bash
./bandit20-do cat /etc/bandit_pass/bandit20
```

</details>

---

### 🌐 Nivel 20 → Nivel 21

<table>
<tr>
<td width="70%">

**Objetivo:** Cliente-servidor con netcat

**Conceptos clave:** `nc`, sockets, cliente-servidor

**Contraseña:** `EeoULMCra2q0dSkYj561DX7s1CpBuOBt`

</td>
<td width="30%" align="center">

📄 **[Ver Guía Completa](./Bandit_Nivel_20___Nivel_21.md)**

🎥 **[Ver Video](#)**

</td>
</tr>
</table>

<details>
<summary>💡 <b>Ver Solución Rápida</b></summary>

```bash
# Terminal 1:
echo "PASSWORD" | nc -lvp 1234
# Terminal 2:
./suconnect 1234
```

</details>

---

### ⏰ Nivel 21 → Nivel 22

<table>
<tr>
<td width="70%">

**Objetivo:** Analizar cronjobs

**Conceptos clave:** `cron`, `/etc/cron.d/`, automatización

**Contraseña:** `tRae0UfB9v0UzbCdn9cY0gQnds9GF58Q`

</td>
<td width="30%" align="center">

📄 **[Ver Guía Completa](./Bandit_Nivel_21___Nivel_22.md)**

🎥 **[Ver Video](#)**

</td>
</tr>
</table>

<details>
<summary>💡 <b>Ver Solución Rápida</b></summary>

```bash
cat /etc/cron.d/cronjob_bandit22
cat /usr/bin/cronjob_bandit22.sh
cat /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
```

</details>

---

### 🔐 Nivel 22 → Nivel 23

<table>
<tr>
<td width="70%">

**Objetivo:** Script cron con hash MD5

**Conceptos clave:** MD5, hashing, análisis de scripts

**Contraseña:** `0Zf11ioIjMVN551jX3CmStKLYqjk54Ga`

</td>
<td width="30%" align="center">

📄 **[Ver Guía Completa](./Bandit_Nivel_22___Nivel_23.md)**

🎥 **[Ver Video](#)**

</td>
</tr>
</table>

<details>
<summary>💡 <b>Ver Solución Rápida</b></summary>

```bash
echo "I am user bandit23" | md5sum | cut -d ' ' -f 1
cat /tmp/8ca319486bfbbc3663ea0fbe81326349
```

</details>

---

### 🔜 Más Niveles Próximamente...

<div align="center">

🚧 **Actualmente trabajando en los siguientes niveles** 🚧

_¡Mantente atento para más actualizaciones!_

</div>

---

### 🎯 Nivel 23 → Nivel 24

<table>
<tr>
<td width="70%">

**Objetivo:** Crear script para cronjob que robe contraseña

**Conceptos clave:** Cron, explotación, scripts maliciosos

**Contraseña:** `gb8KRRCsshuZXI0tUuR6ypOFjiZbf3G8`

</td>
<td width="30%" align="center">

📄 **[Ver Guía Completa](./Bandit_Nivel_23___Nivel_24.md)**

🎥 **[Ver Video](#)**

</td>
</tr>
</table>

<details>
<summary>💡 <b>Ver Solución Rápida</b></summary>

```bash
echo 'cat /etc/bandit_pass/bandit24 > /tmp/bandit24_pass.txt' > /tmp/cron_exploit.sh
chmod 777 /tmp/cron_exploit.sh
# Esperar ejecución del cron
cat /tmp/bandit24_pass.txt
```

</details>

---

### 🔢 Nivel 24 → Nivel 25

<table>
<tr>
<td width="70%">

**Objetivo:** Ataque de fuerza bruta con 10,000 PINs

**Conceptos clave:** Fuerza bruta, scripting, netcat

**Contraseña:** `iCi86ttT4KSNe1armKiwbQNmB3YJP3q4`

</td>
<td width="30%" align="center">

📄 **[Ver Guía Completa](./Bandit_Nivel_24___Nivel_25.md)**

🎥 **[Ver Video](#)**

</td>
</tr>
</table>

<details>
<summary>💡 <b>Ver Solución Rápida</b></summary>

```bash
for pin in {0000..9999}; do
    echo "$PASSWORD $pin"
done | nc localhost 30002 | grep -v "Wrong"
```

</details>

---

### 🔓 Nivel 25 → Nivel 26

<table>
<tr>
<td width="70%">

**Objetivo:** Escape de shell restringido con vi

**Conceptos clave:** Shell escape, `vi`, terminal manipulation

**Contraseña:** `s0773xxkk0MXfdqOfPRVr9L3jJBUOgCZ`

</td>
<td width="30%" align="center">

📄 **[Ver Guía Completa](./Bandit_Nivel_25___Nivel_26.md)**

🎥 **[Ver Video](#)**

</td>
</tr>
</table>

<details>
<summary>💡 <b>Ver Solución Rápida</b></summary>

```bash
# 1. Reducir tamaño de terminal
# 2. ssh -i bandit26.sshkey bandit26@localhost -p 2220
# 3. En vi: :set shell=/bin/bash
# 4. :shell
```

</details>

---

### 🔐 Nivel 26 → Nivel 27

<table>
<tr>
<td width="70%">

**Objetivo:** Usar binario setuid desde shell escapado

**Conceptos clave:** setuid, escalación de privilegios

**Contraseña:** `upsNCc7vzaRDx6oZC6GiR6ERwe1MowGB`

</td>
<td width="30%" align="center">

📄 **[Ver Guía Completa](./Bandit_Nivel_26___Nivel_27.md)**

🎥 **[Ver Video](#)**

</td>
</tr>
</table>

<details>
<summary>💡 <b>Ver Solución Rápida</b></summary>

```bash
./bandit27-do cat /etc/bandit_pass/bandit27
```

</details>

---

### 📦 Nivel 27 → Nivel 28

<table>
<tr>
<td width="70%">

**Objetivo:** Clonar repositorio Git básico

**Conceptos clave:** Git, `git clone`, SSH

**Contraseña:** `Yz9IpL0sBcCeuG7m9uQFt8ZNpS4HZRcN`

</td>
<td width="30%" align="center">

📄 **[Ver Guía Completa](./Bandit_Nivel_27___Nivel_28.md)**

🎥 **[Ver Video](#)**

</td>
</tr>
</table>

<details>
<summary>💡 <b>Ver Solución Rápida</b></summary>

```bash
git clone ssh://bandit27-git@localhost:2220/home/bandit27-git/repo
cd repo && cat README
```

</details>

---

### 📜 Nivel 28 → Nivel 29

<table>
<tr>
<td width="70%">

**Objetivo:** Explorar historial de commits Git

**Conceptos clave:** `git log`, `git checkout`, historial

**Contraseña:** `4pT1t5DENaYuqnqvadYs1oE4QLCdjmJ7`

</td>
<td width="30%" align="center">

📄 **[Ver Guía Completa](./Bandit_Nivel_28___Nivel_29.md)**

🎥 **[Ver Video](#)**

</td>
</tr>
</table>

<details>
<summary>💡 <b>Ver Solución Rápida</b></summary>

```bash
git log
git checkout <commit_hash>
cat README.md
```

</details>

---

### 🌿 Nivel 29 → Nivel 30

<table>
<tr>
<td width="70%">

**Objetivo:** Explorar ramas Git (dev branch)

**Conceptos clave:** `git branch`, ramas, desarrollo

**Contraseña:** `qp30ex3VLz5MDG1n91YowTv4Q8l7CDZL`

</td>
<td width="30%" align="center">

📄 **[Ver Guía Completa](./Bandit_Nivel_29___Nivel_30.md)**

🎥 **[Ver Video](#)**

</td>
</tr>
</table>

<details>
<summary>💡 <b>Ver Solución Rápida</b></summary>

```bash
git branch -a
git checkout dev
cat README.md
```

</details>

---

### 🏷️ Nivel 30 → Nivel 31

<table>
<tr>
<td width="70%">

**Objetivo:** Explorar tags Git

**Conceptos clave:** `git tag`, `git show`, tags

**Contraseña:** `fb5S2xb7bRyFmAvQYQGEqsbhVyJqhnDy`

</td>
<td width="30%" align="center">

📄 **[Ver Guía Completa](./Bandit_Nivel_30___Nivel_31.md)**

🎥 **[Ver Video](#)**

</td>
</tr>
</table>

<details>
<summary>💡 <b>Ver Solución Rápida</b></summary>

```bash
git tag
git show secret
```

</details>

---

### 📤 Nivel 31 → Nivel 32

<table>
<tr>
<td width="70%">

**Objetivo:** Git push con .gitignore bypass

**Conceptos clave:** `.gitignore`, `git add -f`, `git push`

**Contraseña:** `3O9RfhqyAlVBEZpVb6LYStshZoqoSx5K`

</td>
<td width="30%" align="center">

📄 **[Ver Guía Completa](./Bandit_Nivel_31___Nivel_32.md)**

🎥 **[Ver Video](#)**

</td>
</tr>
</table>

<details>
<summary>💡 <b>Ver Solución Rápida</b></summary>

```bash
echo "'May I come in?'" > key.txt
git add -f key.txt
git commit -m "Add key"
git push origin master
```

</details>

---

### 🔤 Nivel 32 → Nivel 33

<table>
<tr>
<td width="70%">

**Objetivo:** Escape de UPPERCASE SHELL

**Conceptos clave:** Shell escape, variables especiales `$0`

**Contraseña:** `tQdtbs5D5i2vJwkO8mEyYEyTL8izoeJ0`

</td>
<td width="30%" align="center">

📄 **[Ver Guía Completa](./Bandit_Nivel_32___Nivel_33.md)**

🎥 **[Ver Video](#)**

</td>
</tr>
</table>

<details>
<summary>💡 <b>Ver Solución Rápida</b></summary>

```bash
$0
cat /etc/bandit_pass/bandit33
```

</details>

---

### 🎉 Nivel 33 → Nivel 34 (Final)

<table>
<tr>
<td width="70%">

**Objetivo:** ¡Completar Bandit y celebrar!

**Logro:** Has dominado todos los niveles de Bandit

**Estado:** ✅ **¡Completado!**

</td>
<td width="30%" align="center">

📄 **[Ver Guía Completa](./Bandit_Nivel_33___Nivel_34.md)**

🎥 **[Ver Video](#)**

</td>
</tr>
</table>

---

## 🎊 ¡Felicitaciones!

Has completado los **34 niveles** de Bandit de OverTheWire.

### 📈 Progreso Final:

```
Niveles Completados: 0 ══════════════════════════ 34
                     ▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓ 100%
```

### 🏆 Habilidades Desarrolladas:

- ✅ Dominio de **Linux y Bash**
- ✅ Manipulación de **archivos y permisos**
- ✅ Uso avanzado de **Git**
- ✅ **Networking** y protocolos
- ✅ **Criptografía** básica
- ✅ **Scripting** y automatización
- ✅ Técnicas de **seguridad** y pentesting
- ✅ **Resolución de problemas** bajo presión

### 🚀 Próximos Desafíos:

- 🔥 [Leviathan](https://overthewire.org/wargames/leviathan/)
- 🌐 [Natas](https://overthewire.org/wargames/natas/)
- 🔐 [Krypton](https://overthewire.org/wargames/krypton/)

---
