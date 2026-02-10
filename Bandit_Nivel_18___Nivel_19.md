# 🔐 Bandit Level 18 → 19

<div align="center">

![Nivel](https://img.shields.io/badge/Nivel-18_→_19-blue?style=for-the-badge)
![Dificultad](https://img.shields.io/badge/Dificultad-Fácil-yellowgreen?style=for-the-badge)

**Objetivo:** Bypass de .bashrc con SSH

[🌐 Desafío Original](https://overthewire.org/wargames/bandit/bandit19.html) | [📺 Video Tutorial](#)

</div>

---


### 🎯 **Objetivo del nivel:**

La contraseña para el siguiente nivel está guardada en un archivo llamado `readme`, ubicado en el **directorio home**.

**Pero hay un problema**:  
Alguien ha modificado el archivo `.bashrc` para que **te desconecte automáticamente** justo cuando te conectas por SSH.

---

### 🛠️ **Comandos que podrías necesitar:**

- `ssh`: Para conectarte al servidor remoto.
    
- `ls`: Para listar archivos.
    
- `cat`: Para leer el contenido del archivo.
    

## Problema
Cuando intentas conectarte al nivel 18 con SSH, la conexión se cierra inmediatamente. Esto ocurre porque el servidor está configurado para desconectar automáticamente al iniciar sesión.

## Solución
Para obtener la contraseña del siguiente nivel (bandit19), necesitas leer el archivo `readme` en el directorio home de bandit18 sin iniciar una sesión interactiva.

### Método 1: Ejecutar comando directamente via SSH
```bash
ssh bandit18@bandit.labs.overthewire.org -p 2220 "cat readme"
```

### Método 2: Usar una shell no interactiva
```bash
ssh bandit18@bandit.labs.overthewire.org -p 2220 -t "bash --noprofile --norc"
```
Luego ejecutas manualmente:
```bash
cat readme
```

## Contraseña obtenida
La contraseña para bandit19 es:
```
cGWpMaKXVwDUNgPAVJbWYuGHVn9zl3j8
```

## Explicación
- El archivo `readme` contiene la contraseña para el siguiente nivel
- Al ejecutar un comando directamente con SSH, se evita la desconexión automática
- La opción `-t "bash --noprofile --norc"` evita que se carguen configuraciones que podrían causar la desconexión



---

## 🔑 Contraseña para Nivel 19

```
cGWpMaKXVwDUNgPAVJbWYuGHVn9zl3j8
```

---

## 🚀 Conectarse al Siguiente Nivel

```bash
ssh bandit19@bandit.labs.overthewire.org -p 2220
```

---

<div align="center">

**[⬅️ Nivel Anterior](./Bandit_Nivel_17___Nivel_19.md)** | **[🏠 Volver al README](./README.md)** | **[➡️ Siguiente Nivel](./Bandit_Nivel_19___Nivel_20.md)**

</div>
