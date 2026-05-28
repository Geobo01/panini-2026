# ⚽ Panini 2026 - Gestionnaire de Collection Sur-Mesure

Une application web d'inventaire légère, ultra-rapide et optimisée pour smartphone, conçue spécifiquement pour suivre, analyser et échanger les vignettes de l'album Panini 2026.

Projet entièrement développé sans base de données lourde, basé sur une structure de données optimisée en mémoire tampon (*buffer*) pour garantir un affichage instantané sur mobile, même avec 980 cartes.

---

## 🚀 Fonctionnalités Clés

* **Ouverture de paquets (Ajout Express) :** * Saisie tolérante aux erreurs : supprime automatiquement les espaces accidentels (ex: `MEX 12` ou `fra  14` deviennent immédiatement valides).
  * Système de double validation avec affichage du nom du joueur, de l'équipe et de la **page exacte de collage** pour éviter les erreurs dans le feu de l'action.
* **Inventaire dynamique & Filtrable :** * Affichage trié scrupuleusement selon l'**ordre officiel de l'album** (et non par ordre d'ajout).
  * Filtres croisés instantanés : par équipe (avec les groupes spéciaux *FIFA* et *History*) et par état (Toutes, Manquantes, Possédées, Doubles).
  * Affichage modulable (masquer/afficher le nom, l'équipe ou la page d'un clic).
  * Ajustement rapide des quantités (+ / -) directement depuis la liste.
* **Statistiques Avancées :** Calcul en temps réel du pourcentage de complétion, du nombre total de cartes physiques récoltées, et du volume exact de doubles disponibles pour l'échange.
* **Module d'Échanges "Peer-to-Peer" :** Interface simplifiée pour simuler un troc avec un ami. L'application vérifie si vous possédez déjà la carte proposée, valide l'échange, ajoute la nouvelle vignette et déduit automatiquement un de vos doubles disponibles.
* **Sécurité des données (Anti-perte) :** Système d'importation et d'exportation de la collection sous forme de code textuel compressé. Permet de sauvegarder sa progression ou de la transférer sur un autre téléphone sans aucun compte cloud.

---

## 🛠️ Architecture Techniques & Règles Métier

L'application intègre des algorithmes mathématiques stricts dictés par la configuration asymétrique de l'album Panini 2026 :

### Gestion de la Pagination
* **Cartes Spéciales (FWC) :** Pagination non-linéaire répartie entre le début de l'album (Pages 1 à 3 pour la section *FIFA*) et la fin de l'album (Pages 106 à 109 pour la section *History*).
* **Cartes Pays (Équipes) :** Répartition automatique sur deux pages par pays (Cartes 1 à 10 sur page paire / Cartes 11 à 20 sur page impaire).
* **Le "Saut des Groupes" :** Prise en compte automatique d'un décalage physique de 2 pages inséré par l'éditeur entre la dernière équipe du Groupe F (Tunisie, p.54-55) et la première équipe du Groupe G (Belgique, p.58-59).

### Structure des Fichiers
* `index.html` : L'interface utilisateur épurée et scannable, pensée pour le responsive mobile.
* `style.css` : Le design de l'application (code couleur adaptatif selon l'état des cartes : gris pour manquante, vert pour possédée, rouge pour double).
* `data.js` : La base de données brute de l'album contenant la cartographie complète des 980 vignettes.
* `app.js` : Le moteur logique (calculs, filtres, écouteurs d'événements et gestion du `localStorage`).

---

## 📦 Déploiement Local / En Ligne

### Mode Local
Téléchargez simplement les fichiers dans un même dossier et double-cliquez sur `index.html` pour lancer l'application dans votre navigateur.

### Déploiement Cloud (Gratuit via GitHub Pages)
1. Créez un dépôt public sur GitHub.
2. Déposez-y les fichiers `index.html`, `style.css`, `app.js` et `data.js`.
3. Allez dans **Settings > Pages**.
4. Sous *Branch*, sélectionnez `main` (ou `master`) et cliquez sur **Save**.
5. Votre application est en ligne !

> 💡 **Astuce Mobile :** Une fois le site ouvert sur smartphone, utilisez l'option **"Ajouter à l'écran d'accueil"** de votre navigateur (Safari/Chrome) pour utiliser l'application en plein écran, comme une application native.

---

## 🔒 Confidentialité
L'application respecte la vie privée de l'utilisateur. Aucune donnée n'est envoyée vers un serveur externe. Tout l'inventaire est stocké localement dans le `localStorage` du navigateur web de l'appareil utilisé.
