# 🔐 Bandit Level 22 → 23

<div align="center">

![Nivel](https://img.shields.io/badge/Nivel-22_→_23-blue?style=for-the-badge)
![Dificultad](https://img.shields.io/badge/Dificultad-Medio-orange?style=for-the-badge)

**Objetivo:** Script cron con hash MD5

[🌐 Desafío Original](https://overthewire.org/wargames/bandit/bandit23.html) | [📺 Video Tutorial](#)

</div>

---



## Objetivo del Nivel
Un programa se está ejecutando automáticamente a intervalos regulares desde cron, el programador de trabajos basado en tiempo. Busca en /etc/cron.d/ la configuración y observa qué comando se está ejecutando.

NOTA: Examinar scripts de shell escritos por otras personas es una habilidad muy útil. El script para este nivel está intencionalmente hecho para ser fácil de leer. Si tienes problemas para entender lo que hace, intenta ejecutarlo para ver la información de depuración que imprime.

## Comandos que puedes necesitar para resolver este nivel
cron, crontab, crontab(5) (usa "man 5 crontab" para acceder a esto)


**Paso a paso para resolver el nivel:**

1. **Conectar al servidor del nivel 22:**
   ```bash
   ssh bandit22@bandit.labs.overthewire.org -p 2220
   ```
   Contraseña: `tRae0UfB9v0UzbCdn9cY0gQnds9GF58Q` (obtenida del nivel anterior).

2. **Inspeccionar los trabajos cron en `/etc/cron.d/`:**
   ```bash
   cat /etc/cron.d/cronjob_bandit23
   ```
   Salida:
   ```
   @reboot bandit23 /usr/bin/cronjob_bandit23.sh  &> /dev/null
   * * * * * bandit23 /usr/bin/cronjob_bandit23.sh  &> /dev/null
   ```

3. **Examinar el script ejecutado por el cron job:**
   ```bash
   cat /usr/bin/cronjob_bandit23.sh
   ```
   Salida:
   ```bash
   #!/bin/bash
   myname=$(whoami)
   mytarget=$(echo I am user $myname | md5sum | cut -d ' ' -f 1)
   echo "Copying passwordfile /etc/bandit_pass/$myname to /tmp/$mytarget"
   cat /etc/bandit_pass/$myname > /tmp/$mytarget
   ```
Mejor explicación: 

4. **Calcular el hash MD5 del string "I am user bandit23":**
   ```bash
   echo "I am user bandit23" | md5sum | cut -d ' ' -f 1
   ```
   Salida (hash calculado):
   ```
   8ca319486bfbbc3663ea0fbe81326349
   ```

5. **Acceder al archivo en `/tmp` con el hash generado:**
   ```bash
   cat /tmp/8ca319486bfbbc3663ea0fbe81326349
   ```
   Esto mostrará la contraseña para el nivel 23.

**Contraseña obtenida:** 0Zf11ioIjMVN551jX3CmStKLYqjk54Ga


Mejor explicación: 
```bash
#!/bin/bash

myname=$(whoami)
mytarget=$(echo I am user $myname | md5sum | cut -d ' ' -f 1)

echo "Copying passwordfile /etc/bandit_pass/$myname to /tmp/$mytarget"

cat /etc/bandit_pass/$myname > /tmp/$mytarget
```

---

### 1. `#!/bin/bash`

Esto indica que el script debe ejecutarse usando **bash**. Es la primera línea estándar en scripts de bash.

---

### 2. `myname=$(whoami)`

- `whoami`: comando que imprime el nombre del usuario actual.
    
- `$(...)`: ejecuta el comando dentro de los paréntesis y captura su salida.
    

🔍 Por ejemplo, si estás logueado como `bandit23`, esta línea guarda ese nombre en la variable `myname`:

```bash
myname="bandit23"
```

---

### 3. `mytarget=$(echo I am user $myname | md5sum | cut -d ' ' -f 1)`

Este es un poco más complejo, veamos paso a paso:

#### a. `echo I am user $myname`

- Si `myname=bandit23`, esto genera la cadena:
    

```bash
I am user bandit23
```

#### b. `| md5sum`

- Pasa esa cadena por `md5sum`, que devuelve el hash MD5:
    

```bash
e.g., 8c6976e5b5410415bde908bd4dee15df  -
```

#### c. `| cut -d ' ' -f 1`

- `cut` divide la salida usando el espacio (`' '`) como delimitador y selecciona el primer campo (`-f 1`), que es el hash.
    

📦 El resultado final (por ejemplo):

```bash
mytarget="8c6976e5b5410415bde908bd4dee15df"
```

---

### 4. `echo "Copying passwordfile /etc/bandit_pass/$myname to /tmp/$mytarget"`

- Muestra un mensaje indicando qué archivo se está copiando y a dónde.
    
- Este `echo` es solo informativo.
    

Ejemplo de salida:

```bash
Copying passwordfile /etc/bandit_pass/bandit23 to /tmp/8c6976e5b5410415bde908bd4dee15df
```

---

### 5. `cat /etc/bandit_pass/$myname > /tmp/$mytarget`

- `cat` muestra el contenido del archivo `/etc/bandit_pass/bandit23`.
    
- `>` redirige esa salida a un archivo temporal con nombre igual al hash MD5 generado.
    
- Este archivo temporal estará en `/tmp/`.
    

🔐 Ese archivo contiene la **contraseña del usuario actual** (`bandit23`), copiada con nombre codificado para que no sea tan fácil de adivinar.

---

### En resumen:

Este script, que se ejecuta cada minuto por `cron`, genera un archivo en `/tmp/` con la contraseña del usuario actual. El nombre del archivo es un hash de `"I am user <usuario>"`.

---


---

## 🔑 Contraseña para Nivel 23

```
0Zf11ioIjMVN551jX3CmStKLYqjk54Ga
```

---

## 🚀 Conectarse al Siguiente Nivel

```bash
ssh bandit23@bandit.labs.overthewire.org -p 2220
```

---

<div align="center">

**[⬅️ Nivel Anterior](./Bandit_Nivel_21___Nivel_23.md)** | **[🏠 Volver al README](./README.md)** | **[➡️ Siguiente Nivel](./Bandit_Nivel_23___Nivel_24.md)**

</div>
