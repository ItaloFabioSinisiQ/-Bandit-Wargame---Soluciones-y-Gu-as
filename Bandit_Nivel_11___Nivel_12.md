# 🔐 Bandit Level 11 → Level 12

<div align="center">

![Nivel](https://img.shields.io/badge/Nivel-11_→_12-blue?style=for-the-badge)
![Dificultad](https://img.shields.io/badge/Dificultad-Medio-orange?style=for-the-badge)

**Objetivo:** Decodificar texto con cifrado ROT13

[🌐 Desafío Original](https://overthewire.org/wargames/bandit/bandit12.html) | [📺 Video Tutorial](#)

</div>

---

## 📌 Objetivo del Nivel

La contraseña para el siguiente nivel está almacenada en el archivo `data.txt`, donde todas las letras minúsculas (a-z) y mayúsculas (A-Z) han sido rotadas 13 posiciones.

---

## 🛠️ Comandos que Puedes Necesitar

`grep`, `sort`, `uniq`, `strings`, `base64`, `tr`, `tar`, `gzip`, `bzip2`, `xxd`

---

## 📖 Lectura Útil

- **Rot13 en Wikipedia**

---

## 🎯 Solución Paso a Paso

### Paso 1️⃣: Listar los archivos en el directorio

```bash
ls
```

Esto te mostrará el archivo `data.txt`.

---

### Paso 2️⃣: Verificar el contenido del archivo

```bash
cat data.txt
```

Verás un texto cifrado con ROT13.

---

### Paso 3️⃣: Decodificar el texto usando `tr`

```bash
cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
```

Esto convertirá el texto a su versión legible.

---

## 🔑 Contraseña para Nivel 12

```
7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4
```

---

### Paso 4️⃣: Usar la contraseña para acceder al siguiente nivel

```bash
ssh bandit12@bandit.labs.overthewire.org -p 2220
```

Cuando te pida la contraseña, ingresa la que obtuviste.

---

## 📚 Conceptos Aprendidos

- ✅ Cifrado ROT13
- ✅ Uso del comando `tr` para traducción de caracteres
- ✅ Cifrados por sustitución
- ✅ Concepto de cifrado reversible

---

## 🔧 Comandos Utilizados

| Comando | Descripción |
|---------|-------------|
| `tr 'A-Za-z' 'N-ZA-Mn-za-m'` | Aplica el cifrado ROT13 |
| `cat data.txt` | Muestra el contenido del archivo |

---

## 💡 Explicación del Cifrado ROT13

### ¿Qué es ROT13?

El cifrado **ROT13** es una forma simple de cifrado por sustitución, en la que cada letra del alfabeto es reemplazada por la letra que está **13 posiciones después** en el alfabeto.

**Ejemplo de transformación:**
- **A → N**
- **B → O**
- **C → P**
- **...**
- **M → Z**
- **N → A**
- **O → B**
- **...**
- **Z → M**

Dado que el alfabeto tiene 26 letras, aplicar ROT13 **dos veces** devuelve el texto original.

---

### Desglose del Comando `tr`

```bash
cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
```

#### 1. Explicación general

- `cat data.txt`: Muestra el contenido del archivo
- `|`: Pasa la salida como entrada al siguiente comando
- `tr 'A-Za-z' 'N-ZA-Mn-za-m'`: Usa `tr` (**translate**) para reemplazar caracteres

---

#### 2. Funcionamiento de `tr 'A-Za-z' 'N-ZA-Mn-za-m'`

- **`'A-Za-z'`**: Define el **conjunto de entrada**
  - Todos los caracteres del alfabeto en mayúsculas (`A-Z`) y minúsculas (`a-z`)

- **`'N-ZA-Mn-za-m'`**: Define el **conjunto de salida**
  - Los mismos caracteres pero desplazados 13 posiciones

---

#### 3. Desglose del mapeo de caracteres

**Mayúsculas (`A-Z` → `N-ZA-M`):**
- `A → N`, `B → O`, ..., `M → Z`
- `N → A`, `O → B`, ..., `Z → M`

**Minúsculas (`a-z` → `n-za-m`):**
- `a → n`, `b → o`, ..., `m → z`
- `n → a`, `o → b`, ..., `z → m`

Esto implementa el **cifrado ROT13**, que es una variante del cifrado César con un desplazamiento de 13 posiciones.

---

### Ejemplo Práctico

**Texto original:**
```
Hello World!
```

**Al ejecutar el comando:**
```bash
echo "Hello World!" | tr 'A-Za-z' 'N-ZA-Mn-za-m'
```

**Salida:**
```
Uryyb Jbeyq!
```

**Explicación:**
- `H → U`, `e → r`, `l → y`, `l → y`, `o → b`
- `W → J`, `o → b`, `r → e`, `l → y`, `d → q`

---

### Propiedades de ROT13

✅ **Es reversible:** Aplicar ROT13 dos veces devuelve el texto original
✅ **Es simétrico:** El mismo proceso codifica y decodifica
✅ **Mantiene caracteres no alfabéticos:** Números, símbolos y espacios no cambian
❌ **NO es seguro:** Es extremadamente fácil de romper (no usar para información sensible)

---

### Usos de ROT13

- 🎯 Ocultar spoilers en foros
- 🎯 Ofuscar texto de forma rápida sin encriptación fuerte
- 🎯 Ejercicios de programación y criptografía básica
- 🎯 Puzzles y rompecabezas

---

### Otros Comandos Útiles con `tr`

```bash
# Convertir a mayúsculas
echo "hola" | tr 'a-z' 'A-Z'  # Output: HOLA

# Convertir a minúsculas
echo "HOLA" | tr 'A-Z' 'a-z'  # Output: hola

# Eliminar caracteres
echo "Hola123" | tr -d '0-9'  # Output: Hola

# Reemplazar espacios por guiones
echo "hola mundo" | tr ' ' '-'  # Output: hola-mundo
```

---

<div align="center">

**[⬅️ Nivel Anterior](./Bandit_Nivel_10___Nivel_11.md)** | **[🏠 Volver al README](./README.md)** | **[➡️ Siguiente Nivel](./Bandit_Nivel_12___Nivel_13.md)**

</div>
