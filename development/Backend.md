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

## Base de donnée
Par defaut la base de donnée utilisée est `sqlite3`. Cette base de donnée a l'avantage d'être très légère et adapter aux dispositifs de petite taille.
Dans notre cas, cette base de donnée est adapté pour le développement mais pas forcement pour la production.

Nous avons mis en place une base de donnée `PostgreSQL` pour la production.

### Modifier les paramètres
Dans le fichier project/project/settings.py : 
- pour sqlite3 :
```python
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.sqlite3',
        'NAME': BASE_DIR / 'db.sqlite3',
    }
}

```

- pour PostgreSQL : 
```python
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql_psycopg2',
        'NAME': 'dbgreencollect', 
        'USER': 'root', 
        'PASSWORD': 'root',
        'HOST': '172.24.0.3', 
        'PORT': '5432',
    }
}

```

### Configuration supplémentaire pour PostgreSQL
Il faut lancer les container Docker afin de disposer de PostgreSQL et PgAdmin :
> foo@docker $> docker-compose -f db.yml up

Une fois les container lancer, il faut maintenant créer la base de donnée dans postgreSQL. Pour cela nous allons nous aider de PgAdmin que nous allons de voir aussi configurer : 
- Register > Server :
    + Name : greencollect
    + Host/Address : 172.24.0.3
    + Port : 5432
    + Maintenance database : postgres
    + Username : root
    + Password : root
- Servers > greencollect > Create > Database :
    + Name : dbgreencollect
    + Owner : root

### Finaliser la mise en place de la base de donnée
Mise en place du modèle : 
> foo@project $> python manage.py migrate

Insertion de fausses données : 
> foo@project $> python manage.py insert_fakedata

Autre commande pour la base de donnée

- Réintialiser complètement la base de donnée : 
> foo@project $> python manage.py flush

### Information supplémentaire 
Super user
- Username: admin
- Email: superuser@greencollect.fr
- Password: admin

## Serveur python

Lancement du serveur :
> foo@project $> python manage.py runserver

> foo@project $> python manage.py runserver 8080

En utilisant 0.0.0.0 cela permet d'ouvrir un port de votre machine pour que le serveur soit accéssible depuis votre réseau privé (192.168.X.X)
> foo@project $> python manage.py runserver 0.0.0.0:8080

## Commande à garder
Créer un Token d'identification : 
> foo@project $> python manage.py drf_create_token <username>

Vérifier si l'application est prête au déploiement (notemment pour la sécurité) :
> foo@project $> python manage.py check --deploy