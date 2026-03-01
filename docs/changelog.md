# Changelog

> Regista aqui alterações relevantes (Docker + OMV).
> Mantém entradas pequenas e objetivas.

### 2026-02-28 — [infra] normalização de docs + serviços
- **O que mudou:** páginas `docs/services/*` preenchidas (AdGuard, Tailscale, Jellyfin, Portainer); `docs/network.md` e `docs/architecture.md` atualizados.
- **Porquê:** consolidar a fonte de verdade para rede/serviços.
- **Impacto:** documentação alinhada com o estado atual (IPs, portas, paths).
- **Como validar:** abrir cada UI (8080/8096/9443) via LAN e via Tailscale.
- **Como reverter:** voltar aos placeholders anteriores (git revert).
- **Ficheiros/links:** `docs/services/*.md`, `docs/network.md`, `docs/architecture.md`.

### 2026-02-28 — [docker] convenções e hygiene
- **O que mudou:** adicionadas recomendações para `restart`, `logging`, redes (`apps_net`), e `.env` sem segredos.
- **Porquê:** reduzir risco (logs a crescer), facilitar manutenção.
- **Impacto:** composes mais consistentes; sem alterações disruptivas.
- **Como validar:** `docker compose config` por stack; `docker ps` e `docker logs`.
- **Ficheiros/links:** `docker/*/compose.yml` (próxima alteração), `.env` (novo).

### 2026-02-27
- **chore:** criei o repositório `omv-homeserver` e a estrutura inicial de documentação.

---

## Template para novas entradas

### AAAA-MM-DD — [categoria] resumo curto
- **O que mudou:**
- **Porquê:**
- **Impacto:**
- **Como validar:**
- **Como reverter:**
- **Ficheiros/links:**
  - (ex.: `docker/jellyfin/compose.yml`)
  - (link para issue / commit, se fizer sentido)