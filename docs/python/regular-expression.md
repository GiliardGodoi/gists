# Regular expression

```python
import re
```

Documentação oficial:
- [re module documentation](https://docs.python.org/3/library/re.html)

See also:
- [re : How To](https://docs.python.org/3/howto/regex.html#regex-howto)
- [Wikipedia: Regular expression](https://en.wikipedia.org/wiki/Regular_expression)
- [Untitled Pattern](https://regexr.com/)

## Meta caracteres:

> ''' . ^ $ * + ? { } [ ] \ | ( ) '''

- `[ ]` (conjunto) define um conjunto de caracteres. Exemplos [abc] [a-c] [0-9]. Metacaracteres dentro de um conjunto são tomados como caracteres normais. Ver: `[^ ]`;

- `( )` (grupo) define um grupo;

- `[^ ]` (negação) indica negação, exceção ou complemento. Por exemplo, `[^5]` encontra qualquer caracter exceto 5;

- `\` (backslash) ou escape. Pode representar conjuntos predefinidos, quando seguido por uma letra;

- `.` (ponto) corresponde a qualquer caractere, exceto new line `\n`. Corresponde a `re.DOTALL`;

- `^` (inicio) identifica um padrão no início da string.

- `$` (final) identifica um padrão no final da string.

- `|` (ou... ou...) expressa uma alternativa

## Caracteres especiais

- `\n` : new line
- `\t` : tab space
- `\r` :
- `\f` :
- `\v` :

## Conjuntos pré-definidos

- `\d` equivale a `[0-9]`

- `\D` equivale a `[^0-9]`

- `\s` equivale a `[\t\n\r\f\v]`

- `\S` equivale a `[^\t\n\r\f\v]` white space character

- `\w` equivale a `[a-zA-Z0-9_]`

- `\W` equivale a `[^a-zA-Z0-9_]`

Podem ser incluídos dentro de uma classe ou conjunto, por exemplo, [\s,.]

## Indicando repetições

- `{m, n}` minímo de `m` e máximo de `n` repetições.

- `*` equivale a zero ou mais repetições de uma classe. Equivalente a `{0,}`

- `+` equivale a 1 ou mais repetições, isto é, `{1,}`

- `?` equivale a 0 ou 1 repetições:  `{0,1}`

- `{n}` exatamente `n` repetições

## Module-Level Functions

Compile uma padrão em um objeto que pode ser reusado.
```python
re.compile(*pattern, flags=0*)
```

Flags
```python
    re.ASCII      or re.A
    re.UNICODE
    re.IGNORECASE or re.I
    re.MULTILINE  or re.M
    re.DOTALL     or re.S
    re.VERBOSE    or re.X
    re.LOCALE  #
    re.DEBUG   # display debug information
```
> É possível combinar flags com o operador `|`

```python
re.compile(pattern, flags=0)
```

Verifica toda a string por uma correspondência. Retorna um objeto match para a primeira ocorrência. Retorna um objeto `match`.
```python
re.search(str_pattern, string, flags=0)
```

Verifica o início da string por uma correspondência. Retorna um objeto `match`.
```python
re.match(str_pattern, string, flags=0)
```

Verifica se toda a string corresponde ao padrão desejado. Retorna um objeto `match`.
```python
re.fullmatch(str_pattern, string, flags=0)
```

Divide uma `string` de acordo com o padrão desejado:
```python
re.split(pattern, string, maxsplit=0, flags=0)
```

Retorna uma lista de palavras que correspondem ao padrão desejado:
```python
re.findall(pattern, string, flags=0)
```

Retornar um objeto iterável com os matches da string:
```python
re.finditer(pattern, string, , flags=0)
```

Substituir um padrão por uma outra expressão em uma string.
```python
re.sub(pattern, repl, string, count=0, flags=0)
```
Onde:
- `pattern` pode ser uma string ou um Pattern Object
- `repl` pode ser uma nova string ou uma função
- `string` é a string onde será feita a substituição
- `count` é o número máximo de substituições

Se `repl` é uma função, ela recebe um *match object*:
```python
>>> def dashrepl(matchobj):
...     if matchobj.group(0) == '-': return ' '
...     else: return '-'

>>> re.sub('-{1,2}', dashrepl, 'pro----gram-files')
'pro--gram files'

>>> re.sub(r'\sAND\s', # pattern
            ' & ',     # repl
            'Baked Beans And Spam',  # string
            flags=re.IGNORECASE)
'Baked Beans & Spam'
```

Já `re.subn` perfoma a mesma operação que `re.sub` porém returna uma tupla indicando a nova string e o número de substituições: `(new_string, number_of_subs_made)`
```python
re.subn(pattern, repl, string, count=0, flags=0)
```

Adiciona `\` (*backslash*) para caracteres especiais:
```python
re.escape('https://www.python.org')
# https://www\.python\.org
```

Limpar o cache de expressões regulares. Por que eu iria fazer isso?
```python
re.purge()
```

## Padrão (*Pattern object*)

Compila uma expressão regular em um objeto que pode ser reusado.
```python
pattern = re.compile("d")
pattern.search('dog')
```
Verifica toda a string e retorna a primeira ocorrência.
```python
Pattern.search(string [, pos[, endpos]])
```
Onde:
- `pos` indica o indice da posição inicial

Verifica se o início da (sub)string corresponde ao padrão desejado.
```python
Pattern.match(string [, pos[, endpos]])
```

Verifica se toda a string corresponde com o padrão desejado.
```python
Pattern.fullmatch(string [, pos[, endpos]])
```

Divide a string no padrão considerado:
```python
Pattern.split(string, maxsplit=0)
```
O resultado é algo como:
```python
['string-anterior', 'pattern', 'string-apos']
```

Retorna uma lista de strings que correspondem ao padrão.
```python
Pattern.findall(string [, pos[, endpos]])
```

Retorna uma iterador com os objetos *matches*.
```python
Pattern.finditer(string [, pos[, endpos]])
```

Retorna uma nova string substituindo as conrrespodencias pelo conteúdo de `repl`
```python
Pattern.sub(repl, string, count=0)
```

Além de retornar uma nova string, também retorna a quantidade de vezes que a substituição foi realizada.
```python
Pattern.subn(repl, string, count=0)
```

Atributos:
```python
Pattern.flags
```

```python
Pattern.groups
```

```python
Pattern.groupindex
```

Indica a string ou padrão compilado.
```python
Pattern.pattern
```

## *Scanner object*
```python
scanner.match()
scanner.search()
scanner.pattern
```

## Correspondência (*Match object*)

Objeto que indica uma correspondência.
```python
<re.Match object; span=(5, 11), match='RegExr'>
```

Retorna a (sub)string correspondente a um grupo:
```python
match.group()
```
Pode existir diversos grupos dentro de uma correspondência e esses grupos são identificados por números inteiros.

Retorna a posição inicial da correspondência:
```python
match.start()
```

Retorna a posição final da correspondência:
```python
match.end()
```

Retorna uma tupla indicando a posição inicial e final de uma correspondência:
```python
match.span()
```

```python
match.groups()
```

```python
match.groupdict()
```

## The backslash plague

Leia o artigo *The Backslash Plague* nesse [link](https://docs.python.org/3/howto/regex.html#the-backslash-plague).


## Exemplos de expressões regulares

Outros exemplos podem ser vistos neste
[notebook](https://colab.research.google.com/drive/1FDYFdDqUTtVyUGg7WTZTT0lgBnwda7cw?usp=sharing) em Google Collab.
