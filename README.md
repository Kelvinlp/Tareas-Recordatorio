# Tareas Match v5 🔥

Sistema de gestión personal de tareas con Firebase Authentication, Firestore en tiempo real y colaboración entre dispositivos.

---

## 🚀 Despliegue en GitHub Pages

### Paso 1 — Subir el repositorio

```bash
git init
git add .
git commit -m "feat: Tareas Match v5 con Firebase"
git branch -M main
git remote add origin https://github.com/TU_USUARIO/tareas-match.git
git push -u origin main
```

### Paso 2 — Activar GitHub Pages

1. Ve a tu repositorio en GitHub
2. **Settings** → **Pages**
3. En *Source* selecciona: `Deploy from a branch`
4. Branch: `main` / Folder: `/ (root)`
5. Clic en **Save**
6. Tu app estará en: `https://TU_USUARIO.github.io/tareas-match/`

---

## 🔥 Configurar Firebase para GitHub Pages

Esto es **obligatorio** — sin este paso el login fallará.

### Agregar dominio autorizado en Firebase Auth

1. Ve a [Firebase Console](https://console.firebase.google.com/)
2. Selecciona el proyecto **tareas-task**
3. **Authentication** → **Settings** → **Authorized domains**
4. Clic en **Add domain**
5. Agrega exactamente: `TU_USUARIO.github.io`
6. Clic en **Save**

### Habilitar métodos de autenticación

1. **Authentication** → **Sign-in method**
2. Habilita: ✅ **Email/Password**
3. Habilita: ✅ **Google** (agrega tu correo de soporte)
4. Habilita: ✅ **Anonymous**

### Configurar Firestore Rules

1. **Firestore Database** → **Rules**
2. Pega estas reglas:

```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {

    // Cada usuario solo accede a sus propios datos
    match /users/{uid} {
      allow read, write: if request.auth != null && request.auth.uid == uid;
    }
    match /users/{uid}/{collection=**} {
      allow read, write: if request.auth != null && request.auth.uid == uid;
    }

    // Salas de colaboración: cualquier usuario autenticado
    match /rooms/{roomId} {
      allow read, write: if request.auth != null;
    }
    match /rooms/{roomId}/{collection=**} {
      allow read, write: if request.auth != null;
    }
  }
}
```

3. Clic en **Publish**

---

## 🌐 Despliegue alternativo — Firebase Hosting

Si prefieres usar Firebase Hosting (HTTPS garantizado, dominio personalizado):

```bash
# Instalar Firebase CLI
npm install -g firebase-tools

# Login
firebase login

# Deploy
firebase deploy --only hosting
```

Tu app estará en: `https://tareas-task.web.app`

---

## 📁 Estructura del repositorio

```
tareas-match/
├── index.html          # App completa (HTML + CSS + JS + Firebase)
├── firebase.json       # Configuración Firebase Hosting
├── .firebaserc         # Proyecto Firebase vinculado
├── .nojekyll           # Evita que GitHub Pages procese con Jekyll
├── _headers            # Headers HTTP para seguridad
├── .gitignore          # Archivos ignorados por Git
└── README.md           # Este archivo
```

---

## ⚡ Características

- 🔐 **Login** con Email/Contraseña, Google y modo Invitado
- ☁️ **Firestore** — datos sincronizados en tiempo real entre dispositivos
- 📋 **Tareas** con categorías, prioridades y áreas personalizadas
- 🛒 **Lista de compras** del hogar con categorías y precios
- 🔁 **Recordatorios recurrentes** — pagos, servicios, citas
- 👥 **Colaboración** en salas compartidas vía Firestore
- 🔔 **Alertas por correo** — resumen de pendientes (mailto)
- 📊 **Analytics** — eventos registrados en Firebase Analytics

---

## 🔧 Configuración Firebase integrada

```javascript
const firebaseConfig = {
  apiKey:            "AIzaSyAyxW4KZlWVHwlkudzJZIncCau6qtAeNlo",
  authDomain:        "tareas-task.firebaseapp.com",
  projectId:         "tareas-task",
  storageBucket:     "tareas-task.firebasestorage.app",
  messagingSenderId: "850116411488",
  appId:             "1:850116411488:web:a19f550de6eb2002d30305",
  measurementId:     "G-8G7MW4FVQG"
};
```

---

## ⚠️ Solución de problemas comunes

| Error | Solución |
|-------|----------|
| `auth/unauthorized-domain` | Agrega `TU_USUARIO.github.io` en Firebase Auth → Authorized domains |
| `permission-denied` en Firestore | Verifica las Firestore Rules (ver arriba) |
| Login con Google no funciona | Habilita Google en Authentication → Sign-in method |
| La app carga en blanco | Verifica que `.nojekyll` esté en la raíz del repo |
| `CORS error` | Usa Firebase Hosting en lugar de GitHub Pages |

