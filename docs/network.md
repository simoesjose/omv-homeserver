# Rede

## Objetivo
Documentar IPs, portas, DNS e acessos (LAN vs Tailscale).

## LAN
- IP do OMV: 192.168.1.200
- Gateway: <preencher>
- DNS: (clientes LAN apontam para 192.168.1.200 quando AdGuard estiver ativo)

## Tailscale
- Máquina/host no tailnet: homeserver
- IP Tailscale: 100.80.202.44
- Subnet routes (se aplicares): 192.168.1.0/24
- ACLs (se aplicável): <link para admin Tailscale>

## Portas (resumo)
> As portas detalhadas estão descritas por serviço.

- AdGuard Home: 53/tcp+udp (DNS), 8080/tcp (UI)
- Jellyfin: 8096/tcp (HTTP), 8920/tcp (HTTPS opcional)
- Portainer: 9443/tcp (UI HTTPS), [9000/tcp]

## Notas
- Evitar expor serviços desnecessários para fora.
- Preferir acesso via Tailscale quando possível.