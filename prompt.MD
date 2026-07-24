# Prompt para Claude Code — Slideshow en "Directo de la parrilla"

Trabaja sobre `index.html` (sitio one-page de Restaurante Los Ángeles). Usa la skill de UI/UX pro max.

## Objetivo

Reemplaza el grid de placeholders actual de la sección `<section class="fotos">` (id no explícito, encabezada por "Directo de la parrilla") por un **slideshow automático** con 10 fotos reales del restaurante que ya viven en la carpeta `/img/`.

## Fotos disponibles (ya subidas al repo, formato .webp)

Reemplaza los nombres exactos según cómo se llamen los archivos en la carpeta `/img/`. Son 10:
- 8 de comida (platillos, parrilla, etc.)
- 2 del local/restaurante

Ejemplos de nombres:
`img/arrachera.webp`, `img/costillas-bbq.webp`, `img/alambre.webp`, `img/tacos.webp`, `img/enchiladas.webp`, `img/parrilla-01.webp`, `img/pancita.webp`, `img/huarache.webp`, `img/interior-01.webp`, `img/interior-02.webp`

Yo confirmo los nombres exactos al final; asume estos como placeholders y cámbialos si te doy la lista real.

## Comportamiento del slideshow

1. **Auto-avanza cada 4 segundos** con fade suave (opacity 0.6s).
2. **Loop infinito** (después de la 10 vuelve a la 1).
3. **Se pausa** cuando el usuario pasa el mouse encima (hover) o toca la imagen en móvil.
4. **Controles**:
   - Flechas izquierda/derecha semitransparentes que aparecen al hover (o siempre visibles en móvil, tamaño mínimo 44×44 px para tocar).
   - Dots/indicadores abajo (10 puntitos): el activo en color brasa, los inactivos en línea; permiten saltar directamente.
   - Soporte de swipe táctil en móvil (arrastrar dedo para cambiar).
5. **Accesibilidad**: `aria-live="polite"` en el contenedor, alt descriptivo en cada `<img>`, botones con `aria-label`, y `prefers-reduced-motion` desactiva el auto-play.

## Diseño visual

- Ancho: mismo `contenedor` (max 1040px), padding lateral respeta el resto del sitio.
- Aspect ratio del slideshow: **16:9 en desktop**, **4:5 (vertical) en móvil** para que las fotos de comida se vean grandes en celular. Usa `object-fit: cover`.
- Bordes redondeados sutiles (mismo `border-radius` del sitio, ~8px).
- Contador tipo "3 / 10" abajo a la derecha, discreto, con la misma tipografía del sitio.
- Fondo de la sección se queda como está (`--crema-2`).
- Mantén el eyebrow "Conócenos", título "Directo de la parrilla" y el lede tal cual.

## Performance (crítico)

- La primera foto con `loading="eager"` y `fetchpriority="high"`.
- Las otras 9 con `loading="lazy"` y `decoding="async"`.
- Ninguna librería externa. Vanilla JS puro dentro del mismo `index.html`.
- El script se ejecuta después del DOM (usa `DOMContentLoaded` o pon el `<script>` al final del body).

## Restricciones

- No rompas ningún otro estilo o comportamiento del sitio.
- No agregues CSS ni JS externos.
- No cambies la paleta de colores ni las tipografías.
- Al terminar, dame un resumen de qué agregaste y qué debería revisar yo.

Confirma los nombres exactos de los archivos conmigo antes de aplicar.