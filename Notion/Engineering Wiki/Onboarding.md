---
Owner: Jeremie Cyrille
tags:
  - Guides-and-Processes
Last edited time: 2024-08-06T09:14
---
- [[#Welcome aboard !!!]]
- [[#Computer]]
    - [[#Windows]]
        - [[#WSL]]
        - [[#GIT]]
        - [[#Docker]]
        - [[#IDE]]

# Welcome aboard !!!

Pour travailler sur le projet de l’entreprise, vous devrez installer et vérifier certaines exigences :

# Computer

## Windows

### WSL

Pour travailler sur les différents projets de l’entreprise, vous devrez d’abord installer WSL (Windows Subsystem for Linux) :

```PowerShell
wsl --install
```

Après avoir choisi une distribution à installer, (Debian ou Ubuntu).

```PowerShell
wsl --install -d <Distribution Name>
```

NodeJS

après avoir créer ton profile wls, tu dois installer nvm(node version manager):

```PowerShell
# curl version
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.0/install.sh | bash
\#wget version
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.0/install.sh | bash
```

> [!important] en cas de bug ajoute ce code a ton
> 
> `~/.bash_profile`, `~/.zshrc`, `~/.profile`, ou `~/.bashrc` :
> 
> ```PowerShell
> export NVM_DIR="$([ -z "${XDG_CONFIG_HOME-}" ] && printf %s "${HOME}/.nvm" || printf %s "${XDG_CONFIG_HOME}/nvm")"
> [ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh" # This loads nvm
> ```

> [!important] tu dois executer toute ces commandes dans l’environement wsl, pas dans le windows

### GIT

[[GIT]]

> [!important] En cas d’erreur lors du clonage Git du projet, si le message concerne les droits d’accès au dépôt, contactez @Jeremie Cyrille afin qu’il puisse vous ajouter les privilèges de lecture et d’écriture.

### Docker

[[Docker]]

### IDE

Si tu utilise la suite jetbrain, neovim ou un autre IDE n’est pas un probleme, neanmoins tu dois etre capable d’installer ces extentions:

VSCODE:

> [!info]  
>  
> [https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)  

> [!info]  
>  
> [https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint)  

> [!info]  
>  
> [https://marketplace.visualstudio.com/items?itemName=Prisma.prisma](https://marketplace.visualstudio.com/items?itemName=Prisma.prisma)  

> [!info]  
>  
> [https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-docker](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-docker)  

JETBRAIN:

> [!info] ESLint - IntelliJ IDEs Plugin | Marketplace  
> ESLint intellij integration.  
> [https://plugins.jetbrains.com/plugin/7494-eslint](https://plugins.jetbrains.com/plugin/7494-eslint)  

> [!info] Prisma ORM - IntelliJ IDEs Plugin | Marketplace  
> Support for Prisma ORM.  
> [https://plugins.jetbrains.com/plugin/20686-prisma-orm](https://plugins.jetbrains.com/plugin/20686-prisma-orm)  

> [!info] Prettier - IntelliJ IDEs Plugin | Marketplace  
> Provides Prettier support to all JetBrains IDEs that support JavaScript.  
> [https://plugins.jetbrains.com/plugin/10456-prettier](https://plugins.jetbrains.com/plugin/10456-prettier)  

> [!info] Docker - IntelliJ IDEs Plugin | Marketplace  
> Provides integration with Docker.  
> [https://plugins.jetbrains.com/plugin/7724-docker](https://plugins.jetbrains.com/plugin/7724-docker)  

Neovim

[https://www.youtube.com/watch?v=8um8OYwvz3c](https://www.youtube.com/watch?v=8um8OYwvz3c)