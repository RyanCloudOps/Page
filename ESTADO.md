# Estado del proyecto — Portafolio de Gary Flores

_Última actualización: 2026-10-07. Léelo al empezar la próxima sesión._

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
4. Hero animado: nombre "GARY" gigante de fondo, titular "Systems Engineer.", y el personaje real de Gary con 12 poses (recortadas del fondo verde) que cambian con fundido cada 3,6 s, con bocadillo por pose (ES/EN). Pausa con hover, clic avanza, respeta `prefers-reduced-motion`.
5. Todo subido a GitHub (último push: "Hero animado con poses del personaje y bocadillos").

## Archivos clave
- `index.html` — contenido en español (`data-i18n` para traducir)
- `script.js` — traducciones EN (`EN`), skills (`SK`), poses y bocadillos (`SAY`), tarjeta ID, tema, idioma
- `styles.css` — estilos; colores como variables en `:root`
- `assets/poses/pose-01..12.webp` — poses recortadas (880x800, pies abajo, cabeza centrada)
- `assets/gary-character.svg` — personaje vectorial (solo se usa en la tarjeta ID) · `assets/gary.webp` — foto de traje
- `cv-gary-flores.pdf` — CV descargable
- Poses originales (fondo verde): `C:\Users\pflor\Documents\Codex\2026-10-07\en-e\outputs\poses-fondo-verde.zip` (fuera del repo)

## Pendiente / ideas para mañana
- [ ] Tarjeta ID de "Sobre mí": cambiar el personaje vectorial por una pose real o un recorte de la foto de traje.
- [ ] Las poses miden ~500 px de origen y se escalaron a ~780 px (se ven algo suaves). Pedir versiones de mayor resolución si se quiere más nitidez.
- [ ] Revisar/cambiar los mensajes de los bocadillos (`SAY` en `script.js`); son inventados a partir de sus datos.
- [ ] Oracle: descripción genérica ("Manejo de bases de datos Oracle"). Preguntar si usó PL/SQL, administración, etc. y si añadirlo a la experiencia.
- [ ] README del perfil de GitHub (repo `RyanCloudOps/RyanCloudOps`) con este mismo estilo; es un repo distinto, aún no tocado.
- [ ] Probar vista móvil (no se ha comprobado en pantalla pequeña) y el scroll lateral de logros.
- [ ] Idea: usar poses distintas según la sección visible.
- [ ] Decidir si se borra `arcade-backup/` y `assets/gary-character.svg` si ya no se usan.

## Notas técnicas
- Para recortar fondos verdes se usó un entorno virtual temporal (numpy + opencv + pillow) en el scratchpad de la sesión; el script de recorte no está en el repo. Si hay que recortar más poses, hay que recrearlo (chroma key: `g - max(r,b)`, despill, alinear pies y centrar cabeza).
- Servidor local para probar: `python -m http.server 5500` en la carpeta, luego http://localhost:5500
- Publicar: `git add -A && git commit -m "..." && git push origin main`
