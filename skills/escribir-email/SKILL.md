---
name: escribir-email
description: Julián escribe el primer email para un lead de /workspace/leads.csv con el link de su landing; deja el borrador y presiona Discard, nunca Send. Úsala cuando pidan escribir, redactar o preparar el email de un lead.
---

# Escribir el email

## Cuándo usarla
Cuando pidan el email del lead #N (por defecto, el #1). Solo email.

## Insumos y accesos
- Fila del lead en `/workspace/leads.csv`: `nombre`, `problema`, `problema_url`, `contacto`.
- Link del sitio en `/workspace/landing-<slug>/sitio.txt`.
- `[quién soy en una línea]`: lo da la persona. Si no lo dio, deja la variable tal cual.
- No necesitas conectores.

## Pasos
1. Lee la fila y el link del sitio.
2. Llena la plantilla. "Qué noté" usa el problema concreto y dónde se ve (ej. "el link de su web en Wanderlog abre una página de apuestas").
3. Cuenta palabras: 120 o menos con el asunto. Si te pasas, recorta "qué noté".
4. Guarda `/workspace/email-<slug>.md` y muéstralo en el chat.
5. Si la app abre un borrador con **Send / Discard**, presiona **Discard**.

## Plantilla
```
Para: <email público del lead o "no encontrado">
Asunto: Página de ejemplo para [restaurante]

Buen día:

[quién soy en una línea].

Vi que [problema concreto]. Lo noté aquí: [link de evidencia]

Sin que nadie me lo pidiera, preparé una página de ejemplo para [restaurante] con datos públicos: [link del sitio]

¿Le gustaría que la ajustemos con su información?

Si no le interesa, responda "no, gracias" y no le escribo más.

Saludos,
[firma]
```

## Validación
- Asunto exacto: `Página de ejemplo para <nombre>`.
- Las 4 piezas en orden: quién soy, qué noté, qué preparé, una pregunta.
- Incluye "Sin que nadie me lo pidiera" y la salida fácil.
- Sin estadísticas, cifras de mercado ni promesas de resultados. De usted.
- Cada dato sale del CSV o de `sitio.txt`.

## Salida
`/workspace/email-<slug>.md` y el texto en el chat, más una línea: "Borrador listo; no se envió."

## Aprobaciones
- **Nunca presionas Send** ni envías por ningún canal. Si aparece Send / Discard: Discard.
- No buscas emails privados ni inicias sesión en cuentas del negocio.
