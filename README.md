#!/bin/bash

# Fonction pour jouer au jeu
guessing_game() {
    # Obtenez le nombre de fichiers dans le répertoire actuel
    correct_guess=$(ls -1 | wc -l)
    
    while true; do
        # Demander à l'utilisateur combien de fichiers il pense qu'il y a
        echo "Devinez combien de fichiers sont présents dans ce répertoire:"
        read user_guess

        # Vérifier si la réponse de l'utilisateur est correcte
        if [[ "$user_guess" -eq "$correct_guess" ]]; then
            echo "Félicitations, vous avez deviné correctement!"
            break
        elif [[ "$user_guess" -lt "$correct_guess" ]]; then
            echo "Trop bas, essayez encore!"
        else
            echo "Trop haut, essayez encore!"
        fi
    done
}

# Lancer le jeu
guessing_game
# Variables
SCRIPT_NAME = guessinggame.sh
README_NAME = README.md

# Règle principale
all: $(README_NAME)

# Création du fichier README.md
$(README_NAME): $(SCRIPT_NAME)
	echo "# Projet Guessing Game" > $(README_NAME)
	echo "Date et Heure: $(shell date)" >> $(README_NAME)
	echo "Lignes de code dans $(SCRIPT_NAME): $(shell wc -l < $(SCRIPT_NAME))" >> $(README_NAME)
# Projet Guessing Game
Date et Heure: Fri Dec 13 12:34:56 UTC 2024
Lignes de code dans guessinggame.sh: 20
make
bash guessinggame.sh

