# 🔐 Bandit Level 21 → 22

<div align="center">

![Nivel](https://img.shields.io/badge/Nivel-21_→_22-blue?style=for-the-badge)
![Dificultad](https://img.shields.io/badge/Dificultad-Medio-orange?style=for-the-badge)

**Objetivo:** Analizar cronjobs

[🌐 Desafío Original](https://overthewire.org/wargames/bandit/bandit22.html) | [📺 Video Tutorial](#)

</div>

---


## Objetivo del Nivel
Un programa se está ejecutando automáticamente a intervalos regulares desde cron, el programador de trabajos basado en tiempo. Mira en /etc/cron.d/ la configuración y observa qué comando se está ejecutando.

## Comandos que puedes necesitar para resolver este nivel
- `cron`
- `crontab`
- `crontab(5)` (usa "man 5 crontab" para acceder a esto)

## Explicación adicional:
En este nivel, necesitas investigar los trabajos programados en cron para encontrar cómo se está ejecutando automáticamente un programa. El directorio /etc/cron.d/ contiene archivos de configuración para cron, donde puedes encontrar qué comandos se ejecutan y con qué frecuencia.


### **Paso 1: Conectarse al servidor**
Ejecuta el siguiente comando para conectarte al servidor del juego:
```bash
ssh bandit21@bandit.labs.overthewire.org -p 2220
```
- **Contraseña**: Introduce la contraseña del nivel actual (bandit21). Si no la tienes, búscala en los niveles anteriores.

---

### **Paso 2: Explorar los trabajos de cron**
Los trabajos de cron se almacenan en `/etc/cron.d/`. Accede a ese directorio y lista los archivos:
```bash
cd /etc/cron.d
ls -l
```
Verás archivos como `cronjob_bandit22`. Este es el que nos interesa.

---

### **Paso 3: Analizar el cronjob de bandit22**
Usa `cat` para ver el contenido del archivo `cronjob_bandit22`:
```bash
cat cronjob_bandit22
```
Verás algo como esto:
```
@reboot bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null
* * * * * bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null
```
- Esto indica que el script `/usr/bin/cronjob_bandit22.sh` se ejecuta **cada minuto** con los permisos del usuario `bandit22`.

---

### **Paso 4: Inspeccionar el script del cronjob**
Abre el script para ver qué hace:
```bash
cat /usr/bin/cronjob_bandit22.sh
```
El contenido será algo como:
```bash
#!/bin/bash
chmod 644 /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
cat /etc/bandit_pass/bandit22 > /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
```
- **Explicación**:
  1. `chmod 644 ...`: Cambia los permisos del archivo `/tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv` para que sea legible por cualquier usuario.
  2. `cat /etc/bandit_pass/bandit22 > ...`: Guarda la contraseña de `bandit22` en ese archivo temporal.

---

### **Paso 5: Leer el archivo temporal**
El archivo `/tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv` contiene la contraseña de `bandit22`. Ejecuta:
```bash
cat /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
```
- **Nota**: El nombre del archivo puede variar, pero en este nivel es estático. Si no existe, espera 1 minuto a que el cronjob se ejecute.

---

### **Resultado**
Obtendrás una cadena de texto como esta:
```
tRae0UfB9v0UzbCdn9cY0gQnds9GF58Q
```
¡Esta es la contraseña para el nivel 22!

---

### **Comandos clave usados**
1. `cd /etc/cron.d`: Navega al directorio de cron.
2. `cat cronjob_bandit22`: Muestra el contenido del cronjob.
3. `cat /usr/bin/cronjob_bandit22.sh`: Analiza el script que se ejecuta.
4. `cat /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv`: Lee la contraseña del archivo temporal.

---

### **¿Por qué funciona?**
- El cronjob se ejecuta con los permisos de `bandit22`, por lo que puede leer `/etc/bandit_pass/bandit22`.
- El script guarda la contraseña en un archivo con permisos públicos (`644`), lo que nos permite leerlo como `bandit21`.
¡No hay problema! Vamos a desglosar todo **paso a paso, con ejemplos y explicaciones detalladas**. 🌟

---

## **1. ¿Qué es `/etc/cron.d/`?**
Es un **directorio del sistema** donde se guardan archivos de configuración para programar tareas automáticas con `cron`.  
- **`cron`** es un "programador de tareas" en Linux. Permite ejecutar comandos o scripts en momentos específicos (ej. cada minuto, cada día a las 3 AM, etc.).
- **`/etc/cron.d/`** contiene archivos de configuración **para todos los usuarios y servicios**. Cada archivo define tareas específicas.

### Ejemplo:
Si ejecutas `ls -l /etc/cron.d/`, verás archivos como:
```
cronjob_bandit22
```
Cada uno de estos archivos define **qué comando se ejecuta, cuándo y con qué usuario**.

---

## **2. Entendiendo el cronjob: `@reboot` y `* * * * *`**
El contenido del archivo `cronjob_bandit22` es:
```
@reboot bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null
* * * * * bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null
```

### Explicación línea por línea:
1. **`@reboot bandit22 ...`**:
   - **`@reboot`**: Indica que el comando se ejecutará **una vez, cuando el sistema se reinicie**.
   - **`bandit22`**: El usuario con el que se ejecuta el comando.
   - **`/usr/bin/cronjob_bandit22.sh`**: Ruta del script que se ejecutará.
   - **`&> /dev/null`**: Redirige cualquier salida (errores o mensajes) a un "agujero negro" (no se muestra nada en pantalla).

2. **`* * * * * bandit22 ...`**:
   - **`* * * * *`**: Define **cuándo** se ejecuta el comando. Los asteriscos corresponden a:
     ```
     minuto (0-59)  
     hora (0-23)  
     día del mes (1-31)  
     mes (1-12)  
     día de la semana (0-7, donde 0 y 7 son domingo).
     ```
   - Como todos son `*`, significa **"ejecutar cada minuto, todos los días"**.

### Ejemplo de uso de `*`:
- `0 3 * * *` = Ejecutar todos los días a las 3:00 AM.
- `*/5 * * * *` = Ejecutar cada 5 minutos.

---

## **3. Entendiendo el script: `/usr/bin/cronjob_bandit22.sh`**
El contenido del script es:
```bash
#!/bin/bash
chmod 644 /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
cat /etc/bandit_pass/bandit22 > /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
```

### Explicación línea por línea:
1. **`#!/bin/bash`**: Indica que es un script de Bash (el intérprete de comandos de Linux).
   
2. **`chmod 644 /tmp/...`**:
   - **`chmod`**: Comando para cambiar permisos de archivos.
   - **`644`**: Define los permisos:
     - **`6`** (propietario): Lectura (`4`) + Escritura (`2`).
     - **`4`** (grupo): Solo lectura.
     - **`4`** (otros): Solo lectura.
   - Es decir: Cualquier usuario puede **leer** el archivo, pero solo el propietario puede modificarlo.

3. **`cat /etc/bandit_pass/bandit22 > /tmp/...`**:
   - **`cat`**: Muestra el contenido de un archivo.
   - **`/etc/bandit_pass/bandit22`**: Archivo con la contraseña del nivel 22 (solo el usuario `bandit22` puede leerlo).
   - **`>`**: Redirige la salida del `cat` (la contraseña) al archivo `/tmp/...`.
   - **Resultado**: La contraseña de `bandit22` se guarda en `/tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv`.

---

## **4. ¿Por qué esto nos da la contraseña?**
- **El cronjob se ejecuta como `bandit22`**:
  - El usuario `bandit22` **sí tiene permiso** para leer `/etc/bandit_pass/bandit22`.
  - El script guarda la contraseña en un archivo en `/tmp` con permisos `644` (todos pueden leerlo).
  
- **Como `bandit21`**:
  - Tú no puedes leer directamente `/etc/bandit_pass/bandit22`.
  - **Pero sí puedes leer el archivo en `/tmp`**, porque tiene permisos públicos (`644`).

---

## **5. Comando final para obtener la contraseña**
Simplemente lee el archivo temporal:
```bash
cat /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
```
Verás algo como:
```
tRae0UfB9v0UzbCdn9cY0gQnds9GF58Q
```


---

## **Resumen visual del proceso:**
```
Cronjob (ejecutado por bandit22 cada minuto)
  │
  └─→ Ejecuta script: /usr/bin/cronjob_bandit22.sh
          │
          ├─→ Cambia permisos del archivo /tmp/... a 644
          │
          └─→ Guarda contraseña de bandit22 en /tmp/...
                   │
                   └─→ Tú (bandit21) lees /tmp/... → ¡Contraseña obtenida!
```

### **Estructura de `* * * * *` en cron**
Cron usa **5 campos** para definir cuándo se ejecuta un comando. Cada campo representa una unidad de tiempo, separados por espacios:

```
┌─────────── minuto (0 - 59)
│ ┌───────── hora (0 - 23)
│ │ ┌─────── día del mes (1 - 31)
│ │ │ ┌───── mes (1 - 12)
│ │ │ │ ┌─── día de la semana (0 - 6, 0 = domingo, 7 = domingo)
│ │ │ │ │
* * * * *
```

---

### **Significado de cada campo**

| Campo         | Rango       | Ejemplo de valor | Explicación                          |
|---------------|-------------|------------------|--------------------------------------|
| **Minuto**    | 0-59        | `5`, `30`        | Minuto en que se ejecuta.            |
| **Hora**      | 0-23        | `0` (medianoche) | Hora del día en formato 24h.         |
| **Día del mes**| 1-31       | `15`             | Día específico del mes.              |
| **Mes**       | 1-12        | `12` (diciembre) | Mes del año.                         |
| **Día de la semana** | 0-7   | `0` o `7` (domingo) | Día de la semana (0 y 7 = domingo). |

---

### **Cómo funcionan los asteriscos (`*`)**
- **`*`** significa **"cada"** en ese campo. Por ejemplo:
  - `*` en **minuto** → cada minuto.
  - `*` en **hora** → cada hora.

#### Ejemplo 1: `* * * * *`
- **Significado**: Todos los campos son `*`, por lo que se ejecuta **cada minuto, todos los días, todos los meses**.
  ```
  Ejecución: Cada minuto, sin excepción.
  ```

#### Ejemplo 2: `0 3 * * *`
- **Significado**:
  - Minuto: `0` (en punto).
  - Hora: `3` (3 AM).
  - Día, mes, día semana: `*` (todos los días/meses).
  ```
  Ejecución: Todos los días a las 3:00 AM.
  ```

#### Ejemplo 3: `*/5 * * * *`
- **Significado**:
  - Minuto: `*/5` (cada 5 minutos).
  - Hora: `*` (todas las horas).
  ```
  Ejecución: Cada 5 minutos (ej. 12:00, 12:05, 12:10...).
  ```

---

### **Caracteres especiales en cron**
Además de `*`, cron permite otros caracteres para mayor flexibilidad:

#### 1. **`*/n`** (Intervalos):
   - **Ejemplo**: `*/15 * * * *` → Ejecutar cada 15 minutos.

#### 2. **`,`** (Listas):
   - **Ejemplo**: `0 8,12,18 * * *` → Ejecutar a las 8 AM, 12 PM y 6 PM.

#### 3. **`-`** (Rangos):
   - **Ejemplo**: `0 9-17 * * 1-5` → Ejecutar cada hora de 9 AM a 5 PM, de lunes a viernes.

---

### **Casos prácticos comunes**

| Cronjob               | Explicación                                                                 |
|-----------------------|-----------------------------------------------------------------------------|
| `0 * * * *`           | Cada hora en punto (minuto 0).                                             |
| `30 4 * * 1`          | Ejecutar los lunes (`1`) a las 4:30 AM.                                    |
| `0 0 1 */3 *`         | Ejecutar el primer día de cada trimestre (cada 3 meses) a medianoche.      |
| `0 8-18/2 * * *`      | Ejecutar cada 2 horas entre las 8 AM y 6 PM (8, 10, 12, 14, 16, 18).       |

---

### **¿Por qué `* * * * *` ejecuta cada minuto?**
- Porque **todos los campos están en "cualquier momento"**:
  - **Minuto**: Cualquier minuto.
  - **Hora**: Cualquier hora.
  - **Día del mes**: Cualquier día.
  - **Mes**: Cualquier mes.
  - **Día de la semana**: Cualquier día.

---

### **¿Cómo probar cronjobs?**
Si quieres experimentar, puedes crear un cronjob temporal:
```bash
# Abre el crontab del usuario actual:
crontab -e

# Añade una línea como esta para pruebas:
* * * * * echo "Hola, son las $(date)" >> /tmp/mi_log.txt
```
- Esto escribirá un mensaje en `/tmp/mi_log.txt` cada minuto. ⚠️ **Recuerda borrar el cronjob después**.

---

### **Errores comunes**
1. **Confundir día del mes y día de la semana**:
   - `0 0 1 * 1` ≠ "El primer día del mes y los lunes". Es **ambos**:
     - Día del mes: `1`.
     - Día de la semana: `1` (lunes).

2. **No reiniciar cron**:
   - Si editas cronjobs en `/etc/cron.d/`, no necesitas reiniciar el servicio. Los cambios son automáticos.

---


---

## 🔑 Contraseña para Nivel 22

```
tRae0UfB9v0UzbCdn9cY0gQnds9GF58Q
```

---

## 🚀 Conectarse al Siguiente Nivel

```bash
ssh bandit22@bandit.labs.overthewire.org -p 2220
```

---

<div align="center">

**[⬅️ Nivel Anterior](./Bandit_Nivel_20___Nivel_22.md)** | **[🏠 Volver al README](./README.md)** | **[➡️ Siguiente Nivel](./Bandit_Nivel_22___Nivel_23.md)**

</div>
