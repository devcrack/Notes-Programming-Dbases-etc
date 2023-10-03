## Funciones de Orden superior en Python 

Las funciones de orden superior en Python son aquellas que aceptan una o más funciones como argumentos y/o devuelven una función como resultado. Aquí hay algunos ejemplos de funciones de orden superior en Python:

1. Funciones map, filter, y reduce:

    - **map** aplica una función a todos los elementos de una secuencia:
    ```python
    def square(x):
        return x * x

    numbers = [1, 2, 3, 4]
    squared_numbers = map(square, numbers)
    print(list(squared_numbers))  # Output: [1, 4, 9, 16]
    ```
    - **filter** filtra los elementos de una secuencia que cumplan con una condición dada por una función:
    ```python
    def is_even(x):
        return x % 2 == 0

    numbers = [1, 2, 3, 4]
    even_numbers = filter(is_even, numbers)
    print(list(even_numbers))  # Output: [2, 4]
    ```

    - **reduce** aplica una función de dos argumentos acumulativamente a los elementos de una secuencia:

    ```python
    from functools import reduce

    def add(x, y):
        return x + y

    numbers = [1, 2, 3, 4]
    sum_numbers = reduce(add, numbers)
    print(sum_numbers)  # Output: 10
    ```

2. **Decoradores**:

    Los decoradores son una forma de funciones de orden superior que permiten envolver una función con comportamiento adicional:
    ```python
    def my_decorator(func):
    def wrapper():
        print("Something is happening before the function is called.")
        func()
        print("Something is happening after the function is called.")
    return wrapper

    @my_decorator
    def say_hello():
        print("Hello!")

    say_hello()  # Output:
                # Something is happening before the function is called.
                # Hello!
                # Something is happening after the function is called.
    ```

3. Funciones que devuelven funciones:

    También puedes crear funciones que devuelven otras funciones:    

    ```python
    def greet(prefix):
    def greeting(name):
        return f"{prefix} {name}"
    return greeting

    say_hello = greet("Hello")
    print(say_hello("World"))  # Output: Hello World

    ```

    ## Lambdas
    Las funciones lambda en Python son una forma de crear funciones pequeñas y anónimas en una línea. A continuación, se presentan algunos ejemplos de cómo se pueden utilizar las funciones lambda en Python:
    
    1. Definición Básica:
    ```python 
    square = lambda x: x * x
    print(square(5))  # Output: 25
    ```

    2. Uso con map

    ```python
    numbers = [1, 2, 3, 4]
    squared_numbers = map(lambda x: x * x, numbers)
    print(list(squared_numbers))  # Output: [1, 4, 9, 16]
    ```
    3. Uson con filter:
    ```python
    numbers = [1, 2, 3, 4]
    even_numbers = filter(lambda x: x % 2 == 0, numbers)
    print(list(even_numbers))  # Output: [2, 4]
    ```

    4. Uso con reduce:
    ```python
    from functools import reduce

    numbers = [1, 2, 3, 4]
    sum_numbers = reduce(lambda x, y: x + y, numbers)
    print(sum_numbers)  # Output: 10
    ```
    5. Uso con sorted:

    ```python
    pairs = [(1, 'one'), (2, 'two'), (3, 'three'), (4, 'four')]
    sorted_pairs = sorted(pairs, key=lambda x: x[1])
    print(sorted_pairs)  # Output: [(4, 'four'), (1, 'one'), (3, 'three'), (2, 'two')]
    ```
    6. Uso en un decorador:
        ```python
        def my_decorator(func):
        return lambda: "Result: " + str(func())

        @my_decorator
        def my_function():
            return 5 + 3

        print(my_function())  # Output: Result: 8```

    7. Uso en una funcion de Orden superior:

    ```python
    def apply_func(func, value):
    return func(value)

    result = apply_func(lambda x: x * x, 5)
    print(result)  # Output: 25
    ```
### Como funciona sort en Python
Sintaxis Basica de SORT:
        
```python
    sorted(iterable, *, key=None, reverse=False)
```
- **iterable**: El objeto iterable cuyos elementos se van a ordenar.

- **key**: Una función personalizada de un solo argumento para extraer una clave de comparación de cada elemento (por ejemplo, key=str.lower). El valor por defecto es None, lo que significa que los elementos se comparan directamente.
- **reverse**: Un booleano. Si se establece a True, los elementos se ordenan en orden descendente. Por defecto es False, lo que significa que los elementos se ordenan en orden ascendente.


1. Ordenamiento basico:

    ```python
        numbers = [34, 2, 23, 12, 45]
        sorted_numbers = sorted(numbers)
        print(sorted_numbers)  
        # Output: [2, 12, 23, 34, 45]
    ```
2. Ordenamiento por longitud:
```python
words = ["apple", "Banana", "cherry"]
sorted_words = sorted(words, key=len)
print(sorted_words)  # Output: ['apple', 'cherry', 'Banana']
```    
    
### Ejemplo decorador

```python
import time

def timing_decorator(func):
    def wrapper(*args, **kwargs):
        start_time = time.time()
        result = func(*args, **kwargs)
        end_time = time.time()
        print(f"Time taken: {end_time - start_time} seconds")
        return result
    return wrapper

@timing_decorator
def slow_function():
    time.sleep(2)

slow_function()

```
    
    

