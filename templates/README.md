# Plantillas de landing para restaurantes

Tres páginas de una sola pieza (un archivo HTML cada una) para armar en vivo la demo de un restaurante con un agente de IA. Cada archivo trae arriba un bloque marcado `EDITA SOLO ESTE BLOQUE`: el agente llena los datos, elige dos colores y pega el link del logo. No hace falta instalar nada; se abren en cualquier navegador y están pensadas primero para celular.

## ¿Cuál uso?

| Plantilla | Para | Estilo |
|---|---|---|
| `comal.html` | Comida típica, comedores, cafeterías, desayunos, antojitos | Cálida y redondeada, borde festoneado |
| `mantel.html` | Cocina de autor, restaurantes formales, carnes, vinos | Oscura y elegante, tipografía serif |
| `barra.html` | Hamburguesas, bares, food trucks, pizzas, cafés de especialidad | Póster de alto contraste, letra condensada |

Si dudas, usa `comal.html`.

## Cómo pedírselo al agente

Pásale el link "Raw" de la plantilla y una sola línea:

```
Copia comal.html como landing.html y llena solo el bloque "EDITA SOLO ESTE BLOQUE" con los datos públicos del lead #1 de /workspace/leads.csv; toma los dos colores del logo y deja "" lo que no encuentres.
```

Cambia `comal.html` por la plantilla que elegiste.

## Qué se puede cambiar

| Campo | Ejemplo | Si queda vacío |
|---|---|---|
| `--primario`, `--secundario` | `#B8432F`, `#F2B544` | Se usan los colores de la plantilla |
| `nombre`, `frase` | `"Comedor Doña Tere"` | `[Nombre del restaurante]`, `[Frase corta…]` |
| `logo` | URL pública de la imagen | Recuadro `[logo]` |
| `whatsapp` o `telefono` | `"50212345678"` | Botón `[WhatsApp o teléfono]` |
| `maps`, `direccion` | Link de Google Maps | Se arma una búsqueda con nombre y dirección; sin ninguno, `[Link de Google Maps]` |
| `redes` | Instagram, Facebook, TikTok | `[Redes sociales]` |
| `menu` | 3 a 6 platillos o servicios | `[Platillo o servicio 1]`… |
| `horario` | `"Lunes a viernes · 7:00 a 15:00"` | `[Horario por confirmar]` |

Detalles que ya resuelve la plantilla:
- El color del texto sobre cada botón se ajusta solo para que se lea bien.
- Un número de WhatsApp de 8 dígitos se toma como número de Guatemala (+502).
- El precio de un platillo aparece solo si se escribió.

## Reglas de uso

- Todas las páginas llevan arriba, fija, la banda *"Demo no oficial creada en un taller. No está afiliada a este negocio."* y la etiqueta `noindex` para que los buscadores no las indexen. No las quites.
- Solo datos públicos del negocio. Nunca inventes precios, horarios ni reseñas: si no hay dato, déjalo vacío y la página mostrará el texto entre corchetes.
- Las fotos son espacios grises con "foto aquí". No uses fotos de terceros sin permiso.
- Publica solo de forma temporal (60 min en Cloudflare o 24 h en here.now), con la banda y el `noindex`. El link no se le manda a nadie sin revisión humana.

---

Hechas por Manuel Valenzuela (@ingemanu) para un taller de Grok Bot en Guatemala. Si las usas o las mejoras, cuéntame.
