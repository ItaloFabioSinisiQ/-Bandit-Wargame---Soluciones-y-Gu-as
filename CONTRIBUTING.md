# 🤝 Guía de Contribución

¡Gracias por tu interés en mejorar este repositorio! Esta guía te ayudará a contribuir de manera efectiva.

## 📋 Tabla de Contenidos

- [Código de Conducta](#código-de-conducta)
- [¿Cómo Puedo Contribuir?](#cómo-puedo-contribuir)
- [Guía de Estilo](#guía-de-estilo)
- [Proceso de Pull Request](#proceso-de-pull-request)

---

## 📜 Código de Conducta

### Nuestros Estándares

✅ **Comportamientos Aceptables:**
- Ser respetuoso con todos los colaboradores
- Aceptar críticas constructivas
- Enfocarse en lo mejor para la comunidad
- Mostrar empatía hacia otros miembros

❌ **Comportamientos Inaceptables:**
- Uso de lenguaje ofensivo o sexual
- Trolling, insultos o ataques personales
- Acoso público o privado
- Publicar información privada sin permiso

---

## 🎯 ¿Cómo Puedo Contribuir?

### 1. Reportar Errores 🐛

¿Encontraste un error? Abre un Issue con:

```markdown
**Descripción del Error:**
Descripción clara del problema

**Pasos para Reproducir:**
1. Ir a '...'
2. Ejecutar '...'
3. Ver error

**Comportamiento Esperado:**
Lo que debería pasar

**Capturas de Pantalla:**
Si aplica, añade capturas

**Entorno:**
- OS: [ej. Ubuntu 22.04]
- Nivel: [ej. Bandit 15]
```

### 2. Sugerir Mejoras 💡

¿Tienes una idea? Abre un Issue con:

```markdown
**Tipo de Mejora:**
[ ] Nueva funcionalidad
[ ] Mejora de documentación
[ ] Mejora de diseño
[ ] Otra: ___________

**Descripción:**
Explica tu sugerencia detalladamente

**Beneficio:**
¿Por qué sería útil?

**Alternativas Consideradas:**
¿Qué otras opciones evaluaste?
```

### 3. Mejorar Documentación 📝

La documentación siempre puede mejorar:

- Corregir errores ortográficos o gramaticales
- Aclarar explicaciones confusas
- Añadir ejemplos adicionales
- Mejorar el formato visual

### 4. Añadir Contenido Nuevo ✨

- Métodos alternativos de solución
- Explicaciones más detalladas
- Diagramas o imágenes ilustrativas
- Trucos y tips adicionales

---

## 🎨 Guía de Estilo

### Formato de Archivos Markdown

#### Headers
```markdown
# Título Principal (H1) - Solo uno por archivo
## Sección (H2)
### Subsección (H3)
```

#### Bloques de Código
```markdown
```bash
# Comando con comentario
comando --opcion argumento
\```
```

#### Énfasis
```markdown
**Negrita** para conceptos importantes
*Cursiva* para énfasis suave
`código` para comandos inline
```

#### Listas
```markdown
- Elemento no ordenado
- Otro elemento

1. Elemento ordenado
2. Siguiente elemento
```

### Convenciones de Nombres

- **Archivos de nivel:** `Bandit_Nivel_X___Nivel_Y.md`
- **Imágenes:** `nivel-X-descripcion.png`
- **Scripts:** `script-nivel-X.sh`

### Estructura de una Guía de Nivel

```markdown
# 🔐 Bandit Level X → Level Y

<div align="center">
[Badges y título]
</div>

---

[Contenido original del nivel]

---

## 🔑 Contraseña para Nivel Y

\```
[contraseña]
\```

---

[Navegación]
```

---

## 🔄 Proceso de Pull Request

### Antes de Empezar

1. **Verifica que no exista un PR similar**
2. **Crea un Issue primero** (para cambios grandes)
3. **Fork el repositorio**

### Pasos para tu PR

#### 1. Configura tu entorno

```bash
# Fork en GitHub, luego:
git clone https://github.com/TU-USUARIO/bandit-wargame-solutions.git
cd bandit-wargame-solutions

# Añade el upstream
git remote add upstream https://github.com/ORIGINAL/bandit-wargame-solutions.git
```

#### 2. Crea una rama

```bash
# Actualiza tu main
git checkout main
git pull upstream main

# Crea una rama descriptiva
git checkout -b mejora/nivel-15-explicacion-ssl
# o
git checkout -b fix/typo-nivel-20
```

**Convenciones de nombres de rama:**
- `mejora/descripcion` - Para mejoras
- `fix/descripcion` - Para correcciones
- `docs/descripcion` - Para documentación
- `feature/descripcion` - Para nuevas funcionalidades

#### 3. Haz tus cambios

```bash
# Edita los archivos necesarios
# Asegúrate de:
# - Mantener el formato existente
# - Probar que los comandos funcionen
# - Revisar ortografía y gramática
```

#### 4. Commit tus cambios

```bash
# Añade los archivos modificados
git add .

# Commit con mensaje descriptivo
git commit -m "Mejora: Añadir explicación detallada de SSL en nivel 15"
```

**Formato de mensajes de commit:**
```
Tipo: Descripción corta

Explicación opcional más detallada del cambio,
por qué fue necesario, y qué impacto tiene.

Fixes #numero-de-issue (si aplica)
```

**Tipos de commit:**
- `Mejora:` - Mejoras al contenido
- `Fix:` - Correcciones de errores
- `Docs:` - Cambios en documentación
- `Style:` - Cambios de formato
- `Test:` - Verificación de comandos

#### 5. Push y crea el PR

```bash
# Push a tu fork
git push origin mejora/nivel-15-explicacion-ssl

# Ve a GitHub y crea el Pull Request
```

#### 6. Describe tu PR

```markdown
## Descripción
Descripción clara de los cambios realizados

## Tipo de Cambio
- [ ] Corrección de error
- [ ] Nueva funcionalidad
- [ ] Mejora de documentación
- [ ] Cambio de estilo/formato

## ¿Cómo se ha probado?
Describe las pruebas realizadas

## Checklist
- [ ] Mi código sigue el estilo del proyecto
- [ ] He revisado mi propio código
- [ ] He comentado las partes complejas
- [ ] Mis cambios no generan nuevos warnings
- [ ] He actualizado la documentación
- [ ] Los comandos han sido probados
```

### Durante la Revisión

- **Responde a los comentarios** de manera constructiva
- **Realiza los cambios solicitados** en la misma rama
- **Sé paciente** - las revisiones pueden tomar tiempo

### Después de la Aprobación

¡Tu PR será mergeado! 🎉

- Tu contribución aparecerá en el historial
- Serás añadido como contribuidor
- Ayudarás a miles de estudiantes

---

## ✅ Checklist Antes de Enviar

Antes de crear tu PR, verifica:

- [ ] ✅ El código/contenido funciona correctamente
- [ ] ✅ Sigue la guía de estilo del proyecto
- [ ] ✅ No hay errores ortográficos
- [ ] ✅ Los enlaces funcionan
- [ ] ✅ Las imágenes se ven correctamente
- [ ] ✅ El formato Markdown es correcto
- [ ] ✅ Has probado los comandos
- [ ] ✅ Tu rama está actualizada con main
- [ ] ✅ El mensaje de commit es descriptivo

---

## 🏆 Reconocimiento a Contribuidores

Todos los contribuidores son reconocidos en:

- El archivo [CONTRIBUTORS.md](./CONTRIBUTORS.md)
- La página principal del README
- Los release notes

---

## 📧 ¿Preguntas?

Si tienes dudas sobre cómo contribuir:

- 📧 Abre un Issue con la etiqueta `question`
- 💬 Únete a nuestro Discord [Link](#)
- 📝 Revisa Issues existentes etiquetados como `good first issue`

---

## 📚 Recursos Útiles

- [Guía de Markdown](https://www.markdownguide.org/)
- [Guía de Git](https://git-scm.com/book/es/v2)
- [Cómo escribir buenos commits](https://chris.beams.io/posts/git-commit/)
- [Conventional Commits](https://www.conventionalcommits.org/)

---

<div align="center">

**¡Gracias por contribuir! 🙏**

**Juntos hacemos este proyecto mejor para todos 🚀**

[⬅️ Volver al README](./README.md)

</div>
