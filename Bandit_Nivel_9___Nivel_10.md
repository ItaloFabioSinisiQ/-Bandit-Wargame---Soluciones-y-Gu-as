# 🔐 Bandit Level 9 → Level 10

<div align="center">

![Nivel](https://img.shields.io/badge/Nivel-9_→_10-blue?style=for-the-badge)
![Dificultad](https://img.shields.io/badge/Dificultad-Fácil-yellowgreen?style=for-the-badge)

**Objetivo:** Encontrar una contraseña precedida por varios caracteres "="

[🌐 Desafío Original](https://overthewire.org/wargames/bandit/bandit10.html) | [📺 Video Tutorial](#)

</div>

---

## 📌 Objetivo del Nivel

La contraseña para el siguiente nivel está almacenada en el archivo `data.txt`. Se encuentra dentro de una de las pocas cadenas legibles por humanos y está precedida por varios caracteres `=`.

---

## 🛠️ Comandos que Puedes Necesitar

`grep`, `sort`, `uniq`, `strings`, `base64`, `tr`, `tar`, `gzip`, `bzip2`, `xxd`

---

## 🎯 Solución Paso a Paso

### Paso 1️⃣: Extraer cadenas legibles del archivo

El archivo `data.txt` puede contener caracteres no legibles (datos binarios), así que usaremos el comando `strings` para extraer solo las cadenas legibles por humanos.

```bash
strings data.txt
```

Esto mostrará todas las cadenas de texto legibles dentro del archivo.

---

### Paso 2️⃣: Buscar la contraseña

Sabemos que la contraseña está precedida por varios signos `=`. Entonces, usamos `grep` para encontrar líneas que contengan `=`:

```bash
strings data.txt | grep "="
```

**Salida esperada:**
```
...
4========== the
========== password
========== is
======= sGqUmIhG4iagAM57EZxGlzJjzRu7ZGdi
```

---

### Paso 3️⃣: Identificar la contraseña

Si la línea obtenida es algo como esto:

```
======= sGqUmIhG4iagAM57EZxGlzJjzRu7ZGdi
```

La contraseña es **`sGqUmIhG4iagAM57EZxGlzJjzRu7ZGdi`**.

---

## 🔑 Contraseña para Nivel 10

```
sGqUmIhG4iagAM57EZxGlzJjzRu7ZGdi
```

---

## 🚀 Conectarse al Siguiente Nivel

Usa la contraseña obtenida para conectarte al siguiente nivel:

```bash
ssh bandit10@bandit.labs.overthewire.org -p 2220
```

Luego, ingresa la contraseña cuando te la pida.

---

## 📚 Conceptos Aprendidos

- ✅ Extracción de cadenas legibles con `strings`
- ✅ Diferencia entre datos binarios y texto
- ✅ Búsqueda de patrones con `grep`
- ✅ Combinación de comandos con pipes

---

## 🔧 Comandos Utilizados

| Comando | Descripción |
|---------|-------------|
| `strings data.txt` | Extrae cadenas de texto legibles del archivo |
| `grep "="` | Busca líneas que contengan el carácter "=" |
| `\|` (pipe) | Conecta la salida de `strings` con `grep` |

---

## 💡 Explicación Técnica

### ¿Qué hace el comando `strings`?

El comando `strings` extrae secuencias de caracteres imprimibles de archivos binarios.

**Sintaxis:**
```bash
strings [opciones] archivo
```

**¿Por qué es útil?**
- Archivos binarios (ejecutables, imágenes, archivos comprimidos) contienen mayormente datos no legibles
- `strings` filtra y muestra solo las partes que son texto legible
- Por defecto, muestra cadenas de al menos 4 caracteres consecutivos

**Ejemplo:**
```bash
strings programa.exe
# Puede mostrar:
# "Error: File not found"
# "Copyright 2024"
# "C:\Windows\System32"
```

---

### Opciones Útiles de `strings`

| Opción | Descripción |
|--------|-------------|
| `-n NUM` | Muestra cadenas de al menos NUM caracteres (default: 4) |
| `-a` | Escanea todo el archivo (no solo secciones de datos) |
| `-t x` | Muestra el offset en hexadecimal |
| `-e {s,S,b,l,B,L}` | Selecciona el tipo de codificación |

---

### ¿Por qué buscar el carácter "="?

En este nivel, la pista dice que la contraseña está "precedida por varios caracteres =".

Esto significa que la línea se verá algo así:
```
========== contraseña_aquí
```

El uso de `grep "="` filtra todas las líneas que contienen al menos un `=`, lo que nos ayuda a reducir los resultados y encontrar la contraseña más fácilmente.

---

### Flujo Completo del Comando

```bash
strings data.txt | grep "="
```

1. `strings data.txt` → Extrae todo el texto legible del archivo
2. `|` → Pasa ese texto como entrada al siguiente comando
3. `grep "="` → Filtra solo las líneas que contienen "="
4. Resultado: Solo las líneas con "=" que probablemente contengan la contraseña

---

¡Listo! 🚀 Has pasado al **Nivel 10**. 😊

<div align="center">

**[⬅️ Nivel Anterior](./Bandit_Nivel_8___Nivel_9.md)** | **[🏠 Volver al README](./README.md)** | **[➡️ Siguiente Nivel](./Bandit_Nivel_10___Nivel_11.md)**

</div>
