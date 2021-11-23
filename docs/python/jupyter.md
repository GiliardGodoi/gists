
# Jupyter

Jupyter, IPython and IPythonKernel are three differents things.

## Creating a kernel specification

Pretend we have a conda environment called `lab`

```
(base)$ conda activate lab
(lab)$ conda install ipykernel
(lab)$ ipython kernel install --user --name=<any_name_for_kernel>
(lab)$ conda deactivate
```

## Listing kernels

```
jupyter kernelspec list
```

## Removing a kernel

```
jupyter kernelspec remove <kernel-name>
```

## Register a Kernel for a different enviroment

[Link](https://ipython.readthedocs.io/en/stable/install/kernel_install.html#kernels-for-different-environments) for documentation.

    source activate myenv
    conda install pip
    conda install ipykernel

    python -m ipykernel install --user --name myenv --display-name "Python (myenv)"
