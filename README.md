# Hafaliana Kely

**Les petits bonheurs malagasy** — un mini-jeu d'aventure en 3D isométrique, jouable dans le navigateur, pensé d'abord pour le téléphone.

**▶ [Jouer maintenant](https://chafidy.github.io/Hafaliana-Kely-game/)**

On y vit une journée ordinaire à Madagascar, du matin à la nuit. Chaque petit moment de joie remplit la jauge « Hafaliana » jusqu'à 100 %.

## Le jeu

Une partie dure quelques minutes et enchaîne six quêtes sur deux îles flottantes reliées par un pont : un village à Antananarivo et les rizières en terrasses de Betafo.

| # | Quête | Ce qu'il faut faire | Récompense |
|---|-------|---------------------|------------|
| 1 | Mofo gasy | Aller à la gargote et réussir le mini-jeu de cuisson (taper quand l'aiguille est dans la zone dorée) | MATSIRO! +20 |
| 2 | Taxi-be | Attendre le bus à l'arrêt et monter | MISY TOERANA! +20 |
| 3 | Vary | Ramasser les 6 gerbes de riz dans les terrasses | VOKATRA BE! +20 |
| 4 | Mody | Reprendre le taxi-be pour rentrer avant la nuit | — |
| 5 | Jiro | Délestage : aller au poteau à la bougie et taper vite pour remettre le courant | TONGA NY JIRO! +20 |
| 6 | Sakafo | Rejoindre la famille sur le tsihy pour le dîner | MIARAKA ISIKA! +20 |

En bonus, 10 étoiles « tsiky » (sourires) sont cachées sur les îles, et le meilleur temps est enregistré sur l'appareil.

## Commandes

| Action | Téléphone | Ordinateur |
|--------|-----------|------------|
| Se déplacer | Joystick à gauche | ZQSD, WASD ou flèches |
| Agir | Gros bouton à droite | Espace, E ou Entrée |
| Sprinter (5 s de recharge) | Bouton 😊 | Maj |
| Couper le son | Bouton 🔊 | Bouton 🔊 |

Une balise lumineuse, une flèche à l'écran et un point sur la mini-carte indiquent toujours l'objectif en cours.

## Lancer le jeu

Le jeu tient dans un seul fichier, sans installation ni étape de compilation.

1. Ouvrir `index.html` dans un navigateur récent (Chrome, Firefox, Safari, Edge).
2. Appuyer sur **ANDAO!**

Une connexion internet est nécessaire au chargement, car three.js et les polices viennent d'un CDN. Pour un usage hors ligne, il suffit de placer `three.min.js` (r128) à côté de `index.html` et de modifier la balise `<script>` correspondante.

Pour le mettre en ligne, n'importe quel hébergement statique convient (GitHub Pages, Netlify, etc.) : il n'y a qu'un fichier à déposer.

## Technique

- **Rendu** : [three.js](https://threejs.org/) r128, caméra orthographique isométrique qui suit le héros, ombres portées, matériaux « toon » en aplats.
- **Décor** : entièrement construit en code à partir de formes simples (aucun modèle 3D ni image externe).
- **Lumière** : quatre ambiances (matin, fin d'après-midi, crépuscule, nuit) avec transitions progressives.
- **Interface** : HTML et CSS par-dessus le canvas — jauge, mini-carte, horloge, notifications, bannières.
- **Son** : musique et effets générés en direct avec la Web Audio API.
- **Sauvegarde** : seul le meilleur temps est conservé, dans le `localStorage` du navigateur (clé `hk_best`).
- **Polices** : Lilita One et Poppins (Google Fonts).

### Organisation du code

Tout est dans `index.html`, découpé en sections commentées :

| Section | Contenu |
|---------|---------|
| `RENDERER` | Scène, caméra, lumières, fonctions de construction des formes |
| `WORLD` | Îles, route, pont, maisons, gargote, rizières, personnages, taxi-be |
| `LIGHTING PRESETS` | Ambiances lumineuses et couleurs du ciel |
| `AUDIO` | Séquenceur musical et effets sonores |
| `INPUT` | Clavier, joystick tactile, boutons |
| `GAME STATE` | Quêtes, score, mini-jeux, récompenses, écran de victoire |
| `LOOP` | Boucle principale : déplacements, collisions, animations, caméra |

Pour ajouter une quête, il faut l'ajouter au tableau `QUESTS` (texte, cible, bouton d'action) puis traiter son action dans `onAction()`.

## État du projet

- Parcours complet vérifié dans un navigateur de test, en format téléphone (390 × 844) et bureau (1280 × 800).
- Pas encore testé sur de vrais téléphones : la fluidité et le confort du joystick restent à confirmer.

Pistes pour la suite : nouvelles quêtes, personnage plus détaillé, mini-jeux plus difficiles, mode hors ligne complet.

## Langues

Les textes du jeu sont en malgache, avec une traduction française en sous-titre.

## Crédits

Conception : Safidy Raharijesy.

L'interface s'inspire des codes visuels des MOBA mobiles, mais tous les éléments du jeu sont originaux.

> *Ny hafaliana kely no tena harena.* — Les petits bonheurs sont la vraie richesse.
