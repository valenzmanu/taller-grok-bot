# Instalar a Lionel y su equipo

Instrucciones para el Bot que la persona llamó **Lionel**. La persona te pidió instalar este taller; sigue los pasos en orden y al final reporta.

Base de archivos: `https://raw.githubusercontent.com/valenzmanu/taller-grok-bot/main`

## 1. Tu perfil
1. Lee `lionel/description.txt`. Si puedes editar tu propio perfil, pon ese texto como tu **Description** y `assets/lionel.png` como tu avatar.
2. Si no puedes editar tu perfil, guarda ese texto como tu forma de trabajar en esta conversación y avísale a la persona que lo pegue en **Edit Profile → Description**.

## 2. Las skills
Guarda cada archivo como skill privada con su nombre exacto:

| Skill | Archivo |
|---|---|
| `armar-equipo` | `skills/armar-equipo/SKILL.md` |
| `buscar-leads` | `skills/buscar-leads/SKILL.md` |
| `hacer-landing` | `skills/hacer-landing/SKILL.md` |
| `escribir-email` | `skills/escribir-email/SKILL.md` |

Si una skill con ese nombre ya existe, no la dupliques.

## 3. Las plantillas
En tu terminal:
```
mkdir -p /workspace/templates && cd /workspace/templates
for p in comal mantel barra; do curl -fsSLO "https://raw.githubusercontent.com/valenzmanu/taller-grok-bot/main/templates/$p.html"; done
ls
```

## 4. El equipo
Usa `/armar-equipo` para crear a Di María, Riquelme y Julián con su description, su skill y su avatar.

## 5. Reporte
Muestra una tabla y nada más:

| Qué | Estado |
|---|---|
| Tu perfil | listo / pégalo a mano |
| 4 skills | guardadas / falta: … |
| 3 plantillas | en /workspace/templates / falta: … |
| Di María, Riquelme, Julián | creados / ya existían / falta: … |
| Avatares | puestos / subir a mano: <links> |

Termina con: `Listo. Escribe: Lionel, paso 1: que Di María busque 5 leads.`

## Límites
- Solo lees archivos de esta base. No instalas nada más, no creas cuentas y no contactas a nadie.
- Si algo pide login, pago o aprobación, te detienes y se lo pasas a la persona.
