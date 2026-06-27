Los solucionarios estan basados en los contenedores de dockerlabs pero deployandolos en un equipo secundario por lo que se exponen los puertos de cada uno:
https://hub.docker.com/r/hacksociety/

Una vez terminado el lab:

# 🧹 Limpieza completa de Docker

Este documento explica cómo **dejar limpio tu entorno Docker**, eliminando contenedores, imágenes, redes y volúmenes. Incluye comandos paso a paso y un modo agresivo para resetear todo.

---

## 🔧 1. Detener y eliminar todos los contenedores

docker stop $(docker ps -aq)
docker rm $(docker ps -aq)
docker ps -aq → lista todos los IDs de contenedores.

docker stop → detiene los que estén corriendo.

docker rm → elimina todos los contenedores.

🔧 2. Eliminar todas las imágenes
bash
docker rmi $(docker images -q)
docker images -q → lista los IDs de todas las imágenes.

docker rmi → borra esas imágenes.

🔧 3. Eliminar todas las redes personalizadas
bash
docker network rm $(docker network ls -q)
docker network ls -q → lista todas las redes creadas por el usuario.

docker network rm → elimina esas redes (no afecta las internas de Docker).

🔧 4. Eliminar todos los volúmenes
bash
docker volume rm $(docker volume ls -q)
docker volume ls -q → lista todos los volúmenes persistentes.

docker volume rm → borra esos volúmenes.

🔧 5. Limpieza total con un solo comando
bash
docker system prune -a --volumes -f
-a → elimina imágenes no usadas además de las dangling.

--volumes → borra volúmenes.

-f → fuerza la acción sin pedir confirmación.

📌 Recomendaciones
Usa los comandos separados si quieres mantener algunos volúmenes o imágenes.

Usa docker system prune -a --volumes -f si quieres un reset total.

✅ Checklist rápido
Detener contenedores

Eliminar contenedores

Eliminar imágenes

Eliminar redes

Eliminar volúmenes

Prune completo

## Tutorial para cargar las imagenes

sudo docker login

## Crear la imagen


sudo docker tag autoescuela:latest tu_usuario_docker/autoescuela:latest
sudo docker tag autoescuela:latest hacksociety/autoescuela:latest

## Cargar la imagen a la nube de docker hub

sudo docker push hacksociety/autoescuela:latest
