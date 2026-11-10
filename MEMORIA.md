# Memoria — as studio (web)
_Actualizado: 2026-11-09_

## Estado actual
- Landing estática de una página: `index.html` + `styles.css` + `assets/`, **sin JavaScript**, sin build ni dependencias.
- **Publicada 2026-11-09** con GitHub Pages (rama `main`, `/ (root)`): https://josueeeee.github.io/as-studio/ — cada push a `main` la actualiza en 1-2 min. 404 propia en `404.html` (rutas absolutas `/as-studio/...`).
- Git: remoto `origin` = github.com/Josueeeee/as-studio, rama `main` (primer push 2026-11-09). Push con PowerShell, no Git Bash.
- Efectos de scroll 100 % CSS (`animation-timeline: scroll()/view()`), dentro de `@supports` y `prefers-reduced-motion`: barra de progreso, cabecera que se compacta, parallax de círculos, cintas que avanzan, sección Antes/Durante/Después fijada en escritorio (300vh + sticky), recap que gira y se destapa.
- Vista previa: config `as-studio-web` en `Desktop/.claude/launch.json` → http://localhost:4196.
- Secciones: hero, Servicios (4 tarjetas sticky que se apilan), Antes/Durante/Después (eventos), caso Halloween Party (La Zona Food Park), cierre "Cuéntanos tu idea" con confeti, footer.
- Contacto (dado por el usuario 2026-11-09): Instagram `@as.studiocreativ` (botones "Escríbenos"), Instagram `@magnifiq_mq`, TikTok `@iam_magnifiq`, WhatsApp +504 9954-5663 (botón flotante + cierre + pie), San Marcos, Ocotepeque. JSON-LD `LocalBusiness` en `index.html` con los mismos datos: cambiarlos en los dos lugares.
- Verificada en navegador 2026-11-09: escritorio y 375 px sin scroll horizontal, consola limpia, red 200.

## Decisiones
- 2026-11-09 — Se usa la marca del cliente (no getdesign): morado #5B2DFF, amarillo #FFC31D, coral #FE5B3C, crema #FAF7F2, tinta #141220, Poppins. **Por qué:** el cliente ya tiene identidad visual (posts y logo).
- 2026-11-09 — Logo recortado con fondo transparente desde los posts (`_originales/`), no redibujado en SVG. **Por qué:** rápido y fiel; si el cliente entrega el logo vectorial, reemplazar `assets/mark-light.png`.
- 2026-11-09 — Sin modo oscuro. **Por qué:** la marca ya es de fondo morado.
- 2026-11-09 — Texto chico en coral sobre crema usa `--coral-texto` #C4401F, no el coral de marca. **Por qué:** #FE5B3C sobre crema no llega a contraste AA.
- 2026-11-09 — Sin JS; los enlaces de contacto van directo en el HTML (comentarios `Contacto:`). **Por qué:** pedido del usuario (solo HTML + CSS).

- 2026-11-09 — El confeti del cierre "explota" desde el logo con rangos `cover <n>vh` sobre la línea `--cta`, no con `entry %`. **Por qué:** con `entry %` en una sección más alta que la pantalla la explosión ocurría antes de ver el logo.

## Errores a evitar
- Para verificar animaciones de scroll no fiarse de capturas (llegan con retraso): leer `el.getAnimations()[i].effect.getComputedTiming().progress` tras un `setTimeout`, recalculando la posición de la sección en cada paso.
- Cintas giradas con margen negativo daban 21 px de scroll lateral; `overflow-x:clip` en `body` no basta (se propaga al viewport) → va en `main`. Nunca `overflow:hidden` en ancestros de `.fases-sticky` (rompe el sticky); usar `clip`.
- Las animaciones de scroll usan `translate`/`scale`/`rotate` sueltos y la de flotar usa `transform`, para que no se pisen.

## Pendientes
- [ ] Confirmar que `@magnifiq_mq` es Instagram (el usuario solo dio el nombre).
- [ ] Firefox/Safari antiguos sin scroll-driven animations ven la página estática (correcto, pero sin efectos).
- [ ] Pedir logo vectorial (SVG) y más trabajos/fotos reales para el portafolio.
- [ ] Falta de la checklist web: aviso legal/privacidad (investigación legal por país → `LEGAL.md`), JSON-LD, Lighthouse, Search Console. Si se compra dominio propio, cambiar `canonical`, `og:*` y `sitemap.xml` (hoy apuntan a github.io) y agregar CNAME. En github.io de proyecto, `robots.txt` no está en la raíz del dominio, así que los buscadores no lo leen.
- [ ] Confirmar con el cliente el texto del hero ("Somos una agencia creativa…"), es redacción propia.

## Propuestas para CLAUDE.md / AGENTS.md
- (ninguna)
