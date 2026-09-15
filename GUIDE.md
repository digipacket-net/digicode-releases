# DigiCode — guide de l'utilisateur

Éditeur de code natif pour macOS, par [Digipacket](https://digipacket.net).
Cette page couvre tout ce que la version 1.0.0 sait faire.

**Français** · [English](GUIDE.en.md)

Une question, un bug, une idée : <https://digipacket.net/contact>.

---

## Sommaire

1. [Installer](#installer)
2. [Premiers pas](#premiers-pas)
3. [L'interface](#linterface)
4. [Raccourcis clavier](#raccourcis-clavier)
5. [La palette de commandes](#la-palette-de-commandes)
6. [Éditer](#éditer)
7. [Explorateur de fichiers](#explorateur-de-fichiers)
8. [Rechercher dans le projet](#rechercher-dans-le-projet)
9. [Terminal](#terminal)
10. [Git](#git)
11. [Project Launcher](#project-launcher)
12. [Écrire sa propre recette](#écrire-sa-propre-recette)
13. [Serveur local](#serveur-local)
14. [Plugins WordPress](#plugins-wordpress)
15. [Réglages](#réglages)
16. [Où DigiCode range ses fichiers](#où-digicode-range-ses-fichiers)
17. [Limites connues](#limites-connues)

---

## Installer

```sh
brew install --cask digipacket-net/tap/digicode
```

Ou téléchargez le `.dmg` depuis
[les releases](https://github.com/digipacket-net/digicode-releases/releases) et
glissez DigiCode dans Applications.

**Configuration requise :** macOS 13 Ventura ou plus récent. L'application est
universelle — native sur Apple Silicon comme sur Intel.

**Téléchargement manuel :** au premier lancement, faites **clic droit → Ouvrir**
plutôt qu'un double-clic. DigiCode est signé mais pas notarié par Apple, et
macOS refuse d'ouvrir une application téléchargée qu'il ne connaît pas. Une
seule fois : les lancements suivants sont normaux. Passer par Homebrew évite
cette étape.

**Désinstaller :** `brew uninstall --cask digicode`, ou jetez
`DigiCode.app` à la corbeille. Pour effacer aussi les données (base de données,
recettes, préférences) : `brew uninstall --zap --cask digicode`.

---

## Premiers pas

1. **Ouvrez un dossier** — ⇧⌘O, ou le bouton de l'écran d'accueil, qui propose
   aussi *Open File…*, *New File*, *New Project from Recipe* et la palette.
   C'est ce qui donne un projet à l'explorateur, à la recherche, à Git et au
   serveur.
2. **Ouvrez un fichier** — cliquez-le dans l'explorateur, ou ⌘P pour le trouver
   par son nom.
3. **Trouvez n'importe quelle commande** — ⇧⌘P, puis tapez. Tout ce que
   DigiCode sait faire est là.

Pas encore de projet ? ⌃⌘N ouvre le **Project Launcher**, qui en crée un —
WordPress, Laravel, React, Vue, Next.js, Node, Python, PHP — en un clic.

---

## L'interface

```
┌──────────────────────────────────────────────────┐
│ ●●●              DigiCode                        │  barre de titre + onglets
├────┬─────────────┬───────────────────────────────┤
│ 📁 │             │  chemin du fichier            │  fil d'Ariane
│ 🔍 │  panneau    ├───────────────────────────────┤
│ ⑂  │  latéral    │                               │
│ ▤  │             │  éditeur                      │
│ 🧩 │             │                               │
│    │             ├───────────────────────────────┤
│ ── │             │  TERMINAL · SERVER · …        │  panneau du bas
│ ⌨  │             │                               │
│ 🔌 │             │                               │
│ ── │             │                               │
│ ⚙  │             │                               │
├────┴─────────────┴───────────────────────────────┤
│ branche ↑2↓0    Swift    Ln 12, Col 4    UTF-8   │  barre d'état
└──────────────────────────────────────────────────┘
```

**Le rail de gauche** a deux groupes, séparés par un filet. Les cinq icônes du
haut changent le **panneau latéral** : Explorateur, Recherche, Source Control,
Project Launcher, Extensions. Les deux du bas ouvrent le **panneau du bas** :
Terminal et Serveur. Un second clic sur la même icône referme le panneau.

**Le panneau du bas** porte les onglets Terminal, Server, Problems et Output —
plus **Plugins** lorsque le projet ouvert est un WordPress.

**La barre d'état** montre la branche Git, son avance et son retard sur le
distant, le nombre de fichiers modifiés, puis le langage du fichier, son
encodage, la position du curseur, la longueur de la sélection et le nombre de
curseurs quand il y en a plusieurs.

Le rail et la barre d'état se masquent dans les réglages (⌘,).

---

## Raccourcis clavier

### Fichiers

| Raccourci | Action                      |
| --------- | --------------------------- |
| ⌘N        | Nouveau fichier             |
| ⌘O        | Ouvrir un fichier           |
| ⇧⌘O       | Ouvrir un dossier de projet |
| ⌘S        | Enregistrer                 |
| ⇧⌘S       | Enregistrer sous            |
| ⌘W        | Fermer l'onglet             |
| ⌘P        | Ouverture rapide par nom    |

### Édition et sélection

| Raccourci | Action                            |
| --------- | --------------------------------- |
| ⌘F        | Rechercher dans le fichier        |
| ⌥⌘F       | Rechercher et remplacer           |
| ⌘G        | Occurrence suivante               |
| ⇧⌘G       | Occurrence précédente             |
| ⎋         | Fermer la barre de recherche      |
| ⌘D        | Ajouter l'occurrence suivante     |
| ⇧⌘L       | Sélectionner toutes les occurrences |
| ⌥⌘↑       | Ajouter un curseur au-dessus      |
| ⌥⌘↓       | Ajouter un curseur en dessous     |
| ⌃Space    | Autocomplétion                    |

### Navigation et panneaux

| Raccourci | Action                        |
| --------- | ----------------------------- |
| ⇧⌘P       | Palette de commandes          |
| ⌘B        | Replier le panneau latéral    |
| ⌘J        | Replier le panneau du bas     |
| ⇧⌘E       | Explorateur                   |
| ⇧⌘F       | Recherche projet              |
| ⌃⇧G       | Source Control                |
| ⇧⌘N       | Project Launcher              |
| ⇧⌘X       | Extensions                    |
| ⌃`        | Terminal                      |
| ⌃⇧`       | Nouvelle session de terminal  |
| ⌃⇧S       | Serveur local                 |
| ⌥⌘Z       | Retour à la ligne             |
| ⌘,        | Réglages                      |

### Projet et Git

| Raccourci | Action                     |
| --------- | -------------------------- |
| ⌃⌘N       | Nouveau projet (launcher)  |
| ⇧⌘R       | Rafraîchir le statut Git   |
| ⌘↵        | Commiter ce qui est indexé |

---

## La palette de commandes

**⇧⌘P** ouvre la palette. Elle liste **55 commandes**, filtrées à la frappe :
taper `opf` trouve « Open Folder… », les initiales suffisent. Les commandes sans
raccourci ne sont accessibles que par là.

Les catégories : **File**, **View**, **Find**, **Selection**, **Editor**,
**Terminal**, **Git**, **Search**, **Project**, **Server**, **Plugins**.

**⌘P** ouvre une palette différente : la recherche de fichier par son nom dans
le projet.

---

## Éditer

L'éditeur est bâti sur TextKit 2, la couche de texte native de macOS.

**Coloration syntaxique** par Tree-sitter, une vraie analyse de la grammaire et
non des expressions régulières, sur **sept langages** : Swift, JavaScript,
Python, PHP, HTML, CSS, JSON. Le langage est reconnu à l'extension du fichier et
affiché dans la barre d'état.

**Multi-curseur.** ⌘D ajoute l'occurrence suivante du mot sélectionné, ⇧⌘L les
prend toutes, ⌥⌘↑ et ⌥⌘↓ empilent des curseurs. Toute frappe s'applique à tous
d'un bloc, et une seule annulation (⌘Z) défait l'ensemble. Un clic ou une flèche
ramène à un seul curseur.

**Recherche dans le fichier.** ⌘F ouvre la barre ; ⌥⌘F ajoute le champ de
remplacement. Trois options : respecter la casse, mot entier, expression
régulière. Le compteur indique « 3 sur 12 ». ⌘G et ⇧⌘G circulent, ⎋ ferme.

En mode expression régulière, le remplacement développe les groupes de capture
(`$1`, `$2`). En mode littéral, tout est pris au pied de la lettre.

**Autocomplétion.** ⌃Space propose les mots du document et les mots-clés du
langage. ↑ ↓ pour choisir, ↵ pour insérer, ⎋ pour abandonner.

**Onglets.** Un onglet par fichier ouvert, un point à côté du nom quand il y a
des modifications non enregistrées.

---

## Explorateur de fichiers

⇧⌘E. L'arborescence du dossier ouvert.

- Un clic ouvre le fichier, un clic sur un dossier le déplie.
- **Clic droit** : *New File…*, *New Folder…*, *Rename…*, *Move to Trash*,
  *Copy Path*, *Reveal in Finder*.
- **Glisser-déposer** pour déplacer un fichier ; les onglets ouverts suivent le
  fichier déplacé ou renommé.
- Un fichier supprimé part à la corbeille, il n'est pas effacé. La confirmation
  se désactive dans les réglages.
- L'en-tête du panneau porte trois boutons : nouveau fichier, nouveau dossier,
  rafraîchir.

---

## Rechercher dans le projet

⇧⌘F. Cherche dans les fichiers, pas seulement dans celui qui est ouvert.

**Trois portées**, choisies par les trois boutons sous le champ :

| Portée         | Ce qui est lu                                 |
| -------------- | --------------------------------------------- |
| **Project**    | tout le dossier ouvert                        |
| **Open File**  | le fichier de l'onglet actif, et lui seul     |
| **Folder**     | un dossier choisi n'importe où sur le disque  |

Les mêmes trois options que la barre de recherche : casse, mot entier,
expression régulière.

**Filtrer les fichiers** — le bouton à droite des options ouvre deux champs,
*inclure* et *exclure*, qui acceptent des motifs séparés par des virgules :
`*.swift`, `src/**`, `*.test.js`. Ces filtres servent à choisir des fichiers
dans une arborescence, ils n'apparaissent donc pas en portée « Open File ».

Les dossiers de construction et de dépendances sont ignorés d'office, et un
fichier binaire est détecté à son premier octet nul plutôt que lu.

**Remplacer partout** — le bouton ✓ à droite du champ de remplacement réécrit
tous les fichiers sur le disque. Une confirmation annonce ce qui va être touché.
C'est irréversible depuis l'éditeur : faites-le sur un projet suivi par Git.

---

## Terminal

⌃` ouvre le panneau, ⌃⇧` crée une session de plus. Ce sont de vrais shells —
`zsh` par défaut, modifiable dans les réglages — démarrés dans le dossier du
projet, avec la couleur, les touches et le redimensionnement qu'attend un
programme en plein écran comme `vim` ou `top`.

Plusieurs sessions vivent côte à côte ; la barre d'onglets du panneau permet d'en
fermer une. Toutes s'arrêtent à la fermeture de l'application.

---

## Git

⌃⇧G. DigiCode appelle le `git` installé sur la machine — pas une
réimplémentation — donc votre configuration, vos identifiants et vos hooks
s'appliquent tels quels.

**Ce que le panneau montre :** la branche et son avance sur le distant, les
fichiers en conflit, ceux qui sont indexés, ceux qui ne le sont pas. Un clic sur
un fichier ouvre son **diff** dans l'éditeur, ligne par ligne.

**Ce qu'il fait :**

- indexer ou désindexer un fichier, ou tout d'un coup ;
- **commiter** — écrivez le message dans le champ, puis ⌘↵ ;
- **changer de branche** ou en créer une, par le menu de la branche ;
- **fetch**, **pull**, **push**. Le pull est en avance rapide seulement
  (`--ff-only`) : un historique divergent est signalé plutôt que fusionné dans
  votre dos.

⇧⌘R relit l'état du dépôt.

---

## Project Launcher

⌃⌘N, ou ⇧⌘N pour le panneau latéral. Crée un projet complet — dossier,
fichiers, dépendances installées — en un clic, puis l'ouvre.

**Les dix recettes livrées :**

| Recette          | Ce qu'elle produit                                       | Outils requis        |
| ---------------- | -------------------------------------------------------- | -------------------- |
| **WordPress**    | le dernier WordPress, prêt pour son installateur          | php, tar, git        |
| **Laravel**      | une application Laravel créée par Composer                | php, composer, git   |
| **PHP**          | un projet PHP vide servi par le serveur intégré de PHP    | php, git             |
| **React**        | une application React sur Vite, avec rafraîchissement à chaud | node, npm        |
| **Vue**          | une application Vue 3 sur Vite                            | node, npm            |
| **Next.js**      | une application Next.js avec l'app router                 | node, npm, npx       |
| **Node · Express** | un serveur HTTP Express avec un script de démarrage     | node, npm, git       |
| **Python**       | un environnement virtuel, un `requirements.txt`, un module | python3, git        |
| **Static Site**  | HTML, CSS et JavaScript, rien à installer                 | git                  |
| **Empty Project**| un dossier, un README et un dépôt Git                     | git                  |

**Options courantes :** la plupart des recettes proposent « Initialiser un dépôt
Git » ; React et Vue proposent **TypeScript** et « installer les dépendances » ;
Node propose d'installer Express ; Python propose l'environnement virtuel.
Décochez ce que vous ne voulez pas.

**Outils manquants.** Le panneau affiche pour chaque recette les outils dont
elle a besoin et lesquels manquent. DigiCode cherche les exécutables dans le
`PATH` de votre shell de connexion, donc Homebrew, nvm ou Herd sont trouvés même
quand l'application est lancée depuis le Finder. Une recette dont il manque un
outil n'est pas lancée : elle le dit avant de créer quoi que ce soit.

**Pendant la création**, une barre de progression et le journal des commandes
défilent. On peut annuler.

---

## Écrire sa propre recette

Les recettes sont des fichiers **YAML** ou **JSON** déposés dans :

```
~/Library/Application Support/DigiCode/Recipes
```

La commande « Open the Recipes Folder » (palette) l'ouvre et le crée au besoin ;
« Reload Project Recipes » relit le dossier. Une recette qui porte le même `id`
qu'une recette livrée la remplace.

### Squelette

```yaml
recipes:
  - id: mon-projet
    name: Mon projet
    summary: Ce que la liste affichera sous le nom.
    category: Web
    symbol: shippingbox        # nom de symbole SF
    requires: [git, npm]       # outils exigés en plus de ceux des étapes
    next:                      # affiché à la fin, une ligne par entrée
      - npm run dev

    options:
      - key: git
        title: Initialiser un dépôt Git
        summary: Explication facultative
        default: true

    steps:
      - title: Créer le dossier public
        mkdir: public

      - title: Écrire la page
        write: public/index.html
        contents: |
          <!doctype html>
          <h1>{{name}}</h1>

      - title: Installer les dépendances
        run: npm
        arguments: [install]

      - title: Initialiser le dépôt
        run: git
        arguments: [init]
        when: git                # seulement si l'option est cochée
```

### Les actions possibles

| Clé        | Ce qu'elle fait                | Clés associées                  |
| ---------- | ------------------------------ | ------------------------------- |
| `run`      | lance un exécutable            | `arguments` (liste)             |
| `mkdir`    | crée un dossier                |                                 |
| `write`    | écrit un fichier               | `contents`                      |
| `download` | télécharge une URL             | `to`                            |
| `extract`  | dépaquette une archive         | `to`, `strip`                   |
| `move`     | déplace un fichier             | `to`                            |
| `delete`   | supprime un fichier            |                                 |

### Les clés communes à toute étape

| Clé        | Effet                                                     |
| ---------- | --------------------------------------------------------- |
| `title`    | ce que le journal affiche                                  |
| `in`       | sous-dossier où l'étape s'exécute                          |
| `when`     | n'exécuter que si cette option est cochée                  |
| `unless`   | n'exécuter que si cette option est **dé**cochée            |
| `optional` | un échec n'interrompt pas la recette                       |

### Variables

`{{name}}` le nom du projet, `{{path}}` son chemin complet, `{{parent}}` le
dossier qui le contient.

### Deux règles de sûreté

Une étape lance un **exécutable et ses arguments**, jamais une ligne de shell :
il n'y a donc rien à échapper et aucune injection possible. Et tout chemin est
résolu à l'intérieur du dossier du projet — une recette qui essaie d'écrire au
dehors est refusée, avant comme après la substitution des variables.

---

## Serveur local

⌃⇧S. Fait tourner un site PHP et une base de données, **sans Docker ni
installation système**.

### Web

La ligne **WEB** sert le projet ouvert sur `127.0.0.1:8000` par le serveur
intégré de PHP. Le dossier servi est `public/` s'il existe — c'est le cas de
Laravel — et la racine du projet sinon, comme pour WordPress.

PHP n'est pas téléchargé : DigiCode utilise celui de votre machine (Herd,
Homebrew ou le système) et affiche `brew install php` s'il n'en trouve aucun.

### Base de données

La ligne **DATABASE** installe MySQL d'un clic : environ 180 Mo téléchargés une
seule fois dans le dossier de l'application. Rien n'est posé sur le système, et
le menu `…` de la ligne sait tout supprimer.

- **Copy** met l'hôte, le port, l'utilisateur et le mot de passe dans le
  presse-papiers, à coller dans TablePlus, Sequel Ace ou DBeaver. La connexion
  est `127.0.0.1`, port **33060**, utilisateur **digicode**.
- **Le menu `…`** exporte une base vers un fichier `.sql` (`mysqldump`, en une
  seule transaction) à l'endroit de votre choix.

Le serveur n'écoute que la boucle locale, `root` a un mot de passe aléatoire
joignable seulement par le socket, et les fichiers d'identifiants sont en `0600`.

### WordPress

Quand le projet ouvert est un WordPress sans `wp-config.php`, une bande propose
**Set it up** : la base est créée, le fichier écrit avec ses huit sels tirés au
hasard. Il ne reste qu'à ouvrir le site et remplir le formulaire d'installation.

### Retrouver son serveur

Ce qui tournait pour un projet est noté. **Rouvrir le dossier relance la base et
le serveur web, sur le même port**, pour que le lien que vous aviez gardé
réponde encore. Un serveur que vous arrêtez exprès reste arrêté.

---

## Plugins WordPress

Lorsque le projet ouvert est un WordPress, un onglet **Plugins** apparaît à côté
de Serveur. Il liste les plugins publiés par Digipacket et les installe dans
`wp-content/plugins` d'un clic : Backup Toolkit, Login Security, Partner for
WooCommerce, Republish AI.

Le bouton devient **Reinstall** et **Remove** pour un plugin déjà présent, et le
bandeau indique la version installée. Réinstaller remplace, ça ne double pas.

Après l'installation, activez le plugin dans l'administration WordPress comme
d'habitude.

---

## Réglages

⌘, — cinq volets.

**Appearance :** thème de couleurs, afficher ou non le rail d'activité et la
barre d'état.

**Editor :** police et taille, hauteur de ligne, largeur de tabulation (2, 4 ou
8), espaces au lieu de tabulations, conserver l'indentation à la ligne suivante,
numéros de ligne, surbrillance de la ligne courante, retour à la ligne. Un
bouton remet les valeurs par défaut.

**Terminal :** chemin du shell, taille de police.

**Key Bindings :** la liste des raccourcis en vigueur. Elle se lit, elle ne se
modifie pas encore.

**Extensions :** l'emplacement où DigiCode ira les chercher.

> **Les réglages ne sont pas encore conservés d'une session à l'autre.** Ils
> reprennent leurs valeurs par défaut à chaque lancement. C'est la phase 9 du
> développement.

---

## Où DigiCode range ses fichiers

Tout est sous `~/Library/Application Support/DigiCode/` :

| Chemin                    | Contenu                                        |
| ------------------------- | ---------------------------------------------- |
| `Servers/mysql/`          | MySQL, ses données et ses identifiants          |
| `Recipes/`                | vos recettes de projet                          |
| `Extensions/`             | les extensions, à venir                         |
| `server-session.json`     | ce qui tournait pour chaque projet              |
| `plugin-catalogue.json`   | la liste des plugins, en cache une heure        |

Supprimer ce dossier remet DigiCode à neuf sans toucher à vos projets.

---

## Limites connues

Dites plutôt que cachées.

- **Les réglages ne persistent pas** entre deux lancements (phase 9).
- **Les panneaux Extensions, Problems et Output** affichent un badge `PREVIEW` :
  ils montrent des données d'exemple. Le registre d'extensions arrivera avec un
  format d'extension publié.
- **Pas de notarisation Apple.** L'application est signée mais Apple ne l'a pas
  contresignée, faute de certificat payant. Homebrew s'en occupe ; un
  téléchargement manuel demande un clic droit → Ouvrir la première fois.
- **MySQL plutôt que MariaDB.** MariaDB ne publie plus de binaires macOS ; MySQL
  Community parle le même protocole et est ce à quoi WordPress et Laravel se
  connectent.
- **`pull` en avance rapide seulement.** Une divergence est signalée, pas
  fusionnée automatiquement.

---

## Une question ?

<https://digipacket.net/contact>

DigiCode est développé par **Digipacket**.
