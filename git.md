# Git

`git clone https://github.com/USER-NAME/REPO-NAME.git` : cloner un
repo depuis GitHub
  * `git clone --bare MYREPO` : cloner vers un repo nu
  * `git clone --single-branch` : cloner uniquement la HEAD distante (par
    défaut: origin/master)

`git init --bare` : créer un repo nu (par exemple pour un repo
central)

`git config user.name "My Name"` : donner un nom d'utilisateur pour le
repo
  * `git config user.name` : afficher le nom d'utilisateur
  * `git config user.email "myemail@tmp.com"` : donner une adresse mail
  * `--global` : pour que les paramètres s'appliquent à tous les repos
  * `git config --list` : lister tous les paramètres de configuration
    trouvés et utilisés par git

`git status` : afficher l'état du repo
  * `git status -s` : afficher l'état du repo en version courte

`git diff` : afficher les différences entre le répertoire et les
fichiers staged
  * `git diff --staged` : afficher les différences entre les fichiers
    staged et la dernière révision
  * `git diff SAH1..OTHER-SAH1` : afficher les différences entre les
    commits SAH1 et OTHER-SAH1
  * `git difftool` : visualiser les différences.

`git add FILENAME` : ajouter au prochain commit les modifications d'un
fichier
  * `git add -u` : ajoute toutes les modifications courantes (hors
    nouveaux fichiers)

`git reset HEAD FILENAME` : inverse de `add`, sans modifier le fichier
en lui-même (le fichier devient simplement unstaged)

`git branch` : lister les branches
  * `git branch NEW-BRANCH` : créer une nouvelle branche appelée
    NEW-BRANCH (tout en restant sur la branche courante)
  * `git branch NEW-BRANCH HEAD~n` : créer une nouvelle branche sur le
    n-ième ancestre de HEAD
  * `git branch NEW-BRANCH SAH1` : créer une nouvelle branche sur le
    commit SAH1
  * `git branch NEW-BRANCH TAG` : créer une nouvelle branche sur le
    tag TAG
  * `git branch -u REMOTE/BRANCH BRANCH` : faire suivre à la branche
    BRANCH la branche correspondante du remote
  * `git branch -r` : lister les branches de `remote`
  * `git branch -d BRANCH` : supprimer la branche BRANCH
  * `git branch -D BRANCH` : supprimer la branche BRANCH, même si elle
    n'a pas été fusionnée
  * `git branch --merged` : lister les branches fusionnées avec la
    branche courante
  * `git branch --no-merged` : lister les branches non fusionnées avec
    la branche courante

`git checkout BRANCH` : placer HEAD au niveau de BRANCH
  * `git checkout -b BRANCH` : créer la branche BRANCH et y placer
    HEAD
  * `git checkout --track REMOTE/BRANCH` : créer une branche qui suit
    BRANCH sur REMOTE
  * `git checkout BRANCH -- FILENAME` : récupérer un fichier depuis la
    branche BRANCH

`git checkout -- FILENAME` : remet le fichier dans l'état du dernier
commit (annule les modifications)
  * `git checkout -- .` : annule tous les changements locaux

`git commit` : committer des changements
  * `git commit --amend` : pour modifier le dernier commit en date
  * `git commit -a` : pour ajouter tous les fichiers tous les fichiers
    suivis non encore stagés

`git merge OTHER-BRANCH` : fusionner HEAD avec OTHER-BRANCH
  * Fast forward merge : fusionner avec un descendant (nécessaire pour
    déplacer les branches)
  * `git merge --ff-only` : abandonner si l'avance rapide est
    impossible
  * `git mergetool` : lancer une interface d'outil de fusion
  * `git merge --abort` : abandonner la fusion en cours
  * `git merge --strategy-option theirs` : résoudre les conflits de
    fusion en favorisant la branche vers laquelle on merge
  * `git merge --strategy-option ours` : résoudre les conflits de
    fusion en favorisant la branche depuis laquelle on merge

`git rebase OTHER-BRANCH` : rebaser HEAD par dessus OTHER-BRANCH
  * `git rebase --onto B1 B2 B3` : "Take the B3 branch, figure out the
    patches since it diverged from the B2 branch, and replay these
    patches in the B3 branch as if it was based directly off the B1
    branch instead"

`git push REMOTE BRANCH` : pousser des commits
  * `git push origin master` : pour le premier push
  * `git push` : après le premier push
  * `git push -u REMOTE BRANCH` : pousser une nouvelle branche vers
    REMOTE
  * `git push REMOTE --delete BRANCH` : supprimer BRANCH de REMOTE

`git fetch` : tirer des commits
  * `git fetch REMOTE BRANCH` : tirer une branche donnée d'un remote
    spécifique

`git pull` : tirer des commits et les merger avec le répertoire de
travail
  * `git pull` = `git fetch && git merge`

`git remote` : lister les répertoires distants
  * `git remote -v` : afficher la liste des répertoires distants
  * `git remote show` : lister les répertoires distants
  * `git remote show REMOTE` : afficher des informations sur le
    répertoire distant REMOTE
  * `git remote set-url REMOTE URL` : changer l'URL associée au
    répertoire distant REMOTE (en particulier : `git remote set-url
    origin git@github.com:OWNER/REPOSITORY.git` pour se connecter en
    SSH à un répertoire distant sur GitHub)
  * `git remote add REMOTE URL` : ajouter le dépôt REMOTE
  * `git remote prune REMOTE` : supprimer dans le dépôt local les
    références aux branches de REMOTE qui n'existent plus dans REMOTE
    (les éventuelles branches locales qui suivent ces branches
    distantes ne sont pas affectées)

Pousser un repo existant vers GitHub :
  * Créer le repo sur GitHub
  * `git remote add origin https://github.com/USER-NAME/REPO-NAME.git`
  * `git push -u origin master`

`git log` : afficher l'historique
  * `git log -n` : afficher les n derniers commits (il faut que n soit
    un entier)
  * `git log --graph` : afficher un graphe ASCII
  * `git log --since=2.weeks` : afficher les révisions des deux
    dernières semaines
  * `git log -S "my string"` : afficher les révisions qui ont ajouté
    ou supprimé la chaîne de caractères "my string"

`git ls-files` : afficher l'ensemble des fichiers suivis

`git tag` : lister les tags
  * `git tag -l "v1.8.5*"` : lister tous les tags qui matchent le
    pattern
  * `git tag -a MYTAG` : ajouter un tag à la révision courante (des
    informations de tag sont ajoutées au tag)
  * `git tag -a MYTAG REV` : ajouter un tag à la révision REV
  * `git tag -d MYTAG` : supprimer un tag local
  * `git push REMOTE TAGNAME` : pousser le tag TAGNAME vers REMOTE

`git stash` : sauvegarder temporairement les modifications courantes
et revenir à un repo propre
  * `git stash pop` : réappliquer les modifications les plus récentes
    sauvegardées par `git stash`
  * `git stash clear` : supprime le contenu de la stash list
