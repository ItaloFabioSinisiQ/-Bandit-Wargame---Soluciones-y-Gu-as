# 🔐 Bandit Level 2 → Level 3

<div align="center">

![Nivel](https://img.shields.io/badge/Nivel-2_→_3-blue?style=for-the-badge)
![Dificultad](https://img.shields.io/badge/Dificultad-Fácil-yellowgreen?style=for-the-badge)

**Objetivo:** Leer un archivo con espacios en el nombre

[🌐 Desafío Original](https://overthewire.org/wargames/bandit/bandit3.html) | [📺 Video Tutorial](#)

</div>

---

## 📌 Objetivo del Nivel

La contraseña para el siguiente nivel está almacenada en un archivo llamado **"spaces in this filename"**, ubicado en el directorio personal (_home directory_).

---

## 🛠️ Cómo leer archivos con espacios en el nombre

Cuando un archivo tiene espacios en su nombre, no puedes escribirlo directamente porque el terminal interpretará cada palabra como un argumento separado. Hay varias formas de solucionarlo:

---

### 🔹 Método 1: Usar comillas

```bash
cat "spaces in this filename"
```

Las comillas indican que todo el texto es un solo nombre de archivo.

---

### 🔹 Método 2: Usar barras invertidas (`\`)

```bash
cat spaces\ in\ this\ filename
```

Cada `\` indica que el espacio forma parte del nombre del archivo.

---

### 🔹 Método 3: Usar autocompletado con `Tab`

1. Escribe `cat spa` y presiona **Tab**.
2. El sistema completará el nombre automáticamente.

```bash
cat spa[TAB]
# Se autocompleta a:
cat spaces\ in\ this\ filename
```

> 💡 **Tip:** Este es el método más rápido y evita errores de escritura.

---

## 🔑 Contraseña para Nivel 3

```
MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx
```

---

## ✅ Pasos Finales

### 1️⃣ Ejecuta uno de los comandos anteriores para obtener la contraseña

### 2️⃣ Usa la contraseña para conectarte al siguiente nivel con:

```bash
ssh bandit3@bandit.labs.overthewire.org -p 2220
```

### 3️⃣ Cuando te pida la contraseña, introduce la que acabas de encontrar

---

## 📚 Conceptos Aprendidos

- ✅ Manejo de espacios en nombres de archivo
- ✅ Uso de comillas para agrupar texto
- ✅ Escape de caracteres con barra invertida (`\`)
- ✅ Autocompletado con Tab
- ✅ Diferencia entre argumentos separados y nombres de archivo

---

## 🔧 Comandos Utilizados

| Comando | Descripción |
|---------|-------------|
| `cat "spaces in this filename"` | Lee el archivo usando comillas |
| `cat spaces\ in\ this\ filename` | Lee el archivo escapando espacios |
| `[TAB]` | Autocompletado de nombres de archivo |

---

## 💡 Explicación Técnica

### ¿Por qué los espacios son problemáticos?

En la línea de comandos, los espacios separan diferentes argumentos. Por ejemplo:

```bash
cat archivo uno dos
# El sistema interpreta esto como:
# - Comando: cat
# - Argumento 1: archivo
# - Argumento 2: uno
# - Argumento 3: dos
```

Para indicar que "spaces in this filename" es **un solo argumento**, necesitamos:
- **Comillas:** Agrupan todo el texto
- **Escape (`\`):** Indica que el espacio es literal, no un separador

---

## 🚀 ¡Ya estarás en el Nivel 3! 💪😃

<div align="center">

**[⬅️ Nivel Anterior](./Bandit_Nivel_1___Nivel_2.md)** | **[🏠 Volver al README](./README.md)** | **[➡️ Siguiente Nivel](./Bandit_Nivel_3___Nivel_4.md)**

</div>
