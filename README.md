# PocketTables

Apprendre les tables de multiplication jusqu’au réflexe, et s’entraîner au calcul mental.

PocketTables est une web app minimaliste pensée pour le téléphone. Elle s’installe sur l’écran d’accueil, s’ouvre en plein écran et fonctionne hors ligne. Il n’y a ni compte, ni serveur, ni dépendance : un seul fichier HTML.

## Ce que fait l’app

### Tables de multiplication

**La grille de maîtrise.** L’écran d’accueil affiche toute la table, de 2 à 10, 12 ou 20. Chaque case prend une couleur selon ton niveau sur ce fait : à revoir, en cours, solide ou réflexe. Touche une case pour voir le fait, sa stratégie, tes statistiques et la date de la prochaine révision.

**Apprendre.** Une suite de leçons, chacune consacrée à une stratégie :

- ×10, ×2, ×5 servent d’appuis.
- Le reste se déduit de ces appuis :
  - ×4 = double du double ;
  - ×9 = dix fois moins une fois ;
  - ×3 = double plus une fois ;
  - les carrés et leurs voisins, (n − 1)(n + 1) = n² − 1 ;
  - ×6 = cinq fois plus une fois ;
  - ×8 = trois doublements ;
  - ×7, qu’on obtient presque entièrement par commutativité.
- Pour les grands nombres : ×11, ×12, de 13 à 19 fois un chiffre, deux nombres entre 11 et 19, puis ×15, ×19 et ×20.

Chaque leçon propose des exemples qui se déroulent étape par étape. L’exercice guidé affiche la stratégie pendant la première moitié des questions, puis la retire. Les faits ratés et les tables les moins sûres sont mémorisés et regroupés dans la section « À retravailler ».

**S’entraîner.** Six approches :

| Mode | Principe |
|---|---|
| Adaptatif | Répétition espacée : faits dus, points faibles et quelques nouveaux, mélangés. C’est le mode recommandé au quotidien. |
| Bilan | Chaque fait jamais vu, une fois, pour calibrer la grille. |
| Une table | Pratique ciblée, dans le désordre. |
| Familles | Le même fait sous trois formes : 7 × 8, 7 × ? = 56 et 56 ÷ 7. |
| Points faibles | Les faits ratés ou lents, chacun deux fois. |
| Sprint 60 s | Un maximum de bonnes réponses en une minute. Facultatif. |

### Calcul mental

Cinq types de calcul, en trois niveaux, plus un mode mélange :

- **Puissances** : carrés, cubes, puissances de 2, 3, 5 et 7.
- **Grandes multiplications** à décomposer : découpage, arrondi, m² − d², ×11, ×25, ×125.
- **Additions** : de gauche à droite ou par compensation.
- **Soustractions** : compensation, compter en avançant, retirer par morceaux.
- **Modulo** : derniers chiffres, puissances de 2, somme des chiffres pour mod 3, 9 et 11, multiples ronds. Les nombres négatifs sont inclus, avec la différence de convention entre Python et C/Java/JavaScript.

Après une erreur, la décomposition complète s’affiche. Chaque type a sa fiche de techniques, et l’app signale celui où tu réussis le moins.

### Saisie et gestes

- Le pavé numérique est intégré à l’app. La réponse est validée dès qu’elle a le bon nombre de chiffres ; ce comportement est désactivable.
- Glisser vers la gauche pour passer, vers le haut pour un indice, et depuis le bord gauche pour revenir en arrière.
- Au clavier d’ordinateur : les chiffres, Entrée, ← pour passer, ↑ pour un indice, Échap pour quitter.

## La méthode

L’app applique les principes sur lesquels la recherche sur la mémoire et l’apprentissage des faits arithmétiques converge.

1. **Comprendre avant de mémoriser.** Les stratégies dérivées rendent chaque fait reconstructible, puis la pratique l’automatise.
2. **Se tester plutôt que relire.** Chaque question demande de produire la réponse, sans choix multiple.
3. **Espacer.** Chaque fait a un niveau de 0 à 5, comme dans les boîtes de Leitner. Une réponse juste et rapide le fait monter, une erreur le ramène à 0. Les révisions suivantes ont lieu après 10 min, 1 jour, 3 jours, 7 jours, puis 21 jours.
4. **Mélanger.** L’entraînement adaptatif mélange les tables au lieu de les réviser une par une.
5. **Réussir souvent.** Les faits fragiles sont glissés entre des faits sûrs, environ un pour deux.
6. **Corriger tout de suite.** Après une erreur, on recopie la bonne réponse, et le fait revient quelques questions plus tard dans la même séance.
7. **Mesurer la vitesse sans mettre la pression.** Un fait est « réflexe » quand il est juste en moins de 3 s, de façon répétée. Ce seuil est réglable. Le temps est mesuré sans être affiché, et le sprint reste facultatif.

Références : Baroody (2006) ; Roediger et Karpicke (2006) ; Leitner (1972) ; Cepeda et al. (2006) ; Rohrer et Taylor (2007) ; Burns (2005) ; Skinner, McLaughlin et Logan (1997) ; Ramirez et al. (2013) ; Boaler (2014).

## Installation

### Sur iPhone

1. Ouvre le site dans Safari.
2. Touche Partager, puis « Sur l’écran d’accueil ».
3. L’app s’ouvre désormais en plein écran et fonctionne hors ligne.

### Sur Android ou ordinateur

Dans Chrome ou Edge, utilise « Installer l’application » dans le menu ou dans la barre d’adresse.

## Déploiement sur GitHub Pages

1. Place les fichiers à la racine du dépôt.
2. Va dans Settings, puis Pages, puis Build and deployment.
3. Choisis « Deploy from a branch », avec la branche `main` et le dossier `/ (root)`.
4. Le site est servi à l’adresse `https://<pseudo>.github.io/<dépôt>/`.

### Mettre à jour

Après une modification, change la constante `VERSION` dans `sw.js`, par exemple `pockettables-v2`. Sans cette étape, l’app installée peut continuer à servir l’ancienne version depuis son cache.

## Données

La progression est enregistrée dans le `localStorage` du navigateur, sur l’appareil uniquement. Les Réglages permettent de l’exporter en JSON, de l’importer sur un autre appareil ou de l’effacer. Rien n’est envoyé à un serveur.

La seule ressource externe est la police STIX Two Text, chargée depuis Google Fonts puis mise en cache. Sans réseau, l’app utilise la police serif du système.

## Fichiers

```
index.html             l’app complète (HTML, CSS et JavaScript)
manifest.webmanifest   nom, icônes, affichage plein écran
sw.js                  service worker : cache hors ligne
icon-192.png           icônes de l’app
icon-512.png
apple-touch-icon.png   icône de l’écran d’accueil iOS
```

## Réglages disponibles

| Réglage | Valeurs |
|---|---|
| Tables jusqu’à | 10, 12 ou 20 |
| Seuil réflexe | 2, 3 ou 4 s (+2 s par facteur au-delà de 12) |
| Questions par séance | 10, 20 ou 30 |
| Validation | automatique ou avec ✓ |
| Thème | auto, clair ou sombre |

## Technique

L’app est écrite en HTML, CSS et JavaScript, sans framework ni étape de compilation. Côté navigateur, elle s’appuie sur Web Animations, les Pointer Events et un service worker. Elle respecte le thème clair ou sombre du système et le réglage « réduire les animations ».
