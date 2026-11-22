# Agenda de eventos en San Luis Potosí

Página web sencilla con la agenda semanal de eventos de la ciudad, publicada gratis con **GitHub Pages**.

## ¿Qué hay en esta carpeta?

| Archivo | Para qué sirve |
|---|---|
| `index.html` | La página pública que ve la gente (agenda por día y hora, con filtros). |
| `eventos.json` | **Los datos.** Es el único archivo que cambia cada semana. |
| `admin.html` | Tu editor: agregas, editas o borras eventos, pegas tu lista de texto y publicas. |
| `README.md` | Estas instrucciones. |

La página lee `eventos.json` cada vez que alguien la abre y **se vuelve a revisar sola cada 60 segundos**. Por eso nunca tienes que tocar `index.html`: solo actualizas los datos.

---

## 1. Crear tu cuenta y tu repositorio (una sola vez)

1. Entra a <https://github.com> y haz clic en **Sign up** para crear tu cuenta (confirma tu correo).
2. Arriba a la derecha, haz clic en **+** › **New repository**.
3. En **Repository name** escribe un nombre corto, por ejemplo `agenda-eventos-slp`.
4. Elige **Public** (GitHub Pages gratis necesita que sea público).
5. Haz clic en **Create repository**.

## 2. Subir los archivos

1. Dentro del repositorio, haz clic en **Add file** › **Upload files**
   (si el repositorio está vacío, usa el enlace **uploading an existing file**).
2. Arrastra `index.html`, `eventos.json`, `admin.html` y `README.md`.
   *(Opcional: puedes no subir `admin.html` y usarlo solo desde tu computadora; ver “Seguridad”.)*
3. Abajo, en el cuadro del mensaje, escribe algo como “Primera versión” y haz clic en **Commit changes**.

## 3. Activar GitHub Pages

1. En el repositorio, haz clic en **Settings** (pestaña de arriba).
2. En la barra izquierda, sección *Code, planning, and automation*, haz clic en **Pages**.
3. En **Build and deployment** › **Source**, elige **Deploy from a branch**.
4. En **Branch** elige **main** y la carpeta **/ (root)**. Haz clic en **Save**.
5. Espera 1 o 2 minutos y recarga esa misma pantalla: aparecerá el aviso *“Your site is live at…”*.

Tu página quedará en:

```
https://USUARIO.github.io/REPO/
```

Por ejemplo, si tu usuario es `maria-slp` y el repositorio `agenda-eventos-slp`:
`https://maria-slp.github.io/agenda-eventos-slp/`
El editor quedaría en `https://maria-slp.github.io/agenda-eventos-slp/admin.html`.

## 4. Crear tu “llave” (token) para publicar desde el editor (una sola vez)

El botón **Publicar en GitHub** del editor necesita un token: una llave que solo puede modificar **ese** repositorio.

1. Arriba a la derecha en GitHub, haz clic en tu foto › **Settings**.
2. En la barra izquierda, hasta abajo, haz clic en **Developer settings**.
3. En **Personal access tokens**, haz clic en **Fine-grained tokens** › **Generate new token**.
4. **Token name**: por ejemplo `Editor agenda SLP`.
5. **Expiration**: elige una fecha (por ejemplo 90 días). Cuando venza, solo creas otro.
6. **Repository access**: elige **Only select repositories** y selecciona **solo** tu repositorio de la agenda.
7. **Permissions** › **Repository permissions** (en algunas versiones, botón **Add permissions**): busca **Contents** y ponlo en **Read and write**. No actives nada más.
8. Haz clic en **Generate token** y **copia el token** (empieza con `github_pat_`). GitHub solo lo muestra una vez.

## 5. Uso semanal del editor

1. Abre `admin.html` (en tu página: `https://USUARIO.github.io/REPO/admin.html`, o el archivo en tu computadora).
2. La primera vez, abre **Ajustes de GitHub** y llena: usuario, repositorio, rama (`main`), archivo (`eventos.json`) y pega tu token. Haz clic en **Guardar ajustes**.
   Se guardan solo en ese navegador; no tendrás que volver a escribirlos en ese dispositivo.
3. Agrega los eventos de la semana de cualquiera de estas formas:
   - **Pegar texto**: pega tu lista con el formato de siempre, haz clic en **Ver vista previa**, revisa la tabla y luego **Agregar a la lista**. Los eventos repetidos (misma fecha y título) se omiten solos.
   - **Formulario**: para agregar o corregir un evento a mano. Usa **Editar** o **Borrar** en la lista de la izquierda.
4. Si quieres, usa **Quitar eventos pasados** para limpiar lo que ya terminó.
5. Haz clic en **Publicar en GitHub**. Verás “¡Publicado!”.
6. En **1 a 2 minutos** el cambio aparece en la página pública. Quien ya la tenga abierta lo verá sin recargar, porque se revisa sola cada 60 segundos.

**Plan B sin token:** usa **Descargar eventos.json** y súbelo en GitHub con **Add file › Upload files** (reemplaza el anterior) y **Commit changes**.

### Formato del texto que puedes pegar

```
**Lunes 23 de noviembre 2026**
- Título - Lugar - Precio - Horario - [info](https://enlace)

**Jueves 26**
- Otro evento - Otro lugar - Gratis - 20:00 - [info](https://enlace)
```

- Si un encabezado no trae mes o año (`**Jueves 26**`), usa los del encabezado anterior.
- “Gratis” o “Entrada libre” en el precio marcan el evento como gratuito.
- La primera hora que aparezca (`19:00`) se usa como hora del evento; el texto completo del horario se guarda como nota.
- “del 23 al 29 nov” o “del 28 nov al 5 dic” se guardan como evento de varios días.
- Los renglones “Nada en la app.” se ignoran.
- La categoría (música, teatro, festival, bazar, otro) se adivina por el título; puedes corregirla con **Editar**.

## 6. Ponerla en Google Sites

**Opción A (más fácil):** en Google Sites, menú derecho **Insertar** › **Insertar** (Embed) › pestaña **Por URL**, pega `https://USUARIO.github.io/REPO/` y elige *Página completa*. Agranda el recuadro hasta que se vea bien.

**Opción B (código):** **Insertar** › **Insertar** › pestaña **Insertar código** y pega:

```html
<iframe src="https://USUARIO.github.io/REPO/"
        style="width:100%; height:1200px; border:0;"
        title="Eventos en San Luis Potosí" loading="lazy"></iframe>
```

La página se ajusta al ancho del recuadro y se actualiza sola dentro de Google Sites. Si la agenda es larga, se desplaza dentro del recuadro.

## 7. Seguridad

- `admin.html` es público si lo subes, pero **no sirve de nada sin tu token**: no contiene ninguna contraseña.
- El token **nunca** se sube al repositorio; solo vive en el navegador donde lo escribiste. Si desmarcas “Recordar el token en este dispositivo”, se olvida al cerrar la pestaña.
- No guardes el token en computadoras compartidas. Usa **Borrar token** cuando termines en una computadora ajena.
- Si crees que alguien vio tu token: GitHub › Settings › Developer settings › Fine-grained tokens › bórralo y crea otro.
- Si prefieres que nadie vea el editor, **no subas `admin.html`**: guárdalo en tu computadora y ábrelo con doble clic. Funciona igual (usa **Cargar desde GitHub** para traer la lista actual y **Publicar en GitHub** para guardar).

## Preguntas frecuentes

- **Publiqué y no veo el cambio.** Espera 2 minutos y recarga. GitHub Pages tarda un poco en publicar.
- **El editor dice que no puede leer eventos.json.** Pasa al abrirlo con doble clic desde tu computadora; usa **Cargar desde GitHub** o **Abrir archivo…**.
- **Error 401 o 403 al publicar.** El token venció o no tiene permiso *Contents: Read and write* sobre ese repositorio. Crea otro.
