# tvpanama-config

Configuracion remota de la app **TV Panama** (Android TV, uso personal / senal abierta TDT de Panama).
La app lee este `config.json` al abrir para saber que canales mostrar, asi se pueden **arreglar o cambiar canales sin reinstalar** la app.

## Que hay aqui
- `config.json` — la lista de canales que usa la app.

## Formato de config.json

    {
      "config_version": 3,
      "min_version_code": 2,
      "update_url": "",
      "update_message": "Hay una version nueva...",
      "channels": [
        { "name": "TVN", "url": "https://tvnpass.com/channel/tvn-en-vivo", "mode": "auto" }
      ]
    }

Campo `mode`:
- `hls` — la URL ya es un .m3u8 directo.
- `auto` — TVN Pass (la app caza el stream con token temporal).
- `web` — abre la web oficial (Dailymotion/Vimeo) a pantalla completa.

## Como arreglar un canal (sin reinstalar)
1. Pulsa el lapiz / "Edit" en `config.json` y cambia la `url` del canal.
2. "Commit changes".
3. En unos 5 minutos todas las cajas toman el cambio solas (cache del CDN). No se reinstala nada.

## Diagnostico rapido si un canal se cae
- **auto (TVN/TVMAX)** no entra: casi siempre la URL del canal cambio. Ve a https://tvnpass.com/channel y usa la **pagina directa** del canal (ej. `/channel/tvn-en-vivo`). No usar la home.
- **web (Telemetro/RPC/SerTV/FETV)**: si no va a pantalla completa, el sitio cambio su reproductor (requiere ajuste en la app).
- **hls (Hosanna/NexTV)**: la URL del .m3u8 cambio; buscar la nueva en la web oficial del canal.

## Notas
- Uso personal. Solo senal abierta (TDT) gratuita de Panama; sin canales de paga ni DRM.
- La documentacion tecnica completa y el codigo de la app se mantienen aparte (privados).
