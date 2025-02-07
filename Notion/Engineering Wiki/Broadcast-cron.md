---
Owner: Jeremie Cyrille
tags:
  - project
Last edited time: 2024-08-05T18:31
---
https://github.com/ka2b/Broadcaster

- [[#Introduction]]
- [[#Codebase]]
- [[#Architecture]]
- [[#Installation]]
    - [[#Prérequis]]
    - [[#Git]]
- [[#Pour début]]

## Introduction

---

Le Projet Broadcaster SAP Analytics Cloud est une initiative visant à améliorer la diffusion des rapports utilisateurs depuis [SAP Analytics Cloud](https://www.sap.com/products/technology-platform/cloud-analytics.html) (SAC). L'objectif principal du projet est de permettre une distribution automatique et personnalisée des rapports afin que les bonnes informations soient envoyées aux bonnes personnes au bon moment.

Le Broadcaster SAP Analytics Cloud récupère les rapports depuis le SAP cloud, identifie les différents e-mails associés à l'envoi de ce rapport pour la date spécifiée, et envoie ces e-mails avec les rapports intégrés.

[https://github.com/ka2b/Broadcaster](https://github.com/ka2b/Broadcaster)

Plusieurs fonctionnalités y sont incluses :

- Diffusion Personnalisée
    
    Le produit permet de maximiser l'efficacité de la communication en l'adressant directement au public visé  
    grâce à une diffusion personnalisée. Il est également possible d'envoyer les rapports sous format PDF et ZIP  
    pour une plus grande flexibilité.  
    
    - Report : Les documents générés sur les services peuvent être facilement récupérés pour être  
        intégrés ensuite au Broadcaster, assurant ainsi une gestion fluide et efficace des  
        communications.  
        
    - Mail : Chaque e-mail peut être personnalisé selon le destinataire, avec la possibilité de définir  
        un sujet spécifique et de sélectionner les fichiers à joindre pour chaque personne concernée.  
        18  
        
- Planification Maîtrisée
    
    La fonctionnalité de planification permet d'organiser efficacement les tâches, réunions et événements,  
    garantissant une gestion optimisée de l'emploi du temps.  
    
    - Schedule : L'envoi des e-mails peut être planifié avec précision. Il est possible de choisir une  
        date et une heure spécifiques pour chaque envoi et d'ajuster ces paramètres selon les besoins.  
        • Surveillance Approfondie  
        
    - Monitoring : Les envois peuvent être surveillés attentivement. Ce système de surveillance  
        alerte en cas d'erreur lors de l'envoi des e-mails, garantissant une fiabilité sans faille.  
        
- Surveillance Approfondie
    
    Le suivi en temps réel des performances du système assure une gestion proactive et efficace des  
    opérations.  
    
    - Monitoring : Les envois peuvent être surveillés attentivement. Ce système de surveillance  
        alerte en cas d'erreur lors de l'envoi des e-mails, garantissant une fiabilité sans faille.  
          
        
- Broadcast Flow
    
    Grâce à Broadcast Flow, les listes de diffusion et les rapports peuvent être administrés de manière  
    graphique, offrant une interface visuelle qui simplifie la gestion et l'organisation des communications.  
    

## Codebase

---

Le project a été realiser en tierement en javascript, les librairy utiliser sont:

- [Puppeter](https://pptr.dev/guides/what-is-puppeteer):
    
    Puppeteer est une bibliothèque Node.js qui fournit une API haut-niveau pour contrôler Chrome ou Chromium via le protocole DevTools. Elle est largement utilisée pour le scraping, les tests automatisés et la génération de PDF ou d'images de pages web.
    
- [nodemailer](https://nodemailer.com/):
    
    Nodemailer est une bibliothèque pour Node.js permettant l'envoi d'e-mails. Elle offre une API simple et flexible pour envoyer des e-mails avec divers services de messagerie, y compris SMTP, Gmail, et bien d'autres. Nodemailer est largement utilisée pour l'envoi de notifications, de rapports, et pour toute autre tâche nécessitant la communication par e-mail.
    
- [node postgres](https://node-postgres.com/):
    
    Node postgres est une bibliothèque pour Node.js qui permet d'interagir avec des bases de données PostgreSQL. Elle offre une API simple et puissante pour exécuter des requêtes SQL, gérer des transactions et interagir avec la base de données de manière asynchrone et performante.
    

https://github.com/ka2b/Broadcast-gui

## Architecture

# Installation

### Prérequis

> [!important] Les element nécessaire pour faire fonctionner les projets react sont:
> 
> - NodeJS v18+
> - npm
> - PostgresSQL server
> - dotenv-cli(using npm)
> 
> Un Docker-compose contenant une image Postgres et un Admirer est present dans tout les project

## Git

[[GIT]]

# Pour début

Dans un premier tant il faut verifier si vous possédez les prérequis. Apres avoir verifier il vous faut configurer votre`.env` si dessous est le .env minimum pour faire un project fonctionner:

```Plain
# Environment variables declared in this file are automatically made available to Prisma.
# See the documentation for more detail=https://pris.ly/d/prisma-schema\#accessing-environment-variables-from-the-schema

# Prisma supports the native connection string format for PostgreSQL, MySQL, SQLite, SQL Server, MongoDB and CockroachDB.
# See the documentation for all the connection string options=https://pris.ly/d/connection-strings

DATABASE_URL="postgresql://youruser:youpassword@youradress:yourport/yourdatabase?schema=public"
```

> [!important] Ne modifier jamais le .env toujours créée un
> 
> `.env.local` ou vous mettrez vos valeur local

Maintenant il manque juste que a faire installer les package nécessaire en faisant la commande:

```Shell
npm install
```

Afin de simplifier le débugger un fichier de configuration du lancement du project en mode debug est disponible ici :  
  

```JSON
{
  "name": "bitool",
  "version": "0.0.1",
  "description": "bitool",
  "main": "runbitree.js",
  "dependencies": {
    "@supercharge/promise-pool": "^1.6.0",
    "adm-zip": "^0.5.4",
    "cheerio": "*",
    "dotenv": "^8.2.0",
    "exceljs": "^4.2.1",
    "lodash": "^4.17.21",
    "moment": "^2.29.1",
    "nodemailer": "^6.5.0",
    "pdf-lib": "^1.16.0",
    "pg": "^8.5.1",
    "puppeteer": "^2.0.0",
    "winston": "^3.3.0"
  },
  "scripts": {
    "reportgen": "node reportgen.js --batch 202406",
    "sendmail": "node sendMail.js --batch 202406"
  },
  "author": "",
  "license": "ISC"
}
```

lancer le project la command est la suivante:

```Shell
npm run reportgen
npm run sendmail
```