# Git Commands

Git é uma conhecida ferramenta para versionamento de código.

A documentação oficial pode ser encontrada em: [Git - Reference](https://www.git-scm.com/docs)

## Introdução
...

## Repositório
O que é um repositório?

### Repositório local

Criar um repositório no diretório atual:
```
git init
```

Verificar o estado dos arquivos e diretório no repositório:
```
git status
```


#### Adicionando arquivos para área de stage
Adicionar todos os arquivos (ou diretórios) para a área de stage:
```
git add .
```

Adicionar arquivo específico para a área de stage:
```
git add meu-arquivo.py
```

Adicionar um arquivo que está listado no `.gitignore` (por que eu iria querer fazer isso?)
```
git add -f meu-arquivo-ignorado.py
```

#### Commitando mudanças
Commit nas áreas de stage (considerando que ela não está fazia)
```
git commit -m "Mensagem do commit"
```

Comitar um arquivo ou vários (quando se utiliza essa opção?)
```
git meu-arquivo.txt

git arquivo1.txt arquivo2.txt
```

> Importante: quando uma mensagem não é informada pelo parâmetro `-m` o git irá abrir o editor de texto definido nas configurações.

Comitar arquivos que já estão sendo monitorados, sem precisar adicionar na área de *staged*
```
git commit -a -m "message"
```

#### Renomeando arquivos
Renomear um arquivo ou diretório pelo git (pode ter as suas vantagens)
```
git mv <origem> <destino>
```

#### Removendo arquivos

Remover um arquivo:
```
git rm pagina-web.html
```

Remover um diretório:
```
git rm -f diretorio
```

#### Desfazendo ações
Desfazendo uma alteração local quando o arquivo não foi adicionada ao área de *staged*:
```
git checkout meu-arquivo.txt
```

Desfazendo uma alteração local, com o arquivo adicionado na área de *staged*:
```
git reset HEAD meu-arquivo.txt
```

Se o resultado abaixo for exibido, o arquivo foi retirado da área de *staged* mas ainda não foi alterado no diretório
```
Unstaged changes after reset:
M	meu-arquivo.txt
```

Agora para alterar no diretório, basta executar o comando anterior:
```
git checkout meu-arquivo.txt
```

### Repositório remoto
Baixar um clone de um repositório remoto
```
git clone link-para-o-repositorio-remoto
```

Exibir os links dos repositórios remotos vinculados ao repositório local:
```
git remote [-v]
```
Opções:
- `-v` : verbose

Vincular repositório local ao repositório remoto:
```
git remote add origin git@link-para-repositorio-remoto.git
```

Desvincular repositórios local e remoto:
```
git remote rm origin
```

Exibir informações do repositório remoto:
```
git remote show origin
```

Renomear um repositório remoto (por padrão eles são nomeados como *origin*)
```
git remote rename origin new-name
```

#### Workday: push and pull

Realizando o primeiro push para um repositório remoto
```
git push --set-upstream origin master
```
ou
```
git push -u origin main
```

Enviando mudanças para um repositório remoto:
```
git push
```

Baixando as mudanças do repositório remoto.
```
git pull
```

Buscar as alterações mas não aplica-las no branch atual (por que eu iria querer fazer isso?)
```
git fetch
```

#### Branches
Listar branches do repositório local
```
git branch
```

Criar branch
```
git branch bug-123
```

Criar branch e trocar
```
git checkout -b bug-123
```

Trocar entre branches locais (que já existem)
```
git checkout bug-123
```

Apagar branch local
```
git branch -d bug-123
```

Renomear branch: *de dentro*
```
git checkout old-branch-name
git branch -m new-branch-name
```

Renomear branch: *de fora*
```
git branch -m old-branch-name new-branch-name
```

#### Branches em repositórios remotos

Baixar branch de um repositório remoto
```
git checkout -b bug-142 origin/bug-142
```

Criar branch em um repositório remoto:
```
git push origin bug-143
```

Criar branch em um repositório remoto com *nome diferente*:
```
git push origin localname:remotename
```

Apagar branch em um repositório remoto:
```
git push origin bug-145 --delete
```

Renomear branch de repositório remoto:

> Não é possível renomear um repositório remoto diretamente. Porém, pode-se substituir o branch no reposiório remoto utilizando a seguinte sequência de comandos:
```
git checkout old-name
git branch -m new-name
git push origin :old-name (*)
git push --set-upstream origin new-name
```

(\*) na verdade eu não entendi esse comando: `git push origin :old-name`

## Visualizar histórico
Exibir histórico
```
git log --oneline -n5
```
Opções:
 - `--oneline` : exibe uma modificação por linha.
 - `-n5` : exibe as *n* últimas modificações.
 - `--decorate`: identifica o último commit do repositório remoto em relação ao repositório loca.

Ou então:

```
git log --oneline -n5 --decorate
```

Exibe resumo do histórico:
```
git log --stat
```

Exibe:
```
commit ...
Author: ...
Date: ...
Message:
	...
Files:
	arquivo.txt | 21
1 files changed, 21 insertions(+), 0 deletions(-)
```

Exibir informações resumidas em uma única linha:
```
git log --pretty=oneline
```

Exibir informações com uma formatação específica:
```
git log --pretty=format:"%h - %an, %ar : %s"
```
Opções:
-   %h: Abreviação do hash;
-   %an: Nome do autor;
-   %ar: Data;
-   %s: Comentário.

Ver outras opções de formatação em: [Git - Viewing the Commit History](http://git-scm.com/book/en/v2/Git-Basics-Viewing-the-Commit-History)

 Exibir o histórico de um arquivo específico:
 ```
git log -- caminho-do-arquivo
```

Exibir o histórico de um usuário em específico:
```
git log --author= ...
```

## Stash
Para alternar entre branches, é necessário comitar as alterações do branch atual para permitir a troca.
Quando, por alguma razão, não é interessante realizar um comite das alterações atuais, podemos criar um *stash*.

Um *stash* é como se fosse um branch temporário que contém apenas as alterações não comitadas. Os principais comandos dessa funcionalidade são:

Criar um *stash*:
```
git stash
```

Listar *stashes*:
```
git stash list
```

Voltar para o último *stash*:
```
git stash apply
```

Voltar para um *stash* especifício (então é possível criar vários *stashes* a partir de um *branch*)
```
git stash apply stash@{2}
```
Onde 2 é o indíce do stash desejado.

Criar um branch a partir de um stash:
```
git stash branch b-name
```

Apagar um stash:

Apagar um stash específico:

## Merge
...

## Rebasing
...

## Reescrevendo o histórico (danger zone)
...

## Criar Tag (ou Releases)
Uma *tag* serve para marcar a geração de um release (uma versão do *software*)

## Obter ajuda
Comando geral:
```
git help
```

Para comandos em especifíco:
```
git help add
git help commit
git help log
```

## Configurações do Git
Definir informações do usuário
```
git config --global user.name "Giliard Godoi"
git config --global user.email <...>
```

Definindo o editor padrão:
```
git config --global core.editor vim
```
Outros editores possíveis (?)

Definir a ferramenta de merge:
```
git config --global merge.tool vimdiff
```

Definindo arquivos a serem ignorados de forma global (por que eu iria querer fazer isso?)
```
git config --global core.excludesfile ~/.gitignore
```

Listar configurações:
```
git config --list
```
---

## Sobre
Algumas informações importantes que não estão diretamente relacionadas ao conteúdo.

### Fork Me!
Esse arquivo é baseado no trabalho de Leonardo Comelli: [Lista de comandos úteis do GIT](https://gist.github.com/leocomelli/2545add34e4fec21ec16)

Ao longo dos anos eu realizei umas mudanças, fiz os meus próprios forks, mas senti a necessidade de ir mais a fundo e reorganizar as informações.

Os princípios para organizar essas notas são:

### Inserindo uma entrada
Para inserir uma nota, utilize o seguinte padrão:


Texto explicativo
```
git <command>
```

