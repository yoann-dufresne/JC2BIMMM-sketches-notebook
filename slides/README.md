# Slides du TP « sketches »

Support de cours (Beamer, thème *Metropolis*) accompagnant le notebook
`TP_sketches.ipynb`. Quatre parties :

1. Énumérer les k-mers (sous-chaînes → entiers sur 64 bits) ;
2. Hachage & **Bottom-*s* MinHash** (set, puis tas) ;
3. **Partition sketch** (slots indépendants, comparaison sans tri) ;
4. **HyperMin** (compression 16 bits, compromis mémoire / qualité).

`slides_precision.tex` est une **annexe expérimentale** sur la *précision* de
l'estimation de Jaccard : modèle binomial, variance `J(1−J)/s`, loi en `1/√s`
(figure pgfplots), distance de Mash, compromis mémoire/précision. Fondée sur la
revue de C. Marchet et les articles cités (Broder ; Li & König ; Flajolet *et al.* ;
Ondov *et al.*/Mash ; Yu & Weber/HyperMinHash ; Baker & Langmead/Dashing).

## Compilation

Nécessite **XeLaTeX** (le thème Metropolis utilise la police Fira ;
l'annexe utilise aussi `pgfplots`) :

```sh
make            # produit slides.pdf ET slides_precision.pdf
make clean      # supprime les fichiers temporaires
```

ou directement :

```sh
latexmk -xelatex slides.tex
latexmk -xelatex slides_precision.tex
```

Les schémas sont inspirés du billet de blog de Camille Marchet,
<https://kamimrcht.github.io/webpage/sketch.html> (autorisation accordée).
