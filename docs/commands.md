# Comandos úteis

## Docker
- containers: `docker ps`
- logs: `docker logs <container> --tail 200`
- redes: `docker network ls`
- volumes: `docker volume ls`

## Rede
- portas: `ss -tulpn`
- resolver DNS: `nslookup exemplo.com`
- ping: `ping 1.1.1.1`

## Storage
- espaço: `df -h`
- blocos: `lsblk`
- fstab: `cat /etc/fstab`

## Dica
Sempre que um comando for “especial” (ou tiver flags importantes),
coloca-o também no changelog na entrada correspondente.