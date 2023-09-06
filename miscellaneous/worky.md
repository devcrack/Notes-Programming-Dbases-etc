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
La programación funcional es un paradigma de programación que se centra en el uso de funciones y la inmutabilidad de los datos.  En Python tenemos algunas caracteristicas y conceptos de programacion funcional que incluyen: 

1. Funciones de orden superior.

2. **Funciones lambda**: Las funciones lambda son funciones anónimas y pequeñas que se pueden definir en línea. Son útiles cuando necesitas una función rápida para una operación simple.

```suma = lambda x, y: x + y```


En Python, lambda es una palabra clave que se utiliza para definir funciones anónimas y pequeñas, también conocidas como funciones lambda o expresiones lambda. Estas funciones son "anónimas" porque no se les asigna un nombre como las funciones regulares definidas con la palabra clave def.

La sintaxis general de una función lambda en Python es la siguiente:

```lambda argumentos: expresión```

- argumentos: Son los argumentos de la función, separados por comas, similares a los argumentos de una función definida con def. Puedes tener cero o más argumentos.
- expresión: Es una expresión que se evalúa y devuelve como resultado cuando se llama la función.

Ejemplo: 
```python
suma = lambda x, y: x + y
resultado = suma(3, 5)  # Devuelve 8
```

### Funciones de orden Superior

Una función de orden superior es una función que toma una o más funciones como argumentos y/o devuelve una función como resultado. 

## Clases Mixin en Python. 

En Python, una clase mixin es una clase que proporciona funcionalidad adicional a otras clases a través de la herencia múltiple sin ser la clase principal de la jerarquía de herencia. Las clases mixin no se suponen que sean instanciadas por sí mismas ni que formen parte de la jerarquía de herencia principal de un programa; en su lugar, se diseñan específicamente para mezclarse (o combinarse) con otras clases.

Las clases mixin son útiles para extender y enriquecer la funcionalidad de clases existentes sin tener que modificar su código fuente. Esto promueve la reutilización de código y la modularidad. Las clases mixin pueden contener métodos, atributos o propiedades que se pueden usar en múltiples clases sin tener que copiar y pegar código.

Características de las clases mixin en Python:

- No se instancian por sí mismas: Las clases mixin generalmente no se crean instancias por sí mismas, sino que se utilizan como componentes para enriquecer otras clases.

- No son la clase principal de la jerarquía de herencia: Las clases mixin se mezclan con otras clases que forman parte de la jerarquía de herencia principal.

- Proporcionan funcionalidad adicional: Las clases mixin aportan métodos, atributos o comportamientos específicos que enriquecen las clases que las utilizan.

- Pueden ser combinadas en múltiples clases: Las clases mixin pueden ser mezcladas en múltiples clases sin problemas, lo que promueve la reutilización de código.

- Mezcla de clases múltiples: Python admite la herencia múltiple, lo que significa que una clase puede heredar de varias clases, incluyendo clases mixin.

```python
class LoggerMixin:
    def log(self, message):
        print(f"Log: {message}")

class EmailSenderMixin:
    def send_email(self, to, subject, message):
        # Código para enviar un correo electrónico
        pass

class MiClase(LoggerMixin, EmailSenderMixin):
    def __init__(self, nombre):
        self.nombre = nombre

    def realizar_accion(self):
        self.log("Realizando acción")
        self.send_email("destinatario@example.com", "Asunto", "Mensaje")

instancia = MiClase("Ejemplo")
instancia.realizar_accion()
```

En este ejemplo, LoggerMixin y EmailSenderMixin son clases mixin que proporcionan funcionalidad de registro y envío de correo electrónico. La clase MiClase mezcla ambas clases mixin y utiliza sus métodos log() y send_email(), sin tener que implementar esos métodos por sí misma.

Las clases mixin son una técnica poderosa en Python para agregar funcionalidad adicional de manera modular y reutilizable en una aplicación, lo que facilita la composición de clases con diferentes comportamientos.

## Cors
CORS (Cross-Origin Resource Sharing) es un mecanismo de seguridad que se implementa en los navegadores web para controlar las solicitudes de recursos (como archivos, datos o servicios web) que se realizan desde un dominio web (origen) a otro dominio web diferente. 
La política de seguridad de mismo origen en los navegadores impide que una página web haga solicitudes a un dominio diferente al que se cargó la página originalmente, con el fin de evitar ataques de seguridad como el robo de información.

Sin embargo, en muchos casos, es necesario que una página web realice solicitudes a otros dominios, por ejemplo, para cargar recursos externos o interactuar con servicios web de terceros (como API REST). Es aquí donde entra en juego CORS para permitir estas solicitudes de manera segura.

El funcionamiento básico de CORS es el siguiente:

Cuando una página web realiza una solicitud a un dominio diferente (un dominio cruzado), el navegador envía una solicitud HTTP previa (pre-flight) al servidor del dominio destino para verificar si se permite que la solicitud se complete.

El servidor del dominio destino debe estar configurado para permitir el acceso desde otros orígenes mediante encabezados HTTP específicos, como Access-Control-Allow-Origin.

Si el servidor responde con encabezados que indican que la solicitud está permitida (por ejemplo, Access-Control-Allow-Origin: * o un origen específico), el navegador permitirá que la solicitud continúe. De lo contrario, bloqueará la solicitud y generará un error CORS.


