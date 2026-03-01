# Tailscale

## Objetivo
Acesso remoto seguro ao servidor (e opcionalmente à LAN) sem abrir portas no router.

## Acesso
- Máquina no tailnet: `homeserver`
- IP Tailscale: `100.80.202.44`
- (opcional) Rotas/subnets: `192.168.1.0/24` (se vieres a anunciar a LAN)

## Docker
- network mode: **host**
- volumes:
  - `/appdata/tailscale/state:/var/lib/tailscale`
  - `/dev/net/tun:/dev/net/tun`
- capabilities:
  - `CAP_NET_ADMIN`, `CAP_NET_RAW`
- notas:
  - Autenticação inicial com `TS_AUTHKEY` (ou `tailscale up` dentro do container).
  - Para *subnet routing* adicionar `TS_ROUTES=192.168.1.0/24` e `TS_EXTRA_ARGS=--accept-routes` no container de destino.

## Compose
- `docker/tailscale/compose.yml` (importado do Portainer)

## Operação
- atualizar: Pull → Recreate (o estado persiste em `/appdata/tailscale/state`)
- backup: `state/` (se quiseres preservar chaves/estado)
- restore: repor `state/` + `tailscale up` se precisar

## Troubleshooting
- Sem ping por Tailscale:
  - `docker logs <container> --tail 200`
  - Confirma hora/TZ do host (TLS sensível à hora)
  - Verifica ACLs e *advertised routes* no admin da Tailscale