# 🧠 Cerebro de Proyectos IA

Sistema inteligente de recordatorios y notificaciones para proyectos de taller CNC con funcionalidades de gestión de equipo.

## 🚀 Despliegue en Vercel

### Opción 1: Deploy directo desde GitHub

1. **Sube tu código a GitHub:**
   ```bash
   git init
   git add .
   git commit -m "Initial commit"
   git branch -M main
   git remote add origin https://github.com/tu-usuario/reminder-app.git
   git push -u origin main
   ```

2. **Deploy en Vercel:**
   - Ve a [vercel.com](https://vercel.com)
   - Conecta tu cuenta de GitHub
   - Selecciona tu repositorio
   - Vercel detectará automáticamente la configuración
   - ¡Deploy automático!

### Opción 2: Deploy directo con Vercel CLI

1. **Instala Vercel CLI:**
   ```bash
   npm i -g vercel
   ```

2. **Deploy:**
   ```bash
   cd C:\Users\emili\OneDrive\Escritorio\reminder_app
   vercel
   ```

3. **Sigue las instrucciones en pantalla**

## 📱 Características

- ✅ **PWA Completa**: Instalable como app nativa
- 🔔 **Notificaciones Multi-canal**: WhatsApp, Email, Browser
- 👥 **Gestión de Equipo**: Agregar, editar y eliminar miembros
- 🤖 **IA Integrada**: Análisis y predicciones de proyectos
- 📊 **Analytics**: Métricas y reportes detallados
- 🌐 **Offline Ready**: Funciona sin conexión

## 🛠️ Funcionalidades de Edición de Equipo

- **Agregar miembros**: Botón "Agregar Miembro" 
- **Editar miembros**: Clic en el ícono de lápiz azul ✏️
- **Eliminar miembros**: Clic en el ícono de papelera roja 🗑️
- **Modal moderno**: Interfaz intuitiva para edición

## 📂 Estructura del Proyecto

```
reminder_app/
├── reminder.html       # Aplicación principal
├── index.html         # Página de inicio (redirect)
├── manifest.json      # PWA manifest
├── sw.js             # Service Worker
├── vercel.json       # Configuración de Vercel
└── README.md         # Este archivo
```

## 🔧 Configuración Local

Para desarrollo local:

```bash
# Opción 1: Python
python -m http.server 8000

# Opción 2: Node.js
npx serve .

# Opción 3: PHP
php -S localhost:8000
```

Luego abre: `http://localhost:8000`

## 🌟 Ventajas de Vercel

- ✅ **Deploy gratuito** hasta 100GB bandwidth
- ✅ **HTTPS automático** 
- ✅ **CDN global** para velocidad máxima
- ✅ **Auto-scaling** 
- ✅ **Analytics integrados**
- ✅ **Perfecto para PWAs**

## 📱 Después del Deploy

Una vez desplegada en Vercel:

1. La app será accesible en una URL como: `https://tu-app.vercel.app`
2. Se podrá instalar como PWA en móviles y escritorio
3. Funcionará completamente offline
4. Las notificaciones browser funcionarán perfectamente
5. No más errores de Service Worker

## 🔒 Datos y Privacidad

- Toda la data se almacena en Firebase (configuración incluida)
- La app funciona 100% en el navegador
- Sin servidor backend necesario
- Datos encriptados en tránsito y reposo

---

**Desarrollado para talleres CNC profesionales** 🔧⚙️
