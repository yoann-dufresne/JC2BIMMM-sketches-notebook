# Slides du TP « sketches »

Support de cours (Beamer, thème *Metropolis*) accompagnant le notebook
`TP_sketches.ipynb`. Quatre parties :

1. Énumérer les k-mers (sous-chaînes → entiers sur 64 bits) ;
2. Hachage & **Bottom-*s* MinHash** (set, puis tas) ;
3. **Partition sketch** (slots indépendants, comparaison sans tri) ;
4. **HyperMin** (compression 16 bits, compromis mémoire / qualité).

## Compilation

Nécessite **XeLaTeX** (le thème Metropolis utilise la police Fira) :

```sh
make            # produit slides.pdf
make clean      # supprime les fichiers temporaires
```

ou directement :

```sh
latexmk -xelatex slides.tex
```

Les schémas sont inspirés du billet de blog de Camille Marchet,
<https://kamimrcht.github.io/webpage/sketch.html> (autorisation accordée).
