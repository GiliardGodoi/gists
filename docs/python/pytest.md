# Pytest

Páginas de referência

1. [Documentação PyTest](https://docs.pytest.org/)
2. [Pytest: Uma introdução, por Dunossauro](https://www.youtube.com/watch?v=MjQCvJmc31A)
3. [Pytest Fixtures, por Dunossauro](https://www.youtube.com/watch?v=sidi9Z_IkLU)

Muito dessa nota foi baseada na Live do Dunossauro sobre Pytest.

## Metodologias de teste

GWT
    - GIVEN
    - WHEN
    - TEST

## Convenções

É importante observar algumas convenções:

- Os arquivos de testes devem ficar em um diretório denominado ```test``` ou ```tests``` na raiz do projeto.
- O nome dos arquivos de teste devem iniciar com o prefixo ```test_```
- Os nomes das funções de teste devem iniicar com o prefixo ```test_```

## Comandos básicos

```shell
pytest .
```

### Opções de linha de comando

```shell
    -v Mostra o nome dos testes executados (verbose)
    -s Mostra as saídas do console
    -k 'key_world' para filtrar os testes a serem executados com base no nome do método
    -x saída rápida (fail first)

    -m mark_name: executa os testes identificados com esse marcador. Ver seção sobre marcação.
    -m 'not mark_name': filtro invertido, não executa esse grupo de testes

    -rs: mostra a razão para os testes que foram ignorados (skipados)

    --pdb: console iterativo do debugador (quando um teste falha)
    --fixture: retorna todas as fixtures registradas
```

### Tipos de retornos do teste

Os possíves resultados para um teste são:

```shell
        . (ponto) Passou
        F : Falhou
        x (minúsculo) falha esperada
        X (maiúsculo) falha era esperada, mas não falhou
        s (skip) ignorou o teste
```

### Marcações, argumentos e metadados

Marcações serverm para prover informações adicionais como:

#### Criando um grupo de métodos de teste

```python
from pytest import mark

@mark.custom_tag_name
def test_brincadeira_retorna_queijo_quando_recebe_3():
    ...
```

#### Parametrização

```python
from pytest import mark
@mark.parametrize(
    'parametro,resultado',
    [(1,1), (2,2), (3, 'queijo'), (4, 4), (5, 'goiabada')]
)
def test_brincadeira_whatever(parametro, resultado):
    ...
```

Repare que o primeiro argumento são os nomes das variáveis recebida pela função. Uma string única separada por vírgula.

#### Pular testes (skip)

Simplesmente pular um teste:

```python
from pytest import mark

@mark.skip
def test_brincadeira_retorna_romeu_e_julieta():
    ...

@mark.skip(reason='bom motivo para pular um teste')
def test_testando_se_o_teste_eh_ignorado():
    ...
```

Pular um teste quando uma condição é percebida

```python
from pytest import mark

@mark.skipif(
    sys.platform == 'win32',            # condition
    reason='Não funciona no windows',   # reason
)
def test_faz_chamada_linux():
    ...
```

#### Quando se espera que o teste falhe

```python
from pytest import mark

@mark.xfail(
    sys.platform == 'win32',
    reason='Não é para funcionar no windows',
)
def test_esperado_que_falhe():
    ...
```

#### Fixtures

Assunto complexo. Tem haver com contexto.

### Exportando resultados em XML

```shell
pytest --junitxml report.xml
```

Onde ```report.xml``` é o nome do arquivo de destino.
