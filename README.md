# Álbum Mundial 26

Checklist personal del álbum Panini del Mundial 2026 — para llevar cuenta de las estampas que tengo, las que faltan y las repetidas para intercambio.

**Abrir el álbum:** https://xguilxr.github.io/album-mundial-26/

## Uso

- Click en una tarjeta → marcar como **tengo**.
- Botones `+` / `−` → ajustar repetidas (el numerito de abajo cuenta repetidas).
- Filtros: Todas · Faltantes · Tengo · Repetidas.
- Buscador por país, jugador o código.
- Botones para copiar faltantes/repetidas y descargar CSV.
- Todo se guarda en el navegador (localStorage).

## Estructura por equipo (20 estampas)

`#01` Escudo · `#02` Portero · `#03–12` jugadores 1–10 · `#13` Plantel (foil/dorada con ★) · `#14–20` jugadores 11–17.

## Instalar en el iPhone (acceso desde la pantalla de inicio)

1. Abre el link de tu álbum en **Safari** (debe ser Safari, no Chrome).
2. Toca el botón **Compartir** (cuadrito con flecha hacia arriba, abajo en el centro).
3. Baja en el menú y elige **Añadir a la pantalla de inicio**.
4. Confirma el nombre (por defecto "Álbum 26") → **Añadir**.
5. Ya queda un ícono con el trofeo en tu home, como cualquier app. Se abre a pantalla completa, sin barra de Safari.

Igual funciona en Android: en Chrome → menú `⋮` → **Instalar app** o **Añadir a pantalla principal**.

## Sincronizar entre dispositivos (opcional)

Por defecto, cada dispositivo guarda su propio progreso por separado. Si quieren tú y otra persona (o tu compu + tu celu) compartir un mismo álbum en vivo, hay que conectar Firebase. Es gratis y se hace una sola vez.

### Paso 1 · Crear proyecto en Firebase (5 min)

1. Ve a https://console.firebase.google.com → **Add project** / *Agregar proyecto*.
2. Nombre cualquiera (ej. `album-mundial-glez`). Acepta los términos. Puedes desactivar Google Analytics, no hace falta.
3. Una vez creado, en el menú izquierdo → **Build → Realtime Database** → **Create Database**.
4. Elige la región más cercana (`us-central` o similar).
5. **Start in test mode** → **Enable**.
6. Ya creada, ve a la pestaña **Rules** y reemplaza el contenido con esto:

   ```json
   {
     "rules": {
       "rooms": {
         "$room": {
           ".read": true,
           ".write": true,
           ".validate": "$room.matches(/^[a-z0-9_-]{3,40}$/)"
         }
       }
     }
   }
   ```

   Click **Publish**. (Esto evita que caduque a los 30 días del test mode).

### Paso 2 · Sacar el `firebaseConfig`

1. En Firebase Console, click el ⚙ arriba a la izq → **Project settings**.
2. Baja hasta **Your apps** → click el ícono `</>` ("web app") → ponle un nickname → **Register app**.
3. Te mostrará un bloque de código con un objeto `firebaseConfig = { ... }`. Copia **solo el objeto** (desde el `{` hasta el `}`).

### Paso 3 · Pegarlo en el álbum

1. Abre tu álbum (compu o celu) → barra "🔗 Sala" → botón **⚙ Firebase**.
2. Pega el objeto que copiaste → **OK**.
3. Listo. Ahora pon un nombre de sala (ej. `glez-2026`) → **Conectar**.
4. En el otro dispositivo: pega el **mismo** firebaseConfig y el **mismo** nombre de sala → sincroniza al instante.

> **Tip:** el nombre de la sala es lo que actúa de "candado" — usa algo que solo ustedes conozcan. Cualquiera con el mismo proyecto Firebase + el mismo nombre de sala vería/editaría las mismas estampas.

Para desconectar: botón **Desconectar** (sigue funcionando solo local). Para borrar tu config: botón **⚙ Firebase** → deja el campo vacío → OK.

## ¿Quieres el tuyo? (fork)

Cada quien tiene su propio álbum guardado en su navegador, así que para tener el tuyo:

1. Arriba a la derecha del repo → **Fork** → *Create fork* (con tu cuenta de GitHub).
2. En tu fork: **Settings → Pages → Build and deployment**.
3. Source: **Deploy from a branch** · Branch: `main` · carpeta: `/ (root)` → **Save**.
4. Espera ~1 min y abre `https://TU-USUARIO.github.io/album-mundial-26/`.

Si quieres sincronización entre tus dispositivos, sigue la sección **Sincronizar entre dispositivos** arriba con tu propio Firebase.

## Notas

Datos basados en la lista oficial del álbum Panini FIFA World Cup 26 — para uso propio.
