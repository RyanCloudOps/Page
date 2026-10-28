# Estado del proyecto — Portafolio de Gary Flores

_Última actualización: 2026-10-28. Léelo al empezar la próxima sesión._

## Cierre (2026-10-28)
- Todo subido a GitHub (`main` = `origin/main`). Recursos en `?v=9`. Si la web publicada se ve antigua: Ctrl+F5 o incógnito (GitHub Pages tarda 1–2 min y cachea 10 min).
- Sin tareas a medias. Posibles siguientes pasos: ajustar `EGG_SPOT` si Gary quiere la mitad derecha más cerca/lejos del dedo; revisar en un móvil real el hero y el huevo; el resto de "Pendiente / ideas" abajo.
- El clip original de Kling (`assets/hf_20261028_020311_*.mp4`, 10 MB) sigue en local pero no se sube (ignorado por git).
- Servidor local parado.

## Sesión 2026-10-27/28
- Hero nuevo: personaje 3D. Fuente: un único clip de Kling de 15 s (`assets/hf_*.mp4`, ignorado por git, 1244x1664, fondo verde plano). El verde se quita offline (`tools/hero-key.py`: recorte 816x1377 en 214,160 → 640x1080, alfa por `g - max(r,b)`, despill, contracción del borde de 1 px) y se guarda en `assets/gary-hero.mp4` como vídeo "apilado": 640x2160, color premultiplicado arriba y alfa abajo. El shader WebGL (`keyer()` en `script.js`) solo los combina. El bucle es lineal y dura 15 s (360 fotogramas, sin bumerán ni morph): el clip ya acaba con los brazos cruzados igual que empieza, solo se quita el último fotograma, que repite el primero. `assets/gary-hero.webp` es el póster transparente (fallback sin WebGL / reduced motion).
- Nubes sincronizadas con el vídeo (`BEATS` en `script.js`): 0,2–2,9 s "¡Hola! Bienvenido…", 3,1–5 s "Baja y mira lo que hago 👇" (señala abajo), 9–13,4 s "Une las 2 piezas 🥚" (señala a la derecha, dedo en la barbilla y luego se inclina y señala abajo a la derecha). Entre 5,5 y 8,9 s mira a los lados y las mitades del huevo brillan. La mitad derecha del huevo se coloca por JS (`placeSpot()`, `EGG_SPOT = [0.92, 0.72]` como fracción del escenario del personaje) justo donde señala a los 12–13,4 s; se recalcula al redimensionar.
- Huevo de Pascua: dos mitades en las esquinas superiores del hero (en móvil, a los lados del cuerpo). Se arrastran para unirlas (con teclado, Enter las une); aparece "¡Rómpelo!" y un martillo; 3 golpes lo rompen y sale el mensaje "Si puedes imaginarlo, puedes programarlo." con el botón "Programación ATS" → https://www.youtube.com/channel/UC7QoKU6bj1QbXQuNIjan82Q
- Reglas del skill `landing-page-design` (instalado en `.claude/skills/`) aplicadas: fuente Geist + Geist Mono, sin cursivas ni pesos 800, nav flotante en píldora con menú móvil a pantalla completa, curva `--ease`, fondo oscuro #000, sección de tagline que se ilumina palabra a palabra, enlace "saltar al contenido", meta og.
- Borrados `gary-talk.webp` y `gary-anim.webp` (sprites del hero anterior). También instalado el skill `scroll-world` en `.claude/skills/` (no se usó: necesita APIs de pago Monid/Higgsfield).
- Para regenerar el clip (con un venv con numpy + pillow, y opencv-python-headless para el morph):
  1. `python tools/hero-key.py assets/hf_XXX.mp4 <carpeta>` genera los PNG apilados y `poster.webp`.
  2. `ffmpeg -framerate 24 -i <carpeta>/%04d.png -frames:v 360 -vf format=yuv420p -c:v libx264 -preset slow -crf 22 -tune animation -movflags +faststart -an assets/gary-hero.mp4`, y copiar `poster.webp` a `assets/gary-hero.webp`.
  3. Subir `?v=` y reajustar `BEATS`/`PEEK`/`EGG_SPOT` a los gestos del nuevo clip.
  Si un clip no acaba en la pose inicial, `tools/hero-morph.py <carpeta> <salida> 14` (OpenCV DIS optical flow) hace un morph de vuelta en los últimos fotogramas.

## Cierre anterior (2026-10-09)
- Todo está subido a GitHub; rama `main` = `origin/main`, árbol de trabajo limpio. Último commit: "Versiona recursos para evitar caché antigua en la tarjeta ID" (`16ed481`).
- La web publicada ya sirve la versión nueva (se comprobó con `curl`: `index.html` con `?v=4`). Si Gary ve algo antiguo, es caché del navegador: Ctrl+F5 o incógnito.
- Hecho en la última sesión: hero con dos clips (hablando 24 fotogramas + brazos cruzados 12) alternados con fundido; tarjeta ID con el retrato anime (`gary-id.webp`); versionado `?v=` de recursos.
- Sin tareas a medias. Lo siguiente que probablemente quiera: más animaciones (saludando, pulgar arriba), README del perfil de GitHub y revisar la vista móvil. Ver "Pendiente / ideas" abajo.
- Servidor local parado; no hay procesos abiertos.

## Qué es
Portafolio personal (HTML + CSS + JS sin frameworks), bilingüe ES/EN, modo claro/oscuro.
- Repo: https://github.com/RyanCloudOps/Page (rama `main`)
- Web: https://ryancloudops.github.io/Page/ (GitHub Pages; tarda 1–2 min en actualizar)
- Carpeta local: `D:\Index\portfolio` (ya es un repo git con `origin` = Page; credenciales de GitHub ya guardadas, `git push` funciona)
- Autor: Gary Bryan Flores Peñafiel (usuario GitHub: RyanCloudOps), Systems Engineer en Sothis (PLM), Barcelona. Idioma de trabajo: español.

## Qué se hizo
1. Se vio un portafolio de referencia en Instagram (cuenta `sl_tech_journal`): blanco y negro, nombre gigante de fondo, personaje de cuerpo entero, tarjeta ID que gira, tabla periódica de skills, logros con scroll lateral.
2. Se reemplazó el diseño arcade "Cloud Quest" por uno minimalista inspirado en esa referencia. La versión arcade queda en `arcade-backup/` (ignorada por git; sigue en el historial de git, commit `0a5b68d`).
3. Contenido: hero, Sobre mí (tarjeta ID con flip + stats), Skills (tabla periódica con filtros, incluye Oracle en bases de datos), Experiencia (timeline) + Formación, Logros (certificaciones, scroll lateral), Proyectos + roadmap, Contacto.
4. Hero animado: nombre "GARY" gigante de fondo, titular "Systems Engineer." y el personaje anime en un `<canvas>` con DOS clips que se alternan con fundido: `assets/gary-talk.webp` (hablando, 24 fotogramas, 6x4, bucle de 4 s) mientras se muestra el bocadillo, y `assets/gary-anim.webp` (brazos cruzados, 12 fotogramas, 4x3, bucle de 2 s) entre mensajes. Bocadillos rotativos ES/EN cada 5,6 s; pausa con hover, clic avanza; con `prefers-reduced-motion` queda estático.
5. Las 12 poses reales de Gary (traje azul, fondo verde) se usaron antes en el hero y se retiraron al cambiar al personaje anime. Siguen en el historial de git (commit `fac2c63`, carpeta `assets/poses/`) y en el zip original.
6. Todo subido a GitHub.

## Archivos clave
- `index.html` — contenido en español (`data-i18n` para traducir)
- `script.js` — traducciones EN (`EN`), skills (`SK`), hero (vídeo + nubes `BEATS`), huevo de Pascua, tarjeta ID, tema, idioma, menú móvil
- `styles.css` — estilos; colores como variables en `:root`
- `assets/gary-hero.mp4` (clip del hero ya recortado: color arriba, alfa abajo; se combina en WebGL) y `assets/gary-hero.webp` (póster transparente)
- `tools/hero-key.py` y `tools/hero-morph.py` — scripts para procesar un clip nuevo de Kling (ver la sesión 2026-10-27/28)
- `.claude/skills/` — skills `landing-page-design` y `scroll-world` del proyecto
- `assets/gary-id.webp` — retrato anime de la tarjeta ID · `assets/gary.webp` — foto real de traje (botón "Ver foto real")
- `cv-gary-flores.pdf` — CV descargable
- Originales (fuera del repo, en `C:\Users\pflor\Documents\Codex\2026-10-07\en-e\outputs\`): `animacion-brazos-cruzados.zip` y las 2 hojas de "hablando" (en el chat, no hay zip) y `poses-fondo-verde.zip` (poses reales de traje azul)

## Pendiente / ideas
- [x] Tarjeta ID de "Sobre mí": ya usa el retrato anime (`gary-id.webp`); el SVG vectorial se eliminó.
- [ ] Faltan más animaciones del personaje anime (saludando, pulgar arriba) y usarlas según la sección; ya se dieron los prompts para ChatGPT (hojas 4x3 fondo #00FF00, 2 partes por animación).
- [ ] El personaje anime viene con fotogramas pequeños (~170x410 px útiles) escalados a 720 px de alto; se ve algo suave. Pedir versión de mayor resolución si se quiere más nitidez.
- [ ] Revisar/cambiar los mensajes de los bocadillos (`SAY` en `script.js`); son inventados a partir de sus datos.
- [ ] Oracle: descripción genérica ("Manejo de bases de datos Oracle"). Preguntar si usó PL/SQL, administración, etc. y si añadirlo a la experiencia.
- [x] README del perfil de GitHub (repo `RyanCloudOps/RyanCloudOps`, commit `18148dc`): publicado con el tema del portfolio (cabecera SVG con personaje animado incrustado, tabla periódica SVG, botones, variantes claro/oscuro con `<picture>`). El generador es `build_profile.py` (scratchpad de la sesión, no está en el repo); lo antiguo está en `archive/` de ese repo. Pendiente de revisar: aspecto en tema claro y en móvil, y peso de la cabecera (~750 KB).
- [ ] Vista móvil: el hero se ve bien con ~650 px de ancho; falta revisar el resto de secciones y el scroll lateral de logros.
- [ ] Idea: animaciones/poses distintas según la sección visible (p. ej. usar las poses reales de traje azul).
- [ ] Decidir si se borra `arcade-backup/` (carpeta local ignorada por git).

## Notas técnicas
- Para recortar fondos verdes (scripts `key2.py`/`key3.py` en el scratchpad de la sesión, no están en el repo; `key3.py` une varias hojas 4x3, alinea los pies y monta un spritesheet) se usó un entorno virtual temporal (numpy + opencv + pillow) en el scratchpad de la sesión. Si hay que recortar más imágenes hay que recrearlo: chroma key con `g - max(r,b)`, despill, y una misma ventana de recorte para todos los fotogramas.
- Servidor local para probar: `python -m http.server 5500` en la carpeta, luego http://localhost:5500
- Si cambias imágenes/CSS/JS con el mismo nombre, sube el número `?v=` en `index.html` y `script.js` para saltar la caché del navegador (GitHub Pages cachea 10 min).
- Publicar: `git add -A && git commit -m "..." && git push origin main`
