# 🔐 Bandit Level 19 → 20

<div align="center">

![Nivel](https://img.shields.io/badge/Nivel-19_→_20-blue?style=for-the-badge)
![Dificultad](https://img.shields.io/badge/Dificultad-Medio-orange?style=for-the-badge)

**Objetivo:** Usar binario setuid

[🌐 Desafío Original](https://overthewire.org/wargames/bandit/bandit20.html) | [📺 Video Tutorial](#)

</div>

---

19
### **Objetivo del Nivel**  
Para avanzar al siguiente nivel, debes usar el **binario con setuid** ubicado en el directorio personal. Ejecútalo sin argumentos para descubrir cómo usarlo. La contraseña de este nivel se encuentra en el lugar habitual (`/etc/bandit_pass`), pero **solo después** de haber usado el binario con setuid.  

### **Concepto Clave: ¿Qué es setuid?**  
Un binario con **setuid** (Set User ID) es un archivo ejecutable que, cuando se ejecuta, lo hace con los permisos de su **propietario** (en este caso, bandit20), no con los permisos del usuario que lo ejecuta (bandit19). Esto permite realizar acciones privilegiadas temporalmente.  

### **Material de Referencia Útil**  
🔗 [setuid en Wikipedia](https://en.wikipedia.org/wiki/Setuid)  

---

### **Pasos para Resolver el Nivel**  
1. **Conéctate al servidor**:  
   ```bash
   ssh bandit19@bandit.labs.overthewire.org -p 2220
   ```
   Contraseña: La obtenida en el nivel anterior.

2. **Localiza el binario**:  
   ```bash
   ls -l
   ```
   Verás un archivo llamado `bandit20-do`.

3. **Ejecútalo sin argumentos**:  
   ```bash
   ./bandit20-do
   ```
   Mostrará instrucciones de uso, algo como:  
   ```
   Run a command as another user. Example: ./bandit20-do id
   ```

4. **Úsalo para leer la contraseña de bandit20**:  
   ```bash
   ./bandit20-do cat /etc/bandit_pass/bandit20
   ```
   Esto mostrará la contraseña, ya que el binario tiene permisos de bandit20.

---

### **¿Por qué funciona?**  
El truco está en que `bandit20-do` es un binario con **setuid activado**, lo que significa que aunque lo ejecutes como bandit19, el sistema lo tratará como si bandit20 lo hubiera ejecutado. Por eso puede acceder al archivo `/etc/bandit_pass/bandit20`, que solo bandit20 tiene permiso para leer.  

### **Contraseña Obtenida**  
Al ejecutar el comando anterior, obtendrás una cadena de texto como:  
```
0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO
```  
¡Úsala para acceder al nivel 20!  


---

## 🔑 Contraseña para Nivel 20

```
0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO
```

---

## 🚀 Conectarse al Siguiente Nivel

```bash
ssh bandit20@bandit.labs.overthewire.org -p 2220
```

---

<div align="center">

**[⬅️ Nivel Anterior](./Bandit_Nivel_18___Nivel_20.md)** | **[🏠 Volver al README](./README.md)** | **[➡️ Siguiente Nivel](./Bandit_Nivel_20___Nivel_21.md)**

</div>
