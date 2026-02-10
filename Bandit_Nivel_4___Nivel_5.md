# 🔐 Bandit Level 4 → Level 5

<div align="center">

![Nivel](https://img.shields.io/badge/Nivel-4_→_5-blue?style=for-the-badge)
![Dificultad](https://img.shields.io/badge/Dificultad-Fácil-yellowgreen?style=for-the-badge)

**Objetivo:** Encontrar el único archivo legible por humanos en el directorio `inhere`

[🌐 Desafío Original](https://overthewire.org/wargames/bandit/bandit5.html) | [📺 Video Tutorial](#)

</div>

---

## 📌 Objetivo del Nivel

La contraseña para el siguiente nivel está almacenada en el único archivo legible por humanos en el directorio **inhere**.

> ⚠️ **Consejo:** Si tu terminal se desconfigura, prueba el comando `reset`.

---

## 🛠️ Comandos que Podrías Necesitar

`ls`, `cd`, `cat`, `file`, `du`, `find`

---

## 🎯 Solución Paso a Paso

### Paso 1️⃣: Navegar al directorio `inhere`

```bash
cd inhere
```

---

### Paso 2️⃣: Listar los archivos

```bash
ls -la
```

**Salida esperada:**
```
-file00  -file01  -file02  -file03  -file04  
-file05  -file06  -file07  -file08  -file09
```

---

### Paso 3️⃣: Identificar el archivo legible por humanos

Para encontrar el único archivo legible por humanos, usa el comando `file`, que muestra el tipo de contenido de cada archivo:

```bash
file ./*
```

**Salida esperada:**
```
./-file00: data
./-file01: data
./-file02: data
./-file03: data
./-file04: data
./-file05: data
./-file06: data
./-file07: ASCII text
./-file08: data
./-file09: data
```

Este comando mostrará qué archivos contienen texto legible. En este caso, **`-file07`** es "ASCII text" (texto legible).

---

### Paso 4️⃣: Leer el archivo correcto

Una vez identificado el archivo con texto ASCII, usa `cat` para leer su contenido:

```bash
cat ./-file07
```

> 💡 **Nota:** Recuerda usar `./` antes del nombre del archivo porque comienza con `-`.

---

## 🔑 Contraseña para Nivel 5

```
4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw
```

---

## 🚀 Conectarse al Siguiente Nivel

```bash
ssh bandit5@bandit.labs.overthewire.org -p 2220
```

---

## 📚 Conceptos Aprendidos

- ✅ Uso del comando `file` para identificar tipos de archivo
- ✅ Diferencia entre archivos binarios y archivos de texto
- ✅ Lectura de archivos con nombres especiales
- ✅ Navegación y exploración de directorios

---

## 🔧 Comandos Utilizados

| Comando | Descripción |
|---------|-------------|
| `cd inhere` | Cambia al directorio `inhere` |
| `ls -la` | Lista todos los archivos |
| `file ./*` | Identifica el tipo de cada archivo en el directorio |
| `cat ./-file07` | Lee el contenido del archivo de texto |

---

## 💡 Explicación Técnica

### ¿Qué hace el comando `file`?

El comando `file` examina el contenido de un archivo y determina su tipo, mostrando información como:
- **ASCII text** → Archivo de texto legible
- **data** → Archivo binario o datos no legibles
- **gzip compressed** → Archivo comprimido
- **executable** → Archivo ejecutable

Esto es muy útil cuando necesitas identificar archivos sin basarte solo en su extensión.

---

<div align="center">

**[⬅️ Nivel Anterior](./Bandit_Nivel_3___Nivel_4.md)** | **[🏠 Volver al README](./README.md)** | **[➡️ Siguiente Nivel](./Bandit_Nivel_5___Nivel_6.md)**

</div>
