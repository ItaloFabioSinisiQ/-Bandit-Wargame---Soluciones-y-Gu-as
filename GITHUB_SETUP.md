# 🚀 Guía Rápida: Subir tu Repositorio Bandit a GitHub

## 📋 Prerequisitos

- ✅ Tener Git instalado
- ✅ Tener una cuenta de GitHub
- ✅ Todos los archivos descargados en una carpeta

---

## 🎯 Opción 1: Desde GitHub Web (Más Fácil)

### Paso 1: Crear Repositorio en GitHub

1. Ve a [GitHub.com](https://github.com)
2. Click en el botón **"+"** (arriba derecha) → **"New repository"**
3. Configura tu repositorio:
   ```
   Repository name: bandit-wargame-solutions
   Description: Soluciones completas y profesionales del wargame Bandit de OverTheWire
   Public/Private: Public (recomendado para portafolio)
   ✅ Add a README file: NO (ya tienes uno)
   ✅ Add .gitignore: NO (ya tienes uno)
   ✅ Choose a license: NO (ya tienes uno)
   ```
4. Click en **"Create repository"**

### Paso 2: Subir Archivos desde la Web

1. En tu nuevo repositorio, click en **"uploading an existing file"**
2. Arrastra TODOS tus archivos `.md` a la zona de upload
3. También sube: `LICENSE`, `.gitignore`, `INSTALL.md`, `CONTRIBUTING.md`
4. Escribe un mensaje de commit: `Initial commit: Documentación completa Bandit niveles 0-34`
5. Click en **"Commit changes"**

### Paso 3: Personalizar

1. Edita el `README.md` desde GitHub
2. Reemplaza los enlaces de YouTube con tus videos
3. Añade tu información de contacto
4. Commit los cambios

---

## 💻 Opción 2: Desde la Terminal (Más Profesional)

### Paso 1: Crear Repositorio en GitHub

Igual que la Opción 1, paso 1.

### Paso 2: Preparar tu Carpeta Local

```bash
# Navega a la carpeta donde están tus archivos
cd ruta/a/tu/carpeta/bandit

# Verifica que todos los archivos estén ahí
ls *.md
# Deberías ver: README.md, Bandit_0.md, Bandit_Nivel_0___Nivel_1.md, etc.
```

### Paso 3: Inicializar Git

```bash
# Inicializar repositorio Git
git init

# Añadir todos los archivos
git add .

# Hacer el primer commit
git commit -m "Initial commit: Documentación completa Bandit niveles 0-34"
```

### Paso 4: Conectar con GitHub

```bash
# Añadir el repositorio remoto (reemplaza TU-USUARIO con tu usuario de GitHub)
git remote add origin https://github.com/TU-USUARIO/bandit-wargame-solutions.git

# Renombrar la rama a main (si es necesario)
git branch -M main

# Subir los archivos
git push -u origin main
```

### Paso 5: Verificar

1. Ve a `https://github.com/TU-USUARIO/bandit-wargame-solutions`
2. Deberías ver todos tus archivos
3. El README.md se mostrará automáticamente

---

## 🔧 Personalización Post-Upload

### Actualizar Enlaces de YouTube

```bash
# Edita el README.md
nano README.md
# o
code README.md

# Busca todos los '#' en los enlaces de video
# Reemplázalos con tus URLs reales de YouTube

# Guarda y commitea los cambios
git add README.md
git commit -m "Update: Añadir enlaces de videos de YouTube"
git push
```

### Añadir tu Información Personal

Actualiza estas secciones en el README:

```markdown
## 📧 Contacto

- 📺 YouTube: [Tu Canal](https://www.youtube.com/c/TU-CANAL)
- 💼 LinkedIn: [Tu Nombre](https://www.linkedin.com/in/TU-PERFIL)
- 🐦 Twitter: [@TuUsuario](https://twitter.com/TU-USUARIO)
- 📧 Email: tu.email@ejemplo.com
```

---

## 🎨 Opcionales: Hacer tu Repo Aún Mejor

### 1. Añadir una Imagen de Portada

1. Crea una carpeta `images` en tu repo
2. Añade una imagen banner (1200x400px recomendado)
3. En el README.md, añade al principio:
   ```markdown
   ![Banner](./images/banner.png)
   ```

### 2. Activar GitHub Pages

1. Ve a Settings → Pages
2. Source: Deploy from a branch
3. Branch: main, folder: / (root)
4. Save
5. Tu sitio estará en: `https://TU-USUARIO.github.io/bandit-wargame-solutions`

### 3. Añadir Más Badges

En el README.md, añade:
```markdown
![GitHub stars](https://img.shields.io/github/stars/TU-USUARIO/bandit-wargame-solutions?style=social)
![GitHub forks](https://img.shields.io/github/forks/TU-USUARIO/bandit-wargame-solutions?style=social)
![GitHub watchers](https://img.shields.io/github/watchers/TU-USUARIO/bandit-wargame-solutions?style=social)
![Last Commit](https://img.shields.io/github/last-commit/TU-USUARIO/bandit-wargame-solutions)
```

### 4. Crear un CHANGELOG.md

```markdown
# Changelog

## [1.0.0] - 2026-02-09

### Añadido
- Documentación completa de todos los niveles (0-34)
- Guías paso a paso con ejemplos
- Videos de YouTube integrados
- Secciones de soluciones rápidas
- Navegación entre niveles

### Documentado
- Comandos de Linux
- Conceptos de Git
- Técnicas de seguridad
- Buenas prácticas
```

---

## 🐛 Solución de Problemas

### Error: "Permission denied (publickey)"

```bash
# Genera una nueva SSH key
ssh-keygen -t ed25519 -C "tu-email@example.com"

# Añade la key a GitHub
# 1. Copia la key pública
cat ~/.ssh/id_ed25519.pub

# 2. Ve a GitHub → Settings → SSH and GPG keys → New SSH key
# 3. Pega la key y guarda

# 4. Usa SSH URL en lugar de HTTPS
git remote set-url origin git@github.com:TU-USUARIO/bandit-wargame-solutions.git
```

### Error: "Repository not found"

```bash
# Verifica que el nombre del repo es correcto
git remote -v

# Si está mal, actualízalo
git remote set-url origin https://github.com/TU-USUARIO/NOMBRE-CORRECTO.git
```

### Error: "Failed to push some refs"

```bash
# Pull primero (si hay cambios remotos)
git pull origin main --rebase

# Luego push
git push origin main
```

---

## 📝 Comandos Git Útiles para el Futuro

```bash
# Ver estado de cambios
git status

# Ver diferencias
git diff

# Añadir archivo específico
git add archivo.md

# Añadir todos los archivos
git add .

# Commit con mensaje
git commit -m "Mensaje descriptivo"

# Push al remoto
git push

# Pull cambios remotos
git pull

# Ver historial
git log --oneline

# Crear nueva rama
git checkout -b nombre-rama

# Cambiar de rama
git checkout main

# Merge rama a main
git merge nombre-rama
```

---

## 🎊 ¡Felicitaciones!

Tu repositorio Bandit ahora está en GitHub y listo para:

- ✅ Mostrar en tu portafolio
- ✅ Compartir con reclutadores
- ✅ Ayudar a otros estudiantes
- ✅ Recibir contribuciones de la comunidad

---

## 🔗 Próximos Pasos

1. **Comparte tu repo:**
   - LinkedIn (con hashtags: #cybersecurity #linux #hacking)
   - Twitter/X
   - Reddit (r/cybersecurity, r/netsec)
   - Discord de programación

2. **Crea tu playlist de YouTube:**
   - Graba un video por cada nivel
   - Crea una playlist "Bandit Wargame Completo"
   - Actualiza los enlaces en el README

3. **Mantén el repo actualizado:**
   - Añade nuevos niveles si salen
   - Responde a Issues
   - Acepta Pull Requests

---

<div align="center">

**¡Tu repositorio profesional de Bandit está listo! 🚀**

[⬅️ Volver a la Guía de Instalación](./INSTALL.md)

</div>
