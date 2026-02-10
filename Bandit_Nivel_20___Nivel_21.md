# 🔐 Bandit Level 20 → 21

<div align="center">

![Nivel](https://img.shields.io/badge/Nivel-20_→_21-blue?style=for-the-badge)
![Dificultad](https://img.shields.io/badge/Dificultad-Difícil-red?style=for-the-badge)

**Objetivo:** Cliente-servidor con netcat

[🌐 Desafío Original](https://overthewire.org/wargames/bandit/bandit21.html) | [📺 Video Tutorial](#)

</div>

---


#### **Objetivo del Nivel**  
En el directorio home hay un binario con `setuid` que hace lo siguiente:  
1. **Establece una conexión** a `localhost` en un puerto que tú especifiques como argumento.  
2. **Lee una línea de texto** desde esa conexión y la compara con la contraseña del nivel anterior (`bandit20`).  
3. **Si la contraseña es correcta**, envía la contraseña del siguiente nivel (`bandit21`).  

**NOTA:** Prueba conectarte a tu propio servicio en red para verificar que funciona como crees.  

---

### **Comandos que podrías necesitar**  
```bash
ssh, nc (netcat), cat, bash, screen, tmux, control de trabajos en Unix (bg, fg, jobs, &, CTRL-Z, ...)
```

---

### **Explicación Detallada**  

#### **1. ¿Qué hace el binario?**  
El binario (probablemente llamado `suconnect`) actúa como un **cliente** que:  
- Se conecta a un puerto específico en `localhost` (127.0.0.1).  
- Espera recibir la contraseña de `bandit20` a través de esa conexión.  
- Si la contraseña es correcta, devuelve la de `bandit21`.  

#### **2. ¿Cómo resolverlo?**  
Debes crear un **servidor temporal** en tu propia sesión que:  
1. **Escuche en un puerto** (ej: 1234) usando `nc` (netcat).  
2. **Envíe la contraseña de bandit20** cuando el binario se conecte.  

---

### **Pasos para Resolverlo**  

#### **Paso 1: Conéctate a Bandit20**  
```bash
ssh bandit20@bandit.labs.overthewire.org -p 2220
```  
(Contraseña: la obtenida en Bandit19).  

#### **Paso 2: Verifica el binario**  
```bash
ls -l
```  
Verás un archivo como `suconnect` (o similar). Ejecútalo sin argumentos para ver su uso:  
```bash
./suconnect
```  
Salida esperada:  
```  
Usage: ./suconnect <portnumber>  
This program will connect to the given port on localhost using TCP.  
```  

#### **Paso 3: Prepara un servidor con netcat**  
Abre **dos terminales** (o usa `tmux`/`screen` para multitarea):  

- **Terminal 1 (Servidor)**:  
  ```bash
  echo "0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO" | nc -lvp 1234
  ```  
  - `-l`: Modo escucha.  
  - `-v`: Verbose (para ver la conexión).  
  - `-p 1234`: Puerto arbitrario (puedes usar otro).  

- **Terminal 2 (Cliente)**:  
  ```bash
  ./suconnect 1234
  ```  

#### **Paso 4: Resultado**  
Si hiciste todo correctamente:  
1. El binario se conectará a tu servidor `nc`.  
2. `nc` enviará la contraseña de `bandit20`.  
3. El binario verificará la contraseña y devolverá la de `bandit21`.  

Ejemplo de salida en **Terminal 1**:  
```  
Read: GbKksEFF4yrVs6il55v6gwY5aVje5f0j  
Password matches, sending next password  
```  

Y en **Terminal 2**:  
```  
gE269g2h3mw3pwgrj0Ha9Uoqen1c9DGr  
```  

---

### **¿Por qué funciona?**  
- El binario `suconnect` actúa como un **cliente verificador**.  
- Tú creas un **servidor temporal** (`nc`) que le envía la contraseña correcta.  
- Al validarla, te devuelve el premio: la contraseña de `bandit21`.  

---

### **Contraseña Obtenida**   21
La cadena mostrada por `suconnect` 
```  
EeoULMCra2q0dSkYj561DX7s1CpBuOBt
```  

---

### **Conceptos Clave**  
- **setuid**: El binario se ejecuta con permisos de `bandit21`, pero solo hace una tarea específica.  
- **Netcat (`nc`)**: Herramienta para crear conexiones TCP/UDP rápidas.  
- **Trabajos en segundo plano**: Útil si usas una sola terminal (usa `CTRL+Z`, `bg`, `jobs`).  



---

## 🔑 Contraseña para Nivel 21

```
EeoULMCra2q0dSkYj561DX7s1CpBuOBt
```

---

## 🚀 Conectarse al Siguiente Nivel

```bash
ssh bandit21@bandit.labs.overthewire.org -p 2220
```

---

<div align="center">

**[⬅️ Nivel Anterior](./Bandit_Nivel_19___Nivel_21.md)** | **[🏠 Volver al README](./README.md)** | **[➡️ Siguiente Nivel](./Bandit_Nivel_21___Nivel_22.md)**

</div>
