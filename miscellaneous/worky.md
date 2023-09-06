En python un SET o conjunto es una coleccion de elementos no ordenados y unicos. En los conjuntos no tenemos elementos repetidos y no conservan un orden especifico. Los conjuntos son una estructura de datos mutable lo que significa que podemos agregar o remover elementos de un conjunto. 

Para crear un conjunto se utilizan las llaves ```{}``` o la funcion set()

Ejemplo:
```python
my_set = {1, 2, 3, 4}
other_set = set([3 ,2 , 4])
```

Son utiles para almacenar elementos unicos y no es importante el orden con el que se guarden



## Tuplas
Una tupla es una coleccion de elementos ordenados e inmutables. Una vez que se define una tupla no se puede cambiar su contenido ni su tamaño. Las tuplas se utilizan para almacenar un conjunto de elementos relacionados que deben de conservar un orden especifico. 

Las tuplas se crean utilizando parentesis ```()``` y pueden contener cualquier tipo de dato, numero cadenas, u otros objetos. 
Las tuplas son utiles cuando es necesario alamacenar informacion que no deberia modificarse despues de su creacion como coordenadas o fechas por mencionar un ejemplo. 

## Diccionario
Un diccionario es una estructura de datos que permite almacenar y recuperar valores asociados a una clave. A diferencia de las listas y tuplas que almacenan datos en orden secuencial los diccionarios almacenan pares clave - valor donde cada clave es unica y esta asociada a un valor. 
A partir de python 3.7 los diccionarios conservan el orden en que se insertaron los elementos.


 Las claves de un diccionario deben ser objetos hashables e inmutables, lo que significa que deben ser valores que no cambien y que puedan ser identificados de manera única. Las listas son objetos mutables, lo que las hace inadecuadas para ser claves de diccionario.
 Sin embargo, puedes usar tuplas como claves de un diccionario, ya que las tuplas son inmutables y pueden contener elementos hashables. 

 ### Objeto hasheable

 Un objeto hashable en Python es un objeto que tiene un valor hash único y que es inmutable, lo que significa que no puede cambiar su valor después de haber sido creado. Los objetos hashables se utilizan comúnmente como claves en diccionarios, ya que la capacidad de calcular un valor hash único para una clave permite un acceso eficiente a los valores almacenados en el diccionario.

 1. Inmutabilidad: El objeto no puede cambiar después de haber sido creado. Esto garantiza que el valor hash del objeto permanezca constante durante su vida útil.

2. Valor Hash Único: El objeto debe tener un valor hash único que se calcula mediante la función hash(). Dos objetos hashables iguales deben tener el mismo valor hash.

Los objetos hashables típicos en Python incluyen:

Características son importantes para que un objeto sea considerado hashable en Python:
- Números enteros (int).
- Números de punto flotante (float).
- Cadenas de texto (str).
- Tuplas (si todos sus elementos son hashables).
- Algunos tipos de objetos personalizados si implementan los métodos __hash__() y __eq__() correctamente.

Un elemento mutable es aquel que puede cambiar su contenido despues de haber sido creado. 

En el caso de las cadenas son inmutables porque una vez que se crea una cadena  no se puede modificar su contenido, cualquier operacion que parezca modificar una cadena en realidad esta creando una nueva cadena en memoria en lugar de cambiar la original. 

Una clase abstracta en Python es una clase que no puede ser instanciada directamente pero sirve como un tipo de base para otras clases. Una clase abstracta generalmente define un conjunto de metodos que deben de ser implementados por las clases derivadas. Estos metodos se les conoce como metodos abstractos y actuan como una especificacion que debe de estar presente en las clases hijas. 

En Python, puedes crear una clase abstracta utilizando el módulo abc (Abstract Base Classes). Este módulo proporciona la clase ABC (Abstract Base Class) y el decorador @abstractmethod para definir clases abstractas y métodos abstractos. Aquí tienes un ejemplo simple de cómo crear y utilizar una clase abstracta en Python:

```python
from abc import ABC, abstractmethod

# Definir una clase abstracta
class FiguraGeometrica(ABC):

    @abstractmethod
    def area(self):
        pass

    @abstractmethod
    def perimetro(self):
        pass

# Clases concretas que heredan de la clase abstracta
class Cuadrado(FiguraGeometrica):
    
    def __init__(self, lado):
        self.lado = lado

    def area(self):
        return self.lado ** 2

    def perimetro(self):
        return 4 * self.lado

class Circulo(FiguraGeometrica):
    
    def __init__(self, radio):
        self.radio = radio

    def area(self):
        return 3.14159 * self.radio ** 2

    def perimetro(self):
        return 2 * 3.14159 * self.radio
```


## Programacion Funcional
