## Querysets Doccumentaiton
https://docs.djangoproject.com/en/3.1/ref/models/querysets/

## Mensajes de traduccion 
el .po se tiene que "re-crear" cada vez que se agregan/eliman cadenas.
para recrear el 
**.po** usas ```python manage.py makemessages -l en```

## How execute Test on Django 

### Executing Test of an specific application

```  ./manage.py test apps.signups.tests --settings=api.settings.pre``` 

