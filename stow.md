# [Stow](https://www.gnu.org/software/stow/)

`stow FOO` : ranger les fichiers associés au programme `FOO` (par
défaut dans le dossier parent du `STOW_DIR`, qui est lui-même le
dossier courant par défaut)

`stow FOO --target=TARGET` : idem en construisant l'arborescence
appropriée dans le dossier `TARGET` (e.g. : `stow --target=$HOME ...`
pour gérer des fichiers de paramètrage)

`stow FOO --dotfiles` : remplacer "dot-" par "." au début des noms de
fichiers associés au programme `FOO`
