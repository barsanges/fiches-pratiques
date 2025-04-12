# Ollama

## Dans le terminal

`ollama help` : afficher l'aide

`ollama serve` : démarrer Ollama pour pouvoir l'utiliser dans un autre
terminal

`ollama run gemma3:1b` : démarrer une session avec le modèle Gemma 3
de Google (la version avec "seulement" un milliard de paramètres)

`ollama list` : lister les modèles installés

`ollama rm MODEL` : supprimer le modèle `MODEL`

## Dans la session

`/?` : accéder à l'aide dans la session

`/save <model>` : sauvegarder la session courante

`/load <model>` : charger une session sauvegardée à l'aide de `/save
<model>`

`/bye` : fermer la session

## Modèles

*gemma3:1b* : modèle de Google pour du langage naturel, notamment en
français

*codellama:7b* : modèle de Meta pour du code (notamment Python, C++,
Java, PHP, Typescript, Javascript, C#, Bash)
