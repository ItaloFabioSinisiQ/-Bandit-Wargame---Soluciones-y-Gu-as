# 🔐 Bandit Level 6 → Level 7

<div align="center">

![Nivel](https://img.shields.io/badge/Nivel-6_→_7-blue?style=for-the-badge)
![Dificultad](https://img.shields.io/badge/Dificultad-Medio-orange?style=for-the-badge)

**Objetivo:** Encontrar un archivo en todo el servidor con propiedades específicas

[🌐 Desafío Original](https://overthewire.org/wargames/bandit/bandit7.html) | [📺 Video Tutorial](#)

</div>

---

## 📌 Objetivo del Nivel

La contraseña para el siguiente nivel está almacenada en algún lugar del servidor y tiene todas las siguientes propiedades:

- 👤 Es propiedad del usuario **bandit7**
- 👥 Es propiedad del grupo **bandit6**
- 📏 Tiene un tamaño de **33 bytes**

---

## 🛠️ Comandos que Puedes Necesitar

`ls`, `cd`, `cat`, `file`, `du`, `find`, `grep`

---

## 🎯 Solución Paso a Paso

### Paso 1️⃣: Buscar el archivo en todo el sistema

Para encontrar el archivo con la contraseña, usa el comando `find` con los parámetros adecuados:

```bash
find / -type f -user bandit7 -group bandit6 -size 33c 2>/dev/null
```

---

### 📖 Explicación de los Parámetros

| Parámetro | Descripción |
|-----------|-------------|
| `/` | Busca en todo el sistema (desde la raíz) |
| `-type f` | Busca solo archivos (no directorios) |
| `-user bandit7` | Filtra archivos propiedad del usuario **bandit7** |
| `-group bandit6` | Filtra archivos del grupo **bandit6** |
| `-size 33c` | Filtra archivos de **33 bytes** de tamaño |
| `2>/dev/null` | Oculta errores de "Permiso denegado" |

---

### Paso 2️⃣: Identificar el archivo correcto

**Salida esperada:**
```
/var/lib/dpkg/info/bandit7.password
```

Este es el único archivo que cumple con todos los criterios.

---

### Paso 3️⃣: Leer el contenido del archivo

Después de encontrar el archivo, usa `cat` para leerlo:

```bash
cat /var/lib/dpkg/info/bandit7.password
```

---

## 🔑 Contraseña para Nivel 7

```
morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj
```

---

## 🚀 Conectarse al Siguiente Nivel

¡Bien hecho! Ahora puedes usar la contraseña para acceder al nivel **Bandit 7** con el siguiente comando:

```bash
ssh bandit7@bandit.labs.overthewire.org -p 2220
```

---

## 📚 Conceptos Aprendidos

- ✅ Búsqueda en todo el sistema de archivos
- ✅ Filtrado por propietario de archivo
- ✅ Filtrado por grupo de archivo
- ✅ Redirección de errores (`2>/dev/null`)
- ✅ Permisos y propiedad de archivos en Linux

---

## 🔧 Comandos Utilizados

| Comando | Descripción |
|---------|-------------|
| `find / -type f` | Busca archivos en todo el sistema |
| `-user bandit7` | Filtra por usuario propietario |
| `-group bandit6` | Filtra por grupo propietario |
| `-size 33c` | Filtra por tamaño exacto (33 bytes) |
| `2>/dev/null` | Redirige errores a "la nada" |

---

## 💡 Explicación Técnica

### ¿Qué es `2>/dev/null`?

En Linux, hay tres flujos estándar:
- **0** → STDIN (entrada estándar)
- **1** → STDOUT (salida estándar)
- **2** → STDERR (salida de errores)

El comando `2>/dev/null` hace lo siguiente:
- `2>` → Redirige STDERR (errores)
- `/dev/null` → "Archivo" especial que descarta todo lo que recibe (como un agujero negro)

**¿Por qué lo usamos?**  
Cuando buscamos desde `/` (raíz), `find` intenta acceder a muchos directorios donde no tenemos permisos, generando muchos mensajes de "Permission denied". Con `2>/dev/null` ocultamos estos errores para ver solo los resultados válidos.

---

### Propiedad de Archivos en Linux

Cada archivo en Linux tiene:
- **Usuario propietario** → Quien creó o posee el archivo
- **Grupo propietario** → Grupo al que pertenece el archivo
- **Permisos** → Qué puede hacer cada uno (leer, escribir, ejecutar)

Puedes ver esta información con:
```bash
ls -l archivo
```

Salida ejemplo:
```
-rw-r----- 1 bandit7 bandit6 33 Jan 15 10:00 archivo
           │         │
           └─ usuario └─ grupo
```

---

<div align="center">

**[⬅️ Nivel Anterior](./Bandit_Nivel_5___Nivel_6.md)** | **[🏠 Volver al README](./README.md)** | **[➡️ Siguiente Nivel](./Bandit_Nivel_7___Nivel_8.md)**

</div>
