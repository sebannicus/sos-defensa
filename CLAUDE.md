# SOS Defensa — Instrucciones del Proyecto

## Contexto
Landing jurídica para Carol Garriga y Nancy Cuellar, estudio de derecho laboral + familiar + mediación en La Serena y Coquimbo. Cliente de Sebastián / Gautama Digital. **En producción desde 2026-03-28.**

## Stack
- Astro + Tailwind v4, Playfair Display + Inter
- Modo **static** (output: "static")
- SilkBackground: canvas animado seda dorada como fondo global (fijo, z-index -1)
- Sin framework CSS externo — design tokens custom

## Paleta
- `#0E0E10` negro base (semi-transparente en secciones: `rgba(14,14,16,0.80)`)
- `#C3A75D` dorado accent
- `#E8E1D6` beige cálido (secciones `.section-warm`)
- Gradiente dorado: `#8A6F2F → #C3A75D → #E2C98A`

## Deploy
- Rama activa: `dev` — nunca trabajar directo en `main`
- GitHub: github.com/sebannicus/sos-defensa
- Vercel: https://sos-defensa.vercel.app ✅ — `vercel --prod` desde la carpeta del proyecto
- Último commit deployado: `a238e98` (2026-06-29) — Derecho Civil agregado

## Estructura de componentes
```
src/
  components/
    layout/   Header.astro · Layout.astro · Footer.astro
    sections/ Hero.astro · InfoStrip.astro · Pilares.astro · ConsultaSection.astro
              ServiciosResumen.astro · Testimonios.astro · LeadSection.astro
              VisitaSection.astro · FAQ.astro · CTAFinal.astro
              LeadBot.astro · SilkBackground.astro
  pages/
    index.astro · servicios.astro · conocenos.astro · contacto.astro
    conoce-tus-derechos/index.astro · conoce-tus-derechos/[slug].astro
  styles/
    global.css
```

## Fotos (public/)
- `fotos-carol-garriga/` — carol_garriga_1.webp, carol_garriga_4.webp (portada: _1, servicios/contacto/conocenos: _4)
- `fotos-nancy-cuellar/` — nancy_cuellar_5.webp, nancy_cuellar_6.webp (**_5 = preferida para contacto/servicios, _6 = Hero**)
- `fotos-oficina/` — oficina_1.webp, oficina_2.webp (slideshow en VisitaSection)
- `logo.png` — logo SOS Defensa (también usado como favicon y avatar en LeadBot)
- ⚠️ Todos los jpg/jpeg eliminados del repo (migración webp completada 2026-06-26)

## Secciones del index (en orden)
Hero → InfoStrip → Pilares → ConsultaSection → ServiciosResumen → Testimonios → LeadSection → VisitaSection → FAQ → CTAFinal

## Datos de contacto
- WhatsApp Nancy (principal y LeadBot): `56998078460` (+56 9 9807 8460)
- WhatsApp Carol: `56995630415` (+56 9 9563 0415)
- Email Nancy: n.sosdefensa@gmail.com
- Email Carol: c.sosdefensa@gmail.com
- Instagram: @sosdefensa

## LeadBot (src/components/sections/LeadBot.astro)
- Flujo 6 pasos: área → situación (laboral/familiar/civil) → tiempo → documentos → ciudad → nombre
- `WA_NUMBER = '56998078460'` ✅ número real Nancy (producción)
- Diseño premium: borde degradado dorado, logo avatar, step badge "Paso X de 6", burbujas gold para usuario, CTA WhatsApp verde
- Paso 1: 3 opciones — Derecho Laboral / Derecho Familiar / Derecho Civil
- Civil despliega 10 subtipos: Sucesión, Partición, Curatela, Interdicción, Contratos, Indemnización, Arriendo, Estudio de títulos, Cambio de nombre, Otra

## Servicios implementados
**Derecho Laboral:** Despido injustificado, Autodespido, Acoso laboral, Impago de remuneraciones
**Derecho de Familia:** Divorcio, Pensión de alimentos, Cuidado personal, Relación directa y regular, Violencia intrafamiliar, Separación de bienes
**Mediación Familiar:** sección propia con descripción y bullets
**Derecho Civil (agregado 2026-06-29):** Sucesiones y herencias, Partición de bienes, Curadurías y tutelas, Interdicción, Contratos y litigios, Indemnización de perjuicios, Juicios de arrendamiento, Estudio de títulos, Cambio de nombre y estado civil

## Reglas de negocio
- Solo La Serena y Coquimbo (no Calama)
- Sin botón "Llamar ahora" en ninguna parte del sitio
- Honorarios: "consulta gratuita + honorarios claros según tu causa" (no "solo pagas si ganamos")
- Botón flotante WhatsApp: esquina inferior DERECHA, w-11, palpita verde

## SEO implementado
- robots.txt ✅
- sitemap ✅ (@astrojs/sitemap)
- FAQPage JSON-LD en /index (rich snippets Google)
- LegalService schema.org en Layout.astro
- Canonical URLs automáticas — siteUrl = 'https://sosdefensa.cl'
- og-image: /og-image.jpg

## Variables de entorno
- `PUBLIC_GA_ID` — Google Analytics 4 (pendiente)
- `PUBLIC_GTM_ID` — Google Tag Manager (pendiente)

## Dirección de la oficina
Avenida Balmaceda 391, oficina 220, Edificio Italia, La Serena — implementada en VisitaSection.astro

## Estado sesión 2026-06-29 — TODO DEPLOYADO EN PRODUCCIÓN ✅
- Fotos migradas a webp (jpg/jpeg eliminados del repo)
- Dirección oficina: Avenida Balmaceda 391, oficina 220, Edificio Italia, La Serena
- Derecho Civil agregado: servicios.astro (sección #civil), ServiciosResumen (4ª tarjeta, grid 2→4 col), LeadBot (3ª rama + 10 subtipos)
- Último commit: `a238e98` — rama dev pusheada a GitHub

## Pendientes
- Dominio `sosdefensa.cl` — cliente comprando dominio → conectar en Vercel (Settings → Domains)
- GA4 y GTM IDs (pendiente de cliente)
- Merge rama dev → main cuando cliente apruebe
- Imagen Unsplash en Testimonios.astro (reemplazar por foto real cuando esté disponible)
