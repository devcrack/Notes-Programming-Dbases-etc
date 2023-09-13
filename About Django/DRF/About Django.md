## Initial setup of a Django Project
### Creating a Project in Django
```django-admin startproject <name_of_my_django_project>```
### Creating an app in the project 
```./manage.py start app <name_of_my_awesome_app>```


## Querysets Doccumentaiton
https://docs.djangoproject.com/en/3.1/ref/models/querysets/

## Mensajes de traduccion 
el .po se tiene que "re-crear" cada vez que se agregan/eliman cadenas.
para recrear el 
**.po** usas ```python manage.py makemessages -l en```
```./manage.py makemessages -l en```
<br>
Para compilar los mensajes
```./manage.py compilemessages -l en```

## How execute Test on Django 

### Executing Test of an specific application

```  ./manage.py test apps.signups.tests --settings=api.settings.pre``` 


## AbstractUser vs AbstractBaseUser

The default user model in Django uses a username to uniquely identify a user during authentication. If you'd rather use an email address, you'll need to create a custom user model by either subclassing AbstractUser or AbstractBaseUser.

Options:

1. AbstractUser: Use this option if you are happy with the existing fields on the user model and just want to remove the username field.

2. AbstractBaseUser: Use this option if you want to start from scratch by creating your own, completely new user model.

_models.py_
```python
from django.contrib import admin
from .models import CustomUser


class CustomUser(AbstractUser):
    id = models.UUIDField(primary_key=True, default=uuid.uuid4, editable=False)
    # Overriding email field
    email = models.EmailField(_("email address"), blank=False, unique=True)
    USERNAME_FIELD = 'email'
    REQUIRED_FIELDS = []

    objects = CustomUserManager()
```
#### Model Manager
First, we need to add a custom Manager, by subclassing BaseUserManager, that uses an email as the unique identifier instead of a username.

Create a managers.py file in the "users" directory:

_managers.py_
```python
# 3rd-party
from django.contrib.auth.models import BaseUserManager, UserManager


class CustomUserManager(BaseUserManager):
    def create_user(self, email, password=None, **extra_fields):
        if not email:
            raise ValueError('The given email must be set')
        email = self.normalize_email(email)
        user = self.model(email=email, **extra_fields)
        user.set_password(password)
        user.save(using=self._db)
        return user

    def create_superuser(self, email, password=None, **extra_fields):
        extra_fields.setdefault('is_staff', True)
        extra_fields.setdefault('is_superuser', True)

        return self.create_user(email, password, **extra_fields)


```