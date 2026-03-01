# Portainer (fora de compose)

- Instalação via CLI/OMV (sem `compose.yml`).
- Portas ativas: `9000` (HTTP), `9443` (HTTPS, autoassinado), `8000` (Edge/Tunnel).
- Data dir (host): **`/appdata/portainer/data`** → montado como **`/data`** no container.

## Recriar (referência)

```bash
docker stop portainer && docker rm portainer
docker run -d \
  --name portainer \
  -p 9000:9000 -p 8000:8000 -p 9443:9443 \
  -v /var/run/docker.sock:/var/run/docker.sock \
  -v /appdata/portainer/data:/data \
  --restart unless-stopped \
  --log-driver json-file --log-opt max-size=10m --log-opt max-file=3 \
  portainer/portainer-ce:latest