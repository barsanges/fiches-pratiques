# Emacs

## Raccourcis par défaut

C-x C-f		| Ouvrir un fichier
C-x C-s		| Sauver le fichier
C-g	        | Quitter le minibuffer
C-x b       | Switcher d'un buffer à un autre (dans la même fenêtre)
C-x C-b     | Lister les buffers
M-x shell   | Lancer un shell (!)
C-x k       | Fermer un buffer
C-x o       | Passer à une autre fenêtre
C-x 0       | Fermer la fenêtre courante
C-x 2       | Séparer la fenêtre en deux dans la hauteur
C-x 3       | Séparer la fenêtre en deux dans la largeur
C-w         | Couper
M-w         | Copier
C-y         | Coller
C-s         | Recherche vers la fin du fichier
C-s C-s     | Répéter la dernière recherche
C-s C-w     | Rechercher le mot après le curseur (peut-être étendu)
M-% <x> <y> | Recherche de x et remplacement par y
M-<         | Aller au début du buffer
M->         | Aller à la fin du buffer
C-x u       | Undo
C-x d       | Entrer dans le mode "dired"
C-x TAB     | Mode d'ajustement de l'indentation
M-q         | Réordonnance (fill) le paragraphe
M-h         | Sélectionne tout le paragraphe
C-c C-c     | Compiler le document (avec AucTex)
C-x C-c     | Fermer Emacs (utile en mode 'no window')

## Raccourcis personnels

C-tab       | Complétion (binding par défaut : M-/)
M-up        | Echanger la ligne courante avec la ligne au-dessus
M-down      | Echanger la ligne courante avec la ligne en-dessous
C-c C-d     | Dupliquer la ligne courante
C-c C-r     | Recharger le buffer
C-c C-k     | Replier tous les blocs
C-c C-u     | Déplier tous les blocs
C-v         | Coller (identique à C-y)
C-z  Undo   | Identique à C-x u
C-f         | Curseur multiple sur le prochain mot (remplace 'forward-char')
C-d         | Curseur multiple au début de toutes les lignes sélectionnées (remplace 'delete-char')
M-d         | Aller au début du paragraphe (remplace 'kill-word')
M-f         | Aller à la fin du paragraphe (remplace 'forward-word')

## Commandes inhabituelles

C-h w command-name                   | Trouver le raccourci correspondant à command-name
C-h k key-sequence                   | Trouver la commande correspondant à key-sequence
M-x describe-bindings                | Lister les raccourcis existants
M-x revert-buffer                    | Recharger le buffer (s'il a été modifié par ailleurs)
M-x rgrep                            | Faire une recherche dans un dossier et ses sous-dossiers
M-x customize-face minibuffer-prompt | Changer la couleur du texte dans le minibuffer
M-x list-packages                    | Accéder au menu des paquets (notamment pour en installer)

Pour lancer Emacs dans la console (= 'no window') : emacs -nw

Pour insérer des espaces dans rgrep : C-q SPACE
