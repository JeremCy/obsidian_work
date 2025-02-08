---
Owner: Jeremie Cyrille
tags:
  - Guides-and-Processes
Last edited time: 2024-08-05T11:24
---
Tu sera amené à devoir review une PR introduisant des changements dans le code.

Pour ce faire, il est nécessaire de savoir quand les changements peuvent être approuvé ou non.

  

Le principal objectif d’un reviewer est de s’assurer que les changements introduits :

- s’intègrent bien avec le code source de la branche principale (il ne doit pas y avoir de conflits)
- n’introduisent pas de bug ou de faille dans le code (CodeQL ne doit pas échouer et le code doit être relu)
- respectent les spécifications de l’issue traitée
- passent les tests et les builds
- respectent les conventions de nommage

Si l’une de ces conditions n’est pas respectée, le reviewer ne doit pas approuver la PR et doit demander des changements en explicitant ce qui bloque.

  

Le reviewer peut aussi suggérer des modifications s’il a de meilleures algos/pratiques qui répondent aux spécifications de l’issue traitée.

  

Enfin, le rôle du reviewer se termine quand il approuve la PR. C’est à la personne qui a demandé la review de merger ses changements dans la branche principale.

  

> [!important] En aucun cas il est permit d’user de ses droits d’admin pour merger une PR sans qu’elle ait été approuvée suivant les règles de révision de code.
> 
>   
> Si cette option est abusée, la personne responsable perdra les droits d’admin sur toute l’organisation.  

  

Dans `.github/pull_request_template.md`

```Markdown
### Changes proposed in this pull request
- *describe your work here ...*
- 
-

[FID-]
```