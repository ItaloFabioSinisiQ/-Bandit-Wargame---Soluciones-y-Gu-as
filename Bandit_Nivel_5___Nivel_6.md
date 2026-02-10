# 🔐 Bandit Level 5 → Level 6

<div align="center">

![Nivel](https://img.shields.io/badge/Nivel-5_→_6-blue?style=for-the-badge)
![Dificultad](https://img.shields.io/badge/Dificultad-Medio-orange?style=for-the-badge)

**Objetivo:** Encontrar un archivo con características específicas en `inhere`

[🌐 Desafío Original](https://overthewire.org/wargames/bandit/bandit6.html) | [📺 Video Tutorial](#)

</div>

---

## 📌 Objetivo del Nivel

La contraseña para el siguiente nivel está almacenada en un archivo en algún lugar dentro del directorio `inhere` y tiene todas las siguientes características:

- ✅ Es legible por humanos
- ✅ Tiene un tamaño de **1033 bytes**
- ✅ No es ejecutable

---

## 🛠️ Comandos que Puedes Necesitar

`ls`, `cd`, `cat`, `file`, `du`, `find`

---

## 🎯 Solución Paso a Paso

### Paso 1️⃣: Navegar al directorio home (si no estás ahí)

```bash
cd ~
```

---

### Paso 2️⃣: Usar `find` para localizar el archivo

Para encontrar el archivo que cumple con las condiciones dadas, usa el comando `find` de la siguiente manera:

```bash
find inhere -type f -size 1033c ! -executable
```

---

### 📖 Explicación del Comando

| Parámetro | Descripción |
|-----------|-------------|
| `inhere` | Busca dentro de este directorio |
| `-type f` | Filtra solo archivos (no directorios) |
| `-size 1033c` | Busca archivos de exactamente **1033 bytes** |
| `! -executable` | Excluye archivos ejecutables |

El modificador `c` en `-size 1033c` significa "bytes" (characters).

---

### Paso 3️⃣: Leer el contenido del archivo encontrado

Una vez que encuentres el archivo, usa `cat` para ver su contenido y obtener la contraseña:

```bash
cat inhere/ruta/del/archivo
```

**Ejemplo de ruta completa:**
```bash
cat inhere/maybehere07/.file2
```

---

## 🔑 Contraseña para Nivel 6

```
HWasnPhtq9AVKe0dmk45nxy20cvUa6EG
```

---

## 🚀 Conectarse al Siguiente Nivel

Ahora puedes usarla para acceder a **Bandit Level 6** con el siguiente comando:

```bash
ssh bandit6@bandit.labs.overthewire.org -p 2220
```

Cuando te pida la contraseña, ingresa:

```
HWasnPhtq9AVKe0dmk45nxy20cvUa6EG
```

---

## 📚 Conceptos Aprendidos

- ✅ Uso avanzado del comando `find`
- ✅ Filtrado por tamaño de archivo
- ✅ Filtrado por permisos de ejecución
- ✅ Búsqueda recursiva en directorios
- ✅ Combinación de múltiples criterios de búsqueda

---

## 🔧 Comandos Utilizados

| Comando | Descripción |
|---------|-------------|
| `find inhere -type f` | Busca solo archivos en el directorio |
| `-size 1033c` | Filtra por tamaño exacto (1033 bytes) |
| `! -executable` | Excluye archivos ejecutables |
| `cat ruta/archivo` | Lee el contenido del archivo |

---

## 💡 Explicación Técnica

### El Comando `find` y sus Opciones

El comando `find` es una de las herramientas más poderosas para buscar archivos en Linux:

#### Sintaxis básica:
```bash
find [dónde_buscar] [qué_buscar] [qué_hacer]
```

#### Opciones comunes de tamaño:
- `-size 1033c` → Exactamente 1033 bytes
- `-size +1M` → Más de 1 megabyte
- `-size -100k` → Menos de 100 kilobytes

#### Opciones de tipo:
- `-type f` → Archivos regulares
- `-type d` → Directorios
- `-type l` → Enlaces simbólicos

#### Operadores lógicos:
- `!` → Negación (NO)
- `-and` / `-a` → Y lógico
- `-or` / `-o` → O lógico

---

<div align="center">

**[⬅️ Nivel Anterior](./Bandit_Nivel_4___Nivel_5.md)** | **[🏠 Volver al README](./README.md)** | **[➡️ Siguiente Nivel](./Bandit_Nivel_6___Nivel_7.md)**

</div>
