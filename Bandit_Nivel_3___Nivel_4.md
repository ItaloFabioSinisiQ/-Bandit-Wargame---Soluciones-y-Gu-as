# 🔐 Bandit Level 3 → Level 4

<div align="center">

![Nivel](https://img.shields.io/badge/Nivel-3_→_4-blue?style=for-the-badge)
![Dificultad](https://img.shields.io/badge/Dificultad-Fácil-yellowgreen?style=for-the-badge)

**Objetivo:** Encontrar un archivo oculto en el directorio `inhere`

[🌐 Desafío Original](https://overthewire.org/wargames/bandit/bandit4.html) | [📺 Video Tutorial](#)

</div>

---

## 📌 Objetivo del Nivel

La contraseña para el siguiente nivel está almacenada en un archivo oculto en el directorio **inhere**.

---

## 🚀 Solución Paso a Paso

### Paso 1️⃣: Entra en el directorio `inhere`

```bash
cd inhere
```

**Verificación:**
```bash
pwd
# Salida: /home/bandit3/inhere
```

---

### Paso 2️⃣: Lista todos los archivos, incluidos los ocultos

```bash
ls -la
```

**Salida esperada:**
```
total 12
drwxr-xr-x 2 root    root    4096 ... .
drwxr-xr-x 3 root    root    4096 ... ..
-rw-r----- 1 bandit4 bandit3   33 ... .hidden
```

Deberías ver un archivo oculto (`.hidden` o algo similar).

> 💡 **Nota:** Los archivos que comienzan con `.` son archivos ocultos en Linux.

---

### Paso 3️⃣: Lee el contenido del archivo oculto

Si el archivo se llama `.hidden`, usa:

```bash
cat .hidden
```

**Esto mostrará la contraseña para el nivel 4.**

---

## 🔑 Contraseña para Nivel 4

```
2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ
```

---

### Paso 4️⃣: Conéctate al nivel 4 con la nueva contraseña

```bash
ssh bandit4@bandit.labs.overthewire.org -p 2220
```

Cuando te pida la contraseña, ingresa la que encontraste en el archivo oculto.

---

## 📚 Conceptos Aprendidos

- ✅ Navegación entre directorios con `cd`
- ✅ Archivos ocultos en Linux (comienzan con `.`)
- ✅ Comando `ls -la` para ver archivos ocultos
- ✅ Lectura de archivos ocultos con `cat`
- ✅ Verificación del directorio actual con `pwd`

---

## 🔧 Comandos Utilizados

| Comando | Descripción |
|---------|-------------|
| `cd inhere` | Cambia al directorio `inhere` |
| `pwd` | Muestra el directorio de trabajo actual |
| `ls -la` | Lista todos los archivos, incluidos los ocultos |
| `cat .hidden` | Muestra el contenido del archivo oculto |

---

## 💡 Explicación Técnica

### ¿Qué significa `ls -la`?

```bash
ls -la
```

Desglose de las opciones:
- `l` → Lista en formato largo (muestra permisos, propietario, tamaño, fecha)
- `a` → Muestra **all** (todos) los archivos, incluyendo los ocultos

### ¿Por qué algunos archivos están ocultos?

En sistemas Unix/Linux, cualquier archivo o directorio que comienza con un punto (`.`) se considera oculto. Esto se usa típicamente para:
- Archivos de configuración (`.bashrc`, `.gitconfig`)
- Directorios del sistema (`.ssh`, `.cache`)
- Archivos que no necesitas ver constantemente

---

## 🎯 Resumen del Proceso

```
1. cd inhere          → Entrar al directorio
2. ls -la             → Ver archivos ocultos
3. cat .hidden        → Leer la contraseña
4. ssh bandit4@...    → Conectarse al siguiente nivel
```

---

<div align="center">

**[⬅️ Nivel Anterior](./Bandit_Nivel_2___Nivel_3.md)** | **[🏠 Volver al README](./README.md)** | **[➡️ Siguiente Nivel](#)**

</div>
