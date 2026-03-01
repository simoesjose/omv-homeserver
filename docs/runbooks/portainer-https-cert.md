# Runbook — Portainer: trocar certificado (HTTPS em 9443)

## Quando usar
- Remover o aviso do certificado **autoassinado** em `:9443`.
- Passar a **usar certificado válido** (cadeia completa) ou um **autoassinado provisório**.
- (Opcional) **Forçar HTTPS only**.

> Por omissão, o Portainer expõe a UI em **9443/HTTPS** com um **certificado autoassinado**. Podes **substituir** esse certificado **na UI** (após instalação) ou **no arranque** do container com *flags* (cert/key em **PEM**; idealmente com a **cadeia completa**). [1](https://adguard-dns.io/kb/adguard-home/getting-started/)

---

## Pré‑requisitos
- Portainer a correr nas portas `9000` (HTTP) e `9443` (HTTPS) — recomendado ter ambas ativas para não te “fechares fora” durante a troca.
- Certificado **X.509** e **chave privada** em **PEM**.  
- (Recomendado) **Full chain** (certificado + intermediários) para evitar erros de validação. [1](https://adguard-dns.io/kb/adguard-home/getting-started/)

---

## Opção A — Troca via **UI** (mais simples)

1. Abre `https://<IP>:9443` e entra com um utilizador administrador (aceita o autoassinado atual).  
2. Vai a **Settings → SSL certificate**.  
3. (Opcional) Ativa **Force HTTPS only** para desativar o acesso HTTP (nota: não há redireção automática). [2](https://bing.com/search?q=AdGuard+Home+default+ports+53+3000+dashboard+documentation)  
4. Em **Upload X.509 certificate**, seleciona o **certificado PEM** (de preferência a **full chain**).  
5. Em **Upload a private key**, seleciona a **chave privada PEM**.  
6. Clica **Apply changes**. A sessão pode reiniciar; volta a entrar em `https://<IP>:9443`. [3](https://aao.fyi/bits/containers/adguard-home-setup/)

> Dica: confirma primeiro que o acesso HTTPS (mesmo que autoassinado) funciona, **antes** de forçares “HTTPS only”. [3](https://aao.fyi/bits/containers/adguard-home-setup/)

---

## Opção B — Troca via **CLI** (automação)

> Usa esta via se preferes que o container **arranque já** a servir o teu certificado (sem fazer upload na UI).  
> Nas versões atuais, os *flags* **preferidos** são `--tlscert` e `--tlskey`. (Se estiveres a usar `--sslcert/--sslkey`, funcionam, mas podem gerar *warnings deprecação* — atualiza quando te der jeito.)

### Passos

1) **Preparar diretório de certificados** no host (ex.: `/appdata/portainer/certs`) e colocar:
- `/appdata/portainer/certs/portainer.crt`  → **certificado PEM** (idealmente *full chain*)  
- `/appdata/portainer/certs/portainer.key`  → **chave privada PEM**

2) **Recriar** o container com as *flags*:

```bash
docker stop portainer && docker rm portainer

docker run -d \
  --name portainer \
  -p 9000:9000 -p 8000:8000 -p 9443:9443 \
  -v /var/run/docker.sock:/var/run/docker.sock \
  -v /appdata/portainer/data:/data \
  -v /appdata/portainer/certs:/certs:ro \
  --restart unless-stopped \
  --log-driver json-file --log-opt max-size=10m --log-opt max-file=3 \
  portainer/portainer-ce:latest \
  --tlscert /certs/portainer.crt \
  --tlskey  /certs/portainer.key