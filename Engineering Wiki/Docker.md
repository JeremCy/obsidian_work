---
Owner: Jeremie Cyrille
tags:
  - Infrastructure
Last edited time: 2024-08-27T11:03
---
- [[#introduction]]
- [[#installation]]
- [[#Utilisation]]

# introduction

---

Docker est une plateforme de développement qui permet d'automatiser le déploiement, la mise à l'échelle et la gestion des applications dans des conteneurs. Ces conteneurs peuvent être déployés sur n'importe quel serveur sans souci de compatibilité. Nous utilisons Docker pour sa portabilité, sa facilité de mise en place et sa capacité à isoler et gérer les dépendances, ce qui rend les applications plus fiables et plus faciles à maintenir.

# installation

---

Si docker n’est pas installer sur votre machine, referez vous la a documentation si dessous:

> [!info] Overview of Docker Desktop  
> Explore more of Docker Desktop, what it has to offer, and its key features.  
> [https://docs.docker.com/desktop/](https://docs.docker.com/desktop/)  

# Utilisation

---

Pour configurer docker un `==Docker-compose.yml==`est present dans tous les projet et contient deja les container, la command d’activation est:

```Shell
\#for launch only some container
docker-compose up -d yourcontainernames
# for launch all container
docker-compose up 
```