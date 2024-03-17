# Ubuntu

## apt

`sudo apt install foo` : installer le paquet `foo`

`apt search foo` : chercher dans le dépôt les paquets dont le nom ou
la description contiennent `foo`

`apt search foo --names-only` : chercher dans le dépôt les paquets
dont le nom contient `foo`

`apt list foo --installed` : indiquer si le paquet `foo` est installé

`sudo apt purge --autoremove foo` : supprimer le paque `foo` et les dépendances
qui ont été installées en même temps que `foo`
