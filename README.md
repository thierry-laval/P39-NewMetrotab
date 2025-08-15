# ![left 100%](https://raw.githubusercontent.com/thierry-laval/archives/master/images/logo-portfolio.png "Un bien beau logo !")

## Auteur

👤 &nbsp; **Thierry LAVAL** [🇫🇷 Contactez-moi 🇬🇧](mailto:contact@thierrylaval.dev)

* Github: [@Thierry Laval](https://github.com/thierry-laval)  
* LinkedIn: [@Thierry Laval](https://www.linkedin.com/in/thierry-laval)  
* Visitez ==> 🏠 [Site Web](https://thierrylaval.dev)

***

### 📎 Projet : P39-NewMetrotab

_`Projet basé sur new-metrotab abandonné`_

![Présentation NewMetrotab](https://github.com/thierry-laval/P00-mes-archives/blob/master/images/new-metrotab-v3.jpg?raw=true "Capture d'écran de l'extension")

***

### Table des matières

1. [À propos](#-à-propos)
2. [Fonctionnalités](#-fonctionnalités-principales)
3. [Installation](#-installation)
4. [Utilisation](#-usage)

***

### 🧩 À propos

Ce projet est une version remise à jour et améliorée de [new-metrotab](https://github.com/frabarz/new-metrotab), un plugin Chrome désormais abandonné par son auteur, [frabarz](https://github.com/frabarz).

Cette extension, malgré le fait que ce soit probablement la meilleure dans son genre, a été supprimée du Chrome Web Store et personne ne la maintient plus.

Je n'ai pas vocation à me l'approprier ni à en revendiquer la propriété. Cependant, comme c'est celle que j'utilise personnellement, j'ai décidé de la mettre à jour et de la maintenir autant que possible sur mon temps libre.

Je travaille sur ce fork traduit et amélioré afin de réparer et maintenir le plugin, notamment pour permettre la réalisation de sauvegardes :  
[https://github.com/thierry-laval/new-metrotab](https://github.com/thierry-laval/new-metrotab)

J'intégrerais ces réparations dans ce plugins.  
Chrome n'accepte plus les extensions en Manifest V2, je la passe donc en V3.

***

### 🎯 Fonctionnalités principales

* Compatibilité avec Chrome manifest v3

* Correction de bugs critiques

* Ajout de fonctionnalités mineures

* Optimisation des performances

***

### 📥 Installation

**Je ne pense pas la lister sur la boutique Chrome. Donc, si vous voulez la télécharger et l'utiliser :**

1. Téléchargez le référentiel (clone ou zip) et placez-le dans un emplacement statique sur votre machine (attention, vous **ne pouvez pas déplacer le dossier après l'avoir ajouté à Chrome**)
2. Ouvrez la page des extensions Chrome : `chrome://extensions/`
3. Activez le **mode développeur** (en haut à droite)
4. Cliquez sur **« Charger déballé »**
5. Sélectionnez le dossier contenant le référentiel (le dossier avec le numéro de version, par exemple `1.1.0_0`)
6. Activez l'extension, c'est prêt !

***

### 🖱 Usage

#### À quoi sert cette extension ?

Ce plugin remplace la page des nouveaux onglets Chrome par un tableau de bord personnalisable avec :

* Vos sites/webapp favoris sous forme de tuiles
* Un design épuré et organisable
* Une intégration native avec Chrome

#### Utilisation de base

1. **Ajouter une tuile** :
   * Cliquez sur le bouton "+" en haut à droite
   * Entrez l'URL et un nom
   * Choisissez une icône (optionnel)

2. **Organiser** :
   * Glissez-déposez pour réarranger
   * Clic droit sur une tuile pour les options

3. **Paramètres** :
   * Accès via l'icône ⚙️ en bas à droite
   * Personnalisation du fond d'écran
   * Choix du thème (clair/sombre)

#### Raccourcis utiles

* `Alt+M` : Recherche rapide
* `Ctrl+N` : Basculer mode nuit

***

### Comment sauvegarder les réglages du plugin ?

Les tuiles sont stockées dans la base de données indexée du navigateur, accessible par l'extension.

**Attention :** La procédure suivante exécute un script dans le contexte de la page.  
Ne l'exécutez pas sur d'autres sites (Facebook, messagerie, etc.) sans savoir précisément ce que fait le code.

#### Étapes 01 pour télécharger la sauvegarde des tuiles :

1. Ouvrez les options du plugin (survolez le badge utilisateur > Options)  
2. Faites un clic droit n'importe où sur la page des options, puis sélectionnez **Inspecter** (souvent en dernier dans le menu)  
3. Dans le panneau qui s'ouvre, sélectionnez l'onglet **Console**  
4. Collez ce code :

```js

MT.miniDB.cursor().then(tiles => {
  const blob = new Blob([JSON.stringify(tiles, null, 2)], {type: "application/json"});
  const anchor = document.createElement("a");
  anchor.href = window.URL.createObjectURL(blob);
  anchor.download = "metrotab_tiles.json";
  anchor.click();
});

```

Appuyez sur Entrée pour exécuter le script

La boîte de dialogue de téléchargement s'affiche, sauvegardez le fichier

#### Étapes 02 sauvegarder les autres options ?

Effectuez la même procédure, puis collez ce code dans la console :

```js
(function() {
  const config = {
    "instalado": localStorage.getItem("instalado"),
    "bloques_info": localStorage.getItem("bloques_info"),
    "apar_bgcolor": localStorage.getItem("apar_bgcolor"),
    "apar_bgimg": localStorage.getItem("apar_bgimg"),
    "livet_clima_ubic": localStorage.getItem("livet_clima_ubic"),
    "livet_da_include": localStorage.getItem("livet_da_include"),
    "livet_zonahora": localStorage.getItem("livet_zonahora"),
  };
  document.querySelectorAll('.autosave').forEach(node => {
    const value = localStorage.getItem(node.name);
    if (value) {
      Object.defineProperty(config, node.name, {value});
    }
  });

  const blob = new Blob([JSON.stringify(config, null, 2)], {type: "application/json"});
  const anchor = document.createElement("a");
  anchor.href = window.URL.createObjectURL(blob);
  anchor.download = "metrotab_config.json";
  anchor.click();
})();

```

***

#### 📦 &nbsp; Technologies utilisées

| Langages/Technos | Outils/Applications |
|:----------------:|:-------------------:|
|      HTML5       | Visual Studio Code  |
|       CSS3       |     Git/GitHub      |
|    JavaScript    |  Chrome Web Store   |
|   Manifest V3    |                     |

***

### 🌟 &nbsp; Améliorations possibles

<details>
<summary>📌 Voir la liste des améliorations</summary>

- [x] **Compatibilité Manifest V3** (implémentée)
- [ ] Internationalisation (i18n)
- [ ] Thèmes personnalisables
- [ ] Synchronisation cloud
- [ ] Documentation améliorée

</details>

<div style="background: #f8f9fa; padding: 1rem; border-radius: 0.5rem; margin: 1rem 0;">
💡 <strong>Comment contribuer ?</strong><br>
1. Forkez le projet<br>
2. Créez une branche (<code>git checkout -b ma-fonctionnalite</code>)<br>
3. Commitez (<code>git commit -am 'Ajout cool'</code>)<br>
4. Pushez (<code>git push origin ma-fonctionnalite</code>)<br>
5. Ouvrez une Pull Request
</div>

***

### 📝 &nbsp; Licence

![License MIT](https://img.shields.io/badge/License-MIT-blue.svg)  
Copyright © 2025 [Thierry Laval](https://thierrylaval.dev)

***

### 💖 &nbsp; Soutien

<a href="https://paypal.me/thierrylaval01" target="_blank" style="display: inline-block; margin-right: 1rem;">
  <img src="https://www.paypalobjects.com/digitalassets/c/website/logo/full-text/pp_fc_hl.svg" height="40">
</a>

***

### ♥ &nbsp; Love Markdown

<span style="font-family: Papyrus; font-size: 2em; color: #ff6b6b;">FAN DE GITHUB !</span>

<a href="#">
  <img src="https://github.com/thierry-laval/P00-mes-archives/blob/master/images/octocat-oley.png" width="300">
</a>

**[⬆ Retour en haut](#auteur)**
