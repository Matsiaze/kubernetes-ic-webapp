# Source Projet
The repository "app" is the core project of this work and comes from https://github.com/sadofrazer/ic-webapp as of March 24th.
(Or see here https://github.com/Matsiaze/ic-webapp)
# Containerising ic-webapp:
Using the Dockerfile, I released a ic-webapp:1.0 image. Available on my docker hub registry: https://hub.docker.com/repository/docker/mclab7. The repository docker-resources contains a the Dockerfile and the docker-compose.yml used to containerise all the stacks of the app.
# Kubernetes deployment:
I then deployed using the repository named "manifests" the entire application according to the architecture provided in the ic-webapp's project Readme.md
# Notes
Please note that for enhancing best practices and securise your infrastructure you need to use Kubernetes Secrets.
