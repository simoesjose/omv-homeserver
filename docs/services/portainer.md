# Portainer

## Objetivo
Gestão de containers/stacks Docker via UI.

## Acesso
- URL (LAN): http://192.168.1.200:9000
- URL (LAN – HTTPS): https://192.168.1.200:9443 *(certificado autoassinado por omissão)*
- URL (Tailscale): http://100.80.202.44:9000 / https://100.80.202.44:9443
- Portas:
  - 9000/TCP (UI HTTP — em uso)
  - 9443/TCP (UI HTTPS — ativo; podes carregar um certificado na UI)
  - 8000/TCP (Edge/Tunnel — publicado)

## Docker
- network mode: **bridge**
- volumes:
  - `/var/run/docker.sock:/var/run/docker.sock`
  - `/appdata/portainer/data:/data`
- notas:
  - A 9443/HTTPS é o padrão do Portainer; 9000/HTTP é legado (mantido por compatibilidade).
  - Faz backup de `/data` (agora em `/appdata/portainer/data`) para restauro simples.

## Operação
- atualizar: Pull → Recreate
- backup: `tar/rsync` à pasta `/appdata/portainer/data`
- restore: parar container, repor `/appdata/portainer/data`, recriar container

## Troubleshooting
- UI não abre:
  - `ss -tulpn | grep -E ':9443|:9000|:8000'`
  - `docker logs portainer --tail 200`