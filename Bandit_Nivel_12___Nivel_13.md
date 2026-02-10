# 🔐 Bandit Level 12 → 13

<div align="center">

![Nivel](https://img.shields.io/badge/Nivel-12_→_13-blue?style=for-the-badge)
![Dificultad](https://img.shields.io/badge/Dificultad-Difícil-red?style=for-the-badge)

**Objetivo:** Descomprimir archivo hexdump múltiples veces

[🌐 Desafío Original](https://overthewire.org/wargames/bandit/bandit13.html) | [📺 Video Tutorial](#)

</div>

---

### Objetivo del Nivel 12 → Nivel 13

La contraseña para el siguiente nivel está almacenada en el archivo `data.txt`, el cual es un **hexdump** de un archivo que ha sido comprimido varias veces. Para este nivel, puede ser útil crear un directorio en `/tmp` donde puedas trabajar. Usa `mkdir` con un nombre difícil de adivinar o, mejor aún, usa el comando:

```bash
mktemp -d
```

Luego, copia el archivo de datos con `cp` y renómbralo con `mv` (consulta las páginas del manual para más información).

### Comandos útiles para resolver este nivel:

- `grep`
- `sort`
- `uniq`
- `strings`
- `base64`
- `tr`
- `tar`
- `gzip`
- `bzip2`
- `xxd`
- `mkdir`
- `cp`
- `mv`
- `file`

### Lectura recomendada:

- **Hex dump en Wikipedia** (explica cómo representar archivos en formato hexadecimal).

---

Aquí tienes una versión optimizada en un solo script:

```bash
#!/bin/bash

# Crear un directorio temporal y moverse a él
tempdir=$(mktemp -d)
cd "$tempdir"

# Copiar el archivo de origen
cp ~/data.txt .

# Convertir el archivo en binario
xxd -r data.txt data.bin

# Bucle de extracción hasta obtener un archivo de texto
file_type=$(file data.bin)

while [[ ! "$file_type" =~ "ASCII text" ]]; do
    case "$file_type" in
        *gzip*)    mv data.bin data.gz && gunzip data.gz ;;
        *bzip2*)   mv data.bin data.bz2 && bunzip2 data.bz2 ;;
        *tar*)     mv data.bin data.tar && tar -xf data.tar && rm data.tar ;;
        *)         echo "Formato desconocido: $file_type" && exit 1 ;;
    esac
    data_file=$(ls -1 | head -n 1)  # Obtener el nombre del archivo extraído
    mv "$data_file" data.bin         # Normalizar el nombre para el siguiente ciclo
    file_type=$(file data.bin)       # Volver a comprobar el tipo de archivo
done

# Mostrar el contenido del archivo de texto
cat data.bin
```

Aquí tienes una explicación detallada paso a paso de cada comando:

---

### 1. **Crear un directorio temporal y cambiar a él**

```bash
tempdir=$(mktemp -d)
echo "Directorio de trabajo: $tempdir"
cd "$tempdir"
```

- `mktemp -d`: Crea un directorio temporal único en `/tmp` y devuelve su ruta.
- `tempdir=$(...)`: Guarda la ruta del directorio en la variable `tempdir`.
- `echo "Directorio de trabajo: $tempdir"`: Muestra la ruta del directorio creado.
- `cd "$tempdir"`: Cambia al directorio temporal para trabajar ahí sin modificar otros archivos.

---

### 2. **Copiar el archivo `data.txt` al directorio temporal**

```bash
cp ~/data.txt .
```

- `cp ~/data.txt .`: Copia el archivo `data.txt` desde la carpeta personal (`~`) al directorio actual (`.`).

---

### 3. **Convertir el archivo `data.txt` a binario**

```bash
xxd -r data.txt data.bin
```

- `xxd`: Es una herramienta para ver archivos en formato hexadecimal o revertirlos a binario.
- `-r`: Indica que se debe revertir un archivo desde texto hexadecimal a su forma binaria.
- `data.txt`: Archivo de entrada en formato hexadecimal.
- `data.bin`: Archivo de salida en formato binario.

---

### 4. **Identificar el tipo de archivo**

```bash
file data.bin
```

- `file`: Muestra información sobre el tipo de archivo.
- `data.bin`: Identifica si es un archivo comprimido o de otro tipo.
- Se indica que es un archivo `gzip`.

---

### 5. **Renombrar y descomprimir el archivo `gzip`**

```bash
mv data.bin data.gz
gunzip data.gz
```

- `mv data.bin data.gz`: Renombra `data.bin` a `data.gz` para reflejar su formato real.
- `gunzip data.gz`: Descomprime el archivo `gzip`, eliminando `data.gz` y dejando `data`.

---

### 6. **Verificar el tipo del archivo descomprimido**

```bash
file data
```

- Indica que es un archivo `bzip2`.

---

### 7. **Renombrar y descomprimir el archivo `bzip2`**

```bash
mv data data.bz2
bunzip2 data.bz2
```

- `mv data data.bz2`: Renombra `data` a `data.bz2` para reflejar su formato real.
- `bunzip2 data.bz2`: Descomprime el archivo `bzip2`, eliminando `data.bz2` y dejando `data`.

---

### 8. **Verificar el tipo del archivo**

```bash
file data
```

- Ahora es otro archivo `gzip`.

---

### 9. **Renombrar y descomprimir el archivo `gzip`**

```bash
mv data data.gz
gunzip data.gz
```

- Renombra y descomprime nuevamente un archivo `gzip`.

---

### 10. **Verificar el tipo del archivo resultante**

```bash
file data
```

- Ahora es un archivo `tar` (archivo comprimido en formato `.tar`).

---

### 11. **Renombrar y extraer el archivo `tar`**

```bash
mv data data.tar
tar -xf data.tar
```

- `tar -xf data.tar`: Extrae los archivos contenidos en `data.tar`.

---

### 12. **Ver el contenido del directorio**

```bash
ls -l
```

- Se muestra un nuevo archivo `data5.bin`.

---

### 13. **Verificar el tipo de `data5.bin`**

```bash
file data5.bin
```

- Es otro archivo `tar`.

---

### 14. **Extraer `data5.bin`**

```bash
tar -xf data5.bin
```

- Extrae el contenido de `data5.bin`.

---

### 15. **Revisar el nuevo contenido del directorio**

```bash
ls -l
```

- Aparece `data6.bin`.

---

### 16. **Verificar el tipo de `data6.bin`**

```bash
file data6.bin
```

- Es un archivo `bzip2`.

---

### 17. **Descomprimir `data6.bin`**

```bash
bunzip2 data6.bin
```

- Si `bunzip2` no puede renombrar automáticamente el archivo, se generará `data6.bin.out`.

---

### 18. **Verificar el tipo de `data6.bin.out`**

```bash
file data6.bin.out
```

- Es otro archivo `tar`.

---

### 19. **Extraer `data6.bin.out`**

```bash
tar -xf data6.bin.out
```

- Se extrae el contenido del archivo `tar`.

---

### 20. **Ver el contenido del directorio**

```bash
ls -l
```

- Aparece `data8.bin`.

---

### 21. **Verificar el tipo de `data8.bin`**

```bash
file data8.bin
```

- Es un archivo `gzip`.

---

### 22. **Renombrar y descomprimir `data8.bin`**

```bash
mv data8.bin data8.gz
gunzip data8.gz
```

- Renombra y descomprime el archivo `gzip`.

---

### 23. **Verificar el tipo del archivo final**

```bash
file data8
```

- Se confirma que es un archivo de texto.

---

### 24. **Leer el contenido del archivo final para obtener la contraseña**

```bash
cat data8
```

- Se muestra la salida del archivo, que contiene la contraseña para el siguiente nivel:

```
The password is FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn
```

Ahora puedes usar esta contraseña para acceder al siguiente nivel en **Bandit (bandit13).** 🚀


Claro, te explicaré el código paso a paso, detallando cada línea y su propósito.

---

## **Explicación detallada del código**

Este script automatiza la extracción de un archivo que está comprimido múltiples veces en distintos formatos. Su objetivo es desempaquetarlo iterativamente hasta encontrar un archivo de texto con la contraseña.

---

### **1. Crear un directorio temporal y moverse a él**

```bash
tempdir=$(mktemp -d)
cd "$tempdir"
```

#### 🔍 Explicación:

- `mktemp -d`:
    - `mktemp` crea un archivo o directorio temporal con un nombre aleatorio.
    - `-d` indica que se debe crear un directorio en lugar de un archivo.
- `tempdir=$(mktemp -d)`:
    - Guarda la ruta del directorio temporal en la variable `tempdir`.
- `cd "$tempdir"`:
    - Cambia al directorio temporal recién creado.
    - Usamos comillas `""` para evitar problemas con espacios en la ruta.

---

### **2. Copiar el archivo `data.txt` al directorio temporal**

```bash
cp ~/data.txt .
```

#### 🔍 Explicación:

- `cp`: Copia archivos.
- `~/data.txt`: Ruta del archivo de origen (ubicado en el home del usuario).
- `.`: Indica que el destino es el directorio actual.

Después de este paso, el archivo `data.txt` se encuentra en nuestro directorio temporal.

---

### **3. Convertir el archivo `data.txt` en binario**

```bash
xxd -r data.txt data.bin
```

#### 🔍 Explicación:

- `xxd`:
    - Comando usado para crear representaciones hexadecimales de archivos.
    - Con la opción `-r` (reverse), reconstruye el archivo original a partir de su representación en texto.
- `data.txt`: Archivo de entrada con el contenido en formato hexadecimal.
- `data.bin`: Archivo de salida en formato binario (original).

Después de este paso, `data.bin` es la versión binaria real de `data.txt`.

---

### **4. Detectar el tipo de archivo**

```bash
file_type=$(file data.bin)
```

#### 🔍 Explicación:

- `file data.bin`:
    - El comando `file` analiza el tipo de contenido de `data.bin`.
    - Devuelve una cadena indicando el tipo de archivo, por ejemplo:
        
        ```
        data.bin: gzip compressed data
        ```
        
- `file_type=$(...)`:
    - Guarda el resultado en la variable `file_type` para su uso posterior.

---

### **5. Descomprimir el archivo hasta encontrar un texto**

```bash
while [[ ! "$file_type" =~ "ASCII text" ]]; do
```

#### 🔍 Explicación:

- `while [[ ! "$file_type" =~ "ASCII text" ]]; do`
    - Ejecuta el bloque de código dentro del `while` hasta que `file_type` contenga `"ASCII text"`.
    - `"ASCII text"` significa que el archivo ya es un texto legible, por lo que no hay más compresión.

---

### **6. Verificar el tipo de compresión y descomprimir**

```bash
case "$file_type" in
    *gzip*)    mv data.bin data.gz && gunzip data.gz ;;
    *bzip2*)   mv data.bin data.bz2 && bunzip2 data.bz2 ;;
    *tar*)     mv data.bin data.tar && tar -xf data.tar && rm data.tar ;;
    *)         echo "Formato desconocido: $file_type" && exit 1 ;;
esac
```

#### 🔍 Explicación:

- `case "$file_type" in ... esac`
    - Estructura condicional que evalúa la variable `file_type` y ejecuta la acción correspondiente según el formato detectado.

##### 📌 **Si el archivo es un `gzip`**

```bash
*gzip*)    mv data.bin data.gz && gunzip data.gz ;;
```

- `mv data.bin data.gz`
    - Renombra `data.bin` a `data.gz` (porque `gunzip` requiere la extensión `.gz`).
- `gunzip data.gz`
    - Descomprime el archivo y lo reemplaza con su contenido descomprimido.

##### 📌 **Si el archivo es un `bzip2`**

```bash
*bzip2*)   mv data.bin data.bz2 && bunzip2 data.bz2 ;;
```

- `mv data.bin data.bz2`
    - Renombra `data.bin` a `data.bz2` (porque `bunzip2` requiere `.bz2`).
- `bunzip2 data.bz2`
    - Descomprime el archivo `.bz2`.

##### 📌 **Si el archivo es un `tar`**

```bash
*tar*)     mv data.bin data.tar && tar -xf data.tar && rm data.tar ;;
```

- `mv data.bin data.tar`
    - Renombra `data.bin` a `data.tar` (porque `tar` trabaja con archivos `.tar`).
- `tar -xf data.tar`
    - Extrae el contenido del archivo `.tar`.
- `rm data.tar`
    - Elimina el archivo `.tar` después de extraerlo, para mantener el directorio limpio.

##### 📌 **Si el formato no es reconocido**

```bash
*)         echo "Formato desconocido: $file_type" && exit 1 ;;
```

- Si `file_type` no coincide con `gzip`, `bzip2` o `tar`, se muestra un mensaje de error y el script se detiene con `exit 1`.

---

### **7. Obtener el archivo extraído más reciente**

```bash
data_file=$(ls -1 | head -n 1)
```

#### 🔍 Explicación:

- `ls -1`
    - Lista todos los archivos del directorio en una sola columna.
- `head -n 1`
    - Toma solo el primer archivo de la lista.
- `data_file=$(...)`
    - Guarda el nombre del archivo en la variable `data_file`.

Después de este paso, `data_file` contiene el nombre del archivo extraído más reciente.

---

### **8. Renombrar el archivo para continuar el proceso**

```bash
mv "$data_file" data.bin
```

#### 🔍 Explicación:

- `mv "$data_file" data.bin"`
    - Renombra el archivo extraído como `data.bin`, para seguir el proceso en el siguiente ciclo del `while`.

---

### **9. Volver a comprobar el tipo del archivo**

```bash
file_type=$(file data.bin)
```

#### 🔍 Explicación:

- Se actualiza `file_type` con el nuevo tipo de `data.bin`.
- El bucle `while` se repetirá hasta que el archivo sea de tipo `"ASCII text"`.

---

### **10. Mostrar el contenido del archivo final**

```bash
cat data.bin
```

#### 🔍 Explicación:

- `cat data.bin`
    - Muestra el contenido del archivo final en la terminal.
    - Como el `while` se detuvo, `data.bin` ya es un archivo de texto.
    - Contiene la contraseña necesaria para el siguiente nivel.

---

## **Resumen**

📌 El script:  
✅ Crea un directorio temporal y copia `data.txt`.  
✅ Convierte `data.txt` en binario (`data.bin`).  
✅ Detecta el tipo de compresión y la extrae en un bucle.  
✅ Renombra los archivos para procesarlos secuencialmente.  
✅ Se detiene cuando encuentra un archivo de texto.  
✅ Muestra la contraseña en pantalla.


---

<div align="center">

**[⬅️ Nivel Anterior](./Bandit_Nivel_11___Nivel_11.md)** | **[🏠 Volver al README](./README.md)** | **[➡️ Siguiente Nivel](./Bandit_Nivel_13___Nivel_14.md)**

</div>
