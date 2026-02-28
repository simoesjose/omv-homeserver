# OpenMediaVault (OMV)

## O que documentar aqui?
- alterações a ficheiros do sistema (ex.: fstab)
- mounts, permissões, utilizadores/grupos
- shares SMB/NFS
- alterações na rede feitas no OMV
- updates/upgrade do OMV e efeitos

## Onde guardar “snapshots”
- `omv/snapshots/` (sanitizados)
  - exemplo: `omv/snapshots/etc/fstab.example`

## Exemplo: mudança no fstab
Quando alterares o fstab:
1) Regista em `docs/changelog.md` (o que/porquê/reverter).
2) Copia a versão nova (sem dados sensíveis) para `omv/snapshots/etc/fstab.example`.
3) Opcional: cola também o comando que usaste em `docs/commands.md` ou no changelog.

## Notas rápidas do OMV
Ver: `omv/notes.md`