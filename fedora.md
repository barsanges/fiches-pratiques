# Fedora

## dnf

`sudo dnf install foo` : installer le paquet `foo`

`dnf search foo` : chercher le paquet `foo` (ou un paquet approchant)
dans le dépôt

## Latex

Pour installer des paquets Latex, il ne faut *pas* utiliser
`tlmgr`. Il faut à la place passer par `dnf`. Par exemple, pour
installer le paquet `titling` :

	sudo dnf install texlive-titling
