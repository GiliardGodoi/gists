# Strings

Strings são tantos objetos built-in como também existe um módulo `string`.
```python
import string
```

Documentação oficial:
- [string module](https://docs.python.org/3/library/string.html)

## Indexing ans Slice

Indexing
```python
s = 'hello world'
s[1]
```
Slicing
```python
s[start: end : step]
```

Para reverter uma string:
```python
s[::-1]
```

## Operadores

```python
foo + bar

foo * 5

'z' in 'abc'
'z' not in 'xyz'
```

## Built-in functions

Converte um inteiro em um caracter
```python
chr(90)
```
Converte um caracter em um inteiro:
```python
chr('Z')
```
Tamanho de uma string
```python
len('hello world')
```
Converte um objeto em uma string correspondente. Ver também `__str__`:
```python
str(90) # '90'
```

## Interpolação

```python
n = 5, m = 4

prod = n * m

f'The product of {n} and {m} is {prod}'
```

## Case

```python
foo.capitalize()
foo.lower()
foo.upper()
foo.swapcase()
foo.title()
```

## Find and Replace

```python
s.count(<sub> [, <start>[, <end>]])

s.endswith(<suffix> [, <start>[, <end>]])

s.startswith(<prefix> [, <start>[, <end>]])

s.find(<sub> [, <start>[, <end>]])

s.rfind(<sub> [, <start>[, <end>]])

s.index(<sub> [, <start>[, <end>]])

s.rindex(<sub> [, <start>[, <end>]])

```

## Classification

```python
s.isalnum() # is alphanumeric ?

s.isalpha()

s.isdigit()

s.isidentifier() # is a valid python identifier ?

s.islower()

s.isupper()

s.isprintable()

s.isspace() # \n \t \r

s.istitle()

```

## Formatting

```python
s.center(<width>[, <fill>])

s.expandtabs(tabsize=8) # replace \t by white space

s.ljust(<width>[, <fill>])

s.lstrip([<chars>])

s.rjust(<width>[, <fill>])

s.rstrip([<chars>])

s.zfill(<width>) # pads a string on the left with zeros

s.replace(<old>, <new>[, <count>])

s.strip([<chars>])
```

## Converting between string and iterables

```python
s.join(<iterable>)
    ', '.join(['foo', 'bar', 'baz', 'qux'])
    ':'.join('corge') # results 'c:o:r:g:e'

s.partition(<separator>) # divides a string based on a separator. Retorna uma tupla

s.split(sep=',', maxsplit=-1) # splits a string into a list of substring

s.rsplit(sep='.', maxsplit=-1)

s.splitlines([keepends]) # | True or 1

```

## Bytes Object

```python
b = b'foo bar baz'

type(b)

bytes(<string>, <encoding>)

b = bytes('foo.bar', 'utf8)

bytes(<size>)
```

## Constantes interessantes do modulo `string`

Alfabeto ASCII
```python
string.ascii_letters

string.ascii_lowercase
# 'abcdefghijklmnopqrstuvwxyz'

string.ascii_uppercase
# 'ABCDEFGHIJKLMNOPQRSTUVWXYZ'
```

Números:
```python
string.digits
# '0123456789'
```

Pontuação:
```python
string.punctuation
# !"#$%&'()*+,-./:;<=>?@[\]^_`{|}~
```

Outras bases numéricas:
```python
string.hexdigits
# '0123456789abcdefABCDEF'.

string.octdigits
# '01234567'
```

ASCII caracteres considerados espaços em branco:
```python
string.whitespace
# ' \t\n\r\x0b\x0c'
```

## Formatting

```python
from string import Formatter
```

## References

Real Python: [Strings and Characters Data in Python](https://realpython.com/python-strings/) Acessado em <18/07/2018>
