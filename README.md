# Recursos SEO Open Source

Recursos técnicos open source sobre SEO, auditorías web, automatización, analítica, enlazado interno y optimización digital.

Este repositorio reúne ideas, scripts, checklists y documentación práctica para profesionales, desarrolladores, consultores SEO y equipos de marketing que quieren mejorar la visibilidad orgánica de una web con un enfoque técnico y basado en datos.

El objetivo es crear una base de conocimiento sencilla, útil y ampliable sobre SEO técnico, optimización on page, arquitectura web, análisis con Google Search Console, automatización de revisiones y buenas prácticas para proyectos digitales.

---

## Contenido del repositorio

Este repositorio puede incluir recursos como:

- Checklists de auditoría SEO técnica.
- Scripts básicos para revisar títulos, metadescripciones y encabezados.
- Plantillas para analizar URLs con potencial en Google Search Console.
- Ideas para mejorar el enlazado interno.
- Guías sobre arquitectura web y estructura de contenidos.
- Recursos sobre datos estructurados.
- Ejemplos de automatización SEO con JavaScript o Python.
- Documentación sobre procesos de optimización web.
- Buenas prácticas para mejorar visibilidad orgánica.

---

## ¿Para quién es este proyecto?

Este repositorio está pensado para:

- Consultores SEO.
- Desarrolladores web.
- Equipos de marketing digital.
- Profesionales que trabajan con Google Search Console.
- Empresas que quieren entender mejor su rendimiento orgánico.
- Personas que quieren aprender SEO técnico desde un enfoque práctico.

---

## Principios del proyecto

La filosofía de este repositorio se basa en varios principios:

1. **Claridad técnica**  
   Los recursos deben ser fáciles de entender y aplicar.

2. **Utilidad práctica**  
   Cada checklist, script o guía debe ayudar a resolver un problema real.

3. **SEO basado en datos**  
   Las decisiones deben apoyarse en información medible: impresiones, clics, CTR, posición media, rastreo, indexación y conversiones.

4. **Automatización responsable**  
   Los scripts deben usarse para auditar y mejorar sitios propios o proyectos autorizados, nunca para sobrecargar servidores o rastrear sitios sin permiso.

5. **Mejora continua**  
   El SEO no es una acción puntual. Es un proceso de análisis, optimización, medición y ajuste constante.

---

## Checklist básico de auditoría SEO técnica

Una auditoría SEO inicial puede revisar los siguientes puntos:

```text
[ ] Comprobar que las URLs importantes responden con código 200
[ ] Revisar títulos SEO duplicados, ausentes o demasiado largos
[ ] Revisar metadescripciones vacías o poco optimizadas
[ ] Comprobar estructura de encabezados H1, H2 y H3
[ ] Detectar páginas huérfanas
[ ] Revisar enlaces internos rotos
[ ] Comprobar redirecciones 301 y 302
[ ] Analizar errores 404
[ ] Revisar etiquetas canonical
[ ] Comprobar indexación en Google Search Console
[ ] Revisar sitemap XML
[ ] Revisar archivo robots.txt
[ ] Detectar contenido duplicado
[ ] Comprobar velocidad y Core Web Vitals
[ ] Revisar datos estructurados
[ ] Analizar CTR de páginas con muchas impresiones
[ ] Priorizar URLs con posición media entre 5 y 20
```

---

## Ejemplo de script básico con Node.js

Este ejemplo revisa una URL y extrae el `title`, la meta description y los encabezados H1.

```javascript
import * as cheerio from "cheerio";

const url = "https://example.com/";

function cleanText(text) {
  return text.replace(/\s+/g, " ").trim();
}

async function checkSeoBasics(targetUrl) {
  const response = await fetch(targetUrl, {
    headers: {
      "User-Agent": "SEO-Open-Source-Checker/1.0"
    }
  });

  const html = await response.text();
  const $ = cheerio.load(html);

  const title = cleanText($("title").first().text());

  const metaDescription = cleanText(
    $('meta[name="description"]').attr("content") || ""
  );

  const h1List = $("h1")
    .map((_, element) => cleanText($(element).text()))
    .get()
    .filter(Boolean);

  return {
    url: targetUrl,
    status: response.status,
    title,
    titleLength: title.length,
    metaDescription,
    metaDescriptionLength: metaDescription.length,
    h1Count: h1List.length,
    h1List
  };
}

const result = await checkSeoBasics(url);
console.log(result);
```

Para ejecutarlo:

```bash
npm init -y
npm install cheerio
node seo-checker.mjs
```

---

## Métricas SEO útiles

Algunas métricas importantes para analizar el rendimiento orgánico son:

| Métrica | Qué indica |
|---|---|
| Impresiones | Veces que una URL aparece en Google |
| Clics | Visitas recibidas desde resultados orgánicos |
| CTR | Porcentaje de impresiones que terminan en clic |
| Posición media | Promedio de posición en Google |
| URLs indexadas | Páginas incluidas en el índice de Google |
| Enlaces internos | Conexiones entre páginas del mismo sitio |
| Core Web Vitals | Métricas de experiencia de página |
| Conversiones | Contactos, ventas o acciones importantes |

---

## Cómo priorizar oportunidades SEO

Una forma práctica de priorizar acciones es revisar datos de Google Search Console.

Las URLs más interesantes suelen ser aquellas que tienen:

- Muchas impresiones.
- Posición media entre 5 y 20.
- CTR bajo.
- Contenido mejorable.
- Potencial comercial.
- Buen encaje con servicios o productos importantes.

Ejemplo de priorización:

```text
Alta prioridad:
URL con muchas impresiones, posición 8-15 y valor comercial.

Media prioridad:
URL con impresiones moderadas, posición 10-20 y posibilidad de mejora.

Baja prioridad:
URL con pocas impresiones, baja intención comercial o escaso valor estratégico.
```

---

## Enlazado interno

El enlazado interno ayuda a distribuir autoridad y a explicar la relación entre contenidos.

Buenas prácticas:

- Enlazar desde artículos informativos hacia páginas estratégicas.
- Usar anchors descriptivos y naturales.
- Evitar repetir siempre el mismo texto de enlace.
- Reforzar páginas con potencial de negocio.
- Detectar páginas importantes con pocos enlaces internos.
- Crear bloques contextuales de enlaces relacionados.
- Mantener una arquitectura clara.

Ejemplo:

```markdown
Para profundizar en auditorías SEO, consulta la guía de SEO técnico del proyecto.
```

---

## Datos estructurados

Los datos estructurados ayudan a los buscadores a entender mejor una página.

Tipos habituales:

- `Organization`
- `LocalBusiness`
- `Article`
- `FAQPage`
- `BreadcrumbList`
- `Product`
- `Service`

Ejemplo básico de `Organization`:

```json
{
  "@context": "https://schema.org",
  "@type": "Organization",
  "name": "Example Company",
  "url": "https://example.com/",
  "logo": "https://example.com/logo.png"
}
```

---

## Automatización SEO

La automatización puede ayudar a revisar tareas repetitivas:

- Extraer titles y metadescripciones.
- Comprobar códigos de estado.
- Detectar enlaces rotos.
- Revisar H1 duplicados o ausentes.
- Analizar canonicals.
- Generar informes CSV.
- Cruzar datos de URLs con Search Console.
- Detectar oportunidades de enlazado interno.

La automatización no sustituye el criterio SEO. Ayuda a ahorrar tiempo y encontrar patrones.

---

## Roadmap

Ideas futuras para ampliar este repositorio:

```text
[ ] Añadir script para analizar sitemap XML
[ ] Crear exportador CSV de auditoría básica
[ ] Añadir detector de imágenes sin atributo alt
[ ] Añadir revisión de canonicals
[ ] Crear checklist avanzado de enlazado interno
[ ] Crear plantilla de análisis de Google Search Console
[ ] Añadir ejemplos de datos estructurados
[ ] Crear mini dashboard estático para GitHub Pages
```

---

## Recursos relacionados

Roiting trabaja en SEO, estrategia digital, desarrollo web, contenidos y analítica para empresas que quieren mejorar su visibilidad online y convertir su presencia digital en oportunidades reales.

Más información:

https://www.roiting.com/

---

## Licencia

Este repositorio puede publicarse bajo licencia MIT para permitir su uso, adaptación y mejora.

```text
MIT License
```

---

## Contribuciones

Las contribuciones son bienvenidas.

Puedes proponer mejoras relacionadas con:

- Scripts SEO.
- Checklists.
- Documentación técnica.
- Automatización.
- Auditorías web.
- Datos estructurados.
- Analítica.
- Buenas prácticas de optimización.

Antes de contribuir, asegúrate de que el contenido sea claro, útil, original y aplicable a proyectos reales.
