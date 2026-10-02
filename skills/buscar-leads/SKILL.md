---
name: buscar-leads
description: Di María encuentra 5 restaurantes en Zona 10 de Guatemala (12 a 16 calle, 3 a 7 avenida) que cumplen 4 mínimos (sin web propia o con link roto, contacto público, activo en los últimos 3 meses, rating de 4.2 o más), los ordena del mejor al peor y los guarda en /workspace/leads.csv con un link por dato. Úsala cuando pidan buscar leads o restaurantes.
---

# Buscar leads

## Cuándo usarla
Cuando Lionel o la persona pidan leads. Zona por defecto: **Zona 10, Ciudad de Guatemala, de la 12 a la 16 calle y de la 3 a la 7 avenida**, ambas aceras de las calles límite.

## Insumos y accesos
- Navegador nativo del Bot: Google Search, Google Maps, Instagram y Facebook públicos, Wanderlog, Restaurants10, Restaurant Guru.
- Sin login en cuentas de terceros. Sin conectores de búsqueda.
- Puntos de partida: Paseo Plaza (3 av. 12-38), Plaza Diez (6 av. 13-05), Fontabella (4 av. 12-59), Edificio EON (14 calle 3-48).

## Los 4 mínimos
1. **Sin web propia o con link roto.** Busca `<nombre> Guatemala sitio web` y abre el link de web de su ficha o perfil. Cuenta como roto: página de apuestas, dominio estacionado o en venta, dominio que no resuelve (DNS). Un 403 o timeout aislado queda "pendiente". Menú solo en Instagram o Facebook cuenta como sin web.
2. **Contacto público** del negocio: teléfono, WhatsApp, email o Instagram.
3. **Activo en los últimos 3 meses:** publicación o reseña con fecha. Una fecha relativa ("hace 28 días") sirve; anota la fecha de consulta.
4. **Rating de 4.2 o más** atribuido a Google.

## Pasos
1. Revisa candidatos uno por uno desde los puntos de partida. Confirma que la dirección esté dentro del perímetro.
2. Verifica los 4 mínimos en orden. Descarta en cuanto falle uno.
3. Por cada lead anota el **problema concreto** en una frase con su link. Ejemplos: "su web lleva a una página de apuestas", "el dominio currykebab.gt no resuelve", "el menú solo está en Instagram".
4. Detente al tener 5, o al revisar 20 candidatos.
5. Ordena del mejor al peor: problema más claro, actividad más reciente, rating más alto.
6. Guarda `/workspace/leads.csv` y muestra la tabla en el chat.

## Validación
- 5 filas o menos; cada fila con los 4 mínimos y un link por dato.
- Ningún dato inventado. Lo que no hallaste dice `no encontrado` y ese candidato no cuenta.
- Todas las direcciones dentro del perímetro.

## Salida
`/workspace/leads.csv`, UTF-8:
```
rank,nombre,direccion,tipo_cocina,maps_url,problema,problema_url,contacto,contacto_url,actividad_fecha,actividad_url,rating,rating_url,instagram_url,logo_url
```
- `rank`: 1 es el mejor.
- `maps_url`: `https://www.google.com/maps/search/?api=1&query=<nombre>+<plaza>+Zona+10+Guatemala`.
- `logo_url`: solo una URL pública de imagen; si no hay, vacío.

Si quedan menos de 5, entrega los que tengas y di cuántos faltan.

## Aprobaciones
- **CAPTCHA o login:** te detienes y avisas con el link. No intentas saltarlo.
- No contactas a ningún negocio ni usas datos privados.
