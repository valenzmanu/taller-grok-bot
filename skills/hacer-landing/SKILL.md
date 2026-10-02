---
name: hacer-landing
description: Riquelme toma el lead #1 de /workspace/leads.csv, elige la plantilla comal, mantel o barra, llena solo su bloque editable con datos públicos, la publica de forma temporal (Cloudflare, si falla here.now, si falla vista previa) y devuelve el link del sitio y un PNG con su QR. Úsala cuando pidan hacer, armar o publicar la landing de un lead.
---

# Hacer la landing

## Cuándo usarla
Cuando pidan la landing del lead #N de `/workspace/leads.csv` (por defecto, el #1).

## Insumos y accesos
- `/workspace/leads.csv` (skill `buscar-leads`).
- Plantillas en `/workspace/templates/`. Si no están, bájalas:
  ```
  mkdir -p /workspace/templates && cd /workspace/templates
  for p in comal mantel barra; do curl -fsSLO "https://raw.githubusercontent.com/valenzmanu/taller-grok-bot/main/templates/$p.html"; done
  ```
- Terminal con `node`/`npx`, `python3` y `curl`. Navegador para la vista previa.
- Opcional: acceso a Cursor Cloud Agents (cuenta Cursor de pago).

## Pasos

### 1. Elegir plantilla
| Plantilla | Para |
|---|---|
| `comal` | comida típica, comedores, cafés, desayunos |
| `mantel` | cocina de autor, carnes, vinos, cenas |
| `barra` | hamburguesas, bares, pizza, comida rápida, asiática informal |

Si dudas, `comal`.

### 2. Llenar el bloque
1. `slug` = nombre en minúsculas, sin tildes, con guiones (ej. `gracia-cocina-de-autor`). Carpeta: `/workspace/landing-<slug>/`.
2. Copia la plantilla a `/workspace/landing-<slug>/public/index.html`.
3. Edita **solo** lo que está entre `EDITA SOLO ESTE BLOQUE` y `FIN DEL BLOQUE EDITABLE`: `--primario`, `--secundario`, `nombre`, `frase`, `logo`, `whatsapp` o `telefono`, `maps`, `direccion`, `redes`, `menu` y `horario`. Solo datos públicos del lead; lo que falte queda `""`.

### 3. Ajuste visual
**Camino A · Cursor Cloud Agents con Claude.** Úsalo si la cuenta puede lanzar Cursor Cloud Agents.
1. Pide OK en una línea: "Lanzo 1 Cloud Agent con claude-opus-5-5; consume tu cuota de Cursor. ¿Va?" Si el pedido ya lo autoriza, sigue.
2. Lanza **un** Cloud Agent con el modelo `claude-opus-5-5` y este encargo, con el archivo completo pegado al final:
   ```
   Ajusta el aspecto de esta landing de demostración. Cambia solo lo que está entre "EDITA SOLO ESTE BLOQUE" y "FIN DEL BLOQUE EDITABLE": los dos colores (que combinen con el logo y se lean bien), una frase de 70 caracteres o menos y el texto del menú. No toques nada fuera del bloque. No inventes precios, horarios ni reseñas. Revisa la página a 390 px y a 1280 px de ancho. Devuélveme el archivo completo, una captura de cada ancho y el modelo que usaste.
   ```
3. Guarda el archivo devuelto en `public/index.html`. Anota el modelo que reportó el agente.
4. Si Cursor pide un repo, pago o permisos que no hay, pasa al Camino B y dilo en una línea.

**Camino B · en tu computadora.** Abre `public/index.html` en el navegador a 390 px y a 1280 px. Ajusta colores y frase dentro del bloque hasta que se lea bien.

### 4. Publicar
Un intento por destino; sin reintentos en bucle.
```
D=/workspace/landing-<slug>; mkdir -p /workspace/privado && chmod 700 /workspace/privado
cat > $D/wrangler.jsonc <<'EOF'
{ "name": "demo-<slug>", "compatibility_date": "2026-10-01", "assets": { "directory": "./public" } }
EOF
cd $D && npx --yes wrangler@latest deploy --temporary > /workspace/privado/wrangler-<slug>.log 2>&1
grep -o 'https://[a-z0-9.-]*\.workers\.dev' /workspace/privado/wrangler-<slug>.log | head -1 > $D/sitio.txt
cat $D/sitio.txt
```
- Nunca imprimas el log: trae el claim URL.
- Si `sitio.txt` queda vacío, lee solo la última línea de error del log (`tail -3`) y pasa a here.now.

**Respaldo · here.now anónimo (24 h):**
```
cd /workspace/landing-<slug> && python3 - <<'PY'
import json, hashlib, pathlib, urllib.request
d = pathlib.Path("public/index.html").read_bytes()
h = {"content-type": "application/json", "x-herenow-client": "taller-grok-bot", "user-agent": "taller-grok-bot"}
def call(m, u, b=None, hd=None):
    with urllib.request.urlopen(urllib.request.Request(u, data=b, method=m, headers=hd or h), timeout=60) as r:
        return r.read()
body = {"files": [{"path": "index.html", "size": len(d), "contentType": "text/html; charset=utf-8", "hash": hashlib.sha256(d).hexdigest()}]}
r = json.loads(call("POST", "https://here.now/api/v1/publish", json.dumps(body).encode()))
pathlib.Path("/workspace/privado/herenow.json").write_text(json.dumps(r))
up = r["upload"]["uploads"][0]
call("PUT", up["url"], d, up.get("headers") or {"Content-Type": "text/html; charset=utf-8"})
call("POST", r["upload"]["finalizeUrl"], json.dumps({"versionId": r["upload"]["versionId"]}).encode())
pathlib.Path("sitio.txt").write_text(r["siteUrl"] + "\n"); print(r["siteUrl"])
PY
```
Si responde 429 o falla, pasa a la vista previa.

**Último respaldo · vista previa en Grok Bot.** Abre `public/index.html` en el navegador del Bot y entrega captura y ruta. Sin link público, sin QR.

### 5. QR
```
cd /workspace/landing-<slug> && npx --yes qrcode -o qr.png "$(cat sitio.txt)"
```
Si falla: `pip install --quiet "qrcode[pil]" && python3 -c "import qrcode; qrcode.make(open('sitio.txt').read().strip()).save('qr.png')"`.

## Validación
- Fuera del bloque, el archivo es igual a la plantilla; la salida debe quedar vacía:
  ```
  B='/EDITA SOLO ESTE BLOQUE/,/FIN DEL BLOQUE EDITABLE/d'
  diff <(sed "$B" /workspace/templates/<plantilla>.html) <(sed "$B" public/index.html)
  ```
- Siguen la banda "Demo no oficial" y `<meta name="robots" content="noindex">`: `grep -c -e 'Demo no oficial' -e 'noindex' public/index.html` da 3 o más.
- `curl -s "$(cat sitio.txt)" | grep -q 'Demo no oficial'` responde bien.
- El QR abre el mismo link (escanéalo o pídeselo a la persona).

## Salida
```
Plantilla: <comal|mantel|barra> · Camino: A (modelo: …) o B
Sitio: <link> · vence: 60 min (Cloudflare) o 24 h (here.now)
QR: /workspace/landing-<slug>/qr.png
Claim guardado en /workspace/privado/ (no se muestra)
```

## Aprobaciones
- **El claim URL nunca va al chat, a una captura ni a la pantalla compartida.** Solo dices en qué archivo quedó.
- Cloud Agent: un solo agente y solo con OK de la persona; consume su cuota de Cursor.
- No creas cuentas, no reclamas el sitio, no compras dominios, no descargas fotos de terceros.
- No quitas la banda "Demo no oficial" ni el `noindex`.

[No verificado] Que el Cloud Agent acepte `claude-opus-5-5` en cada cuenta; el formato exacto de la salida de `wrangler deploy --temporary`; el cuerpo exacto que hoy acepta here.now (ver https://here.now/docs).
