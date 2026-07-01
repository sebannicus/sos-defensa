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
- Vercel: https://sosdefensa.cl ✅ (dominio propio conectado 2026-06-30)
- Último commit deployado: `ca7ad60` (2026-07-01) — GSC verification + robots.txt
- `vercel --prod` desde la carpeta del proyecto

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
- **WhatsApp CTAs (todos):** `56995630415` (+56 9 9563 0415) — Carol (número principal web)
- WhatsApp Nancy (solo tarjeta personal en /contacto, `tel:` informativo): `56998078460`
- Email Nancy: n.sosdefensa@gmail.com
- Email Carol: c.sosdefensa@gmail.com
- Instagram: @sosdefensa

## LeadBot (src/components/sections/LeadBot.astro)
- Flujo 6 pasos: área → situación (laboral/familiar/civil) → tiempo → documentos → ciudad → nombre
- `WA_NUMBER = '56995630415'` ✅ número Carol (producción)
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
- robots.txt ✅ (`public/robots.txt` — `Allow: /`, apunta a sitemap-index.xml)
- sitemap ✅ (`@astrojs/sitemap` — 17 páginas en `sitemap-0.xml`)
- FAQPage JSON-LD en /index (rich snippets Google)
- LegalService schema.org en Layout.astro
- Canonical URLs automáticas — siteUrl = `https://sosdefensa.cl`
- og-image fallback: `/logo.png` (no existe /og-image.jpg — pendiente crear imagen 1200×630)

## Analytics y GSC — CONFIGURADOS ✅ (2026-07-01)
- **GA4:** `G-3CKHTH7LPX` — env var `PUBLIC_GA_ID` en Vercel production ✅
- **GTM:** `PUBLIC_GTM_ID` — pendiente (opcional, no urgente)
- **Google Search Console:** verificado con meta tag HTML ✅
  - Propiedad: `sosdefensa.cl` (tipo URL prefix: `https://sosdefensa.cl/`)
  - Meta tag: `UVfJICsoETxskM08U-qOy28D3aT7JrJIXXtSBITCQZg` (en Layout.astro)
  - Sitemap enviado: `https://sosdefensa.cl/sitemap-index.xml` ✅ (estado: Correcto)

## Dirección de la oficina
Avenida Balmaceda 391, oficina 220, Edificio Italia, La Serena — implementada en VisitaSection.astro

## Estado sesión 2026-07-01 — PROYECTO CERRADO ✅
- CTAs WhatsApp: todos apuntan a Carol `56995630415` (excepto tarjeta personal Nancy en /contacto)
- "Derecho civil" integrado en toda la web: Hero, Footer, Pilares, FAQ, ServiciosResumen, servicios.astro, LeadBot, metas/titles de todas las páginas
- Dominio `sosdefensa.cl` conectado a Vercel ✅
- GA4 `G-3CKHTH7LPX` activo en producción ✅
- Google Search Console verificado + sitemap enviado (17 páginas) ✅
- robots.txt deployado ✅
- Commits del sprint: `5ab4f48` (civil + teléfono) → `b96cd53` (robots.txt) → `ca7ad60` (GSC + GA4)

## Pendientes
- **og-image real:** crear imagen 1200×630 con branding SOS Defensa y subir como `/public/og-image.png` (actualizar Layout.astro)
- **GTM ID:** opcional, no urgente — `PUBLIC_GTM_ID` en Vercel si lo solicitan
- **Merge dev → main:** cuando cliente apruebe formalmente
- **Testimonios:** reemplazar imagen Unsplash por foto real cuando esté disponible
- **GSC:** en ~5 días verificar que las 17 páginas aparezcan como "descubiertas" en Search Console
