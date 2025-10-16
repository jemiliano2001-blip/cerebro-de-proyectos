# 🔥 Configuración de Firebase para Cerebro de Proyectos IA

## ✅ Estado Actual
- ✅ Proyecto Firebase creado: `cerebro-proyecto-smv`
- ✅ Configuración integrada en la aplicación
- ⏳ **PENDIENTE:** Configurar reglas de Firestore

## 🚨 IMPORTANTE: Configurar Firebase Authentication y Reglas de Firestore

### Paso 1: Configurar Firebase Authentication
1. Ve a [Firebase Console](https://console.firebase.google.com/)
2. Selecciona tu proyecto: **cerebro-proyecto-smv**
3. En el menú lateral, haz clic en **"Authentication"**
4. Ve a la pestaña **"Sign-in method"**
5. Habilita **"Email/Password"**:
   - Haz clic en **"Email/Password"**
   - Activa el primer toggle (Email/Password)
   - Haz clic en **"Save"**

### Paso 2: Crear Usuarios Autorizados
1. En Authentication, ve a la pestaña **"Users"**
2. Haz clic en **"Add user"**
3. Ingresa el email y contraseña para cada miembro del equipo (2-5 personas)
4. Haz clic en **"Add user"** para cada uno
5. Repite este proceso para todos los miembros autorizados

### Paso 3: Configurar Firestore Database
1. En el menú lateral, haz clic en **"Firestore Database"**
2. Si no has creado la base de datos:
   - Haz clic en **"Crear base de datos"**
   - Selecciona **"Comenzar en modo de prueba"**
   - Ubicación: **us-central1** (o la más cercana)

### Paso 4: Configurar Reglas de Seguridad (CRÍTICO)
1. Ve a la pestaña **"Reglas"** en Firestore
2. Reemplaza el contenido con estas reglas SEGURAS:

```javascript
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    // Solo usuarios autenticados pueden acceder
    match /artifacts/{appId}/public/data/projects/{document=**} {
      allow read, write: if request.auth != null;
    }
    
    // Solo usuarios autenticados pueden acceder a configuraciones
    match /artifacts/{appId}/public/settings/{document=**} {
      allow read, write: if request.auth != null;
    }
    
    // Solo usuarios autenticados pueden acceder a datos de equipo
    match /artifacts/{appId}/public/team/{document=**} {
      allow read, write: if request.auth != null;
    }
  }
}
```

3. Haz clic en **"Publicar"**

⚠️ **IMPORTANTE**: Estas reglas bloquean el acceso a usuarios no autenticados.

### Paso 4: Verificar Funcionamiento
- La aplicación debería conectarse automáticamente
- Podrás agregar, editar y eliminar proyectos
- Los datos se guardarán en tiempo real

## 🎯 Estructura de Datos

La aplicación creará automáticamente estas colecciones:
- `artifacts/default-workshop-bot/public/data/projects/` - Proyectos
- `artifacts/default-workshop-bot/public/settings/` - Configuraciones  
- `artifacts/default-workshop-bot/public/team/` - Miembros del equipo

## 👥 Gestión de Usuarios

### Agregar Nuevos Usuarios
1. Ve a Firebase Console → Authentication → Users
2. Haz clic en **"Add user"**
3. Ingresa el email y contraseña del nuevo miembro
4. Haz clic en **"Add user"**
5. Comparte las credenciales de forma segura con el nuevo miembro

### Cambiar Contraseñas
1. En Authentication → Users, encuentra al usuario
2. Haz clic en los tres puntos (⋯) junto al usuario
3. Selecciona **"Reset password"**
4. El usuario recibirá un email para establecer nueva contraseña

### Eliminar Usuarios
1. En Authentication → Users, encuentra al usuario
2. Haz clic en los tres puntos (⋯) junto al usuario
3. Selecciona **"Delete user"**
4. Confirma la eliminación

### Lista de Usuarios Autorizados
Mantén un registro de todos los usuarios con acceso:
- Email del usuario
- Fecha de creación de la cuenta
- Último acceso
- Rol o departamento

## ⚠️ Seguridad
- ✅ Solo usuarios autenticados pueden acceder
- ✅ Credenciales se manejan de forma segura por Firebase
- ✅ Sesiones se mantienen activas automáticamente
- ✅ Protección contra ataques de fuerza bruta

## 🚀 Una vez configurado
1. Tu app en Vercel se conectará automáticamente
2. Solo usuarios autorizados podrán acceder
3. Todos los datos se sincronizarán en tiempo real
4. Múltiples usuarios pueden usar la app simultáneamente
5. Las sesiones se mantienen entre recargas de página
