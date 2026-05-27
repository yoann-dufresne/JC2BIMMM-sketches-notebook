# TP — *Sketches* pour comparer des génomes

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/yoann-dufresne/JC2BIMMM-sketches-notebook/blob/main/TP_sketches.ipynb)
[![License: AGPL v3](https://img.shields.io/badge/License-AGPL_v3-blue.svg)](https://www.gnu.org/licenses/agpl-3.0)

Travaux pratiques de l'**école d'été JC2BIMMM**.

Comparer deux génomes revient souvent à comparer leurs ensembles de **k-mers**
(les sous-mots de longueur *k*), à l'aide de l'**indice de Jaccard** :

```
J(A, B) = |A ∩ B| / |A ∪ B|
```

Le problème : l'ensemble des k-mers d'un génome est **énorme**. Les *sketches*
permettent de n'en garder qu'un petit **sous-échantillon** suffisant pour
*estimer* le Jaccard avec très peu de mémoire — c'est le principe d'outils comme
*Mash* ou *sourmash*.

Le but de ce TP est que **vous codiez vous-mêmes** ces sketches. Tout le reste
(lecture des séquences, hachage, jeux de données, mesures) est fourni dans le
notebook.

## 🚀 Démarrer

### Option 1 — En local avec Jupyter (recommandé)

```bash
# 1. Récupérer le notebook
git clone https://github.com/yoann-dufresne/JC2BIMMM-sketches-notebook.git
cd JC2BIMMM-sketches-notebook

# 2. Installer les dépendances (Python 3.8+)
pip install jupyterlab numpy matplotlib

# 3. Lancer Jupyter
jupyter lab TP_sketches.ipynb
```

Aucune autre dépendance : tout le code repose sur la bibliothèque standard de
Python (`numpy`/`matplotlib` servent uniquement aux graphiques).

### Option 2 — Google Colab (si l'installation locale ne fonctionne pas)

Si vous ne parvenez pas à installer Jupyter, ouvrez le notebook directement dans
votre navigateur, sans rien installer : cliquez sur le badge **« Open in
Colab »** ci-dessus, ou ouvrez ce lien :

<https://colab.research.google.com/github/yoann-dufresne/JC2BIMMM-sketches-notebook/blob/main/TP_sketches.ipynb>

Puis faites une copie dans votre Drive (`Fichier ▸ Enregistrer une copie dans
Drive`) pour conserver votre travail.

## 📋 Déroulé du TP

Le notebook est auto-suffisant : exécutez les cellules dans l'ordre. Les
cellules marquées `# TODO` contiennent un sketch à compléter (elles lèvent une
erreur tant qu'elles ne sont pas implémentées). Après chaque sketch, une cellule
de **vérification** compare votre estimation au Jaccard exact.

| # | Section | Ce que vous codez |
|---|---------|-------------------|
| 1 | Outils fournis (k-mers, hachage, données) | *rien — fourni* |
| 2 | Jaccard exact avec tous les k-mers (`AllKmers`) | *rien — fourni (référence)* |
| 3 | La fonction de hachage : à quoi sert-elle ? | *rien — discussion* |
| 4 | **Bottom-s MinHash** (`Smallers`) | `add_kmers` ( + bonus `heapq`) |
| 5 | **Partition MinHash** (`Partitions`) | `add_kmers` et `jaccard` |
| 6 | *(bonus avancé)* **HyperMinHash** (`HyperMin`) | `add_kmers` et `jaccard` |

Chaque sketch est introduit par un **schéma avec un mini-exemple concret**.

## 🧬 Données

Le notebook **fabrique** des génomes synthétiques de parenté contrôlée (un
ancêtre, deux descendants plus ou moins divergents, un génome indépendant) :
pas besoin de télécharger quoi que ce soit, et les résultats sont reproductibles.

Une fonction `load_ncbi_fasta(accession)` est fournie en fin de notebook pour,
si vous le souhaitez, tester vos sketches sur de **vrais génomes** (ex.
SARS-CoV-2 `NC_045512.2`, bactéries `NZ_CP050202.1`, …).

## ✅ Corrigé

Une version corrigée (avec les implémentations et les sorties d'exécution) est
disponible sur la branche **`correction`** :

```bash
git checkout correction   # fichier TP_sketches_solutions.ipynb
```

ou directement : <https://github.com/yoann-dufresne/JC2BIMMM-sketches-notebook/tree/correction>

## 📚 Pour aller plus loin

- **Temps & mémoire réels.** Hors notebook, préfixez une commande par
  `/usr/bin/time -v` pour lire le *Elapsed time* et le *Maximum resident set size*.
- **Complexité.** Quel est le coût de chaque stratégie en fonction de *s* (taille
  du sketch), *k* (taille des k-mers) et *n* (taille de la séquence) ?
- **HyperMinHash.** L'idée d'encoder les zéros de tête + quelques bits de poids
  faible, et de la combiner au partitionnement, est au cœur des travaux récents
  sur les sketches compressés.

## ✍️ Auteur & licence

Auteur : **Yoann Dufresne**.

Ce TP s'inspire largement du billet de blog de **Camille Marchet**,
[*Sketching for set comparison in bioinformatics*](https://kamimrcht.github.io/webpage/sketch.html)
(2022) — une excellente lecture pour approfondir les variantes de MinHash.

Ce matériel pédagogique est distribué sous licence **GNU Affero General Public
License v3.0** (AGPL-3.0). Voir le fichier [`LICENSE`](LICENSE).

> Copyright (C) 2026 Yoann Dufresne
>
> This program is free software: you can redistribute it and/or modify it under
> the terms of the GNU Affero General Public License as published by the Free
> Software Foundation, either version 3 of the License, or (at your option) any
> later version. This program is distributed in the hope that it will be useful,
> but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY
> or FITNESS FOR A PARTICULAR PURPOSE. See the GNU Affero General Public License
> for more details.
