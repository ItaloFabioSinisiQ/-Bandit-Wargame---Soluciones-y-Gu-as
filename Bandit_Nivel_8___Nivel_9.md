# 🔐 Bandit Level 8 → Level 9

<div align="center">

![Nivel](https://img.shields.io/badge/Nivel-8_→_9-blue?style=for-the-badge)
![Dificultad](https://img.shields.io/badge/Dificultad-Medio-orange?style=for-the-badge)

**Objetivo:** Encontrar la única línea de texto que aparece solo una vez

[🌐 Desafío Original](https://overthewire.org/wargames/bandit/bandit9.html) | [📺 Video Tutorial](#)

</div>

---

## 📌 Objetivo del Nivel

La contraseña para el siguiente nivel está almacenada en el archivo **data.txt** y es la única línea de texto que aparece **solo una vez**.

---

## 🛠️ Comandos que Puedes Necesitar

`grep`, `sort`, `uniq`, `strings`, `base64`, `tr`, `tar`, `gzip`, `bzip2`, `xxd`

---

## 🎯 Solución Paso a Paso

### Comando para Encontrar la Línea Única

```bash
sort data.txt | uniq -u
```

**Salida esperada:**
```
4CKMh1JI91bUIZZPXDqGanal4xvAg0JM
```

---

## 🔑 Contraseña para Nivel 9

```
4CKMh1JI91bUIZZPXDqGanal4xvAg0JM
```

---

## 🚀 Conectarse al Siguiente Nivel

```bash
ssh bandit9@bandit.labs.overthewire.org -p 2220
```

---

## 📚 Conceptos Aprendidos

- ✅ Ordenamiento de archivos con `sort`
- ✅ Detección de líneas únicas con `uniq`
- ✅ Encadenamiento de comandos con pipes
- ✅ Análisis de datos duplicados

---

## 🔧 Comandos Utilizados

| Comando | Descripción |
|---------|-------------|
| `sort data.txt` | Ordena las líneas del archivo alfabéticamente |
| `uniq -u` | Muestra solo las líneas únicas (no repetidas) |
| `\|` (pipe) | Conecta la salida de `sort` con la entrada de `uniq` |

---

## 💡 Explicación Técnica

### Paso a Paso del Comando

```bash
sort data.txt | uniq -u
```

#### 1️⃣ `sort data.txt`
- Ordena todas las líneas del archivo `data.txt` alfabéticamente
- **¿Por qué es necesario?** Porque `uniq` solo puede detectar duplicados cuando las líneas idénticas están **contiguas** (una al lado de la otra)

**Ejemplo sin ordenar:**
```
banana
apple
banana
cherry
apple
```

**Después de `sort`:**
```
apple
apple
banana
banana
cherry
```

---

#### 2️⃣ `|` (pipe o tubería)
- Toma la salida del comando `sort data.txt`
- La pasa como entrada al siguiente comando (`uniq -u`)

---

#### 3️⃣ `uniq -u`
- Muestra solo las líneas que son **únicas**, es decir, las que no tienen duplicados
- La opción `-u` significa "unique" (único)

**Continuando el ejemplo anterior:**
```
apple    ← aparece 2 veces (se descarta)
apple    
banana   ← aparece 2 veces (se descarta)
banana   
cherry   ← aparece 1 vez (¡esta es la única!)
```

**Resultado final:**
```
cherry
```

---

### Otras Opciones Útiles de `uniq`

| Opción | Descripción | Ejemplo |
|--------|-------------|---------|
| `uniq` | Elimina líneas duplicadas consecutivas | `sort file \| uniq` |
| `uniq -u` | Muestra solo líneas únicas | `sort file \| uniq -u` |
| `uniq -d` | Muestra solo líneas duplicadas | `sort file \| uniq -d` |
| `uniq -c` | Cuenta cuántas veces aparece cada línea | `sort file \| uniq -c` |
| `uniq -i` | Ignora mayúsculas/minúsculas | `sort file \| uniq -i` |

---

### ¿Por qué `sort` es Necesario?

`uniq` solo compara líneas **consecutivas**. Observa la diferencia:

#### ❌ Sin `sort`:
```bash
cat data.txt | uniq -u
# Podría mostrar líneas que SÍ están duplicadas pero no están juntas
```

#### ✅ Con `sort`:
```bash
sort data.txt | uniq -u
# Agrupa todas las líneas idénticas, luego encuentra las únicas
```

---

### Ejemplo Completo

**Contenido de `data.txt`:**
```
hello
world
hello
foo
bar
world
baz
```

**Ejecutando el comando:**
```bash
sort data.txt | uniq -u
```

**Resultado:**
```
bar
baz
foo
```

Porque `hello` y `world` aparecen 2 veces cada una, mientras que `bar`, `baz`, y `foo` aparecen solo 1 vez.

---

<div align="center">

**[⬅️ Nivel Anterior](./Bandit_Nivel_7___Nivel_8.md)** | **[🏠 Volver al README](./README.md)** | **[➡️ Siguiente Nivel](./Bandit_Nivel_9___Nivel_10.md)**

</div>
