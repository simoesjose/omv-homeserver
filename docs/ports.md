# Ports & Endpoints

> Tabela de referência rápida. Origem = de onde costumo aceder (LAN/Tailscale).

| Porta/Protocolo | Serviço       | Origem        | Endpoint típico                          | Notas |
|-----------------|---------------|---------------|------------------------------------------|-------|
| 53 / tcp,udp    | AdGuard Home  | LAN           | 192.168.1.200:53                         | DNS local (network_mode: host). |
| 8080 / tcp      | AdGuard Home  | LAN/Tailscale | 192.168.1.200:8080 / 100.80.202.44:8080  | UI configurada em 8080. |
| 8096 / tcp      | Jellyfin      | LAN/Tailscale | 192.168.1.200:8096 / 100.80.202.44:8096  | HTTP; 8920/HTTPS opcional. |
| 8920 / tcp      | Jellyfin      | LAN/Tailscale | 192.168.1.200:8920                       | **Opcional** (ativar se precisares). |
| 9000 / tcp      | Portainer     | LAN/Tailscale | 192.168.1.200:9000                       | HTTP (mantido por agora). |
| 9443 / tcp      | Portainer     | LAN/Tailscale | 192.168.1.200:9443                       | **Desativado** por agora (TLS a configurar). |