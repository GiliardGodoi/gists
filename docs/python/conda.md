# Conda Commands

Resumo de comandos

## Gerenciando ambientes (enviroments)

### Criar um novo ambiente (*enviroment*)

```cmd
conda create --name myprojecenv
conda create --name myprojecenv python=3.8
conda create --name myprojecenv python=3.8 pandas astropy scipy=0.15.0
conda install -n myenv scipy
```

```cmd
conda env create -f environment.yml
```

```cmd
conda create --name myclone --clone myenv
```

### Criando um ambiente a partir de um arquivo de especificação

```
conda install --name myenv --file spec-file.txt
```

### Instalar um ou mais pacotes

```cmd
> conda install pandas
>
> conda install pandas numpy
```

### Listando os ambientes disponíveis

```
conda env list
conda info --envs
```

### Specification File

```cmd
conda list --explicit
```
Irá produzir um arquivo do tipo

```
> # This file may be used to create an environment using:
> # $ conda create --name <env> --file <this file>
> # platform: osx-64
> @EXPLICIT
> https://repo.anaconda.com/pkgs/free/osx-64/mkl-11.3.3-0.tar.bz2
> https://repo.anaconda.com/pkgs/free/osx-64/numpy-1.11.1-py35_0.tar.bz2
> https://repo.anaconda.com/pkgs/free/osx-64/openssl-1.0.2h-1.tar.bz2
> https://repo.anaconda.com/pkgs/free/osx-64/pip-8.1.2-py35_0.tar.bz2
> https://repo.anaconda.com/pkgs/free/osx-64/python-3.5.2-0.tar.bz2
> https://repo.anaconda.com/pkgs/free/osx-64/readline-6.2-2.tar.bz2
> https://repo.anaconda.com/pkgs/free/osx-64/setuptools-25.1.6-py35_0.tar.bz2
> https://repo.anaconda.com/pkgs/free/osx-64/sqlite-3.13.0-0.tar.bz2
> https://repo.anaconda.com/pkgs/free/osx-64/tk-8.5.18-0.tar.bz2
> https://repo.anaconda.com/pkgs/free/osx-64/wheel-0.29.0-py35_0.tar.bz2
> https://repo.anaconda.com/pkgs/free/osx-64/xz-5.2.2-0.tar.bz2
> https://repo.anaconda.com/pkgs/free/osx-64/zlib-1.2.8-3.tar.bz2
```

Pode ser salvo em um arquivo

```cmd
conda list --explicit > spec-file.txt
```

```
conda env export > environment.yml
```

### Removendo um ambiente

```cmd
conda remove --name myenv --all
```

# Referências

[Conda Documentation](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html#creating-an-environment-with-commands) **How to manage a enviroment**
