# La Salud Mental en la Fe — Presentación Interactiva

Una presentación profesional, dinámica e interactiva para jóvenes sobre salud mental desde una perspectiva de fe cristiana, diseñada para ser conducida por dos psicólogas.

## ¿Qué incluye?

Tres aplicaciones que trabajan juntas:

| Archivo | Quién lo usa | Para qué |
|---|---|---|
| `index.html` | Las psicólogas (proyector) | Presentación con los 11 espacios del programa |
| `joven.html` | Los jóvenes (sus celulares) | Acceso vía QR para participar en los ejercicios |
| `dashboard.html` | Las psicólogas (segundo dispositivo) | Visualización en vivo de las respuestas |

---

## 🚀 Cómo empezar (3 pasos)

### Paso 1 — Configurar la base de datos en tiempo real (Firebase)

La sincronización entre los celulares de los jóvenes y la pantalla de las psicólogas requiere Firebase (gratuito, plan Spark).

1. Ve a [https://console.firebase.google.com](https://console.firebase.google.com) e inicia sesión.
2. Haz clic en **"Crear un proyecto"**, asígnale un nombre (ej. `salud-mental-fe`), y completa los pasos (no necesitas habilitar Analytics).
3. En el menú lateral izquierdo, ve a **Build → Realtime Database**.
4. Pulsa **"Crear base de datos"**, selecciona una ubicación (la más cercana a El Salvador es `us-central1`) y elige **"Comenzar en modo de prueba"**.
5. Una vez creada, ve a **Configuración del proyecto** (ícono de engranaje arriba a la izquierda) → **Tus apps** → ícono `</>` (Web) → registra una app web.
6. Copia el objeto `firebaseConfig` que te muestra Firebase. Se verá así:

```js
const firebaseConfig = {
  apiKey: "AIzaSy...",
  authDomain: "tu-proyecto.firebaseapp.com",
  databaseURL: "https://tu-proyecto-default-rtdb.firebaseio.com",
  projectId: "tu-proyecto",
  storageBucket: "tu-proyecto.appspot.com",
  messagingSenderId: "123456789",
  appId: "1:123:web:abc123"
};
```

7. Pega ese objeto **reemplazando el `firebaseConfig`** en los tres archivos:
   - `index.html` (línea ~12)
   - `joven.html` (línea ~12)
   - `dashboard.html` (línea ~12)

### Paso 2 — Publicar en internet (Vercel — gratis y en 2 minutos)

**Por qué Vercel:** despliegue instantáneo, URL pública, HTTPS automático (necesario para que los celulares accedan al QR), gratuito sin límite para este uso.

**Opción A — desde la interfaz web (sin instalar nada):**

1. Crea una cuenta gratuita en [https://vercel.com](https://vercel.com) (puedes usar GitHub o solo email).
2. En el dashboard de Vercel, pulsa **"Add New… → Project"**.
3. Arrastra la carpeta completa de este proyecto a la zona de subida (o conecta un repo de GitHub).
4. Pulsa **"Deploy"**. En menos de un minuto tendrás una URL pública del tipo `salud-mental-fe.vercel.app`.

**Opción B — Netlify Drop (aún más simple):**

1. Ve a [https://app.netlify.com/drop](https://app.netlify.com/drop)
2. Arrastra la carpeta completa del proyecto.
3. Listo: obtienes una URL inmediata.

### Paso 3 — Usar la presentación el día del evento

1. **Antes de empezar:** Abre el `dashboard.html` en una laptop o tablet (segundo dispositivo o ventana secundaria) — las psicólogas verán las respuestas en vivo aquí.
2. **Para la presentación:** Abre `index.html` en el navegador conectado al proyector. Pulsa `F` para pantalla completa.
3. **Navegación con teclado:**
   - `→` / `Espacio` / `Page Down` — siguiente diapositiva
   - `←` / `Page Up` — diapositiva anterior
   - `Home` — primera; `End` — última
   - `ESC` — abre/cierra el índice
   - `F` — pantalla completa
4. **Los jóvenes** escanean los códigos QR que aparecen en los espacios IV y VII con la cámara de sus celulares.

> 💡 **Sobre los códigos QR:** se generan automáticamente con la URL real donde está publicada la presentación. Si necesitas cambiar la URL (por ejemplo, si abriste el archivo localmente antes de publicar), simplemente **toca la URL debajo del QR**, edítala y presiona Enter — el QR se regenerará al instante.

---

## 🎨 Personalización

- **Cambiar el video de Elías:** reemplaza `assets/elias.mp4` por el video deseado (mantén el mismo nombre).
- **Cambiar las imágenes de los slides 5, 6 y 8:** reemplaza `assets/image2.png`, `image3.png`, `image5.png`.
- **Editar contenido de texto:** abre `index.html` con cualquier editor de texto y busca el espacio correspondiente (están comentados como `<!-- ESPACIO 4 -->`).
- **Ajustar los escenarios del ejercicio (espacio 4):** edita `joven.html`, busca las secciones con `data-correcta=` y modifica los textos según necesites.

---

## 🔒 Seguridad y privacidad

- **Datos almacenados:** solo respuestas anónimas (un ID temporal por participante) y palabras de texto libre. No se recoge ningún dato personal identificable.
- **Reset de datos:** desde `dashboard.html` puedes borrar todas las respuestas con los botones inferiores. Recomendado entre sesiones diferentes.
- **Reglas de Firebase:** después del evento, considera cambiar las reglas de tu Realtime Database a modo restringido para evitar escrituras de terceros. En la consola de Firebase → Realtime Database → Reglas:

```json
{
  "rules": {
    ".read": true,
    ".write": false
  }
}
```

(O bórralo cuando termines, lo creas de nuevo cuando lo necesites.)

---

## 🛠️ Modo de prueba sin internet

Puedes abrir `index.html` localmente (doble clic) sin Firebase configurado. La presentación funciona completamente, pero los contadores de respuestas en vivo dirán `—` (porque no hay backend). Útil para ensayar el flujo antes del evento.

---

## 📋 Estructura de los 11 espacios

| # | Espacio | Contenido |
|---|---|---|
| I | Bienvenida | Título, versículo de apertura (Mateo 11:28) |
| II | Dinámica corporal | 4 cartas de emociones con gestos guiados |
| III | Testimonio bíblico | Video de Elías bajo el enebro (1 Reyes 19) |
| IV | Ejercicio dirigido | QR → 4 escenarios para identificar emoción + dashboard en vivo |
| V | ¿Qué es la ansiedad? | Imagen explicativa |
| VI | ¿Qué no es ansiedad? | Imagen comparativa |
| VII | Palabras de depresión | QR → nube de palabras en vivo |
| VIII | ¿Qué es la depresión? | Imagen con síntomas y versículo |
| IX | Primeros auxilios psicológicos | 3 técnicas explicadas |
| X | Respiración 4-7-8 | Animación guiada interactiva |
| XI | Cierre | Salmo 34:18 y mensaje final |

---

## 💝 Notas pastorales

La presentación está diseñada con sensibilidad teológica:

- Las referencias bíblicas son en **Reina Valera 1960**.
- Los versículos elegidos transmiten esperanza sin minimizar el sufrimiento (Sal 34:18, Mt 11:28, 1 P 5:7, Mt 5:4, Sal 91:1).
- El testimonio bíblico (Elías) muestra que personajes de la fe también atravesaron crisis severas — un mensaje normalizador y consolador.
- Se promueve activamente buscar ayuda profesional como un acto de fe, no opuesto a ella.

---

Diseñado con cuidado para acompañar a los jóvenes en su camino de fe y salud integral.

> *"Cerca está Jehová de los quebrantados de corazón"* — Salmo 34:18
