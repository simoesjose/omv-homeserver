# Portainer

## Objetivo
Gestão dos containers/stacks Docker via UI.

## Acesso
- Instalado diretamente no OMV (sem compose no repo).
- URL (LAN): https://192.168.1.200:9443
- Portas (comportamento típico do Portainer CE):
  - 9443/TCP (UI HTTPS) — **preferível**
  - 9000/TCP (UI HTTP – legado, opcional)
  - 8000/TCP (Edge – opcional)

## Docker
- network mode: **bridge**
- volumes:
  - `/var/run/docker.sock:/var/run/docker.sock` (podes manter `:ro` se não usares Edge)
  - `/appdata/portainer/data:/data`
- notas:
  - Se já usas 9443, **desnecessário expor 9000**.
  - Faz backup regular de `/data`.

## Compose
- *N/A* (instalado via OMV/Portainer). Documentado apenas para referência.

## Operação
- atualizar: Pull → Recreate
- backup: `data/`
- restore: repor `data/` com container parado

## Troubleshooting
- UI não abre:
  - `ss -tulpn | grep -E ':9443|:9000'`
  - Ver logs do container e conflitos de portas