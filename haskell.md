# Haskell

## Stack

`stack new PROJECT TEMPLATE` : créer le projet PROJECT avec le
template TEMPLATE (nécessite une connexion internet)

`stack templates` : lister les templates disponibles (nécessite a
priori une connexion internet)

`stack build` : construire le main
   * `stack build --test` : construire et lancer les tests

`stack test` : synonyme de `stack build --test`
  * `stack test --test-arguments "--match=FOO.BAR"` : pour lancer les
    tests associés au module FOO.BAR
  * `stack test PKG:TESTSUITE` pour lancer les tests de la suite
   TESTSUITE (e.g. : `stack test picrochole:end-to-end`)

`stack clean` : nettoyer les paquets locaux
  * `stack clean --full` : nettoyer l'ensemble du répertoire (i.e. :
    supprimer .stack-work)

`stack ghci` : lancer GHCi
  * `stack ghci --package FOO` : lancer GHCi avec la possibilité
    d'importer le package FOO
  * `stack ghci FOO:lib` : lancer GHCi en important la librairie du
    projet FOO
  * `stack ghci FOO:exe:FOO-EXE` : lancer GHCi en important
    l'exécutable du projet FOO

`stack ide targets` : lister les cibles du projet courant

`stack exec EXE` : lancer l'exécutable EXE
  * `stack exec -- whereis EXE` : pour trouver l'emplacement de EXE

`stack list-dependancies` : lister les dépendances de la cible
  * `stack list-dependancies --test` : lister les dépendances des
     tests

`stack haddock` : générer la documentation Haddock (les logs indiquent
où est créé le fichier HTML correspondant)

`stack upgrade` : mettre à jour stack lui-même

`stack update` : mettre à jour la liste des paquets

`stack-clean-old` : outil bâti sur Stack pour nettoyer les
installations Stack (https://github.com/juhp/stack-clean-old) ; pour
agir sur l'instalation globale, il faut se situer en dehors d'un
projet Stack (par exemple dans ~)
  * `stack-clean-old list` : liste la taille et le nombre de snapshots
    par version de GHC
  * `stack-clean-old remove -d GHCVER` : supprime les snapshots liés à
    la version de GHC GHCVER

## GHCi

`:l FILENAME` : charge (load) le fichier FILENAME

`import qualified MODULE as M` : import qualifié du module MODULE

`:m MODULE` : import non qualifié du module MODULE

`:t VARIABLE` : affiche le type de VARIABLE

`:r` : recharge les sources

`:set OPTION` : active une option, par exemple '-Wall' pour avoir tous
les warnings

`:unset OPTION` : désactive une option

`:i NAME` : affiche des informations sur NAME

`:?` : affiche l'aide

## HLint

`hlint FOLDER -i "Redundant bracket"` : ignorer les suggestions
"Redundant bracket"
