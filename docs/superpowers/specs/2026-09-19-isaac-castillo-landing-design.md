# Isaac Castillo Freelance: Landing Neobrutalista

## Objetivo

Crear una landing page estática para Isaac Castillo Freelance que comunique desarrollo web, apps y criterio visual en menos de tres segundos. La experiencia debe sentirse directa, física y memorable, con un embudo claro desde el hero hasta el contacto.

## Dirección visual

- Fondo principal blanco crudo `#f7f3ea`.
- Tinta negra `#111111` para texto, bordes y sombras.
- Acentos saturados: amarillo `#ffda44`, cian `#55d8ff`, rosa `#ff75b8` y verde neón `#c8ff3d`.
- Bordes de `3px solid #111111` en tarjetas, botones, inputs e imágenes.
- Sombras sólidas, principalmente `6px 6px 0 #111111`.
- Tipografía sans geométrica grande, usando una fuente web de display y fallback sans-serif.
- Interacciones físicas: `transform: translate(3px, 3px)` y reducción de sombra en hover/active.

## Estructura

1. **Navbar**: marca “ISAAC CASTILLO / FREELANCE”, enlaces a Servicios, Proyectos y Sobre mí, CTA “Hablemos”.
2. **Hero**: eyebrow de disponibilidad, H1 “Desarrollo web y apps que no aburren y sí venden.”, subtítulo directo, CTAs “Ver proyectos” y “Agenda una llamada”, composición abstracta CSS/SVG.
3. **Servicios**: tres tarjetas para Web/Frontend, Apps móviles y Consultoría Tech/UI-UX.
4. **Proyectos**: dos casos demo editables en formato horizontal/zigzag, con visuales abstractos, tecnologías, reto, solución y CTA.
5. **Social proof**: marquee visual de tecnologías y tres testimonios demo con estrellas.
6. **Sobre mí**: presentación personal, filosofía “Código limpio. Entregas a tiempo.” y dato humano sobre café/CSS.
7. **Contacto/footer**: fondo amarillo, headline de cierre, formulario visual, email, LinkedIn y GitHub.

## Arquitectura Astro

- Proyecto estático en `Freelanceweb`.
- `src/layouts/BaseLayout.astro` contiene HTML base, metadatos, viewport y estilos globales.
- `src/pages/index.astro` compone la página y conserva el contenido de la landing en un solo lugar fácil de editar.
- `src/styles/global.css` contiene reset, tokens, tipografía, responsive utilities y estados compartidos.
- Componentes `.astro` separados por sección cuando mejoren la legibilidad; no se añade React.
- JavaScript limitado a la navegación móvil, si el layout lo necesita. El marquee será CSS.
- Sin imágenes externas obligatorias: los visuales iniciales serán CSS/SVG para mantener velocidad y evitar placeholders rotos.

## Responsive y accesibilidad

- Layout de una columna en móvil y grids de 2/3 columnas en pantallas grandes.
- Targets táctiles mínimos de 44px.
- Contraste alto, foco visible, labels reales en formularios y `alt` descriptivo en imágenes futuras.
- `prefers-reduced-motion` desactiva animaciones no esenciales.
- Navegación por anclas con encabezados semánticos y un único H1.

## Alcance y exclusiones

- El formulario será presentacional en esta primera versión; no simulará envíos exitosos ni integrará backend.
- Testimonios, proyectos y enlaces sociales son contenido demo editable.
- No se agrega CMS, autenticación, analytics ni una librería UI.

## Criterios de aceptación

- `npm run build` termina correctamente.
- El primer viewport muestra marca, propuesta de valor y CTA.
- Todos los bloques principales tienen el sistema neobrutalista: borde negro grueso, sombra sólida y color/acento intencional.
- Los botones tienen estados hover, focus y active visibles.
- La página se puede recorrer por teclado y se mantiene legible en móvil.
