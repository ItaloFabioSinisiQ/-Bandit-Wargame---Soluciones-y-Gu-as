# 🔐 Bandit Level 14 → 15

<div align="center">

![Nivel](https://img.shields.io/badge/Nivel-14_→_15-blue?style=for-the-badge)
![Dificultad](https://img.shields.io/badge/Dificultad-Medio-orange?style=for-the-badge)

**Objetivo:** Enviar contraseña a puerto 30000

[🌐 Desafío Original](https://overthewire.org/wargames/bandit/bandit15.html) | [📺 Video Tutorial](#)

</div>

---

### **Pasos para resolver Bandit 14 → 15**

#### **Objetivo:**

La contraseña del siguiente nivel se obtiene enviando la contraseña actual al puerto **30000** en `localhost`.

---

### **1️⃣ Verificar la contraseña de `bandit14`**

Ejecuta el siguiente comando para obtener la contraseña de `bandit14`:

```bash
cat /etc/bandit_pass/bandit14
```

**📌 Nota:**

- Guarda esta contraseña, la necesitarás en el siguiente paso.
    

---

### **2️⃣ Comprobar si el puerto 30000 está abierto**

Ejecuta:

```bash
nmap -p 30000 localhost
```

Si el puerto está **abierto**, el resultado será similar a:

```
PORT      STATE SERVICE
30000/tcp open  ndmps
```

Si aparece **"closed"**, espera unos segundos e inténtalo de nuevo.

---

### **3️⃣ Enviar la contraseña usando `nc` (netcat)**

Ejecuta:

```bash
echo "<TU_CONTRASEÑA_AQUÍ>" | nc localhost 30000
```

**Ejemplo:** Si la contraseña de `bandit14` fuera `abc123`, el comando sería:

```bash
echo "abc123" | nc localhost 30000
```

Si el comando es exitoso, te devolverá la contraseña de `bandit15`. 📌 **¡Cópiala!**

---

### **4️⃣ Si `nc` no funciona, probar `telnet`**

Si `nc` no responde, prueba con `telnet`:

```bash
telnet localhost 30000
```

Cuando se conecte, **pega la contraseña** de `bandit14` y presiona **Enter**.

---

### **5️⃣ Si `telnet` tampoco funciona, probar con `openssl`**

Algunos servidores requieren SSL/TLS. Usa:

```bash
echo "<TU_CONTRASEÑA_AQUÍ>" | openssl s_client -connect localhost:30000 -quiet
```

---

### **6️⃣ Iniciar sesión en `bandit15`**

Una vez obtenida la contraseña de `bandit15`, inicia sesión con:

```bash
ssh bandit15@bandit.labs.overthewire.org -p 2220
```

Cuando te la pida, **pega la contraseña obtenida** en el paso anterior.

---

✅ **¡Listo!** Ahora estás en el nivel **15**. 🚀
---

<div align="center">

**[⬅️ Nivel Anterior](./Bandit_Nivel_13___Nivel_13.md)** | **[🏠 Volver al README](./README.md)** | **[➡️ Siguiente Nivel](./Bandit_Nivel_15___Nivel_16.md)**

</div>
