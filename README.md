# actualizar_n8n

Comandos:

1. whoami
2. sudo usermod -aG docker USER
3. exit

Cerramos y volvemos a abrir la maquina virtual, para que se efectuen los cambios.

4. docker exec -it n8n n8n --version
5. docker ps -a
6. docker cp <container_id>:/home/node/.n8n ./n8n_backup
7. ls -la ./n8n_backup
8. docker pull docker.n8n.io/n8nio/n8n:'VERSION' (buscar en https://hub.docker.com/r/n8nio/n8n/tags)
9. docker stop <container_id> 
10. docker rm <container_id>
11. docker volume create n8n_data
12. docker run --rm -v n8n_data:/data -v $(pwd)/n8n_backup:/backup busybox sh -c "cp -r /backup/* /data/"
13. sudo chown -R 1000:1000 /var/lib/docker/volumes/n8n_data/_data
14. sudo chmod -R 700 /var/lib/docker/volumes/n8n_data/_data
15. docker run -d --restart unless-stopped --name n8n -p 5678:5678 -e N8N_HOST="n8ncopy.aigenzo.com" -e WEBHOOK_TUNNEL_URL="https://n8ncopy.aigenzo.com/" -e WEBHOOK_URL="https://n8ncopy.aigenzo.com/" -v n8n_data:/home/node/.n8n n8nio/n8n:'VERSION'

Asi es como puse el paso 15 en el video.
Salio distinto pero deberia ser lo mismo.

