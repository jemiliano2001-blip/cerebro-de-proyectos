# 🔥 Configuración de Firebase para Cerebro de Proyectos IA

## ✅ Estado Actual
- ✅ Proyecto Firebase creado: `cerebro-proyecto-smv`
- ✅ Configuración integrada en la aplicación
- ⏳ **PENDIENTE:** Configurar reglas de Firestore

## 🚨 IMPORTANTE: Configurar Reglas de Firestore

### Paso 1: Ir a Firebase Console
1. Ve a [Firebase Console](https://console.firebase.google.com/)
2. Selecciona tu proyecto: **cerebro-proyecto-smv**

### Paso 2: Configurar Firestore Database
1. En el menú lateral, haz clic en **"Firestore Database"**
2. Si no has creado la base de datos:
   - Haz clic en **"Crear base de datos"**
   - Selecciona **"Comenzar en modo de prueba"**
   - Ubicación: **us-central1** (o la más cercana)

### Paso 3: Configurar Reglas de Seguridad
1. Ve a la pestaña **"Reglas"**
2. Reemplaza el contenido con estas reglas:

```javascript
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    // Permitir acceso a la colección de proyectos
    match /artifacts/{appId}/public/data/projects/{document=**} {
      allow read, write: if true;
    }
    
    // Permitir acceso a configuraciones
    match /artifacts/{appId}/public/settings/{document=**} {
      allow read, write: if true;
    }
    
    // Permitir acceso a datos de equipo
    match /artifacts/{appId}/public/team/{document=**} {
      allow read, write: if true;
    }
  }
}
```

3. Haz clic en **"Publicar"**

### Paso 4: Verificar Funcionamiento
- La aplicación debería conectarse automáticamente
- Podrás agregar, editar y eliminar proyectos
- Los datos se guardarán en tiempo real

## 🎯 Estructura de Datos

La aplicación creará automáticamente estas colecciones:
- `artifacts/default-workshop-bot/public/data/projects/` - Proyectos
- `artifacts/default-workshop-bot/public/settings/` - Configuraciones  
- `artifacts/default-workshop-bot/public/team/` - Miembros del equipo

## ⚠️ Seguridad
Estas reglas son para desarrollo/pruebas. Para producción, implementa autenticación de usuarios.

## 🚀 Una vez configurado
1. Tu app en Vercel se conectará automáticamente
2. Todos los datos se sincronizarán en tiempo real
3. Múltiples usuarios pueden usar la app simultáneamente
