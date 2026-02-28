# Começar aqui

## Objetivo
Ter uma referência simples e pesquisável para:
- serviços (portas, volumes, modo de rede, compose)
- alterações no OMV (fstab, mounts, permissões, shares)
- troubleshooting e procedimentos (runbooks)
- histórico: o que mudou, quando e porquê

## Workflow (muito simples)
1. Faço uma alteração (OMV ou Docker).
2. Atualizo o ficheiro relevante (ex.: `docker/<serviço>/compose.yml` ou notas em `docs/omv.md`).
3. Registo a alteração em `docs/changelog.md`.
4. Commit no GitHub.

## Onde está o quê?
- **Wiki**: `docs/`
- **Compose**: `docker/`
- **OMV (snapshots/notas)**: `omv/`

## Quick checks (quando algo falha)
- Containers a correr: `docker ps`
- Logs: `docker logs <container> --tail 200`
- Portas em escuta: `ss -tulpn`
- Espaço em disco: `df -h`