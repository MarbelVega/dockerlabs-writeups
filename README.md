Los solucionarios estan basados en los contenedores de dockerlabs pero deployandolos en un equipo secundario por lo que se exponen los puertos de cada uno:
https://hub.docker.com/r/hacksociety/

## Tutorial para cargar las imagenes
Bash
sudo docker login

## Crear la imagen

Bash
sudo docker tag autoescuela:latest tu_usuario_docker/autoescuela:latest
sudo docker tag autoescuela:latest hacksociety/autoescuela:latest

## Cargar la imagen

Bash
sudo docker push hacksociety/autoescuela:latest
