> [Documentation](../README.md)

# Feuille de triche

## Setup up env
Installation de l'envionnement virtuel python :
> foo@app/back$> python3 -m venv env
> foo@app/back$> source env/bin/activate
> foo@app/back$> pip install -r env/requirements.txt

Activation de l'envionnement :
> foo@app/back$> source env/bin/activate

Desactivation de l'envionnement : 
> foo@app/back$> deactivate

## Serveur python

Lancement du serveur :
> python manage.py runserver

> python manage.py runserver 8080

En utilisant 0.0.0.0 - 0 pour le raccourci 0.0.0.0 - cela permet d'ouvrir un port de votre machine pour que le serveur soit accéssible depuis votre réseau privé (192.168.0.X)
> python manage.py runserver 0:8080

## Super user
Username: admin
Email: superuser@greencollect.fr
Password: admin

## Base de donnée
Réintialiser complètement la base de donnée : 
> python manage.py flush

Mise en place du modèle : 
> python manage.py migrate

Insertion de fausses données : 
> python manage.py insert_fakedata

## Authentication
Créer un Token d'identification : 
> python manage.py drf_create_token <username>