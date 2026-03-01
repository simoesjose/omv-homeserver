# Arquitetura

## Hardware
- Máquina: DIY (OMV bare metal)
- CPU: Intel® Core™ i5-3470 @ 3.20GHz
- RAM: 16 GB
- Disco do SO / appdata: SSD 240 GB
- GPU: (por instalar) NVIDIA GTX 1050 Ti
- Observação: a adicionar HDD/SSD SATA para armazenamento com redundância (ver `docs/storage.md` plano SnapRAID/mergerfs)

## Serviços instalados
- AdGuard Home
- Tailscale
- Jellyfin
- Portainer

## Topologia (texto)
- Clientes na LAN → OMV (192.168.1.200)
- DNS local → AdGuard (porta 53; UI em 8080)
- Acesso remoto → Tailscale (100.80.202.44 / homeserver)
- Media → Jellyfin (8096)
- Gestão Docker → Portainer (9443)