# Gasomotores — Landing Page para Taller Mecánico

> Proyecto real para un taller especializado en motores a gasolina en El Vendrell, Tarragona.
> Desarrollado como parte de mi aprendizaje en frontend, aplicando todo lo que he ido aprendiendo en proyectos con clientes reales.

🔗 **Demo en vivo:** https://stanvanger.github.io/gasomotores/

---

## ¿Qué problema resuelve este proyecto?

El taller no tenía presencia digital. Los clientes no podían encontrarlos en Google, no había forma de pedir presupuesto sin llamar, y no existía ningún canal para mostrar los servicios o los precios orientativos.

**El objetivo era claro:** que alguien en El Vendrell que busque "taller mecánico gasolina" o "cambio aceite moto Tarragona" encuentre este negocio, entienda qué hace y pueda contactar en menos de 30 segundos.

---

## Problemas técnicos que resolví y por qué importan

### 1. SEO local desde cero
**Problema:** sin meta tags ni datos estructurados, Google no sabía qué era este negocio ni dónde estaba.

**Solución:** implementé Schema.org con el tipo `AutoRepair` — específico para talleres — con dirección, horarios, servicios y precios. Añadí también `FAQPage` con preguntas reales que los clientes hacen, porque Google las puede mostrar directamente en los resultados de búsqueda.

**Impacto:** el negocio aparece en búsquedas locales con información enriquecida. Las IAs como ChatGPT o Perplexity también pueden recomendarlo cuando alguien pregunta por talleres en Tarragona.

```json
"@type": "AutoRepair",
"areaServed": ["El Vendrell", "Tarragona", "Baix Penedès"]
```

---

### 2. Accesibilidad real, no decorativa
**Problema:** el menú hamburguesa no comunicaba su estado a lectores de pantalla. Las imágenes no tenían descripciones útiles. No había forma de navegar el sitio solo con teclado.

**Solución:**
- `aria-expanded` en el botón del menú que se actualiza dinámicamente con JavaScript cuando se abre o cierra
- Skip-link para que usuarios de teclado puedan saltar al contenido sin pasar por toda la navegación
- `alt` descriptivo en cada imagen con contexto real, no solo el nombre del archivo
- El menú se cierra con la tecla `Escape` — comportamiento estándar que los usuarios esperan

**Impacto:** la web es navegable sin ratón y compatible con tecnologías de asistencia. También mejora el SEO porque Google lee los textos alternativos como contenido.

---

### 3. Calculadora de mantenimiento interactiva
**Problema:** los clientes no saben qué necesita su vehículo hasta que llegan al taller, lo que genera incertidumbre y frena la decisión de llamar.

**Solución:** construí una calculadora en JavaScript vanilla que, según la marca, kilómetros y síntomas del vehículo, genera un diagnóstico con los servicios recomendados priorizados por urgencia (🔴 urgente / 🟡 pronto / 🟢 ok). Al final genera automáticamente un mensaje de WhatsApp personalizado con los datos del vehículo y los servicios necesarios.

**Impacto:** reduce la fricción entre "me interesa" y "contacto". El cliente llega al WhatsApp ya con información concreta, lo que hace más fácil el cierre para el taller.

```javascript
// El mensaje se genera dinámicamente con los datos del vehículo
const msg = encodeURIComponent('Hola Gasomotores, tengo un ' + marca +
  ' con ' + km + ' km. Necesito: ' + items.map(i => i.t).join(', '));
```

---

### 4. Carrusel sin librerías externas
**Problema:** la mayoría de carruseles se implementan con Swiper, Slick u otras librerías que añaden decenas de KB innecesarios.

**Solución:** lo construí desde cero con CSS `transform: translateX` y JavaScript puro. Funciona con clic, tiene auto-avance y puntos de navegación. El peso total del carrusel es prácticamente cero en comparación con una librería.

**Impacto:** mejor rendimiento de carga. Aprendí cómo funciona un carrusel por dentro, no solo cómo usarlo.

---

### 5. Formulario de contacto sin backend
**Problema:** los formularios de contacto normalmente necesitan un servidor para enviar emails (PHP, Node.js, etc.), lo que complica el despliegue en GitHub Pages.

**Solución:** el formulario recoge los datos del cliente y los convierte en un mensaje de WhatsApp estructurado que se abre directamente. El taller recibe la consulta con todos los datos (nombre, teléfono, vehículo, servicio) sin necesidad de ningún backend.

**Impacto:** funciona 100% en GitHub Pages, sin costes de servidor y con una tasa de respuesta más alta porque WhatsApp tiene más apertura que el email.

---

## Stack técnico

| Tecnología | Uso |
|---|---|
| HTML5 semántico | Estructura con `<section>`, `<nav>`, `<footer>`, `<article>` |
| CSS3 vanilla | Variables CSS, Grid, Flexbox, animaciones, responsive |
| JavaScript ES6 | Carrusel, calculadora, carrito, filtros, formulario |
| Schema.org | SEO estructurado para negocio local |
| ARIA | Accesibilidad para teclado y lectores de pantalla |
| GitHub Pages | Despliegue estático sin servidor |

**Sin frameworks. Sin librerías de UI. Sin npm.**
Todo está escrito a mano porque quería entender cada línea antes de usar atajos.

---

## Estructura del proyecto

```
gasomotores/
├── index.html          ← Todo en un archivo: HTML, CSS y JS inline
├── imagenes/
│   ├── gasomotores_logo_hd.png
│   ├── favicon_gasomotores.png
│   ├── raptor.png      ← Slide coches
│   ├── furgoneta.png   ← Slide furgonetas
│   ├── pcx.jpg         ← Slide motos
│   └── maquinaria.png  ← Slide maquinaria jardín
└── README.md
```

---

## Lo que aprendí construyendo esto

- Que el SEO local no es solo poner palabras clave — el Schema.org es lo que realmente diferencia un negocio en búsquedas locales
- Que la accesibilidad no es un extra, es parte de la calidad del código
- Que un formulario sin backend puede ser igual de efectivo si lo conectas bien con WhatsApp
- Que construir un carrusel desde cero me enseñó más que instalar Swiper

---

## Otros proyectos

| Proyecto | Descripción | Demo |
|---|---|---|
| Zaira Masala | Restaurante indio con menú dinámico desde JSON y carrito | [Ver](https://stanvanger.github.io/demo-zaira-masala/) |
| PawStudio | Landing peluquería mascotas con reservas online | [Ver](https://stanvanger.github.io/pawstudioo/) |
| Blog Desierto | Blog de ejercicio con JS vanilla | [Ver](https://stanvanger.github.io/blog-desierto/) |

---

## Sobre mí

Soy **Carolina Quintero**, diseñadora publicitaria reconvertida en desarrolladora frontend.
Aprendo construyendo proyectos reales para clientes reales.

📧 kinterocarolina0@gmail.com
📱 +34 655 607 610
🔗 github.com/Stanvanger
