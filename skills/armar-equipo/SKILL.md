---
name: armar-equipo
description: Lionel crea su equipo de tres Bots (Di María busca leads, Riquelme hace la landing, Julián escribe el email), cada uno con su description y su skill. Si un Bot ya existe, no lo duplica. Reporta a quién creó. Úsala cuando pidan armar, crear o revisar el equipo.
---

# Armar el equipo

## Cuándo usarla
Cuando te pidan armar el equipo, crear a los jugadores o revisar que estén completos. Úsala una vez por cuenta; repetirla solo verifica.

## Insumos y accesos
- La capacidad de crear Bots: "Your existing Bots can also suggest or create a focused Bot" ([docs](https://docs.x.ai/grok-bot/bots)).
- Biblioteca de skills privadas de la cuenta. Debe tener `buscar-leads`, `hacer-landing` y `escribir-email`.
- Si falta una skill: `https://raw.githubusercontent.com/valenzmanu/taller-grok-bot/main/skills/<nombre>/SKILL.md`.

## Pasos
1. **Revisa las skills.** Busca en la biblioteca privada `buscar-leads`, `hacer-landing` y `escribir-email`. Si falta alguna, abre `https://raw.githubusercontent.com/valenzmanu/taller-grok-bot/main/skills/<nombre>/SKILL.md` y guárdala como skill privada con ese nombre. Si no puedes abrir el link, detente y pide que te peguen el archivo.
2. **Revisa el equipo.** Lista los Bots de la cuenta. Un Bot con el nombre exacto `Di María`, `Riquelme` o `Julián` ya existe: no lo crees de nuevo. Si su description difiere de la de abajo, avisa y no la cambies.
3. **Crea solo los que faltan**, uno por uno, con este nombre, description y skill:

   | Nombre | Skill | Description |
   |---|---|---|
   | Di María | `buscar-leads` | Buscas restaurantes con información pública para el equipo de Lionel. Usas /buscar-leads. Cada dato lleva su link o dice "no encontrado". Si aparece un CAPTCHA o un login, te detienes y avisas. No contactas a nadie, no inicias sesión en cuentas de terceros y no creas otros Bots. |
   | Riquelme | `hacer-landing` | Haces la landing de demostración de un lead con /hacer-landing. Editas solo el bloque marcado de la plantilla y mantienes la banda "Demo no oficial" y el noindex. No inventas precios, horarios ni reseñas. Nunca muestras un claim URL: lo guardas en /workspace/privado/. No creas cuentas ni otros Bots. |
   | Julián | `escribir-email` | Escribes el primer email para un lead con /escribir-email. Solo email, de usted, sin estadísticas ni promesas. Dejas borrador; si aparece Send o Discard, presionas Discard. Nunca envías nada y no creas otros Bots. |

   Avatar de cada uno (PNG transparente, descárgalo y úsalo como imagen del Bot):

   | Nombre | Avatar |
   |---|---|
   | Di María | `https://raw.githubusercontent.com/valenzmanu/taller-grok-bot/main/assets/dimaria.png` |
   | Riquelme | `https://raw.githubusercontent.com/valenzmanu/taller-grok-bot/main/assets/riquelme.png` |
   | Julián | `https://raw.githubusercontent.com/valenzmanu/taller-grok-bot/main/assets/julian.png` |

   Si tu herramienta para crear Bots no acepta imagen, crea el Bot igual y en el reporte pon el link del avatar para que la persona lo suba en **Edit Profile → Upload**. El avatar de Lionel está en `.../assets/lionel.png`.
4. **Comprueba cada jugador.** Pídele a cada uno: `¿Ves la skill /<su skill>? Responde solo sí o no.` Anota la respuesta.
5. **Reporta** en una tabla y detente.

## Validación
- Existen exactamente un `Di María`, un `Riquelme` y un `Julián`.
- Cada uno respondió "sí" a su skill.
- No se creó ningún otro Bot, routine ni plantilla pública.

## Salida
```
| Bot | Estado | Skill | ¿La ve? | Avatar |
|---|---|---|---|---|
| Di María | creado / ya existía | buscar-leads | sí / no | puesto / subir: <link> |
| Riquelme | ... | hacer-landing | ... | ... |
| Julián | ... | escribir-email | ... | ... |
```
Más una línea: qué falta, si falta algo.

## Aprobaciones
- Si la app pide aprobar la creación de un Bot, pásale la aprobación a la persona y espera.
- No crees routines, plantillas públicas ni Bots extra. No cambies la description de un Bot que ya existía sin permiso.

[No verificado] Nombre y argumentos de la herramienta interna que crea Bots (Dr Eggbot usa `CreateAgent`); si acepta una imagen de avatar; cómo un Bot le escribe a otro.
