# Memoria — as studio (web)
_Actualizado: 2026-11-09_

## Estado actual
- Landing estática de una página: `index.html` + `styles.css` + `assets/`, **sin JavaScript**, sin build ni dependencias. Solo local; no publicada.
- Efectos de scroll 100 % CSS (`animation-timeline: scroll()/view()`), dentro de `@supports` y `prefers-reduced-motion`: barra de progreso, cabecera que se compacta, parallax de círculos, cintas que avanzan, sección Antes/Durante/Después fijada en escritorio (300vh + sticky), recap que gira y se destapa.
- Vista previa: config `as-studio-web` en `Desktop/.claude/launch.json` → http://localhost:4196.
- Secciones: hero, Servicios (4 tarjetas sticky que se apilan), Antes/Durante/Después (eventos), caso Halloween Party (La Zona Food Park), cierre "Cuéntanos tu idea" con confeti, footer.
- Todos los botones de contacto van a Instagram `@as.studiocreativ` (leído del post del cliente 2026-11-09; confirmar que el usuario está completo).
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
- [ ] Agregar botón de WhatsApp cuando haya número.
- [ ] Firefox/Safari antiguos sin scroll-driven animations ven la página estática (correcto, pero sin efectos).
- [ ] Pedir logo vectorial (SVG) y más trabajos/fotos reales para el portafolio.
- [ ] Antes de publicar: dominio, `og:image` con URL absoluta, sitemap/robots, 404 propia, aviso de privacidad (checklist web de AGENTS.md con ✅/❌/N/A, investigación legal por país → `LEGAL.md`).
- [ ] Confirmar con el cliente el texto del hero ("Somos una agencia creativa…"), es redacción propia.

## Propuestas para CLAUDE.md / AGENTS.md
- (ninguna)
