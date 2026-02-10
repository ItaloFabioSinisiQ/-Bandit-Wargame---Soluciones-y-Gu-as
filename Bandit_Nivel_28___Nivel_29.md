# 🔐 Bandit Level 28 → 29

<div align="center">

![Nivel](https://img.shields.io/badge/Nivel-28_→_29-blue?style=for-the-badge)
![Dificultad](https://img.shields.io/badge/Dificultad-Medio-orange?style=for-the-badge)

**Objetivo:** Explorar historial de commits Git

[🌐 Desafío Original](https://overthewire.org/wargames/bandit/bandit29.html) | [📺 Video Tutorial](#)

</div>

---

**Objetivo del Nivel**

Hay un repositorio git en ssh://bandit28-git@localhost/home/bandit28-git/repo a través del puerto 2220. La contraseña para el usuario bandit28-git es la misma que para el usuario bandit28.

Clona el repositorio y encuentra la contraseña para el siguiente nivel.

Comandos que podrías necesitar para resolver este nivel

git


1. **Conexión SSH**: Te conectaste al servidor como bandit28 usando:
   ```bash
   ssh bandit28@bandit.labs.overthewire.org -p 2220
   ```

2. **Creación de directorio temporal**: Como no podías crear directorios en tu home, usaste `/tmp`:
   ```bash
   cd /tmp
   mkdir bandit28_28
   cd bandit28_28
   ```

3. **Clonar el repositorio Git**: Clonaste el repositorio específico para bandit28:
   ```bash
   git clone ssh://bandit28-git@localhost:2220/home/bandit28-git/repo
   ```

4. **Explorar el repositorio**: Al revisar el README.md inicial, la contraseña estaba oculta:
   ```bash
   cat README.md
   ```

5. **Revisar el historial de Git**: Usaste `git log` para ver commits anteriores y encontraste uno sospechoso (`fb0df13`):
   ```bash
   git log
   ```

6. **Checkout al commit anterior**: Cambiaste al commit donde la contraseña estaba visible:
   ```bash
   git checkout fb0df1358b1ff146f581651a84bae622353a71c0
   ```

7. **Leer el README.md antiguo**: Al revisar el archivo nuevamente, encontraste la contraseña:
   ```bash
   cat README.md
   ```

La contraseña para el nivel 29 es:  
**4pT1t5DENaYuqnqvadYs1oE4QLCdjmJ7**  

En este caso, no es completamente al tanteo, sino que hay pistas en los mensajes de los commits que te ayudan a identificar cuál revisar. Aquí te explico cómo analizar el historial de Git para encontrar la contraseña sin depender de la suerte:

---

### **Pasos para identificar el commit correcto:**
1. **Ejecutar `git log` y analizar los mensajes:**
   ```bash
   git log
   ```
   - Salida:
     ```
     commit 674690a... "fix info leak"       ← Este commit probablemente OCULTÓ la contraseña.
     commit fb0df13... "add missing data"    ← Este commit probablemente AGREGÓ la contraseña.
     commit a5fdc97... "initial commit"      ← Este es el primer commit (poco relevante).
     ```

2. **Pistas clave en los mensajes:**
   - `fix info leak`: Sugiere que hubo una fuga de información (como una contraseña) y se corrigió.
   - `add missing data`: Implica que se agregó información faltante (posiblemente la contraseña).

3. **Estrategia recomendada:**
   - **El commit `fb0df13` ("add missing data") es el sospechoso principal**, ya que es donde se agregó algo que luego se consideró una "fuga" (y se "arregló" en el commit siguiente).

4. **Verificar el commit sospechoso:**
   ```bash
   git checkout fb0df1358b1ff146f581651a84bae622353a71c0
   cat README.md
   ```
   - Aquí encontrarás la contraseña en texto plano, ya que fue el commit donde se agregó antes de ser eliminada en `fix info leak`.

---

### **¿Por qué no es al tanteo?**
- Los mensajes de commit son descriptivos y siguen un flujo lógico:
  1. **Primer commit (`a5fdc97`)**: Solo crea el `README.md` (sin datos útiles).
  2. **Segundo commit (`fb0df13`)**: Agrega datos faltantes (la contraseña).
  3. **Tercer commit (`674690a`)**: Corrige la "fuga" (elimina la contraseña).

- **Conclusión**: Siempre revisa commits con mensajes como:
  - `add credentials`, `fix password leak`, `remove sensitive data`, etc.

---

### **Comando alternativo (para ver cambios sin hacer checkout):**
Si no quieres cambiar de commit, puedes usar `git show` para inspeccionar cambios:
```bash
git show fb0df1358b1ff146f581651a84bae622353a71c0
```
Esto mostrará las diferencias introducidas en ese commit (incluyendo la contraseña añadida).

---

### **Resumen:**
- **No es al tanteo**, sino de **leer los mensajes de commit** para entender el flujo de cambios.
- **Enfócate en commits que mencionen:** `add`, `leak`, `fix`, `credentials`, etc.
- **El password suele estar en el commit anterior al que "arregla" una fuga**.

---

## 🔑 Contraseña para Nivel 29

```
4pT1t5DENaYuqnqvadYs1oE4QLCdjmJ7
```

---

## 🚀 Conectarse al Siguiente Nivel

```bash
ssh bandit29@bandit.labs.overthewire.org -p 2220
```

---

<div align="center">

**[⬅️ Nivel Anterior](./Bandit_Nivel_27___Nivel_27.md)** | **[🏠 Volver al README](./README.md)** | **[➡️ Siguiente Nivel](./Bandit_Nivel_29___Nivel_30.md)**

</div>
