# AdGuard Home

## Objetivo
DNS local com bloqueio de anúncios/tracking para toda a LAN; opcionalmente pode assumir DHCP (desaconselhado se o router já o faz).

## Acesso
- URL (LAN): http://192.168.1.200:8080
- URL (Tailscale): http://100.80.202.44:8080
- Portas principais:
  - DNS: 53/TCP e 53/UDP
  - UI: 8080/TCP (configurada por ti)
  - (opcional) DHCP: 67/UDP (servidor) e 68/UDP (clientes)

## Docker
- network mode: **host** (recomendado para DNS estável em 53/udp)
- volumes:
  - `/appdata/adguard-home/conf:/opt/adguardhome/conf`
  - `/appdata/adguard-home/work:/opt/adguardhome/work`
- notas:
  - Garante que **mais nenhum serviço** ocupa a porta 53 no host.
  - Se ativares **DHCP** aqui, desativa o DHCP do router (evita conflitos).
  - Define *upstream DNS* redundantes (ex.: 1.1.1.1 e 8.8.8.8) e ativa DoH/DoT se quiseres.

## Compose
- `docker/adguard-home/compose.yml` (importado do Portainer)

## Operação
- atualizar: Pull latest → Recreate (Portainer) ou `docker compose pull && docker compose up -d`
- backup: pasta `conf/` (e opcionalmente `work/`)
- restore: parar o container, repor `conf/` do backup, iniciar

## Troubleshooting
- DNS não resolve:
  - `docker ps` (container a correr?)
  - `docker logs <container> --tail 200`
  - `ss -tulpn | grep -E ':53|:8080'` (conflitos de portas?)
  - mitigação temporária: apontar router/cliente para 1.1.1.1/8.8.8.8