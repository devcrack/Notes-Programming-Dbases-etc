# Managers 
A manager is an interface through which database query operations are provided to Django Models. By Default Django adds a Manager with the name objects to every Django Model class.


There are two mainly reasons you might want to customize a Manager

- To add extra manager methods as we mentioned.
- To modify the initial Query Set the Manager returns.


By default Django adds a Manager with the name **objects** to every Django model Class.

Usally you use this when you do something like:
```python
MyModel.objects.all()
```
Objects is a special attribute through which you query your database. This default Model Manager is with which we perform the queries like all(), get(), filter() , etc.


Basically a Model Manager is an object through wich Django models perform databases queries. Each Django Model has at least one manager, which is the default manager(objects)

You can attach as many Manager() instances to a model as you'd like.  In fact this is an easy way to define commons filters for your models.

## Custom Manager

```python 
from django.db import models

class Customer(models.Model):
    name = models.CharField(max_length=90)
    active = models.BooleanField(default=True)
    work_email = models.EmailField()
    personal_email = models.EmailField(null=True, blank=True)

```

Is important to note that we must define our model Managers before of Model definition.  Avoiding queries all over the place. Concentrate them on your Managers then you can test them better and make changes only in one place.

### Example #1
```python
from django.db import models


class CustomManager(models.Manager):
    
    def find_by_email(self, email):
        return self.filter(
            models.Q(work_email=email) |
            models.Q(personal_email=email)
        )
   
    def find(self, id):
        return self.get(pk=id)


class Customer(models.Model):
    name = models.CharField(max_length=90)
    active = models.BooleanField(default=True)
    work_email = models.EmailField()
    personal_email = models.EmailField(null=True, blank=True)


```

### Example #2

```python
class BlueManager(models.Manager):
    def get_query_set(self):
        return super(BlueManager, self).get_query_set().filter(colour='Blue')


class MyModel(models.Model):
     colour = models.CharField(max_length=64)
     blue_objects = BlueManager()
```
Calling:

```python
MyModel.blue_objects.all()
```


Adding extra manager methods(custom managers) is the preferred way to add **table-level** functionality to your models.

For add Row level Funcionality use **model methods**.

### Example #3

```python 
class SeniorManager(models.Manager):
    def get_queryset(self):
        return super(SeniorManager, self).get_queryset().filter(role='S')

class JuniorManager(models.Manager):
    def get_queryset(self):
        return super(JuniorManager, self).get_queryset().filter(role='J')

class Employee(models.Model):
    ...
    roles_choices = (
        ("J", "Junior"),
        ("S", "Senior"),
    )
    ....
    role = models.CharField(max_length=1, choices=role_choices)

    all_employees = models.Manager()
    seniors = SeniorManager()
    juniors = JuniorManager()

```
This allows you to request:

-  ```Employee.all_employees.all()```
- ```Employee.seniors.all()```
- ```Employee.juniors.all()```



### Calling Methods in Custom Model Managers

```python
class EmployeeQuerySet(models.QuerySet):
    def juniors(self):
        return self.filter(role='J')

    def seniors(self):
        return self.filter(role='S')

class EmployeeManager(models.Manager):
    def get_queryset(self):
        return EmployeeQuerySet(self.model, using=self._db)

    def juniors(self):
        return self.get_queryset().juniors()

    def seniors(self):
        return self.get_queryset().seniors()

class Employee(models.Model):
    ...
    roles_choices = (
        ("J", "Junior"),
        ("S", "Senior"),
    )
    ....
    role = models.CharField(max_length=1, choices=role_choices)

    all_employees = EmployeeManager()
```

This example Allows you call both **juniors()** and **seniors()** directly from the manager ```Employee.all_employees```


Sources:

- [Oficial Documentation](https://docs.djangoproject.com/en/dev/topics/db/managers/)

- https://medium.com/@jairvercosa/django-model-guideline-d48a96c9b38c

- https://medium.com/@MicroPyramid/django-model-managers-and-properties-564ef668a04c

- https://djangocentral.com/adding-custom-model-managers-in-django/

- https://micropyramid.com/blog/how-to-add-a-custom-managers-in-django/