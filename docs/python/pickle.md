# Pickle module

---
> **__CUIDADO:__** Aviso de Segurança
>
> O módulo pickle não faz a verificação dos dados que está lendo quando a existência de códigos ou inicializações maliciosas.
>
> Por isso somente faça o unpickle de objetos apenas de fontes confiáveis.
---

Módulo para serialização de objetos Python:

## Uso básico (salvar e ler arquivos binários)

Salvar dados.

```python
import pickle

data = {k : randrange(500) for k in set(choices(range(1000), k=100))}

with open("example.pck", "wb") as file:
    pickle.dump(data, file)
```

Para ler o objeto:

```python
import pickle

with open("example.pck", "rb") as file:
    data = pickle.load(file)
```

## Modos de arquivos

Relembrando:
- **rb**: ler um arquivo em formato binário;
- **rb+**: permite ler e escrever em um arquivo com formato binário;
- **wb**: escrever em um arquivo em formato binário;
- **wb+**: permite escrever e ler em uma arquivo com formato binário;
- **ab**: abre um arquivo para apensar (appending) em formato binário;
- **ab+**: appending and reading in binary format.

## Anexando objetos a um mesmo arquivo

```python
import pickle

file = open("temperature.pickle", "ab")

b = { 'celcius' : 93 }
pickle.dump(b, file)

# ... some time before

d = { 'farenheight' : 10}
pickle.dump(d, file)

# ... finishing the program

file.close()
```

Para ler vários objetos de um arquivo criado no modo **a** executamos tantas operações de load até surgir um `EOFError`.

```python
import pickle

file = open("temperature.pickle", "rb")

while True:
    try:
        data = pickle.load(file)
        # do something ...
    except EOFError:
        break

file.close()
```

## Referências

[Documentação do módulo `pickle`](https://docs.python.org/3/library/pickle.html)