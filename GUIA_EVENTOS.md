# Sistema de eventos — Guía rápida

La presentación ahora permite **separar las respuestas de cada evento** (cada grupo de jóvenes) y **consultar los anteriores** sin que se mezclen. Todo desde una sola página de dashboard.

## Cómo funciona

Cada evento es como una "carpeta" independiente en la base de datos. El dashboard tiene una barra arriba con:

- **Selector de evento** — elige cuál ver (el activo o uno anterior).
- **● En vivo** — indica que estás viendo el evento que está recibiendo respuestas ahora.
- **Viendo histórico** — aparece cuando consultas un evento anterior.
- **Exportar CSV** — descarga los resultados del evento seleccionado (se abre en Excel).
- **+ Nuevo evento** — crea una sesión limpia y la activa (la anterior queda archivada).

## Flujo para cada nuevo grupo de jóvenes

1. Antes de empezar, abre el dashboard y pulsa **"+ Nuevo evento"**.
2. Escribe un nombre, por ejemplo: *"Jóvenes Mayo 2026"*.
3. Pulsa **"Crear y activar"**.
4. A partir de ese momento, todos los QR escriben en ese evento. Las respuestas del grupo anterior quedan guardadas y separadas.

## Para revisar un evento anterior

1. En el selector de evento, elige el que quieras consultar.
2. Verás todas sus respuestas, nube de palabras y aciertos.
3. Para volver al evento en curso, pulsa **"Volver al evento en vivo"**.

## Para analizar después

1. Selecciona el evento que quieras.
2. Pulsa **"Exportar CSV"**.
3. Se descarga un archivo que puedes abrir en Excel con: respuestas del ejercicio, resumen por escenario, y todas las palabras enviadas.

## IMPORTANTE — Reglas de Firebase

Para que el sistema de eventos funcione, las reglas de tu base de datos deben permitir leer y escribir en `eventos` y `eventoActivo`. En la consola de Firebase → Realtime Database → Reglas, usa esto durante los eventos:

```json
{
  "rules": {
    "eventoActivo": { ".read": true, ".write": true },
    "eventos": { ".read": true, ".write": true }
  }
}
```

Después de todos los eventos, para proteger los datos, puedes cambiar `.write` a `false` (se podrá seguir leyendo y exportando, pero ya nadie podrá escribir):

```json
{
  "rules": {
    "eventoActivo": { ".read": true, ".write": false },
    "eventos": { ".read": true, ".write": false }
  }
}
```

## Temas visuales

La presentación ahora tiene **tres temas** (selector arriba a la derecha, o tecla `T`):

- **Claro de día** (crema) — tema por defecto, luminoso, con esporas claras flotando. Ideal para salas con luz.
- **Bosque sereno** (verde) — con polen dorado.
- **Cielo nocturno** (azul oscuro) — el original.

La elección se recuerda automáticamente para la próxima vez.
