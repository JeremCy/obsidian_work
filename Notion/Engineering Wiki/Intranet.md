---
Owner: Jeremie Cyrille
tags:
  - project
Last edited time: 2024-08-14T15:11
---
https://github.com/ka2b/intranet_fournisseur

- [[#Introduction]]
    - [[#Codebase]]
    - [[#Code quality]]
    - [[#Architecture]]
- [[#Installation]]
    - [[#Prérequis]]
    - [[#Git]]
    - [[#Docker]]
- [[#Pour débuter]]
    - [[#Base de donnée]]
    - [[#Build]]
- [[#UX/UI]]

# Introduction

Ka2b possède **deux types de consultants** : les **salariés** et les **fournisseurs**, qui, à la fin du mois, doivent déclarer leur présence et sur quel projet ils ont travaillé.

Le but de cette application est de permettre **deux choses** :

- Permettre aux fournisseurs de remplir leur **Compte Rendu d’Activité (CRA)** afin de générer un PDF résumant leur présence.
- Créer un hub où les fournisseurs peuvent déposer les documents importants pour l’entreprise, facilitant le travail de la comptabilité.

## Codebase

---

Durant ce projet, nous avons intégré plusieurs bibliothèques et Framework pour optimiser le  
développement et améliorer l'expérience utilisateur.  

- [Next.js](https://nextjs.org/docs) :
    
    Pour le Framework de notre application, nous avons opté pour Next.js. Next.js est un Framework basé sur  
    React qui facilite le rendu côté serveur améliorant ainsi les performances et le référencement (SEO) de  
    notre application. Grâce à ses fonctionnalités telles que le pré-rendu et la gestion des routes, Next.js nous  
    a permis de créer une application web rapide et optimisée.  
    
- [Shadcn/ui](https://ui.shadcn.com/docs) :
    
    Nous avons également intégré shadcn/ui, une bibliothèque de composants UI pour React. Cette  
    bibliothèque nous a fourni une collection de composants stylisés et prêts à l'emploi, nous permettant de  
    développer rapidement une interface utilisateur cohérente et esthétique.  
    
- [Tailwind CSS](https://tailwindcss.com/docs/installation) :
    
    Pour le style de notre application, nous avons choisi Tailwind CSS, un Framework de conception utilitaire  
    qui nous a permis de créer des interfaces utilisateur modernes et réactives. Tailwind CSS nous a offert une  
    grande flexibilité et rapidité dans la création de styles, grâce à ses classes utilitaires prédéfinies.  
    
- [React-hook-form](https://react-hook-form.com/get-started)
    
    React-hook-form est une bibliothèque pour gérer les formulaires dans les applications React. Elle permet de créer des formulaires performants et faciles à utiliser, en gérant les états des entrées et les validations de manière efficace.
    
- [Zod resolver](https://zod.dev/)
    
    Zod est une bibliothèque de validation de schémas pour TypeScript et JavaScript. Elle permet de définir des schémas de données et de valider facilement des objets contre ces schémas, assurant ainsi que les données respectent les structures et types attendus.
    
- [Prisma](https://www.prisma.io/docs)
    
    Prisma est un ORM (Object-Relational Mapping) moderne pour Node.js et TypeScript. Il simplifie l'interaction avec les bases de données en fournissant un API type-safe pour effectuer des requêtes, des migrations de schéma et bien plus encore, facilitant ainsi le développement et la maintenance des applications.
    
- [Nextauth](https://next-auth.js.org/getting-started/example)
    
    NextAuth.js est une bibliothèque d'authentification pour les applications Next.js. Elle permet d'ajouter facilement des fonctionnalités d'authentification sécurisées, telles que la connexion avec des fournisseurs OAuth (comme Google, Facebook, etc.), des identifiants, et la gestion des sessions utilisateur. NextAuth.js simplifie l'intégration de diverses méthodes d'authentification et offre une personnalisation flexible, tout en assurant une sécurité robuste pour les applications web.
    

> [!important] Dans notre cas, nous avons utilisé Docker comme environnement d’exécution de développement. See
> 
> [[Docker]]

## Code quality

---

Nous avons utilisé [Cypress](https://docs.cypress.io/guides/overview/why-cypress), une bibliothèque de test moderne et performante pour JavaScript. Cypress est particulièrement apprécié pour sa simplicité et son efficacité dans l'écriture et l'exécution de tests. Il permet de tester toutes les interactions de l'utilisateur avec l'application, de vérifier les comportements et de détecter les erreurs avant que l'application ne soit mise en production.

[ESLint](https://eslint.org/docs/latest/) nous aide à repérer les erreurs et les problèmes de style avant même que le code ne soit  
compilé. Il vérifie le code contre un ensemble de règles définies et signale les violations, permettant ainsi aux développeurs de corriger les erreurs de manière proactive.  

[Prettier](https://prettier.io/docs/en/) formate le code dès qu'il est envoyé sur GitHub, assurant une  
mise en forme cohérente et lisible pour tous les développeurs de l'équipe.  

[Husky](https://typicode.github.io/husky/) est un outil qui améliore le flux de travail en permettant l'exécution de scripts dans les hooks Git. Il s'assure que certaines actions, telles que le linting ou les tests de code, sont effectuées automatiquement avant les commits et les pushs, maintenant ainsi la qualité et la cohérence du code.

## Architecture

---

L’architecture de notre projet repose sur une [architecture MVC](https://openclassrooms.com/fr/courses/4670706-adoptez-une-architecture-mvc-en-php/7847928-decouvrez-comment-fonctionne-une-architecture-mvc) (Model View Controller).

Nous avons choisi [PostgreSQL](https://www.postgresql.org/docs/) comme système de gestion de base de données

> [!important] Tree view du project
> 
> intranet  
> ┣ .devcontainer // contient les information pour docker  
> ┣ .github  
> ┃ ┣ workflows // contient les github action pour la CI/CD  
> ┣ .husky // contient les command test a lancer avant un commit  
> ┣ .vscode // contient des fichier de debug pour vscode  
> ┣ prisma // contient le schemas et les changement de la BDD  
> ┃ ┣ migration  
> ┣ public  
> ┣ src  
> ┃ ┣ app // dossier ou son situer les page du site  
> ┃ ┃ ┣ (auth) // tt les fichier avec un layout simplifier pour l’authentification  
> ┃ ┃ ┣ (default) / tt les fichier avec le layout de base  
> ┃ ┃ ┃ ┣ api // ce dossier correspond a notre REST api  
> ┃ ┣ components // contient les element a inserer dans les page du dossier app  
> ┃ ┃ ┣ forms // contient tout les formulaire  
> ┃ ┃ ┣ layouts // contient tout ce qui est en lien a ui( navbar, sidebar, etc…)  
> ┃ ┃ ┣ tables // contient toute les tables  
> ┃ ┃ ┣ ui // dossier creer par la librairy Shadcn  
> ┃ ┣ configs // contient des ficher de config  
> ┃ ┣ lib  
> ┃ ┣ types  
> ┗ ┣ utils  

# Installation

### Prérequis

On utilise typscript pour nos projext frontend

On utilise la configuration standard de Nextjs

> [!important] Les element nécessaire pour faire fonctionner les projets react sont:
> 
> - NodeJS v18+
> - npm
> - PostgresSQL server(in a docker container)
> - dotenv-cli(using npm)
> 
> Un Docker-compose contenant une image Postgres et un Admirer est present dans tout les project

## Git

[[GIT]]

## Docker

[[Docker]]

# Pour débuter

Dans un premier tant il faut verifier si vous possédez les prérequis. Apres avoir verifier il vous faut configurer votre`.env` si dessous est le .env minimum pour faire un project fonctionner:

```Plain
# Environment variables declared in this file are automatically made available to Prisma.
# See the documentation for more detail=https://pris.ly/d/prisma-schema\#accessing-environment-variables-from-the-schema

# Prisma supports the native connection string format for PostgreSQL, MySQL, SQLite, SQL Server, MongoDB and CockroachDB.
# See the documentation for all the connection string options=https://pris.ly/d/connection-strings

DATABASE_URL="postgresql://youruser:youpassword@youradress:yourport/yourdatabase?schema=public"
NEXTAUTH_SECRET="yoursecret"
NEXT_AUTH_URL="http://localhost:yourport"
```

> [!important] Ne modifier jamais le .env toujours créée un
> 
> `.env.local` ou vous mettrez vos valeur local

### Base de donnée

Most of the project use `PrismaJS` en tant que `ORM` de ce fait il est nécessaire de synchroniser les changement apporter a la database en utilisant la command ci-dessous

```Shell
dotenv -e .env.local -- npx prisma db push
```

Maintenant il manque juste que a faire installer les package nécessaire en faisant la commande:  
  

```Shell
npm install
```

Afin de simplifier le débugger un fichier de configuration du lancement du project en mode debug est disponible ici :  
  

```JSON
//.vscode/launch.json
{
    "version": "0.2.0",
    "configurations": [
      {
        "name": "Next.js: debug server-side",
        "type": "node-terminal",
        "request": "launch",
        "command": "npm run dev"
      },
      {
        "name": "Next.js: build",
        "type": "node-terminal",
        "request": "launch",
        "command": "npm run build:debug"
      },
      {
        "name": "Next.js: debug client-side",
        "type": "chrome",
        "request": "launch",
        "url": "http://localhost:3000"
      },
      {
        "name": "Next.js: debug full stack",
        "type": "node-terminal",
        "request": "launch",
        "command": "npm run dev",
        "serverReadyAction": {
          "pattern": "started server on .+, url: (https?://.+)",
          "uriFormat": "%s",
          "action": "openExternally"
        }
      },
      {
        "name": "Next.js: prod full stack",
        "type": "node-terminal",
        "request": "launch",
        "command": "npm run start",
        "serverReadyAction": {
          "pattern": "started server on .+, url: (https?://.+)",
          "uriFormat": "%s",
          "action": "openExternally"
        }
      }
    ]
  }
```

lancer le program en utilisant la touche ==`**F5**`== ==ou en faisant ceci:==

aller ici:  
  

![[Untitled.png]]

sélectionner un mode de lancer ou script a executer

![[Untitled 1.png]]

et clicker sur le button play.

Si vous préférer passer par le terminal afin de lance le project la command est la suivante:

```Shell
npm run dev
```

### Build

Le fichier de configuration contient deja une raccourcies pour le build, par line de commande :

```Shell
npm run build
```

Afin de lancer la version build du program:

```Shell
npm run start
```

# UX/UI

https://www.figma.com/design/4gUWtsuAuUyBVL9hcw1z0w/intranet2.0?node-id=0-1&t=OtyLNdFJZRM1TPRO-0