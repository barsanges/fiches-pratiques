# Clojure

[Feuille de référence
officielle](https://www.clojure.org/api/cheatsheet)

## REPL

`(clojure.repl/doc foo)` : afficher la documentation de `foo`

`(clojure.repl/find-doc "foo")` : rechercher les variables et les documentations qui
contiennent `"foo"`

`(clojure.repl/dir foo)` : afficher les variables du namespace `foo`

`(clojure.repl/source foo)` : afficher le code source de `foo`

## [Cider](https://docs.cider.mx/cider/index.html)

`M-x cider-jack-in` : lancer un REPL dans le projet auquel
appartient le fichier courant

`C-c M-n M-r` (`cider-ns-refresh`) : recharger l'ensemble des espaces
de noms

`C-c C-k` : recharger le script courant

`C-c C-z` : passer d'un fichier Clojure au REPL et inversement

`M-p` (`cider-repl-previous-input`) : réécrire la ligne précédente

`C-c M-n M-n` : charger le namespace du fichier courant dans le REPL
