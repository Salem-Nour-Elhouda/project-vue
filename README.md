# TP Gestion d'une liste de tâches

Ce projet est une application web de gestion de tâches (To-Do list) réalisée avec Vue 3.

# Instructions d'installation et d'exécution
1. Installer les dépendances du projet :
   npm install

2 . Lancer le serveur local :
   npm run dev

3. Ouvrir le projet :
   Cliquer sur le lien http://localhost:5173 dans le terminal pour voir le projet dans le navigateur.


# les fonctions réalisées
 - Ajout d'une tâche  : Permet d'ajouter une nouvelle tâche via un champ de saisie texte (les tâches vides ou constituées uniquement d'espaces ne sont pas acceptées).

 - Marquer comme terminée  : Case à cocher permettant de barrer le texte d'une tâche terminée.
 
 - Suppression d'une tâche  : Bouton permettant de retirer une tâche spécifique de la liste.

 -Compteur dynamique  : Calcul automatique du nombre de tâches non terminées.
 
 - Filtrage des tâches : Boutons permettant de filtrer l'affichage (Toutes, En cours, Terminées).

 - ref : Permet de créer des variables réactives (nouvelleTache, taches, filtre). Lorsque leurs valeurs changent, l'interface HTML se met automatiquement à jour.

# Explication des concepts Vue.js utilisés
- v-model : Assure la liaison bidirectionnelle entre les éléments du formulaire (champ texte, case à cocher) et les données réactives du script.

- v-for : Permet de parcourir le tableau des tâches et de générer un élément de liste <li> pour chaque tâche.

- :key : Associe une clé unique (tache.id) à chaque élément de la liste afin d'aider Vue à suivre efficacement les modifications du DOM.

- computed : Propriété calculée permettant d'évaluer automatiquement le nombre de tâches restantes et le filtrage des tâches, en se mettant à jour uniquement lorsque les données dépendantes changent.

- @submit.prevent : Empêche le rechargement par défaut de la page lors de la soumission d'un formulaire HTML.

- @click : Déclenche l'exécution des fonctions d'ajout, de suppression ou de changement de filtre lors d'un clic sur un bouton.

# Captures d'écran

1. Liste des tâches
![Capture 1](./captures/cap1.png)

2. Tâche terminée
![Capture 2](./captures/cap2.png)

3. Dépôt GitHub
![Capture 3](./captures/cap3.png)