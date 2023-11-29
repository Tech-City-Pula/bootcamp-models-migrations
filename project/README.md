# SQL modeli i migracije u djangu

## povezivanje baze podataka

```python
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.sqlite3',
        'NAME': BASE_URL / 'db.sqlite', # ovdje stavimo putanju do nase sqlite baze podataka
    }
}
```

## pokretanje incijalne migracije

```shell
python3 manage.py migrate
```

## stvaranje novih modela

unutar `models.py` filea nase aplikacije:

```python
from django.db import models

class NasModel(models.Model):
    name = models.CharField(max_length=100)

    def __str__(self):
        return f"Artist name is {self.name}"
```

## dodavanje novih migracija iz modela

nakon sto dodamo novi model u `models.py`

```shell
python3 manage.py makemigrations
```

nakon sto smo stvorili migracije treba ih primjeniti (migrirati)

```shell
python3 manage.py migrate
```

## dodavanje novih unosa putem shell-a

```shell
python3 manage.py shell
```

## stvaranje modela iz postojece baze

komandom `inspectdb` ispisujemo u standardni output sve modele koje django sam od sebe slozi

```shell
python3 manage.py inspectdb
```

ako ih zelimo zapisati u file koristimo redirekcijski operator u shellu

```shell
python3 manage.py inspectdb > music_library/models.py
```

## stvaranje admin usera

```shell
python3 manage.py createsuperuser
```