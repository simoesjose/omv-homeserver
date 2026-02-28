# Runbook — DNS down (AdGuard)

## Quando usar
- Sites não abrem por nome, mas IP funciona (ex.: ping 1.1.1.1 funciona).

## Passos
1) Confirmar se o AdGuard está a correr:
   - `docker ps`
2) Ver logs do AdGuard:
   - `docker logs <nome_do_container> --tail 200`
3) Confirmar se a porta DNS está em escuta:
   - `ss -tulpn`
4) Confirmar DNS nos clientes/router:
   - verificar DNS configurado aponta para o OMV

## Recuperação rápida (temporária)
- Trocar DNS no router para 1.1.1.1 / 8.8.8.8 enquanto resolves.

## Depois
- Registar causa e solução em `docs/changelog.md` (e/ou incidentes, se criares).