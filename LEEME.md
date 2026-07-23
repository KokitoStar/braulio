# Landing de prensa — Braulio Espinosa Márquez

Página autocontenida para el subdominio de prensa. Sin frameworks, sin build, sin backend.

## Cómo publicarla

Suba **todos** los archivos de esta carpeta a la raíz del hosting estático
(Netlify, Vercel, Cloudflare Pages, Hostinger, cPanel, etc.). No hay que compilar nada.

```
index.html                 ← la página
logo.png                   ← logo de campaña (también es la descarga del kit)
braulio.png                ← foto oficial en alta resolución (2048×2048) para prensa
braulio-recorte.webp/.png  ← foto sin fondo, usada en el encabezado
braulio-web.jpg            ← foto optimizada que se incrusta en el PDF generado
og-image.jpg               ← vista previa al compartir en WhatsApp/X (1200×630)
favicon.ico
favicon-512.png
apple-touch-icon.png
robots.txt
sitemap.xml
```

## Los 3 cambios pendientes

Están marcados con comentarios dentro de `index.html`.

**1. Dominio.** Hoy dice `https://prensa.braulioespinosa.com`.
Búsquelo y reemplácelo si el subdominio final es otro. Aparece en:
las etiquetas `<meta>` de Open Graph y Twitter, el `<link rel="canonical">`,
el bloque JSON-LD del final, y los archivos `robots.txt` y `sitemap.xml`.

**2. Teléfono de prensa.** Ahora es el temporal `+573212222222`.
Está en **una sola línea**, al inicio del `<script>` final:

```js
const TELEFONO_PRENSA = '+573212222222';
```

Al cambiarlo ahí se actualiza solo en la ficha técnica, la sección de contacto,
el botón de WhatsApp para agendar entrevistas y el PDF descargable.

**3. Disclaimer legal de pauta política.** En el `<footer>`, dentro del bloque
`aviso-legal`, hay dos espacios en blanco para completar: quién financia y
quién es responsable de la publicación.

## Qué incluye

- Menú fijo con indicador de sección activa y menú desplegable en celular.
- Buscador instantáneo sobre biografía, trayectoria, gestión, propuestas y preguntas.
  Ignora tildes y mayúsculas, resalta las coincidencias, permite saltar entre ellas
  con Enter, y muestra sugerencias cuando no hay resultados. Atajo: `Ctrl/Cmd + K`.
- Línea de tiempo desplegable con los cuatro periodos de su carrera.
- Kit de prensa: PDF del perfil generado en el navegador, foto y logo en alta
  resolución, biografía corta y ficha técnica copiables.
  La librería jsPDF se busca en este orden: una copia local `jspdf.umd.min.js`
  (si usted la pone junto a `index.html`), unpkg, jsDelivr y cdnjs. Si ninguna
  responde, el botón abre solo el diálogo de impresión con la página ya formateada.
  **Para que el PDF no dependa de internet de terceros**, descargue
  `jspdf.umd.min.js` desde unpkg.com/jspdf@3.0.3/dist/ y súbalo con los demás
  archivos: el código lo detecta automáticamente.
- Preguntas frecuentes, frases citables con botón de copiado, botones de compartir.
- Control de tamaño de texto (A+), navegación por teclado, foco visible,
  contraste verificado y respeto a `prefers-reduced-motion`.
- Estilos de impresión: al imprimir se abren los acordeones y se ocultan los controles.

## Nota sobre un dato

Los documentos entregados difieren en el lugar de nacimiento: el informe estratégico
dice Medellín y la hoja de vida dice que es envigadeño. La página no afirma ninguno
de los dos; habla de arraigo en Envigado, que es lo que ambos documentos sostienen.
Conviene definirlo antes de que circule entre periodistas.
