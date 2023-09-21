# Conda

`source activate MYENV` : activer l'environnement MYENV

`source deactivate MYENV` : désactiver l'environnement MYENV

`conda create --name MYENV` : créer l'environnement MYENV
  * `conda create -n MYENV` : même commande
  * `conda create -n MYENV numpy pandas` : créer MYENV, avec les
    paquets numpy et pandas
  * `conda create -n MYENV python=3` : créer myenv en Python 3

`conda create -n MYENV --clone BASEENV` : cloner l'environnement
    BASEENV dans un nouvel environnement MYENV

`conda env create -f MYFILE.yml` : créer un environnement à partir du
fichier d'environnement MYFILE.yml (le nom de l'environnement est
donné dans le fichier MYFILE.yml)

`conda env export > MYFILE.yml` : exporte la composition de
l'environnement courant dans le fichier MYFILE.yml

`conda remove -n MYENV numpy` : supprimer le paquet numpy de MYENV
  * `conda remove -n MYENV --all` : supprimer intégralement MYENV

`conda info --envs` : lister les environnements existants
  * `conda env list` : même commande

`conda install numpy` : installer numpy dans l'environnement courant

`conda update numpy` : mettre à jour numpy dans l'environnement
courant
  * `conda update --all` : mettre à jour tous les paquets
