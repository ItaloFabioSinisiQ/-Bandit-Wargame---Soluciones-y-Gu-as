# 🔐 Bandit Level 27 → 28

<div align="center">

![Nivel](https://img.shields.io/badge/Nivel-27_→_28-blue?style=for-the-badge)
![Dificultad](https://img.shields.io/badge/Dificultad-Fácil-yellowgreen?style=for-the-badge)

**Objetivo:** Clonar repositorio Git básico

[🌐 Desafío Original](https://overthewire.org/wargames/bandit/bandit28.html) | [📺 Video Tutorial](#)

</div>

---

**Objetivo del Nivel**  
Hay un repositorio git en `ssh://bandit27-git@localhost/home/bandit27-git/repo` a través del puerto 2220. La contraseña para el usuario `bandit27-git` es la misma que para el usuario `bandit27`.  

Clona el repositorio y encuentra la contraseña para el siguiente nivel. 


### **Solución paso a paso (réplica exacta de lo que hiciste):**

1. **Conectarte al servidor como `bandit27`:**  
   ```sh
   ssh bandit27@bandit.labs.overthewire.org -p 2220
   ```
   - Password: `3ba3118a22e93127a4ed485be72ef5ea` (la del nivel 26 → 27).

2. **Crear un directorio temporal en `/tmp`:**  
   ```sh
   mkdir /tmp/bandit27_certa
   cd /tmp/bandit27_certa
   ```

4. **Corregir el comando con el puerto `2220`:**  
   ```sh
   git clone ssh://bandit27-git@localhost:2220/home/bandit27-git/repo
   ```
   - Aquí ingresaste la misma password de `bandit27` (`3ba3118a22e93127a4ed485be72ef5ea`).

5. **Entrar al repositorio clonado y leer el README:**  
   ```sh
   cd repo
   cat README
   ```
   - **Output:**  
     ```
     The password to the next level is: Yz9IpL0sBcCeuG7m9uQFt8ZNpS4HZRcN
     ```

6. **Salir y conectarte al nivel 28:**  
   ```sh
   exit
   ssh bandit28@bandit.labs.overthewire.org -p 2220
   ```
   - Password: `Yz9IpL0sBcCeuG7m9uQFt8ZNpS4HZRcN`

---

### **Comandos clave :**
```sh
ssh bandit27@bandit.labs.overthewire.org -p 2220
mkdir /tmp/bandit27_certa && cd /tmp/bandit27_certa
git clone ssh://bandit27-git@localhost:2220/home/bandit27-git/repo
cd repo
cat README  # ¡Contraseña encontrada!
```




---

## 🔑 Contraseña para Nivel 28

```
Yz9IpL0sBcCeuG7m9uQFt8ZNpS4HZRcN
```

---

## 🚀 Conectarse al Siguiente Nivel

```bash
ssh bandit28@bandit.labs.overthewire.org -p 2220
```

---

<div align="center">

**[⬅️ Nivel Anterior](./Bandit_Nivel_26___Nivel_26.md)** | **[🏠 Volver al README](./README.md)** | **[➡️ Siguiente Nivel](./Bandit_Nivel_28___Nivel_29.md)**

</div>
