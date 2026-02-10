# 🔐 Bandit Level 15 → 16

<div align="center">

![Nivel](https://img.shields.io/badge/Nivel-15_→_16-blue?style=for-the-badge)
![Dificultad](https://img.shields.io/badge/Dificultad-Medio-orange?style=for-the-badge)

**Objetivo:** Conexión SSL/TLS al puerto 30001

[🌐 Desafío Original](https://overthewire.org/wargames/bandit/bandit16.html) | [📺 Video Tutorial](#)

</div>

---

En el **nivel 15 a 16** del juego Bandit (OverTheWire), el objetivo es conectarse a un servidor SSL/TLS en el puerto **30001** y enviar la contraseña del nivel actual para obtener la del siguiente nivel.

---

### **Instrucciones traducidas y explicadas**

1. La contraseña para el próximo nivel está almacenada en un servidor que solo acepta conexiones **SSL/TLS** en el puerto **30001**.
    
2. Debes conectarte a ese servidor y enviar la contraseña del nivel actual.
    
3. El servidor responderá con la contraseña del nivel 16.
    

---

### **Comandos explicados paso a paso**

#### 1️⃣ Conéctate al servidor usando `openssl s_client`

Ejecuta el siguiente comando desde el usuario `bandit15`:

```bash
echo "<contraseña_actual>" | openssl s_client -connect localhost:30001 -ign_eof
```

📌 **Explicación:**

- `echo "<contraseña_actual>"`: Escribe la contraseña del nivel 15.
    
- `|`: Pasa la contraseña como entrada estándar al siguiente comando.
    
- `openssl s_client -connect localhost:30001`: Conéctate al servidor en `localhost` por el puerto `30001` usando SSL/TLS.
    
- `-ign_eof`: Evita que la conexión se cierre prematuramente, permitiendo recibir la respuesta completa.
    

#### 2️⃣ Obtén la contraseña del nivel 16

El servidor responderá con la contraseña del próximo nivel. **Cópiala y úsala** para acceder al nivel 16 con:

```bash
ssh bandit16@bandit.labs.overthewire.org -p 2220
```


---



---

## 🔑 Contraseña para Nivel 16

```
kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx
```

---

## 🚀 Conectarse al Siguiente Nivel

```bash
ssh bandit16@bandit.labs.overthewire.org -p 2220
```

---

<div align="center">

**[⬅️ Nivel Anterior](./Bandit_Nivel_14___Nivel_16.md)** | **[🏠 Volver al README](./README.md)** | **[➡️ Siguiente Nivel](./Bandit_Nivel_16___Nivel_17.md)**

</div>
