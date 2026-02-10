# 🔐 Bandit Level 7 → Level 8

<div align="center">

![Nivel](https://img.shields.io/badge/Nivel-7_→_8-blue?style=for-the-badge)
![Dificultad](https://img.shields.io/badge/Dificultad-Fácil-yellowgreen?style=for-the-badge)

**Objetivo:** Encontrar una contraseña junto a la palabra "millionth"

[🌐 Desafío Original](https://overthewire.org/wargames/bandit/bandit8.html) | [📺 Video Tutorial](#)

</div>

---

## 📌 Objetivo del Nivel

La contraseña para el siguiente nivel está almacenada en el archivo **data.txt**, junto a la palabra **millionth**.

---

## 🛠️ Comandos que Puedes Necesitar

`man`, `grep`, `sort`, `uniq`, `strings`, `base64`, `tr`, `tar`, `gzip`, `bzip2`, `xxd`

---

## 🎯 Solución Paso a Paso

### Método 1️⃣: Usando `grep` directamente (Recomendado)

```bash
grep millionth data.txt
```

**Salida esperada:**
```
millionth	dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc
```

---

### Método 2️⃣: Usando `cat` con pipe

```bash
cat data.txt | grep millionth
```

---

## 🔑 Contraseña para Nivel 8

```
dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc
```

---

## 🚀 Conectarse al Siguiente Nivel

¡Bien hecho! Has encontrado la contraseña para el siguiente nivel:

```bash
ssh bandit8@bandit.labs.overthewire.org -p 2220
```

---

## 📚 Conceptos Aprendidos

- ✅ Búsqueda de patrones con `grep`
- ✅ Uso de pipes (`|`) para encadenar comandos
- ✅ Diferencia entre usar `cat | grep` vs `grep` directamente
- ✅ Filtrado de texto en archivos grandes

---

## 🔧 Comandos Utilizados

| Comando | Descripción |
|---------|-------------|
| `grep millionth data.txt` | Busca la palabra "millionth" en el archivo |
| `cat data.txt \| grep millionth` | Alternativa usando pipe |

---

## 💡 Explicación Técnica

### Comparación: `cat | grep` vs `grep` directo

Las dos formas hacen lo mismo, pero hay una pequeña diferencia en cómo se ejecutan:

#### 1️⃣ Usando `cat data.txt | grep millionth`

```bash
cat data.txt | grep millionth
```

**Proceso:**
- `cat data.txt` muestra todo el contenido del archivo
- `|` (pipe) pasa la salida de `cat` como entrada a `grep millionth`
- `grep` filtra la línea que contiene "millionth"

🔴 **Desventaja:** `cat` es innecesario porque `grep` ya puede leer el archivo directamente.

---

#### 2️⃣ Usando `grep millionth data.txt` (Forma recomendada)

```bash
grep millionth data.txt
```

**Proceso:**
- `grep` busca directamente en el archivo sin necesidad de `cat`

✅ **Más eficiente** porque `grep` abre el archivo directamente en lugar de recibir datos por un `pipe`.

---

### 💡 Regla General

**Evita el uso innecesario de `cat`** cuando puedes pasar el archivo directamente al comando.

**USELESS USE OF CAT (UUoC)** es un término común en la comunidad Linux para referirse a este anti-patrón.

#### ❌ Mal (innecesario):
```bash
cat archivo.txt | grep patron
cat archivo.txt | wc -l
```

#### ✅ Bien (directo):
```bash
grep patron archivo.txt
wc -l archivo.txt
```

---

### ¿Qué hace `grep`?

`grep` (Global Regular Expression Print) busca patrones de texto en archivos.

**Sintaxis básica:**
```bash
grep [opciones] patron archivo
```

**Opciones útiles:**
- `-i` → Ignora mayúsculas/minúsculas
- `-n` → Muestra números de línea
- `-v` → Invierte la búsqueda (muestra líneas que NO coinciden)
- `-c` → Cuenta cuántas líneas coinciden
- `-r` → Búsqueda recursiva en directorios

---

<div align="center">

**[⬅️ Nivel Anterior](./Bandit_Nivel_6___Nivel_7.md)** | **[🏠 Volver al README](./README.md)** | **[➡️ Siguiente Nivel](./Bandit_Nivel_8___Nivel_9.md)**

</div>
