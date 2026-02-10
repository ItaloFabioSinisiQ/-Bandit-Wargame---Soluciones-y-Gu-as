# 🔐 Bandit Level 24 → 25

<div align="center">

![Nivel](https://img.shields.io/badge/Nivel-24_→_25-blue?style=for-the-badge)
![Dificultad](https://img.shields.io/badge/Dificultad-Difícil-red?style=for-the-badge)

**Objetivo:** Ataque de fuerza bruta con 10,000 PINs

[🌐 Desafío Original](https://overthewire.org/wargames/bandit/bandit25.html) | [📺 Video Tutorial](#)

</div>

---

Un demonio (daemon) está escuchando en el puerto 30002 y te dará la contraseña para bandit25 si le proporcionas la contraseña de bandit24 y un código PIN numérico secreto de 4 dígitos. No hay forma de obtener el PIN excepto probando todas las 10,000 combinaciones posibles, lo que se conoce como fuerza bruta.  
**No es necesario** crear nuevas conexiones cada vez.


#### **1. Accediste al servidor como `bandit24`**  
```bash
ssh bandit24@bandit.labs.overthewire.org -p 2220
```  
- Ingresaste la contraseña de `bandit24` (que obtuviste en el nivel anterior).  

---

#### **2. Creaste un directorio temporal en `/tmp`**  
Como no tienes permisos en `/home/bandit24`, usaste `/tmp`:  
```bash
cd /tmp
mkdir bandit245
cd bandit245
```  

---

#### **3. Creaste un script (`test2.sh`) para probar PINs**  
Usaste `nano` para crear un archivo como este:  
```bash
#!/bin/bash
pass24="TU_CONTRASEÑA_DE_BANDIT24"  # La reemplazaste con la correcta
for pin in {0000..9999}; do
    echo "$pass24 $pin"
done
```  
- **Objetivo**: Probar todas las combinaciones de 4 dígitos (0000–9999) para el servicio en `localhost:30002`.  

---

#### **4. Le diste permisos de ejecución al script**  
```bash
chmod +x test2.sh
```  

---

#### **5. Ejecutaste el script y filtraste la salida**  
```bash
./test2.sh | nc localhost 30002 | grep -v "Wrong"
```  
- **`nc localhost 30002`**: Envía cada combinación al servicio que verifica el PIN.  
- **`grep -v "Wrong"`**: Oculta los mensajes de error, mostrando solo la línea con `Correct!`.  

---

#### **6. ¡Encontraste la contraseña!**  
La salida mostró:  
```bash
Correct!
The password of user bandit25 is: 
```  
- **PIN correcto**: El script encontró el código secreto entre 0000 y 9999.  

---

#### **7. Te conectaste como `bandit25`**  
```bash
ssh bandit25@bandit.labs.overthewire.org -p 2220
```  
- Usaste la contraseña obtenida: `iCi86ttT4KSNe1armKiwbQNmB3YJP3q4`.  

---

### 🔍 **¿Qué hizo el script internamente?**  
1. Generó 10,000 combinaciones de `[contraseña_de_bandit24] [PIN]`.  
2. Envió cada una al puerto `30002`, donde un servicio verificaba si el PIN era correcto.  
3. Al encontrar el PIN válido, el servidor respondió con la contraseña de `bandit25`.  


---

## 🔑 Contraseña para Nivel 25

```
iCi86ttT4KSNe1armKiwbQNmB3YJP3q4
```

---

## 🚀 Conectarse al Siguiente Nivel

```bash
ssh bandit25@bandit.labs.overthewire.org -p 2220
```

---

<div align="center">

**[⬅️ Nivel Anterior](./Bandit_Nivel_23___Nivel_23.md)** | **[🏠 Volver al README](./README.md)** | **[➡️ Siguiente Nivel](./Bandit_Nivel_25___Nivel_26.md)**

</div>
