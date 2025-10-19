# Pandoc

`pandoc ORIGIN.md -o DEST.tex` : convertir un fichier Markdown en un
fichier Latex

`pandoc ORIGIN.md -o DEST.tex -r markdown-auto_identifiers
--shift-heading-level-by=-1` : convertir un fichier Markdown en un
corps de fichier Latex (i.e. : sans préambule)
  * `-r markdown-auto_identifiers` : supprimer les hyperliens ajoutés
    par Pandoc
  * `--shift-heading-level-by=-1` : supprimer le niveau 1 du plan
    (`#`, généralement le titre du document Markdown) et remonter d'un
    cran les autres niveaux (`##` correspond alors à `\section`)
