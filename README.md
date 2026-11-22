# QCM IRA - entraînement

Application d'entraînement au QCM du concours des IRA (instituts régionaux d'administration), qui fonctionne sans connexion et sans installation.

- 928 questions des annales officielles corrigées (sessions 2020-2 à 2024)
- 239 questions sur le système éducatif français (QCM des fiches de révision et questions complémentaires tirées de leur contenu, avec explications)
- Révision espacée (séance du jour), entraînement ciblé, examens blancs chronométrés au barème officiel (+1 / -0,5 / 0), reprise des erreurs, série sans faute
- Les questions identiques ou très proches d'une annale à l'autre ne tombent jamais dans la même séance

## Contenu du dossier

| Fichier | Rôle |
|---|---|
| `index.html` | L'application (interface et logique) |
| `questions.js` | La banque de questions, une question par ligne |
| `.nojekyll` | Fichier vide utile à GitHub Pages, à laisser tel quel |
| `README.md` | Cette notice |

## 1. Utiliser l'appli sur ton ordinateur

1. Télécharge le dossier (sur GitHub : bouton vert **Code**, puis **Download ZIP**) et décompresse-le.
2. Double-clique sur `index.html` : l'appli s'ouvre dans ton navigateur, même sans internet.

`index.html` et `questions.js` doivent rester dans le même dossier.

## 2. Publier l'appli sur GitHub Pages (sans ligne de commande)

1. Crée un compte sur [github.com](https://github.com) si tu n'en as pas.
2. En haut à droite, **+** puis **New repository**. Nom : `qcm-ira`. Choisis **Public** (avec un compte gratuit, GitHub Pages ne publie que les dépôts publics ; voir la section 5 avant de choisir). Clique sur **Create repository**.
3. Sur la page du dépôt, clique sur **uploading an existing file** (ou **Add file** puis **Upload files**), glisse-dépose `index.html`, `questions.js`, `README.md` et `.nojekyll`, puis **Commit changes**.
   - Sur Mac et Linux, `.nojekyll` est un fichier caché : s'il n'apparaît pas, tu peux t'en passer, l'appli fonctionnera quand même.
4. Va dans **Settings** puis **Pages**. Dans **Build and deployment**, choisis **Deploy from a branch**, branche `main`, dossier `/ (root)`, puis **Save**.
5. Une à deux minutes plus tard, l'adresse de ton appli s'affiche en haut de cette page, sous la forme `https://ton-identifiant.github.io/qcm-ira/`. Elle marche aussi sur téléphone.

## 3. Ajouter ou corriger des questions

Tout se passe dans `questions.js`. Sur github.com, ouvre le fichier, clique sur le crayon (**Edit this file**), modifie, puis **Commit changes**. Le site se met à jour en une minute environ.

Chaque question tient sur une ligne et se termine par une virgule (sauf la toute dernière avant `];`) :

```js
{"id":"PERSO-1","y":"Mes questions","s":"jur","q":"Le Défenseur des droits est :","o":["une autorité administrative indépendante","une autorité constitutionnelle indépendante","un service du ministère de la Justice"],"a":1,"x":"Article 71-1 de la Constitution, depuis 2008."},
```

| Champ | Obligatoire | Contenu |
|---|---|---|
| `id` | oui | Identifiant unique. Ne jamais modifier celui d'une question existante : la progression y est rattachée. |
| `y` | oui | Source affichée et utilisée dans les filtres : `2024`, `Fiche 3`, `Mes questions`… |
| `s` | oui | Matière : `jur` (culture administrative et juridique), `fin` (finances publiques), `ue` (institutions européennes), `num` (culture numérique), `edu` (système éducatif) |
| `q` | oui | L'énoncé |
| `o` | oui | Les réponses proposées, entre 2 et 4, entre crochets |
| `a` | oui | Position de la bonne réponse **en partant de 0** : `0` pour A, `1` pour B, `2` pour C, `3` pour D |
| `x` | non | Explication affichée après la réponse |
| `f` | non | Titre de la fiche, affiché à côté de la source |
| `g`, `t` | non | Regroupement des questions proches (calculé automatiquement, inutile pour tes ajouts) |

Points d'attention :
- Les guillemets droits `"` à l'intérieur d'un texte doivent être écrits `\"`. Les apostrophes `'` et les guillemets français « » ne posent aucun problème.
- Si une ligne est mal écrite, l'appli l'ignore et l'indique en haut de l'accueil (« question mal formée ignorée »), le reste continue de marcher. Si l'appli affiche qu'elle ne trouve plus les questions, c'est en général une virgule oubliée ou en trop : annule ta dernière modification (onglet **History** du fichier).

## 4. Ta progression

Elle est enregistrée dans le navigateur, séparément pour chaque adresse : la version GitHub Pages, le fichier ouvert en local et la version sur claude.ai ont chacune la leur.

- Pour ne rien perdre : **Réglages et sauvegarde**, puis **Enregistrer une sauvegarde (fichier)**. Un rappel s'affiche si ta dernière sauvegarde date de plus de 7 jours.
- Pour passer d'une version à l'autre ou d'un appareil à l'autre : sauvegarde d'un côté, **Restaurer depuis un fichier** de l'autre.
- Effacer les données de navigation efface la progression.

## 5. Droits sur les contenus

- Les sujets et corrigés du QCM des IRA sont des documents officiels publiés par l'administration.
- Les questions sur le système éducatif reprennent des **fiches de révision distribuées en préparation**. Avant de rendre le dépôt public, vérifie que leur auteur l'accepte. Sinon, deux solutions : garder le dépôt **privé** et utiliser l'appli en local (section 1), ou retirer de `questions.js` les lignes dont `"s":"edu"` avant de publier.
