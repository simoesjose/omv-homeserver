# Jellyfin

## Objetivo
Servidor de media para LAN (e acesso remoto via Tailscale, se necessário); sem transcoding HW por agora (a 1050 Ti ainda não está instalada).

## Acesso
- URL (LAN): http://192.168.1.200:8096
- URL (Tailscale): http://100.80.202.44:8096
- Portas:
  - 8096/TCP (HTTP)
  - 8920/TCP (HTTPS – opcional, se configurares)

## Docker
- network mode: **bridge** (rede de apps dedicada é recomendado)
- volumes:
  - `/appdata/jellyfin/config:/config`
  - `/appdata/jellyfin/cache:/cache`
  - **(a definir quando os discos de media estiverem prontos)** `</ponto-do-media>:/media:ro`
- notas:
  - Define `PUID`/`PGID` e `TZ` para permissões consistentes.
  - Quando instalares a GPU (1050 Ti), rever o compose para ativar transcoding (NVIDIA).

## Compose
- `docker/jellyfin/compose.yml`

## Operação
- atualizar: Pull → Recreate
- backup: `config/` (bibliotecas/definições)
- restore: repor `config/` e iniciar

## Troubleshooting
- Playback/transcoding lento:
  - Sem HW por agora; quando instalares a GPU, ativar mapeamento `--gpus` e drivers
- Biblioteca não atualiza:
  - Verifica `paths` e permissões do host
  - Força *Library Scan* e revê logs