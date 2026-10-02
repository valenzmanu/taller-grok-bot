# Taller Grok Bot · Lionel y su equipo

Un Bot capitán, Lionel, arma su propio equipo en [Grok Bot](https://docs.x.ai/grok-bot/overview):

| Jugador | Hace | Deja |
|---|---|---|
| Di María | Busca 5 restaurantes sin web propia (o con link roto), con contacto público, activos y con rating de 4.2 o más | `/workspace/leads.csv` |
| Riquelme | Hace una landing de ejemplo del #1 y la publica por unas horas | Link y QR |
| Julián | Escribe el primer email | Un borrador que nadie envía |

Tú le hablas solo a Lionel. Hecho para el Grok Bot Guatemala Meetup (3-oct-2026).

## 1. Crea a Lionel

1. En Grok Bot, crea un Bot nuevo llamado **Lionel**. Avatar opcional: [`assets/lionel.png`](assets/lionel.png).
2. En **Edit Profile → Description**, pega el bloque de [`lionel/DESCRIPTION.md`](lionel/DESCRIPTION.md).
3. En el chat de Lionel:
   ```
   Lionel, arma el equipo.
   ```
   Lionel baja sus skills de este repo y crea a Di María, Riquelme y Julián.

¿Te compartieron el link de la plantilla de Lionel? Ábrelo, elige **Add to Grok Bot** y sigue con el punto 3.

## 2. Los 3 pasos

Uno a la vez. Espera la respuesta de Lionel antes del siguiente.

**Paso 1 · buscar**
```
Lionel, paso 1: que Di María busque 5 leads.
```

**Paso 2 · la página**
```
Lionel, paso 2: que Riquelme haga la landing del #1 y la publique.
```

**Paso 3 · el email**
```
Lionel, paso 3: que Julián escriba el email del #1. Me presento así: [quién eres en una línea].
```

¿Tienes Cursor de pago? Agrega al paso 2: `Usa Cursor con Claude; tienes mi OK para un Cloud Agent.`

¿Algo se trabó? [`RESCATE.md`](RESCATE.md) tiene leads, landing y email de respaldo.

## Reglas

- Solo datos públicos.
- Uno a uno: un paso, un restaurante.
- No se envía nada. Si aparece **Send**, presiona **Discard**.
- Las páginas dicen "Demo no oficial", no salen en buscadores y vencen solas.
- El claim URL de la página es tuyo: no lo muestres.

## Qué hay aquí

| Carpeta | Contenido |
|---|---|
| `lionel/` | La description de Lionel |
| `skills/` | `armar-equipo`, `buscar-leads`, `hacer-landing`, `escribir-email` |
| `templates/` | Plantillas de landing: `comal`, `mantel`, `barra` |
| `rescate/` | Leads, landing y email de respaldo |
| `assets/` | Avatares de Lionel, Di María, Riquelme y Julián |

Los archivos `SKILL.md` también funcionan en otros agentes que leen skills.

---

Hecho por Manuel Valenzuela · [TikTok @ingemanu](https://www.tiktok.com/@ingemanu) · [X @vm623_](https://x.com/vm623_)
