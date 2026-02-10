# 🔐 Bandit Level 25 → 26

<div align="center">

![Nivel](https://img.shields.io/badge/Nivel-25_→_26-blue?style=for-the-badge)
![Dificultad](https://img.shields.io/badge/Dificultad-Difícil-red?style=for-the-badge)

**Objetivo:** Escape de shell restringido con vi

[🌐 Desafío Original](https://overthewire.org/wargames/bandit/bandit26.html) | [📺 Video Tutorial](#)

</div>

---

# Análisis y solución paso a paso para el nivel Bandit25 → Bandit26

## Paso 1: Verificar información del usuario actual
```bash
id
```
Salida:
```
uid=11025(bandit25) gid=11025(bandit25) groups=11025(bandit25)
```
Esto confirma que estamos operando como el usuario bandit25.

## Paso 2: Listar archivos disponibles
```bash
ls -l
```
Salida:
```
total 4
-r--- 1 bandit25 bandit25 1679 Apr 23 18:04 bandit26.sshkey
```
Encontramos una clave SSH privada para acceder a bandit26.

## Paso 3: Investigar la configuración del usuario bandit26
```bash
cat /etc/passwd | grep bandit26
```
Salida:
```
bandit26:x:11026:11026:bandit level 26:/home/bandit26:/usr/bin/showtext
```
Observamos que el shell para bandit26 no es el habitual `/bin/bash` sino `/usr/bin/showtext`.

## Paso 4: Examinar el script showtext
```bash
cat /usr/bin/showtext
```
Salida:
```
#!/bin/sh

export TERM=linux

exec more ~/text.txt
```
Este script:
1. Establece la variable TERM como "linux"
2. Ejecuta el comando `more` sobre el archivo `~/text.txt`

# Extracción de información del comando SSH

## Comando SSH ejecutado:
```bash
ssh -oHostKeyAlgorithms=+ssh-dss -i bandit26.sshkey bandit26@localhost -p 2220
```

## Explicación de los parámetros:

1. `-oHostKeyAlgorithms=+ssh-dss`  
   - **Propósito**: Especifica los algoritmos de clave de host permitidos
   - **Detalle**: Agrega el algoritmo `ssh-dss` (DSA) a los permitidos para la conexión
   - **Contexto**: Se usa cuando el servidor solo soporta algoritmos antiguos

2. `-i bandit26.sshkey`  
   - **Propósito**: Especifica el archivo de clave privada para autenticación
   - **Detalle**: Usa la clave privada `bandit26.sshkey` en lugar de la clave por defecto

3. `bandit26@localhost`  
   - **Propósito**: Especifica usuario y host de conexión
   - **Detalle**: 
     - Usuario: `bandit26`
     - Host: `localhost` (máquina local)

4. `-p 2220`  
   - **Propósito**: Especifica el puerto de conexión
   - **Detalle**: Se conecta al puerto 2220 en lugar del puerto SSH estándar (22)


4. **Dentro de vi**:
```vim
:set shell=/bin/bash  # Configura el shell a usar
:sh                # Inicia una shell interactiva
```

## Explicación técnica:
- El truco funciona porque `more` tiene capacidad de lanzar un editor (vi) cuando necesita paginar
- Al reducir el tamaño de la terminal, forzamos a `more` a entrar en modo paginación
- Una vez en vi, tenemos capacidad de ejecutar comandos con los privilegios de bandit26
- Esto nos permite escapar del entorno restringido y obtener una shell funcional

## Nota importante:
Si no reduces el tamaño de tu terminal antes de conectarte, el comando `more` mostrará todo el contenido de una vez y cerrará la conexión inmediatamente, sin darte oportunidad de interactuar.

s0773xxkk0MXfdqOfPRVr9L3jJBUOgCZ

---

## 🔑 Contraseña para Nivel 26

```
s0773xxkk0MXfdqOfPRVr9L3jJBUOgCZ
```

---

## 🚀 Conectarse al Siguiente Nivel

```bash
ssh bandit26@bandit.labs.overthewire.org -p 2220
```

---

<div align="center">

**[⬅️ Nivel Anterior](./Bandit_Nivel_24___Nivel_24.md)** | **[🏠 Volver al README](./README.md)** | **[➡️ Siguiente Nivel](./Bandit_Nivel_26___Nivel_27.md)**

</div>
