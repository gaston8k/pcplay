# Guía Paso a Paso para Subir la Web a GitHub Pages

## 📋 Requisitos Previos

1. **Cuenta de GitHub** (gratuita) - [Crear cuenta](https://github.com/join)
2. **Git instalado** en tu computadora (opcional, pero recomendado)

## 🚀 Pasos para Subir la Landing Page

### Paso 1: Crear un Repositorio en GitHub

1. Inicia sesión en [GitHub.com](https://github.com)
2. Haz clic en el botón **"+"** (arriba a la derecha) → **"New repository"**
3. Configura el repositorio:
   - **Repository name**: `pcplay-landing` (o el nombre que prefieras)
   - **Description**: "Landing page para PCPLAY.com.ar"
   - **Visibility**: Public (recomendado)
   - **NO marques** "Initialize this repository with a README"
4. Haz clic en **"Create repository"**

### Paso 2: Subir los Archivos al Repositorio

#### Opción A: Usando GitHub Desktop (Recomendado para principiantes)

1. Descarga e instala [GitHub Desktop](https://desktop.github.com/)
2. Inicia sesión con tu cuenta de GitHub
3. Clona el repositorio que creaste:
   - File → Clone repository → Selecciona tu repositorio
4. Copia todos los archivos de la carpeta actual a la carpeta del repositorio:
   - `index.html`
   - `style.css`
   - `script.js`
   - `fondo_mapa.jpg`
   - `README.md`
   - `.nojekyll`
   - `CNAME` (opcional)
5. En GitHub Desktop:
   - Verás los archivos en "Changes"
   - Escribe un mensaje de commit (ej: "Initial commit - Landing page")
   - Haz clic en **"Commit to main"**
   - Haz clic en **"Push origin"**

#### Opción B: Usando la Web de GitHub (Sin Git)

1. En la página de tu repositorio recién creado
2. Haz clic en **"uploading an existing file"**
3. Arrastra y suelta TODOS los archivos de la carpeta:
   - `index.html`
   - `style.css`
   - `script.js`
   - `fondo_mapa.jpg`
   - `README.md`
   - `.nojekyll`
   - `CNAME` (opcional)
4. Haz clic en **"Commit changes"**

#### Opción C: Usando Git por línea de comandos

```bash
# Navega a la carpeta de tu proyecto
cd "g:/IA APPS/PCPLAY web page"

# Inicializa repositorio git
git init

# Agrega todos los archivos
git add .

# Haz el primer commit
git commit -m "Initial commit - Landing page for PCPLAY"

# Conecta con el repositorio remoto (reemplaza TU_USUARIO)
git remote add origin https://github.com/TU_USUARIO/pcplay-landing.git

# Sube los archivos
git branch -M main
git push -u origin main
```

### Paso 3: Activar GitHub Pages

1. En tu repositorio de GitHub, ve a **Settings** (pestaña superior derecha)
2. En el menú lateral izquierdo, haz clic en **Pages**
3. En **Source**, selecciona:
   - Branch: `main`
   - Folder: `/ (root)`
4. Haz clic en **Save**

### Paso 4: Esperar y Verificar

1. Espera 1-2 minutos mientras GitHub despliega tu sitio
2. Refresca la página de Settings > Pages
3. Verás un mensaje: **"Your site is published at https://TU_USUARIO.github.io/pcplay-landing/"**
4. Haz clic en el enlace para ver tu landing page en vivo

## 🔗 URLs de tu Sitio

- **URL de GitHub Pages**: `https://TU_USUARIO.github.io/pcplay-landing/`
- **URL con dominio personalizado** (si configuras CNAME): `www.pcplay.com.ar`

## ⚙️ Configurar Dominio Personalizado (Opcional)

Si quieres usar `www.pcplay.com.ar`:

1. En tu proveedor de dominio (donde compraste pcplay.com.ar):
   - Agrega un registro CNAME que apunte a `TU_USUARIO.github.io`
2. En GitHub Pages Settings:
   - En la sección "Custom domain", escribe `www.pcplay.com.ar`
   - Marca "Enforce HTTPS"
3. Espera hasta 24 horas para que los cambios de DNS se propaguen

## 🔄 Actualizar la Página en el Futuro

Cada vez que hagas cambios:

1. Modifica los archivos en tu computadora
2. Súbelos al repositorio (igual que los pasos iniciales)
3. GitHub Pages se actualizará automáticamente en 1-2 minutos

## 🛠️ Solución de Problemas Comunes

### ❌ La página no se ve bien
- Verifica que todos los archivos estén subidos
- Revisa la consola del navegador (F12) para errores
- Asegúrate de que `fondo_mapa.jpg` esté en el repositorio

### ❌ No aparece el fondo
- La imagen debe estar en la misma carpeta que `index.html`
- Verifica que la ruta en `style.css` sea correcta: `url('fondo_mapa.jpg')`

### ❌ GitHub Pages no se activa
- Asegúrate de que el repositorio sea público
- Verifica que hayas seleccionado la rama `main` y carpeta `/ (root)`
- Espera unos minutos y refresca la página

## 📞 Soporte

- [Documentación oficial de GitHub Pages](https://docs.github.com/es/pages)
- Para problemas técnicos, revisa los [foros de GitHub](https://github.com/orgs/community/discussions)

---

✅ **¡Listo!** Tu landing page de PCPPLAY estará en línea y accesible para todos.