# Decorators

Basicamente um decorator é uma função que recebe uma função e retorna uma função decorada, isto é, com uma funcionalidade adicionada.

```python
def decorator(func):

    def wrapper(*args, **kwargs):
        # do something before
        result = func(*args, **kwargs)
        # do somethin after
        return result

    return wrapper

@decorator
def concrete_func():
    # do your own stuff
    return False
```

Essa sintaxe é equivalente a:

```python
concrete_func = decorator(concrete_func)
```

## Modelo mental alternativo para entendermos *decorators*

Podemos pensar o símbolo `@` como um operador que receberá a função que será utilizada para decorar a função que estamos decorando. Quando escrevemos:

```python
@decorator
def my_function(*args):
    # do something
    return False
```

Podemos pensar que a função `decorator` será atribuída a `@` e o símbolo `my_function` receberá o retorno de `@(my_function)`.

Esse modelo é útil quando queremos implementar decorators com parâmetros e os `decorators factories`.

## Decorators com parâmetros

```python
def decorator(msg="write a message", code=200):

    def decorator(func):
        def wrapper(*args, **kwargs):
            # do somethin with msg and code parameters
            return func(*args, msg=msg, code=code, **kwargs)
        return wrapper
```

Uso

```python
@decorator(msg="example", code=200)
def send_message(dst,msg=None, code=None, **kwargs):
    # do something
    return True
```

## Decorators que recebem parâmetros opcionais

```python
def repeat(_func=None, *, num_times=2):
    def decorator_repeat(func):
        @functools.wraps(func)
        def wrapper_repeat(*args, **kwargs):
            for _ in range(num_times):
                value = func(*args, **kwargs)
            return value
        return wrapper_repeat

    if _func is None:
        return decorator_repeat
    else:
        return decorator_repeat(_func)
```

Uso:

```python
@repeat
def say_whee():
    print("Whee!")

@repeat(num_times=3)
def greet(name):
    print(f"Hello {name}")
```

## Classes que implementam decorators

## Stateful Decorators [Real Python example]

```python
import functools

def count_calls(func):
    @functools.wraps(func)
    def wrapper_count_calls(*args, **kwargs):
        wrapper_count_calls.num_calls += 1   ## <<---  grande mudança
        print(f"Call {wrapper_count_calls.num_calls} of {func.__name__!r}")
        return func(*args, **kwargs)
    wrapper_count_calls.num_calls = 0
    return wrapper_count_calls

@count_calls
def say_whee():
    print("Whee!")
```

## Decorators famosos

```python
@classmethod
@staticmethod
@property
@foo.setter
```

```python
@functools.wraps(func)
```

## Referências

Mais detalhes ver ppgi-steiner-gpx-crossover.

[Decorators for Humans](https://github.com/micheles/decorator)

[PEP 318 -- Decorators for Functions and Methods](https://www.python.org/dev/peps/pep-0318/).

**Real Python**. [Primer on Decorators](https://realpython.com/primer-on-python-decorators/#simple-decorators). Acessado em 15/06/2020. Disponível em <https://realpython.com/primer-on-python-decorators>

[Wiki Python Decorators](https://wiki.python.org/moin/PythonDecorators)
