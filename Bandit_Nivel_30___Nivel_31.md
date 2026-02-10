# 🔐 Bandit Level 30 → 31

<div align="center">

![Nivel](https://img.shields.io/badge/Nivel-30_→_31-blue?style=for-the-badge)
![Dificultad](https://img.shields.io/badge/Dificultad-Medio-orange?style=for-the-badge)

**Objetivo:** Explorar tags Git

[🌐 Desafío Original](https://overthewire.org/wargames/bandit/bandit31.html) | [📺 Video Tutorial](#)

</div>

---


## Objetivo del Nivel
Hay un repositorio git en `ssh://bandit30-git@localhost/home/bandit30-git/repo` a través del puerto 2220. La contraseña para el usuario `bandit30-git` es la misma que para el usuario `bandit30`.

Clona el repositorio y encuentra la contraseña para el siguiente nivel.

## Comandos que podrías necesitar para resolver este nivel
git

## Explicación
En este nivel, necesitas:
1. Clonar el repositorio Git usando SSH (puerto 2220)
2. Inspeccionar el repositorio para encontrar la contraseña del siguiente nivel (bandit31)
3. El repositorio puede contener información en ramas, tags, commits o historial que no es visible directamente.

Paso a paso  para encontrar la contraseña del nivel 31:

1. **Conexión al servidor:**
   ```bash
   ssh bandit30@bandit.labs.overthewire.org -p 2220
   ```
   - Introdujiste la contraseña de bandit30 cuando se te solicitó.

2. **Preparación del entorno:**
   ```bash
   mkdir /tmp/bandit30_31
   cd /tmp/bandit30_31
   ```
   - Creaste un directorio temporal para trabajar.

3. **Clonación del repositorio Git:**
   ```bash
   git clone ssh://bandit30-git@localhost:2220/home/bandit30-git/repo
   ```
   - Introdujiste la misma contraseña de bandit30 cuando se te pidió.

4. **Exploración del repositorio:**
   ```bash
   cd repo
   ls
   ```
   - Solo viste un archivo `README.md` con contenido falso: "just an epmty file... muahaha"

5. **Revisión del historial de commits:**
   ```bash
   git log
   ```
   - Solo mostró un commit inicial sin información útil.

6. **Verificación de ramas:**
   ```bash
   git branch -a
   ```
   - Solo había la rama master, nada interesante.

7. **Descubrimiento crucial - Verificación de tags:**
   ```bash
   git tag
   ```
   - Encontraste un tag llamado "secret".

8. **Inspección del tag:**
   ```bash
   git show secret
   ```
   - Esto reveló la contraseña: `fb5S2xb7bRyFmAvQYQGEqsbhVyJqhnDy`
### Versión semi-automatizada alternativa:
```bash
cd $(mktemp -d)
ssh-keyscan -p 2220 localhost >> ~/.ssh/known_hosts 2>/dev/null
git clone ssh://bandit30-git@localhost:2220/home/bandit30-git/repo
cd repo && git show secret
```

### ¿Por qué falla el método automático?
1. Git/SSH no siempre acepta la entrada estándar para confirmaciones de seguridad
2. La verificación del fingerprint es un mecanismo de seguridad importante
3. El sistema está configurado para pedir confirmación interactiva

### Consejo:
Cuando necesites máxima eficiencia en estos ejercicios, es mejor:
1. Aceptar manualmente el fingerprint (solo una vez)
2. Luego usar directamente: `git show secret` en el repositorio clonado.

---

## 🔑 Contraseña para Nivel 31

```
fb5S2xb7bRyFmAvQYQGEqsbhVyJqhnDy
```

---

## 🚀 Conectarse al Siguiente Nivel

```bash
ssh bandit31@bandit.labs.overthewire.org -p 2220
```

---

<div align="center">

**[⬅️ Nivel Anterior](./Bandit_Nivel_29___Nivel_29.md)** | **[🏠 Volver al README](./README.md)** | **[➡️ Siguiente Nivel](./Bandit_Nivel_31___Nivel_32.md)**

</div>
