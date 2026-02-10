# 🔐 Bandit Level 10 → Level 11

<div align="center">

![Nivel](https://img.shields.io/badge/Nivel-10_→_11-blue?style=for-the-badge)
![Dificultad](https://img.shields.io/badge/Dificultad-Fácil-yellowgreen?style=for-the-badge)

**Objetivo:** Decodificar datos en Base64

[🌐 Desafío Original](https://overthewire.org/wargames/bandit/bandit11.html) | [📺 Video Tutorial](#)

</div>

---

## 📌 Objetivo del Nivel

La contraseña para el siguiente nivel está almacenada en el archivo **data.txt**, el cual contiene datos codificados en **base64**.

---

## 🛠️ Comandos que Puedes Necesitar

`grep`, `sort`, `uniq`, `strings`, `base64`, `tr`, `tar`, `gzip`, `bzip2`, `xxd`

---

## 📖 Material de Lectura Útil

- [Base64 en Wikipedia](https://en.wikipedia.org/wiki/Base64)

---

## 🎯 Solución Paso a Paso

### Paso 1️⃣: Ver el contenido del archivo

```bash
cat data.txt
```

**Salida:**
```
VGhlIHBhc3N3b3JkIGlzIGR0UjE3M2ZaS2IwUlJzREZTR3NnMlJXbnBOVmozcVJy
```

---

### Paso 2️⃣: Decodificar el archivo Base64

```bash
base64 -d data.txt
```

**Explicación del comando:**
- `base64`: Herramienta para codificar o decodificar datos en Base64
- `-d`: Indica que queremos decodificar
- `data.txt`: Archivo que contiene la cadena en Base64

---

## 🔑 Contraseña para Nivel 11

```
dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr
```

---

## 🚀 Conectarse al Siguiente Nivel

```bash
ssh bandit11@bandit.labs.overthewire.org -p 2220
```

---

## 📚 Conceptos Aprendidos

- ✅ ¿Qué es Base64?
- ✅ Codificación vs. Cifrado
- ✅ Uso del comando `base64`
- ✅ Decodificación de datos

---

## 🔧 Comandos Utilizados

| Comando | Descripción |
|---------|-------------|
| `base64 -d data.txt` | Decodifica el contenido Base64 del archivo |
| `base64 -e archivo` | Codifica un archivo a Base64 |

---

## 💡 Base64: Explicación Completa

### ¿Qué es Base64?

**Base64** es un método de codificación que convierte datos binarios en texto ASCII. Se usa principalmente para transferir datos de manera segura en sistemas que solo aceptan caracteres de texto, como correos electrónicos o URLs.

---

### 📌 ¿Cómo funciona Base64?

1. **Divide los datos en bloques de 3 bytes (24 bits)**
2. **Cada bloque de 3 bytes se convierte en 4 caracteres de Base64**, donde cada carácter representa 6 bits
3. **Si los datos no son múltiplos de 3, se agregan caracteres de relleno (`=`)** para completar el bloque

---

### Ejemplo de Codificación Base64

**Texto original:**
```
Hola
```

**Convertido a Base64:**
```
SG9sYQ==
```

Aquí, los caracteres `SG9sYQ==` representan los datos en formato seguro y transportable.

---

### ¿Dónde se usa Base64?

- ✅ **Correos electrónicos (MIME):** Para enviar archivos adjuntos como imágenes o documentos
- ✅ **Autenticación en la web:** En encabezados HTTP con "Basic Authentication"
- ✅ **Almacenamiento de imágenes en bases de datos:** Algunas aplicaciones almacenan imágenes en formato Base64
- ✅ **Codificación de datos en JSON o XML**

---

### Decodificar Base64 Manualmente

Decodificar Base64 manualmente es un proceso detallado. Aquí te explico cómo:

#### **Paso 1: Consulta la tabla Base64**

Cada carácter en Base64 representa un valor entre 0 y 63:

| Carácter | Valor | Carácter | Valor |
|----------|-------|----------|-------|
| A | 0 | a | 26 |
| B | 1 | b | 27 |
| ... | ... | ... | ... |
| Z | 25 | z | 51 |
| 0 | 52 | + | 62 |
| 9 | 61 | / | 63 |
| = | Relleno | - | - |

---

#### **Ejemplo: Decodificar "SG9sYQ==" a mano**

**Paso 1:** Convertir cada carácter a su valor numérico según la tabla:

```
S → 18
G → 6
9 → 61
s → 44
Y → 24
Q → 16
= → Relleno (ignorar)
= → Relleno (ignorar)
```

**Paso 2:** Convertir cada número a binario (6 bits):

```
S  (18) → 010010
G  (6)  → 000110
9  (61) → 111101
s  (44) → 101100
Y  (24) → 011000
Q  (16) → 010000
```

**Paso 3:** Unir los bits y agrupar en bloques de 8 bits:

```
010010 000110 111101 101100 011000 010000
01001000 01101111 01101100 01100001
```

**Paso 4:** Convertir cada bloque de 8 bits a ASCII:

```
01001000 → 72 → H
01101111 → 111 → o
01101100 → 108 → l
01100001 → 97 → a
```

**Resultado final:** **"Hola"**

---

### Codificación en Python

```python
import base64

texto_codificado = "SG9sYSBtdW5kbw=="
texto_decodificado = base64.b64decode(texto_codificado).decode('utf-8')
print(texto_decodificado)  # Output: Hola mundo
```

---

### ⚠️ Base64 NO es Cifrado

**Importante:** Base64 NO es un método de cifrado. Simplemente transforma datos binarios en texto ASCII para facilitar su manejo en sistemas que procesan texto.

Cualquiera puede decodificar Base64 fácilmente con herramientas como:
- `base64 -d` en Linux
- [Base64 Decode](https://www.base64decode.org/) en línea
- Funciones en lenguajes de programación

---

<div align="center">

**[⬅️ Nivel Anterior](./Bandit_Nivel_9___Nivel_10.md)** | **[🏠 Volver al README](./README.md)** | **[➡️ Siguiente Nivel](./Bandit_Nivel_11___Nivel_12.md)**

</div>
