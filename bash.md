# Bash

## Langage

`cmd ARGS &` : lancer la commande `cmd` et rendre la main dans le
terminal courant

`cmd <SYMBOLE> FILE` : pour rediriger les sorties
  * `* >` : redirige la sortie standard de `cmd` vers le fichier
    `FILE` (en écrasant son contenu éventuel)
  * `>>` : redirige la sortie standard de `cmd` à la fin du fichier
    `FILE`
  * `2>` : redirige la sortie d'erreurs de `cmd` vers le fichier
    `FILE` (en écrasant son contenu éventuel)
  * `2>>` : redirige la sortie d'erreurs de `cmd` à la fin du fichier
    `FILE`
  * `2>&1` : redirige la sortie d'erreurs de `cmd` vers la sortie
    standard (que l'on peut elle-même rediriger avec `>` ou `>>`)
  * `cmd 2>&1 | tee FILE` : affiche le résultat à l'écran et écrit
    dans `FILE`

`echo $PATH | tr ':' '\n'` : pour convertir le caractère `:` en `\n`
dans la chaîne de caractères correspondant à `$PATH`

## Manipulation de fichiers

`ls` : afficher le contenu du dossier
  * `ls -a` pour voir les fichiers et les dossiers cachés
  * `ls -l FILENAME` pour voir les permissions associées à un fichier
  * `ls -lh FILENAME` pour avoir la taille en format "human readable"
  * `ls -d DIRNAME` pour regarder les dossiers uniquement
  * `ls -R` : option récursive (?)

`tree` : afficher l'arborescence du dossier courant.
  * `tree -L n` : affiche seulement `n` niveaux d'arborescence.
  * `tree -I MOTIF` : filtre les éléments correspondants au motif `MOTIF`.
  * `tree -d` : n'affiche que les dossiers

`exa` : remplacement de `ls` et de `tree`
  * `exa -l` = `ls -l`
  * `exa -l --git` : afficher aussi l'état au sens git
  * `exa --tree` : affiche l'arborescence du dossier
  * `exa --tree --level N` : affiche l'arborescence sur les `N`
    premiers niveaux seulement

`cp FILE1 FILE2` : copier un fichier
  * `cp -R DIR1 DIR2` : copie récursivement un dossier

`mv OLD NEW` : déplacer un fichier (sert aussi à le renommer)

`rm FILENAME`  : supprimer un fichier
  * `rm -rf DIRNAME` : supprimer un dossier

`touch FILENAME` : mettre à jour la date d'accès et de modification du
fichier ; si le fichier n'existe pas, il est créé

`chmod PERM FILENAME` : changer les permissions d'un fichier
  * PERM = 666 : (rw-rw-rw-) All users may read and write the file.
  * PERM = 644 : (rw-r--r--) The owner may read and write a file,
    while all others may only read the file.
  * PERM = 600 : (rw-------) The owner may read and write a file. All
    others have no rights.
  * PERM = 755 : (rwxr-xr-x) The file's owner may read, write, and
    execute the file. All others may read and execute the file. This
    setting is common for programs that are used by all users.
  * `chmod --reference other this` : copie les permissions du fichier
    ou du dossier `other`

`ln REF SHORTCUT` : créer un lien physique (hard link) vers REF
  * Pour vérifier si deux fichiers X et Y sont liés par un lien
    physique, vérifier leur inode : `ls -li X Y` doit renvoyer la même
    valeur d'inode pour X et Y

`ln -s REF SHORTCUT` : créer un lien symbolique vers REF

`readlink LK` : lire le lien symbolique LK
  * `readlink LK -f` : renvoyer le chemin absolu

`du -hs MYFOLDER` : affiche la taille du dossier MYFOLDER
  * `-h` : format "human readable"
  * `-s` : n'affiche que le total (i.e. : la valeur pour MYFOLDER),
    plutôt qu'un résultat par élément de MYFOLDER
  * `-d n` : ne descend que de n niveaux
  * `--threshold=1G` : ne voir que les résultats de plus de 1G
  * `dust` serait une version plus intuitive faite en Rust

## Recherche

`find . -name "*.pyc" -type f -delete` : supprime tous les fichiers
avec l'extension `pyc` dans le répertoire courant.
  * Attention : `-delete` doit être le **dernier** argument de la
    commande (sinon, on supprime tout !)
  * `find DIR -wholename *path/*/MYFILE` : permet d'inclure le chemin
     dans la recherche
  * `find DIR -perm -g+w` : chercher dans `DIR` les fichiers et dossiers pour
     lesquels a minima le groupe a le droit d'écriture
  * `find DIR -not -perm 644` : chercher dans `DIR` les fichiers et dossiers
     qui ont un droit d'accès différent de 644 (-rw-r--r--)

`grep -e "foo"` : chercher la regexp "foo"
  * `grep -i` : ignorer la casse
  * `grep --include=MOTIF` : ne chercher que les fichiers
    correspondants à MOTIF
  * `grep -r` : recherche récursive dans le dossier et les
    sous-dossiers
  * `grep -o "\<[0-9]*\.[0-9]*\>" MYFILE | awk '{ sum += $1 } END {
    print sum }'` : chercher tous les flottants dans MYFILE et les
    sommer.
  * `grep -o "\<[0-9]*\.[0-9]*\>" MYFILE | sort -nr | head -1` :
    afficher le maximum parmi tous les flottants de MYFILE
  * `grep -nr` : afficher les numéros de ligne

## Archives

`tar` : manipuler une archive (éventuellement compressée)
  * `tar -zcvf archive.tar.gz DIRNAME` : zipper un dossier
    * `-z` : utiliser gzip
    * `-c` : créer une nouvelle archive
    * `-v` : verbose
    * `-f FILENAME.tar.gz` : crée l'archive dans le fichier
      `FILENAME.tar.gz`
  * `tar -zxvf archive.tar.gz` : dézipper un dossier
    * `-x` : extraire le dossier
  * `tar -xjf archive.tar.bz2` : décompresser une archive compressée
    avec bz2
  * `tar -tvf archive.tar.gz` : lister le contenu de l'archive

`zip -r ARCHIVE.zip DIR` : zipper le contenu du dossier DIR dans
ARCHIVE

`unzip archive.zip` : pour dézipper archive.zip
  * `unzip -l archive.zip` : lister le contenu de archive.zip, sans la
    dézipper.

## Utilitaires

`man CMD` : afficher le manuel associé à la commande CMD

`apropos FOO` : lister l'ensemble des fiches man contenant des
références à FOO

`tldr` (tealdeer) : équivalent de `man` mais avec des conseils plus
accessibles

`which CMD` : afficher l'emplacement de l'exécutable CMD
  * `whereis` est similaire

`umount /run/media/foo/bar` : éjecter la clef USB bar montée dans
/run/media/foo/

`display IMAGENAME` : afficher une image (.png ou .jpg, par exemple)

`eog IMAGENAME` : afficher une image avec la visionneuse d'image (Eye
Of Gnome)

`latexmk FILENAME -pdf` : produire un fichier PDF avec Latex
  * `latexmk FILENAME -xelatex` : produire un fichier PDF avec Xelatex
  * `latexmk -c` : supprimer les fichiers temporaires

`kpsewhich` : pour trouver des paquets Latex installés sur disque

`wc -l MYFILE` : compter le nombre de lignes dans MYFILE

`uniq MYFILE` : afficher les lignes de MYFILE en supprimant les
duplicata.
  * `uniq -u MYFILE` : n'afficher que les lignes uniques

`cloc DIRNAME` : compter le nombre de lignes de codes dans un dossier

`lsof PATH` : liste les fichiers ouverts ("list open files") dans le
chemin PATH

## SSH

`ssh TARGET` : se connecter en SSH sur TARGET
  * `ssh TARGET -X` : se connecter en ayant la possibilité de lancer
    des applications graphiques
  * `ssh TARGET ls` : faire un ls sur le home de target

`scp src dist` : copier à travers SSH
  * `scp -r src dist` : copier récursivement le répertoire src
  * `scp foo:fqdn:bar` : copier le fichier `bar` (path depuis le home)
    de l'utilisateur `foo` depuis la machine dont le FQDN (Fully
    Qualified Domain Name) est `fqdn`

## Gestion des utilisateurs

`whoami` : afficher le nom de l'utilisateur courant

`w` : lister les utilisateurs connectés sur le poste

`who` : afficher le nom des utilisateurs connectés

`hostname` : afficher le nom de la machine

`dnsdomainname` : afficher le nom de domaine sur lequel est la machine.
  * Le FQDN (Fully Qualified Domain Name) correspond donc à
    `hostname` + `.` + `dnsdomainname`

## Gestion matérielle

`kill PID` : tue le processus dont le process ID est PID
  * `kill -9 PID` : tue immédiatement le processus

`top` : lister la charge CPU
  * htop semble mieux ; dans htop, `>` permet de choisir comment trier
    les lignes

`lscpu` : afficher des infos sur les CPU dans un format user friendly

`df` : affiche l'utilisation des disques
  * `-h` : format "human readable"
  * `df path` : affiche l'utilisation du disque sur lequel est `path`

## Réseau

`ip` : show / manipulate routing, devices, policy routing and tunnels
  * `ip -a show` : afficher les informations des interfaces réseaux IP
  * `ip -a` : idem (`show` est la commande par défaut)

`traceroute` : print the route packets trace to network host
  * `traceroute www.google.com` : indique par quelles machines on passe pour
    aller de sa machine à www.google.com

## Analyse de certains fichiers binaires

`nm BINARY` : examine un fichier binaire (par exemple pour lister les points
d'entrée d'une librairie statique .a)
  * `nm BINARY.a --demangle` : pour avoir quelque chose de lisible à
    partir d'une librairie C++

`ldd LIB.so` : afficher les dépendances de LIB.so (et leurs
emplacements)

`ncdump MYFILE` : afficher le contenu du fichier NetCDF MYFILE
  * `ncdump -h MYFILE` : affiche le header du fichier MYFILE
