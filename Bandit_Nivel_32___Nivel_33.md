# 🔐 Bandit Level 32 → 33

<div align="center">

![Nivel](https://img.shields.io/badge/Nivel-32_→_33-blue?style=for-the-badge)
![Dificultad](https://img.shields.io/badge/Dificultad-Medio-orange?style=for-the-badge)

**Objetivo:** Escape de UPPERCASE SHELL

[🌐 Desafío Original](https://overthewire.org/wargames/bandit/bandit33.html) | [📺 Video Tutorial](#)

</div>

---

**(UPPERCASE SHELL Escape)**

Este nivel es un reto ingenioso donde te encuentras atrapado en una **"shell en mayúsculas"** que bloquea los comandos normales. Aquí está el desglose de lo que ocurrió y cómo funciona la solución:

---

## **🔍 ¿Qué está pasando?**
1. **Al conectarte con SSH**, entras a una shell especial llamada **"UPPERCASE SHELL"**.
   - Todos los comandos que escribes se **convierten a mayúsculas** (ej: `ls` → `LS`, `id` → `ID`).
   - La shell solo permite comandos en mayúsculas, pero **no existen comandos así en Linux**, por lo que todo falla:
     ```bash
     >> id
     sh: 1: ID: Permission denied
     ```
2. **El truco está en cómo escaparse** de esta shell restrictiva.

---

## **💡 Solución: Usar `$0` para obtener una shell normal**
1. **`$0` es una variable especial en Unix** que contiene el nombre del programa/shell actual.
   - Al ejecutarlo, **se reinicia la shell**, pero esta vez **sin las restricciones de mayúsculas**:
     ```bash
     >> $0
     $   # ¡Ahora estás en una shell normal!
     ```
2. **Verificamos que funciona**:
   ```bash
   $ id
   uid=11033(bandit33) gid=11032(bandit32) groups=11032(bandit32)
   ```
   - ¡Ahora podemos ejecutar comandos en minúsculas!

---

## **🔑 Obteniendo la contraseña de bandit33**
1. **El archivo con la contraseña está en**:
   ```bash
   $ cat /etc/bandit_pass/bandit33
   ```
2. **Contraseña obtenida**:
   ```
   tQdtbs5D5i2vJwkO8mEyYEyTL8izoeJ0
   ```

---

## **📌 ¿Por qué funciona `$0`?**
- En sistemas Unix, `$0` se refiere al **nombre del script o shell actual**.
- Al ejecutarlo, **se lanza una nueva instancia de la shell** (en este caso, `/bin/sh`), pero **sin las modificaciones de la UPPERCASE SHELL**.
- Es un **bypass clásico** en entornos restringidos.

---

## **🚀 Comandos clave usados**
| Comando | Explicación |
|---------|-------------|
| `ssh bandit32@... -p 2220` | Conexión al nivel. |
| `$0` | Escapa de la shell en mayúsculas. |
| `cat /etc/bandit_pass/bandit33` | Lee la contraseña del siguiente nivel. |

---

## **🔐 Contraseña del Nivel 33**
```
tQdtbs5D5i2vJwkO8mEyYEyTL8izoeJ0
```

---
### **Conclusión**
Este nivel enseña:
✅ Cómo escapar de shells restringidas usando variables como `$0`.  
✅ Que las mayúsculas/minúsculas importan en Linux.  
✅ Trucos útiles para bypassear restricciones en sistemas Unix.  



---

## 🔑 Contraseña para Nivel 33

```
tQdtbs5D5i2vJwkO8mEyYEyTL8izoeJ0
```

---

## 🚀 Conectarse al Siguiente Nivel

```bash
ssh bandit33@bandit.labs.overthewire.org -p 2220
```

---

<div align="center">

**[⬅️ Nivel Anterior](./Bandit_Nivel_31___Nivel_31.md)** | **[🏠 Volver al README](./README.md)** | **[➡️ Siguiente Nivel](./Bandit_Nivel_33___Nivel_34.md)**

</div>
