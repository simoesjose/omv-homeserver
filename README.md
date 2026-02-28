# omv-homeserver

Documentação (wiki) + configurações (Docker compose) do meu home server baseado em OpenMediaVault.

## Wiki (docs)
Começar aqui: docs/index.md

- Arquitetura: docs/architecture.md
- Rede: docs/network.md
- Storage: docs/storage.md
- Docker: docs/docker.md
- OMV (sistema): docs/omv.md
- Changelog: docs/changelog.md
- Comandos úteis: docs/commands.md

## Serviços
- AdGuard Home: docs/services/adguard-home.md
- Tailscale: docs/services/tailscale.md
- Jellyfin: docs/services/jellyfin.md
- Portainer: docs/services/portainer.md

## Docker compose (fonte de verdade)
Cada serviço tem a sua pasta em `docker/<serviço>/compose.yml`.

## Regras
- Sem credenciais/tokens/passwords no repositório.
- Cada alteração relevante deve ser registada em `docs/changelog.md`.