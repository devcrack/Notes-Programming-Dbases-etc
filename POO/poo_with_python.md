## What is an object?
An object is a collection of data with associated behaviors. 

An object combines data (the properties and attributes) and functions (usually called methods). The data represents the state of the object and the methods represent the behavior and operations that the object can perform.   
Object oriented means functionally directed toward modeling objects. 


### Properties 

Properties is data that represents characteristics of a certain object. This properties or attributes store data related to this properties or attributes like weigh, color and size. Some times the properties are read only. 

## Behaviors

Behaviors are actions that can occur on an object. The behaviors that can be performed on a specific class of object are called methods. The methods are like simple functions in structured programming but with the big difference that the methods have access to all the data associated with this object. 

## Encapsulation 

It refers to the combination of data and behaviors related or attached in an object and to the concealment of some intern details of the object. This allows modularity, safety and helps to the mantain of the code stablish limits between system components. 
Encapsulation restric the access of private methods because this methods are only used internally by the class and is not exposed to other outside methods. This is helpfull cause this avoid and prevents the incorrect use of methods and attributes of the class object. 


## Inherintance 
Inherintance is a mechanism by which a class can inherit attributes and methods from another existing class, known as a parent class or super class. The inherinting class is known as child class or subclass.

The inherintance allows the code reuse and the creation of class hierarchies. The subclass(Child class) inhertis methods and properties from superclass (father class) and the subclass can add new attributes and methods if is necessary. This helps to modularity, code maintance and class organization. 

In the constructors of the child class is a good practice call the father class constructor from the child class. This allows correctly initialize the inherited attributes and configure the initial state of the father class(super class)

Example:
```python
class Animal:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def make_sound(self):
        pass

class Dog(Animal):
    def make_sound(self):
        print("Woof!")

class Cat(Animal):
    def make_sound(self):
        print("Meow!")

dog = Dog("Buddy", 3)
cat = Cat("Whiskers", 5)

dog.make_sound()  # Output: Woof!
cat.make_sound()  # Output: Meow!
```

## Order calling constructors when instantiating an object with Multiple inherintance

The order in which constructors are called in an instance of multiple  inherintance object follows a secuence called "Method Resolution Order"(MRO), which determines the order in which the constructors and methods are executed en a multiple inherintance hierachy.

The MRO uses the C3 algorithm. If we have multiple classes at the same heriarchy level, the order of appearence in the class declaration determines the order method resolution. 


```Python
class A:
    def __init__(self):
        print("Constructor de A")

class B:
    def __init__(self):
        print("Constructor de B")

class C(A, B):
    def __init__(self):
        super().__init__()
        print("Constructor de C")

obj = C()
```
In this example the C class inherits from the classes A and B. The resolution order methods for the creation of an instance of C will be 'C', 'A', 'B'. Por hence at the moment of create an instance of 'C' the constructor of 'A' will be called before of 'B' constructor.

If we do:

```python
class A:
    def __init__(self):
        print("Constructor de A")

class B:
    def __init__(self):
        print("Constructor de B")

class C(B, A):
    def __init__(self):
        super().__init__()
        print("Constructor de C")

obj = C()
```
If we define ```class C(B,A)```, the resolution order methods will be 'C', 'B', 'A'. When we create an instance of 'C', the constructor of 'B' will be called before of constructor of 'A'.

The ouput will be:
```
Constructor de B
Constructor de A
Constructor de C
```

## Polymorphism

Polymorphism allows to objects of differents classes behave 
similar based on their common type.

The polymorphism is achieved by implementing methods with the same name in different related classes, but with specific behaviors for each class. 

Example:

```python
class Animal:
    def hacer_sonido(self):
        pass

class Perro(Animal):
    def hacer_sonido(self):
        print("El perro ladra")

class Gato(Animal):
    def hacer_sonido(self):
        print("El gato maulla")

def hacer_sonar(animal):
    animal.hacer_sonido()

perro = Perro()
gato = Gato()
```

Output
```
hacer_sonar(perro)  # Salida: El perro ladra
hacer_sonar(gato)  # Salida: El gato maulla
```


Example #2

```python 
class Animal:
    def __init__(self, nombre):
        self.nombre = nombre

    def hacer_sonido(self):
        raise NotImplementedError("Método no implementado")


class Perro(Animal):
    def hacer_sonido(self):
        return "El perro {} ladra".format(self.nombre)


class Gato(Animal):
    def hacer_sonido(self):
        return "El gato {} maulla".format(self.nombre)


class Vaca(Animal):
    def hacer_sonido(self):
        return "La vaca {} hace 'mu'".format(self.nombre)


def hacer_sonar(animales):
    for animal in animales:
        print(animal.hacer_sonido())
```

Any method which we override can have any type and any number of of arguments in their differents overrides. As you can see in the previous method, the method 'hacer_sonar()' acepts an object list as argument, but this can vary depends of the program.  

## Decorators in Python

In python a function is consider an object, which means that as any other type of object, like a list or string for example. 

This include the capacity of pass function as arguments to others functions. 

When a decorator recieves a function as an argument, what it does is take take that function and modify in some way before return it. 

Example 
```python 
ef decorador(funcion):
    def wrapper():
        print("Antes de llamar a la función.")
        funcion()
        print("Después de llamar a la función.")
    return wrapper

@decorador
def mi_funcion():
    print("Hola, soy una función decorada.")

mi_funcion()
```

Output
```
Antes de llamar a la función.
Hola, soy una función decorada.
Después de llamar a la función.
```

Second Example
```python
ef decorador(funcion):
    def funcion_modificada(*args, **kwargs):
        print("Saludo adicional antes de la ejecución de la función")
        resultado = funcion(*args, **kwargs)
        resultado = resultado + " - Saludo adicional después de la ejecución de la función"
        return resultado
    return funcion_modificada

@decorador
def funcion_original():
    resultado = "Hola, soy el resultado"
    return resultado

print(funcion_original())
```

Output 
```
Saludo adicional antes de la ejecución de la función
Hola, soy el resultado - Saludo adicional después de la ejecución de la función
```


## Context manager (Manejadores de contexto en python)

A context manager is a way of working with resources that need to be initialized and released correctly, such as files, databases conections or locks. This provides a clearer syntax and ensures that resources are released correctly even if exceptions occur. 

Example:
```python
with open("archivo.txt", "r") as archivo:
    contenido = archivo.read()
    # Realizar operaciones con el contenido del archivo

# El archivo se cierra automáticamente al finalizar el bloque `with`
```

Los principios SOLID son un conjunto de cinco principios de diseño de software que se utilizan en la programación orientada a objetos para lograr un código limpio, flexible y mantenible. Estos principios fueron introducidos por el ingeniero de software Robert C. Martin, también conocido como "Uncle Bob". A continuación, se describen brevemente cada uno de los principios SOLID:

Principio de Responsabilidad Única (SRP - Single Responsibility Principle): Una clase debe tener una única responsabilidad. Esto significa que una clase debe tener solo una razón para cambiar. Cada clase debe estar enfocada en realizar una sola tarea o función específica.

Principio de Abierto/Cerrado (OCP - Open/Closed Principle): Las entidades de software deben estar abiertas para su extensión pero cerradas para su modificación. Esto significa que se deben poder agregar nuevas funcionalidades sin tener que modificar el código existente.

Principio de Sustitución de Liskov (LSP - Liskov Substitution Principle): Las clases derivadas deben ser sustituibles por sus clases base sin afectar la integridad del programa. Esto implica que cualquier instancia de una clase base debe poder ser reemplazada por una instancia de una clase derivada sin alterar el comportamiento correcto del programa.

Principio de Segregación de Interfaces (ISP - Interface Segregation Principle): Los clientes no deben depender de interfaces que no utilizan. Este principio establece que las interfaces deben ser cohesivas y no deben contener métodos que no sean utilizados por los clientes.

Principio de Inversión de Dependencia (DIP - Dependency Inversion Principle): Los módulos de alto nivel no deben depender de módulos de bajo nivel, ambos deben depender de abstracciones. Además, las abstracciones no deben depender de los detalles, los detalles deben depender de las abstracciones. Este principio fomenta el uso de la inversión de dependencia y la programación orientada a interfaces.

Estos principios SOLID ayudan a producir un código más flexible, escalable y fácil de mantener. Al seguir estos principios, se promueve un diseño orientado a objetos más sólido y se reducen las interdependencias entre las diferentes partes del sistema, lo que facilita la refactorización y extensión del código en el futuro.

___
Principio de Responsabilidad Única (SRP - Single Responsibility Principle):

```python
class Logger:
    def __init__(self, log_file):
        self.log_file = log_file
    
    def log(self, message):
        with open(self.log_file, 'a') as file:
            file.write(f'{message}\n')

class Calculator:
    def add(self, x, y):
        result = x + y
        logger = Logger('app.log')
        logger.log(f'Addition: {x} + {y} = {result}')
        return result
```
En este ejemplo, la clase Logger tiene la responsabilidad de escribir mensajes de log en un archivo. La clase Calculator tiene la responsabilidad de realizar operaciones de suma y utiliza la clase Logger para registrar el resultado de la suma.
___
Principio de Abierto/Cerrado (OCP - Open/Closed Principle):

```python
class Shape:
    def area(self):
        pass

class Rectangle(Shape):
    def __init__(self, width, height):
        self.width = width
        self.height = height
    
    def area(self):
        return self.width * self.height

class Circle(Shape):
    def __init__(self, radius):
        self.radius = radius
    
    def area(self):
        return 3.14 * self.radius ** 2
```

En este ejemplo, la clase Shape es una clase abstracta que define el método area(). Las clases Rectangle y Circle son clases derivadas que implementan el método area() de acuerdo a su propia lógica. Si se desea agregar una nueva forma, solo es necesario crear una nueva clase que herede de Shape y implemente el método area(), sin necesidad de modificar el código existente.

___
Principio de Sustitución de Liskov (LSP - Liskov Substitution Principle)

```python 
class Animal:
    def speak(self):
        pass

class Dog(Animal):
    def speak(self):
        return "Woof!"

class Cat(Animal):
    def speak(self):
        return "Meow!"

def make_animal_speak(animal):
    print(animal.speak())

dog = Dog()
cat = Cat()

make_animal_speak(dog)
make_animal_speak(cat)
```
En este ejemplo, la clase Animal es la clase base que define el método speak(). Las clases derivadas Dog y Cat sobrescriben el método speak() con su propio comportamiento. El método make_animal_speak() acepta cualquier instancia de la clase Animal y llama al método speak(). Podemos sustituir una instancia de Dog o Cat sin afectar el correcto funcionamiento del programa.

___
Principio de Segregación de Interfaces (ISP - Interface Segregation Principle):
```python
class Printer:
    def print(self, document):
        pass

class Scanner:
    def scan(self):
        pass

class Photocopier(Printer, Scanner):
    def print(self, document):
        print(f'Printing: {document}')
    
    def scan(self):
        print('Scanning document')
    
    def photocopy(self, document):
        self.scan()
        self.print(document)
```
En este ejemplo, la clase Printer define el método print(), la clase Scanner define el método scan(), y la clase Photocopier implementa ambos métodos. Sin embargo, el uso de la clase Photocopier solo requiere el método print() y scan(). El principio ISP sugiere dividir las interfaces en interfaces más pequeñas y cohesivas, para que los clientes solo dependan de las interfaces que necesitan.

___
Principio de Inversión de Dependencia (DIP - Dependency Inversion Principle):

```python
class Database:
    def save(self, data):
        pass

class DataManager:
    def __init__(self, database):
        self.database = database
    
    def process_data(self, data):
        # Procesamiento de datos
        self.database.save(data)

database = Database()
data_manager = DataManager(database)
data_manager.process_data("Some data")
```
En este ejemplo, la clase DataManager depende de una interfaz abstracta Database, en lugar de depender directamente de una implementación concreta. Esto permite que la clase DataManager sea independiente de los detalles específicos de la implementación de la base de datos y se pueda cambiar fácilmente a otra implementación sin modificar el código de DataManager. Esto fomenta la flexibilidad y la modularidad del código.



# Patrones de Diseño 
Patrón de Diseño Singleton:

Propósito: Garantizar que una clase tenga una única instancia y proporcionar un punto de acceso global a ella.
Ejemplo de uso: Clases de configuración, registros de eventos.
Patrón de Diseño Factory:

Propósito: Crear objetos sin especificar su clase concreta y delegar la creación a subclases.
Ejemplo de uso: Creación de objetos en base a ciertos parámetros o condiciones.
Patrón de Diseño Observer:

Propósito: Establecer una relación de uno a muchos entre objetos, de modo que cuando un objeto cambie su estado, todos los objetos dependientes sean notificados y actualizados automáticamente.
Ejemplo de uso: Eventos y notificaciones en interfaces gráficas, suscripción a cambios en datos.
Patrón de Diseño Strategy:

Propósito: Definir una familia de algoritmos intercambiables y encapsular cada uno de ellos, permitiendo que el algoritmo pueda ser seleccionado en tiempo de ejecución.
Ejemplo de uso: Diferentes algoritmos de ordenamiento, estrategias de cálculo de impuestos.
Patrón de Diseño Decorator:

Propósito: Agregar dinámicamente funcionalidades adicionales a un objeto, proporcionando una alternativa a la herencia subclasificada.
Ejemplo de uso: Decoración de objetos con características adicionales sin alterar su estructura base.
Patrón de Diseño Adapter:

Propósito: Permitir que objetos con interfaces incompatibles puedan trabajar juntos, envolviendo un objeto existente con una nueva interfaz.
Ejemplo de uso: Adaptación de clases de terceros, compatibilización de APIs.
Patrón de Diseño MVC (Model-View-Controller):

Propósito: Separar la lógica de la aplicación en tres componentes principales: el modelo (manejo de datos y lógica de negocio), la vista (interfaz de usuario) y el controlador (gestión de eventos y coordinación).
Ejemplo de uso: Desarrollo de aplicaciones web y aplicaciones con interfaces gráficas.
Estos son solo algunos de los patrones de diseño más comunes, y hay muchos más patrones disponibles que se adaptan a diferentes situaciones y necesidades. La elección del patrón de diseño adecuado depende del problema que se está resolviendo y del contexto de la aplicación.

Los patrones de diseño más comúnmente utilizados son:

Patrón de Diseño Singleton: Es ampliamente utilizado para garantizar que una clase tenga una única instancia y proporcionar un punto de acceso global a ella.

Patrón de Diseño Factory: Muy común para encapsular la lógica de creación de objetos y proporcionar flexibilidad en la creación de instancias.

Patrón de Diseño Observer: Se utiliza ampliamente en aplicaciones que requieren notificación y actualización automática de objetos cuando cambian de estado.

Patrón de Diseño Strategy: Muy útil cuando se necesitan diferentes algoritmos intercambiables en tiempo de ejecución.

Estos patrones son bastante populares debido a su utilidad y aplicabilidad en una amplia gama de escenarios. Sin embargo, la elección del patrón de diseño más adecuado dependerá del problema específico que se esté abordando y del contexto de la aplicación.

### Ejemplos

Patrón de Diseño Singleton:
```python 
class Singleton:
    _instance = None

    def __new__(cls):
        if not cls._instance:
            cls._instance = super().__new__(cls)
        return cls._instance

# Uso del Singleton
instance1 = Singleton()
instance2 = Singleton()

print(instance1 is instance2)  # True
```

___
Patrón de Diseño Factory
```python
class Product:
    def operation(self):
        pass

class ConcreteProduct1(Product):
    def operation(self):
        return "Product 1"

class ConcreteProduct2(Product):
    def operation(self):
        return "Product 2"

class Creator:
    def factory_method(self):
        pass

class ConcreteCreator1(Creator):
    def factory_method(self):
        return ConcreteProduct1()

class ConcreteCreator2(Creator):
    def factory_method(self):
        return ConcreteProduct2()

# Uso del Factory
creator1 = ConcreteCreator1()
product1 = creator1.factory_method()
print(product1.operation())  # Output: Product 1

creator2 = ConcreteCreator2()
product2 = creator2.factory_method()
print(product2.operation())  # Output: Product 2

```
___
Patrón de Diseño Observer

```python
class Subject:
    def __init__(self):
        self._observers = []

    def attach(self, observer):
        self._observers.append(observer)

    def detach(self, observer):
        self._observers.remove(observer)

    def notify(self, event):
        for observer in self._observers:
            observer.update(event)

class Observer:
    def update(self, event):
        pass

class ConcreteObserver1(Observer):
    def update(self, event):
        print("Observer 1: ", event)

class ConcreteObserver2(Observer):
    def update(self, event):
        print("Observer 2: ", event)

# Uso del Observer
subject = Subject()
observer1 = ConcreteObserver1()
observer2 = ConcreteObserver2()

subject.attach(observer1)
subject.attach(observer2)

subject.notify("Event occurred")  # Output: Observer 1: Event occurred, Observer 2: Event occurred
```
___
Patrón de Diseño Strategy
```python
class Context:
    def __init__(self, strategy):
        self._strategy = strategy

    def execute_strategy(self):
        self._strategy.algorithm()

class Strategy:
    def algorithm(self):
        pass

class ConcreteStrategy1(Strategy):
    def algorithm(self):
        print("Strategy 1")

class ConcreteStrategy2(Strategy):
    def algorithm(self):
        print("Strategy 2")

# Uso del Strategy
context = Context(ConcreteStrategy1())
context.execute_strategy()  # Output: Strategy 1

context = Context(ConcreteStrategy2())
context.execute_strategy()  # Output: Strategy 2
```



