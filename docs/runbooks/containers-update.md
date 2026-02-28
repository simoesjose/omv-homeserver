# Runbook — Atualizar containers (safe-ish)

## Objetivo
Atualizar imagens sem rebentar tudo.

## Passos (genérico)
1) Registar no changelog o que vais fazer (se for relevante).
2) No Portainer:
   - Pull latest image
   - Recreate container
3) Verificar:
   - UI do serviço
   - logs (`docker logs ...`)
   - portas (`ss -tulpn`)

## Rollback
- Se algo falhar, reverter o compose (se mudaste) e voltar a recriar container.
- Registar no changelog.