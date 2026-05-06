# MiAgenda PWA 📱

Gestor personal de recordatorios, compras, pagos y cumpleaños.
App web progresiva (PWA) — instálala en tu teléfono y funciona sin internet.

## Archivos incluidos

```
miagenda/
├── index.html       ← App principal
├── manifest.json    ← Configuración PWA
├── sw.js            ← Service Worker (offline + notificaciones)
└── icons/
    ├── icon-192.png
    └── icon-512.png
```

## Cómo instalar en tu teléfono

### Opción 1 — Servidor local (recomendado para probar)
Necesitas servir los archivos desde un servidor HTTPS o localhost.

**Con Python (en tu PC/Mac):**
```bash
cd miagenda
python3 -m http.server 8080
```
Luego abre en el teléfono: `http://TU_IP:8080`

**Con Node.js:**
```bash
npx serve miagenda
```

### Opción 2 — Hosting gratuito (para usar permanentemente)

#### GitHub Pages (gratis y fácil):
1. Crea una cuenta en github.com
2. Crea un repositorio nuevo (ej: `miagenda`)
3. Sube todos los archivos
4. Ve a Settings → Pages → Deploy from main branch
5. Tu app estará en: `https://tuusuario.github.io/miagenda`

#### Netlify (aún más fácil):
1. Ve a netlify.com → Log in
2. Arrastra la carpeta `miagenda` al dashboard
3. Listo — te da una URL HTTPS automáticamente

### Instalar en el teléfono desde el navegador

**Android (Chrome):**
- Abre la URL de tu app
- Aparecerá un banner "Agregar a pantalla de inicio"
- O: menú ⋮ → "Instalar app" / "Agregar a pantalla de inicio"

**iPhone (Safari):**
- Abre la URL en Safari (no Chrome)
- Toca el botón compartir ↑
- Selecciona "Añadir a pantalla de inicio"
- Ponle un nombre y toca "Añadir"

## Funcionalidades

- ✅ Recordatorios con prioridad y fecha
- ✅ Lista de compras con checkboxes
- ✅ Pagos recurrentes con cálculo automático
- ✅ Cumpleaños con cuenta regresiva
- ✅ Notificaciones del navegador
- ✅ Modo oscuro
- ✅ Funciona sin internet (offline)
- ✅ Exportar/importar datos
- ✅ Badges con alertas en las pestañas
- ✅ Instalable en Android e iPhone

## Notas

- Los datos se guardan localmente en tu dispositivo (localStorage)
- Las notificaciones funcionan cuando la app está abierta o instalada
- Para sincronizar entre dispositivos, usa Exportar/Importar
