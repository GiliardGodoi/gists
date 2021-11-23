# Expressão regulares

Meta caracteres:
''' . ^ $ * + ? { } [ ] \ | ( ) '''

[ ] define um conjunto de caracteres. Exemplos [abc] [a-c] [0-9]. Metacaracteres dentro de um conjunto são tomados como caracteres normais. Exceção: ^

^ indica negação ou complemento. Por exemplo, [^5] encontra qualquer caracter exceto 5.

\ backslash. Caracter de escape. Pode representar conjuntos predefinidos, quando seguido por uma letra.

\d equivale a [0-9]

\D equivale a [^0-9]

\s equivale a [\t\n\r\f\v]

\S equivale a [^\t\n\r\f\v] white space character

\w equivale a [a-zA-Z0-9_]

\W equivale a [^a-zA-Z0-9_]

Pode ser incluidas dentro de uma classe, por exemplo, [\s,.]

Caracter especial . corresponde qualquer caracter exceto new line \n re.DOTALL

## Repeating Things

\* equivale a 0 (zero) ou mais repetições de uma classe. Equivalente a {0,}

\+ equivale a 1 ou mais repetições. Equivalente a {1,}

? equivale a 0 ou 1 repetições. Equivalente a {0,1}

{m,n} minimo de m, e máximo n repetições

## Compiling Regular Expressions

import re
p = re.compile('ab*')

re.IGNORECASE i

re.GLOBAL g

## Module-Level Functions

re.compile(*pattern, flags=0*)

Flags could be:
  
    re.ASCII or re.A
    re.DEBUG -> display debug information
    re.IGNORECASE or re.I
    re.LOCALE
    re.MULTILINE or. re.M
    re.DOTALL or re.S
    re.VERBOSE or re.X
  
re.match(*str_pattern, string, flags=0*)

re.fullmatch(*str_pattern, string, flags=0*) -> return if matches the whole string

re.search(*str_pattern, string, flags=0*) -> return a match object for the first ocurrence

re.split(*pattern, string, maxsplit=0, flags=0*) -> like str split

re.findall(*pattern*, *string*, *flags=0*) -> return a list of strings

re.finditer(*pattern*, *string*, , *flags=0*) -> return a iterator

re.sub(*pattern, repl, string, count=0, flags=0*)

re.purge() -> clear the regular expression cache <(0).(0)>

## Pattern Object

    pattern = re.compile("d")
    pattern.search('dog')
    
Pattern.search(*string [, pos[, endpos]]*)

Pattern.match(*string [, pos[, endpos]]*)

Pattern.fullmatch(*string [, pos[, endpos]]*) (>3.4)

Pattern.split(*string, maxsplit=0*)

Pattern.findall(*string [, pos[, endpos]]*)

Pattern.finditer(*string [, pos[, endpos]]*)

Pattern.sub(*repl, string, count=0*)

Pattern.subn(*repl, string, count=0*) -> return a tuple like (new_string, number_of_subs_made)

Pattern.flags

Pattern.groups

Pattern.groupindex

Pattern.pattern -> string that was compiled


## Match Object

group() -> retorna a string

start() -> retorna a posição inicial

end() -> retorna a posição final

span() -> retorna uma tupla com a posição inicial e final

Evitar **'The Backslash Plague'** utilizar raw string in python: r'/parttner/'


## Examples

...

## References

[REGULAR EXPRESSION How To](https://docs.python.org/3/howto/regex.html#regex-howto)

[Regular Expression module](https://docs.python.org/3/library/re.html)

[Regular Expression Test Online](https://regexr.com/)
