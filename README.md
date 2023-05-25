# plateforme-maintenance-predictive

## Environment Variables

- **VUE_APP_API_URL**: Set the api url for production mode (_dev mode use the proxy defined in vue.config.js_).

## Project setup

```
npm install
```

### Compiles and hot-reloads for development

```
npm run serve
```

### Compiles and minifies for production

```
npm run build
```

### Lints and fixes files

```
npm run lint
```

### Generate documentation

```
npm run doc
```

> **Notes :**
>
> - Use jsdoc and jsdoc-vue
> - Configuration file is `conf.json`
> - To allow jsdoc to parse your Vue file you must add one of those tags before export
>   - `@vue-prop`
>   - `@vue-data`
>   - `@vue-computed`
>   - `@vue-event`

Check [Jsdoc reference](https://jsdoc.app)

### Check formating

```
npm run checkformat
```

### Format files

```
npm run format
```

> **Notes :**
>
> - `checkformat` and `format` will parse js and vue files in `src/`
> - You can ignore files and folder in `.prettierignore`
> - Configuration is in `package.json`

## Getting started
**[Please check INSTALL.MD](./INSTALL.md#getting-started)**
## Conventions

### Naming

- Language used for naming variables, function, modules,... is **English**
- Variable and function are named in **camelCase**
- Modules are named in **PascalCase**
- Vue components are named in **PascalCase**
  - > See [Convention reference](https://v2.vuejs.org/v2/style-guide)
- Other conventions are [here](./src/views/README.md)
- Naming convention for git is heavily recommended, you can check them **[here](https://dev.azure.com/DIN-SmartFactory/Maintenance%20Pr%C3%A9dictive/_wiki/wikis/Maintenance-Pr%C3%A9dictive.wiki/78/Onboarding-Good-Practices?anchor=git-workflow#)**

### Coding

- End of line **must be CRLF**
- Code **must be formatted** (using Prettier or whatever) before being pushed to Azure
- **Mandatory semicolon in the end of line**
- Variables, function, etc should have a **comprehensive name**
- Functions must not be longer than **60 lines** (which is already a lot)
- Maximum length in a line is **150 colums** (which is again a lot)
- If possible don't create variable outside `data()`

### Tools

- [Git](https://git-scm.com/) is mandatory
- [Node](https://nodejs.org/) is mandatory
- [VSCode](https://code.visualstudio.com/) is recommended with Vetur, Prettier
- [Chrome](https://www.google.com/chrome/) or [Firefox](https://www.mozilla.org/fr/firefox/new/) is recommended to debug
  - Chrome has a better console
  - Firefox is better to debug network
- [SourceTree](https://www.sourcetreeapp.com/) is a good tool to work with Git (but not open source)
- [Tortoise git](https://tortoisegit.org/) is also a good tool to work with Git but admin right is required to be installed (open source)

### Useful documentation

- [Introduction to Vue](https://vuejs.org/guide/introduction.html)
- [Vue API](https://vuejs.org/api/)
- [Swagger](https://labs-alten-tls-fpo-maintpred-back-staging.azurewebsites.net/api-docs/#/) Contains all of the api used on the project

## Customize configuration

See [Configuration Reference](https://cli.vuejs.org/config/).

## Librairies utilisées

Bootstrap-vue (feuilles de style)
Chart js (pour les graphiques)
V-calendar (pour le calendrier)

Version 1.2.1

## Passation Mathis (à supprimer par la suite)

- Ajout de la fonctionnalité "Mot de passe oublié"

- Ajout de la page Admin "Connection history"

Pour accéder à la page Admin sur la staging :

  - Se connecter avec un compte admin, un utilisateur est admin si dans la base de données, dans la table user,
  l'attribut "isAdmin" est à 1, et les attributs "isTech" et "isMaintenancePlanner" sont à 0
  - Aller sur la page "Doors"
  - Appuyer sur le bouton "Admin" en haut à droite
  - Choisir l'onglet "Connection history"
 
Remarques pour la suite :

- La staging et la prod partage la même base de données

- L'utilisateur mp.admin@alten.com devrait être le compte admin de référence, nous pouvons modifier son mot de passe via la page "forgot-password"

- Pour l'accès aux pages "Admin", le bouton devrait être déplacé sur la "Home page" au lieu d'être sur la page des portes

- Une grosse mise à jour pour la prod est à prévoir car beaucoup de travail se trouve sur la staging mais n'a pas encore été push sur la prod

- Pour la mise à jour de la prod :

  - Les tests niveau back qui sont exécutés à chaque déploiement sont prévus pour une base de données vide
  Ils diffèrent entre la prod et la staging ce qui n'est pas normal
  Il faudra donc les remodeler pour les adapter à une base de données déjà rempli

  - Après avoir adapté les tests :
    - En local, se positionner sur la dev
    - Faire un git pull
    - Se positionner sur la main
    - Faire un git pull
    - Faire un git merge dev
    - Résoudre les conflits de merge s'il y en a
    - Vérifier en local que tout marche correctement avant de push en prod