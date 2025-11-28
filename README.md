# Projet Kanban 

## Description du projet
Ce projet est une application web de gestion de tâches inspirée de Trello, utilisant la méthode Kanban. Elle permet aux utilisateurs d'organiser leurs tâches dans différentes colonnes (listes), de les déplacer par glisser-déposer, et de personnaliser leur tableau de bord. L'objectif était de créer une application interactive et persistante sans utiliser de frameworks lourds, en se concentrant sur les API natives du navigateur.

## Aperçu
![Capture d'écran du projet](./apercu.png)
*(Apercu du site web developpé sous la thématique kanban)*

## Technologies utilisées
*   **HTML5** : Structure sémantique et utilisation de l'API native Drag & Drop (`draggable="true"`).
*   **CSS3** : Mise en page avec Flexbox, styles modernes (Inter font), transitions et responsive design basique.
*   **JavaScript (ES6+)** : Manipulation du DOM, gestion des événements, et logique algorithmique pour le tri.
*   **LocalStorage** : Persistance des données dans le navigateur.

## Fonctionnalités principales
1.  **Gestion des listes et des tâches** :
    *   Création de nouvelles colonnes (listes).
    *   Ajout de nouvelles tâches avec description et date d'échéance.
2.  **Drag & Drop (Glisser-Déposer)** :
    *   Déplacement des tâches d'une colonne à l'autre.
    *   Réorganisation de l'ordre des tâches dans une même colonne.
    *   Déplacement et réorganisation des colonnes elles-mêmes.
3.  **Édition et Suppression** :
    *   Modification dynamique du titre des listes.
    *   Modification du contenu et de la date des tâches via un bouton d'édition.
    *   Suppression de tâches ou de colonnes entières (avec confirmation).
4.  **Personnalisation** :
    *   Changement de la couleur de fond de chaque tâche via un sélecteur de couleur intégré.
5.  **Persistance des données** :
    *   Sauvegarde automatique de l'état du tableau (listes, tâches, couleurs, positions) dans le `localStorage`. Les données sont restaurées au rechargement de la page.
6.  **Validation** :
    *   Vérification du format de la date (AAAA-MM-JJ) lors de la création ou de l'édition.

## Lien vers la page GitHub Pages
* [Lien vers le site KanbanProj](https://omar-bb.github.io/ben_brahim_omar_kanbanproj/)

## Nouveautés explorées
Ce projet m'a permis d'approfondir plusieurs concepts clés du développement web :

*   **HTML Drag and Drop API** : J'ai appris à gérer les événements complexes du cycle de vie du glisser-déposer (`dragstart`, `dragover`, `dragleave`, `drop`) et l'objet `dataTransfer`.
*   **Manipulation avancée du DOM** : Comprendre comment insérer des éléments dynamiquement (`insertBefore`, `appendChild`) et comment créer des éléments "fantômes" (placeholders) pour guider l'utilisateur visuellement.
*   **Stockage côté client** : Utilisation de `JSON.stringify` et `JSON.parse` pour stocker des objets JavaScript complexes dans le `localStorage`.
*   **Event Bubbling & Delegation** : Gestion des événements sur des éléments créés dynamiquement après le chargement initial de la page.

## Difficultés rencontrées
1.  **Complexité de l'API Drag & Drop** : La prise en main de l'API native HTML Drag and Drop a été le défi principal. Comprendre comment gérer les données transférées, empêcher les comportements par défaut du navigateur et gérer les événements de survol pour créer une expérience fluide n'était pas intuitif.
2.  **Logique de placement (Drop)** : Déterminer exactement où insérer l'élément lâché (au-dessus ou en dessous de la tâche survolée) était complexe.
3.  **Conflits d'événements** : Lorsqu'on cliquait sur le bouton "Supprimer" ou le sélecteur de couleur, cela déclenchait parfois le début du glisser-déposer de la carte (dragstart).
4.  **Synchronisation Données / DOM** : S'assurer que l'objet JavaScript `boardData` reste parfaitement synchronisé avec l'affichage HTML après un déplacement complexe.

## Solutions apportées
1.  **Documentation et Exemples** : Pour surmonter les difficultés liées au Drag & Drop, je me suis appuyé sur la documentation officielle MDN, qui a été indispensable. J'ai particulièrement étudié ces deux ressources :
    *   [HTML Drag and Drop API (MDN)](https://developer.mozilla.org/en-US/docs/Web/API/HTML_Drag_and_Drop_API) pour les concepts de base.
    *   [Kanban board with drag and drop (MDN)](https://developer.mozilla.org/en-US/docs/Web/API/HTML_Drag_and_Drop_API/Kanban_board) pour un exemple concret d'implémentation.
2.  **Calcul géométrique (`getBoundingClientRect`)** : Pour le placement, j'ai implémenté une fonction qui calcule la position de la souris par rapport au centre vertical de l'élément survolé.
3.  **`event.stopPropagation()`** : J'ai utilisé cette méthode sur les boutons d'action pour empêcher les interférences avec le drag & drop.
4.  **Fonction de mise à jour globale** : J'ai créé une fonction `updateBoardDataFromDOM()` pour resynchroniser les données après chaque drop.