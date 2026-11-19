# bouture

Crée un nouveau site à partir de [Sites Conformes][sc] : un projet Django/Wagtail minimal, déjà configuré, sur le modèle de
`wagtail start`.

[sc]: https://github.com/numerique-gouv/sites-conformes

```sh
uvx bouture start monsite
cd monsite
uv run python manage.py migrate
uv run python manage.py collectstatic --noinput
uv run python manage.py create_starter_pages
uv run python manage.py createsuperuser
uv run python manage.py runserver
```

La commande pose quelques questions : titre et sous-titre du site, intitulé
officiel, base de données, puis les fonctionnalités à activer. Le
`config/settings.py` généré ne contient que les réglages des fonctionnalités
choisies :

- connexion à l’administration avec ProConnect ;
- double authentification obligatoire ;
- stockage des médias : fichiers locaux, base de données ou S3 ;
- langues en plus du français ;
- suivi des erreurs avec Sentry.

`--no-input` passe les questions et crée le projet le plus simple : SQLite,
fichiers locaux, aucune de ces fonctionnalités.

## Développer

```sh
uv run pytest
```

Les tests génèrent des projets et lancent `check` et `migrate` dessus avec le
paquet `sites-conformes` installé.
