# Runbook — Disco não montado

## Sintomas
- Pasta de media/config vazia
- Containers a falhar por “no such file or directory”

## Passos
1) Ver mounts:
   - `df -h`
2) Ver dispositivos:
   - `lsblk`
3) Ver fstab:
   - `cat /etc/fstab`
4) Se alteraste recentemente o fstab:
   - consulta `docs/changelog.md` para reverter

## Depois
- Atualiza `docs/storage.md` e faz snapshot sanitizado (se aplicável).