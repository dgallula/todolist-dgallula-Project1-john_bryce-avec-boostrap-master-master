# todolist

On affiche un message si il n'y a pas tâches à faire.
Un champs texte accompagné d'un bouton "Ajouter" sera présent au dessus de la liste et permettra d'ajouter une nouvelle tâche.
Pour chaque tâche, une case à cocher permettra de marquer la tâche comme faite.
Une tâche terminée sera barrée (à l'aide de CSS).
Les tâches à faire seront toujours affichées en premier.
Une case, en bas de liste, permettra de masques les tâches terminées.
Les tâches respeceront le format suivant :

[
    { "title": "Acheter la propriété 'Rue de la Paix'", "completed": false, "date": 20240730 },
    { "title": "Construire un hôtel sur 'Avenue Foch'", "completed": false, "date": 20240730 },
    { "title": "Éviter la case prison", "completed": false, "date": 20240730 }

This template should help get you started developing with Vue 3 in Vite.

## Recommended IDE Setup

[VSCode](https://code.visualstudio.com/) + [Volar](https://marketplace.visualstudio.com/items?itemName=Vue.volar) (and disable Vetur).

## Customize configuration

See [Vite Configuration Reference](https://vitejs.dev/config/).

## Project Setup

```sh
npm install
```

### Compile and Hot-Reload for Development

```sh
npm run dev
```

### Compile and Minify for Production

```sh
npm run build
```
