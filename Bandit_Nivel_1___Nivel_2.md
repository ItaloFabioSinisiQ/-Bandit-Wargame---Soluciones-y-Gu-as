# 🔐 Bandit Level 1 → Level 2

<div align="center">

![Nivel](https://img.shields.io/badge/Nivel-1_→_2-blue?style=for-the-badge)
![Dificultad](https://img.shields.io/badge/Dificultad-Fácil-yellowgreen?style=for-the-badge)

**Objetivo:** Leer un archivo llamado `-` (guion)

[🌐 Desafío Original](https://overthewire.org/wargames/bandit/bandit2.html) | [📺 Video Tutorial](https://www.youtube.com/watch?v=3F2V0pH3UH0)

</div>

---

## 📌 Objetivo del Nivel

La contraseña para el siguiente nivel está almacenada en un archivo llamado **"-"** (un solo guion), ubicado en el directorio personal (_home directory_).

---

## 🛠️ Solución Paso a Paso

### Paso 1️⃣: Lista los archivos en el directorio

```bash
ls -l
```

**Salida esperada:**
```
-rw-r----- 1 bandit2 bandit1 33 ... -
```

Deberías ver un archivo con el nombre `-`.

---

### Paso 2️⃣: Leer el contenido del archivo `-`

⚠️ **El problema:** `-` es un carácter especial en Linux, ya que suele indicar la entrada estándar (_stdin_). Para abrirlo correctamente, usa uno de estos métodos:

#### 🔹 Método 1: Especificar la ruta relativa

```bash
cat ./-
```

Aquí `./` le indica a `cat` que el archivo `-` está en el directorio actual.

---

#### 🔹 Método 2: Usar `--` para indicar que `-` es un archivo

```bash
cat -- -
```

El `--` le dice a `cat` que todo lo que sigue es un nombre de archivo y no una opción.

---

## 🔑 Contraseña para Nivel 2

```
263JGJPfgU6LtdEvgfWU1XP5yac29mFx
```

---

### Paso 3️⃣: Guardar la contraseña y conectarse al siguiente nivel

La contraseña aparecerá en la terminal. Guárdala y úsala para conectarte al siguiente nivel:

```bash
ssh bandit2@bandit.labs.overthewire.org -p 2220
```

Cuando te pida la contraseña, introduce la que acabas de encontrar.

---

## 📚 Conceptos Aprendidos

- ✅ Manejo de caracteres especiales en nombres de archivo
- ✅ Uso de rutas relativas (`./`)
- ✅ Separador de opciones (`--`)
- ✅ Diferencia entre nombres de archivo y opciones de comando

---

## 🔧 Comandos Utilizados

| Comando | Descripción |
|---------|-------------|
| `ls -l` | Lista archivos con detalles (permisos, tamaño, fecha) |
| `cat ./-` | Lee el archivo `-` usando ruta relativa |
| `cat -- -` | Lee el archivo `-` usando separador de opciones |

---

## 💡 Explicación Técnica

### ¿Por qué `-` es especial?

En la mayoría de comandos Unix/Linux, el guion (`-`) tiene significados especiales:
- `-` solo → Representa STDIN (entrada estándar) o STDOUT (salida estándar)
- `-opción` → Indica una opción del comando (flag)

Por eso necesitamos **escapar** o **especificar la ruta** para que el sistema entienda que es un nombre de archivo.

---

<div align="center">

**[⬅️ Nivel Anterior](./Bandit_Nivel_0___Nivel_1.md)** | **[🏠 Volver al README](./README.md)** | **[➡️ Siguiente Nivel](./Bandit_Nivel_2___Nivel_3.md)**

</div>
