# Docker

## Organização
- Cada serviço em `docker/<serviço>/`
- O compose “fonte de verdade” fica no repo.

## Convenções (sugeridas)
- Nome do serviço = nome da pasta.
- Manter `compose.yml` e um `README.md` curto por serviço.

## Operações comuns (exemplos)
- Ver containers: `docker ps`
- Logs: `docker logs <container> --tail 200`
- Reiniciar: `docker restart <container>`

> Detalhes por serviço: ver páginas em `docs/services/`.