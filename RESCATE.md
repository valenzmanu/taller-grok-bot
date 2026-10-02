# Rescate

Para cuando un paso se traba en vivo. Datos públicos consultados el 01-oct-2026 (pid-167); ratings atribuidos a Google por agregadores, sin validar en Maps. Revisar Maps antes del taller.

## 1. Leads de respaldo

Archivo listo: `rescate/leads.csv` (mismo formato que `buscar-leads`).

| # | Restaurante | Dirección | Problema concreto | Contacto | Actividad | Rating |
|---|---|---|---|---|---|---|
| 1 | Gracia Cocina de Autor | Plaza Diez, 6a av. 13-05 | [Su web lleva a una página de apuestas](https://www.restaurants10.com/GT/Guatemala-City/673408066013684/Gracia-Cocina-de-Autor) | [2366-8699](https://wanderlog.com/place/details/483620) | 09-09-2026 | 4.6 |
| 2 | Churrasco Centroamericano | Paseo Plaza, 3a av. 12-38 | [churrascocentroamericano.com no resuelve](https://www.aquienguate.com/perfil/churrasco-centroamericano) | [2375-8550](https://wanderlog.com/place/details/9681751/churrasco-centroamericano) | 15-09-2026 | 4.4 |
| 3 | Curry Kebab | EON, 14 calle 3-48 | [currykebab.gt no resuelve](https://www.restaurants10.com/GT/Guatemala-City/105785385504915/Curry-Kebab--Guatemala) | [5633-1590](https://wanderlog.com/place/details/10097812/curry-kebab-restaurante-guatemala) | 17-08-2026 | 4.9 |
| 4 | Little India | Fontabella, 4a av. 12-59 | [Su web muestra contenido de apuestas](https://wanderlog.com/place/details/7836848/little-india) | [2293-1284](https://wanderlog.com/place/details/7836848/little-india) | 30-07-2026 | 4.6 |
| 5 | Restaurante Yue Lai | Paseo Plaza, 3a av. 12-38 | [Sin web; remite a Facebook](https://www.todosbiz.com/GT/restaurante-yue-lai_1A-2331-5082) | [WhatsApp 3414-6820](https://www.restaurants10.com/GT/Guatemala-City/101562924871536/Restaurante-Yue-Lai-%22Aut%C3%A9ntica-Comida-China%22) | 18-09-2026 | 4.7 |
| 6 | El Establo | 14 calle 5-08 | [Su web es solo Instagram](https://wanderlog.com/place/details/900175) | [4206-9554](https://www.restaurants10.com/GT/Guatemala-City/248816198547666/El-Establo) | 17-07-2026 | 4.4 |
| 7 | Del Griego | Fontabella, 4a av. 12-59 | [delgriego.com dice "Under Construction"](https://wanderlog.com/es/place/details/483618/del-griego--fontabella) | [2458-1515](https://www.restaurants10.com/GT/Unknown/149157821833119/Del-Griego) | 09-09-2026 | 4.6 |
| 8 | Miso Zona Viva | Paseo Plaza, 3a av. 12-38 | [Sin web; remite a Facebook](https://wanderlog.com/es/place/details/2632856/miso--zona-viva) | [4150-3788](https://restaurantguru.com/Miso-Zona-Viva-Guatemala-City) | ~03-09-2026 | 4.3 |

Prompt para Lionel (pega debajo el contenido de `rescate/leads.csv`):
```
Lionel, la búsqueda se trabó. Guarda este CSV como /workspace/leads.csv, márcalo como datos de respaldo y sigue con el paso 2.
```

## 2. Landing de respaldo

Archivo listo: `rescate/landing-gracia-cocina-de-autor/public/index.html` (plantilla mantel, solo el bloque editable lleno con datos públicos; menú y horario quedan "por confirmar").

Prompt:
```
Lionel, usa la landing de respaldo que te adjunto: que Riquelme la guarde en /workspace/landing-gracia-cocina-de-autor/public/index.html y la publique.
```
Si no hay publicación: abre el archivo en el navegador y muestra la vista previa.

## 3. Email de respaldo (78 palabras con asunto)

```
Asunto: Página de ejemplo para Gracia Cocina de Autor

Buen día:

[quién soy en una línea].

Vi que el link de su web en Restaurants10 abre una página de apuestas. Lo noté aquí: https://www.restaurants10.com/GT/Guatemala-City/673408066013684/Gracia-Cocina-de-Autor

Sin que nadie me lo pidiera, preparé una página de ejemplo para Gracia Cocina de Autor con datos públicos: [link del sitio]

¿Le gustaría que la ajustemos con su información?

Si no le interesa, responda "no, gracias" y no le escribo más.

Saludos,
[firma]
```

Nada de esto se envía.
