---
Owner: Jeremie Cyrille
tags:
  - Guides-and-Processes
Last edited time: 2024-08-06T09:16
---
- [[#Install GIT]]
- [[#GIT Clone]]
- [[#Convention de nomage Git]]
- [[#Nommage des branches]]
    - [[#Work type]]
    - [[#Task id]]
    - [[#Word summary]]
- [[#Nommage des PR et des commits]]
    - [[#Work type]]
    - [[#Description]]
- [[#GIT command]]

# Install GIT

voicie les commandes pour installer git:

```PowerShell
# wsl(debian et ubuntu)
sudo apt install git-all
# macos
brew install git
```

# GIT Clone

Clone le code en utilisant `git`, avec `SSH` et securisé par une `GPG key` :

```Shell
git clone yourSSHurl # clone the github repo to your machine
```

pour configurer une clé ssh

> [!info] Generating a new SSH key and adding it to the ssh-agent - GitHub Docs  
> After you've checked for existing SSH keys, you can generate a new SSH key to use for authentication, then add it to the ssh-agent.  
> [https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)  

> [!info] Adding a new SSH key to your GitHub account - GitHub Docs  
> To configure your account on GitHub.  
> [https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account?tool=webui&platform=windows](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account?tool=webui&platform=windows)  

pour configurer une GPG key

> [!info] Generating a new GPG key - GitHub Docs  
> If you don't have an existing GPG key, you can generate a new GPG key to use for signing commits and tags.  
> [https://docs.github.com/en/authentication/managing-commit-signature-verification/generating-a-new-gpg-key](https://docs.github.com/en/authentication/managing-commit-signature-verification/generating-a-new-gpg-key)  

> [!info] Adding a GPG key to your GitHub account - GitHub Docs  
> To configure your account on GitHub.  
> [https://docs.github.com/en/authentication/managing-commit-signature-verification/adding-a-gpg-key-to-your-github-account](https://docs.github.com/en/authentication/managing-commit-signature-verification/adding-a-gpg-key-to-your-github-account)  

# Convention de nomage Git

Afin de préserver une harmonie dans le workflow git, nous adoptons une convention de nommage pour les branches, les commits et les PR.

Source : [https://www.conventionalcommits.org/en/v1.0.0/](https://www.conventionalcommits.org/en/v1.0.0/)

# Nommage des branches

Chaque branche devra respecter ce format :

```JavaScript
{work type}/{task id}/{2-3 word summary}
```

## Work type

- `fix` : pour corriger un bug
- `feat` : pour introduire une nouvelle feature
- `chore` : pour modifier quelque chose en relation avec l’environnement du projet (dépendances, settings, versions,…)
- `refactor` : pour réfactorer une partie de code sans en modifier le fonctionnement
- `doc` : pour modifier la documentation (documentation de code, readme)

## Task id

Ça correspond à l’id de la task traité par la branche.

## Word summary

Une indication très brève de ce que la branche traite.

  

Par exemple, si tu implémente un fix du `UserService` dont l’id de la task est `FID-43`, la branche devra être nommée :

```JavaScript
fix/FID-43/user-service
```

  

# Nommage des PR et des commits

Les PR et les commits suivent la même convention de nommage. Celle-ci ressemble à celle des branches mais apporte plus de détails.

```JavaScript
{work type}: {description}
```

## Work type

- `fix` : pour corriger un bug
- `feat` : pour introduire une nouvelle feature
- `chore` : pour modifier quelque chose en relation avec l’environnent du projet (dépendances, settings, versions,…)
- `refactor` : pour réfactorer une partie de code sans en modifier le fonctionnement
- `doc` : pour modifier la documentation (documentation de code, readme)

  

On peut avoir un `fix` , un `refactor` ou un `doc` à l’intérieur d’une branche d’un autre type.

C.a.d que par exemple dans une branche de type `feat`, on peut avoir un commit `doc` pour introduire la documentation de la nouvelle feature.

## Description

Une brève description du travail effectué dans le commit/PR.

  

Par exemple, le commit du fix du UserService devra ressembler à :

```JavaScript
fix: send code 401 when user is unauthenticated
```

  

Le message d’une PR peut être plus évasif si la branche traite plusieurs étapes différentes.

Il faudra donc que la PR respecte les propriétés de la branche.

  

Par exemple si la branche introduit une feature dans le `UserService` et met à jour la documentation et les tests, le message de la PR devra uniquement renseigner le travail demandé dans la task. La PR ressemblera à :

```JavaScript
feat: add method to load user cards
```

# GIT command

1. `git init` - Initialize a new Git repository
2. `git add <file>` - Add a file to the staging area
3. `git commit -m "<message>"` - Commit changes with a message
4. `git status` - Check status of your repository
5. `git push` - Push changes to remote repository
6. `git pull` - Update local repository to the newest commit
7. `git clone <repository>` - Clone a repository into a new directory
8. `git checkout -b <branch>` - Create a new branch and switch to it
9. `git merge <branch>` - Merge a branch into the active one
10. `git branch -d <branch>` - Delete a branch