---
title: Project Jupyter
---

Project Jupyter is a collection of services that are used for creating and sharing live and interactive code in multiple languages. It requires Python to be install to set it up.

## Examples to try

- [TypeScript](jupyter/TypeScript.md)  
  Id generation, random seed generator.

## Installation

There are multiple tools that can be used for working with Jupyter notebooks. When installing with `pip`, run as an administrator. Adding `--user` may also work (but I have not tested this).

### Jupyter Lab

Web based application.

```
pip install jupyterlab
```

Launch via the command.

```
jupyter lab
```

[jupyterlab.readthedocs.io](https://jupyterlab.readthedocs.io/)

### Jupyter Lab Desktop

Desktop (Electron) application. Installation instruction found on GitHub. 
[jupyterlab/jupyterlab-desktop](https://github.com/jupyterlab/jupyterlab-desktop)

It can also be installed using winget.
```
winget install jupyterlab
```

### Jupiter Notebook

The classic way of working with Jupyter notebooks.

```
pip install notebook
```

Launch via the command.

```
jupyter notebook
```

[jupyter-notebook.readthedocs.io](https://jupyter-notebook.readthedocs.io/)

### Voilà

Voilà can be used to create an interactive dashboard based on your notebooks.

```
pip install viola
```

[voila.readthedocs.io](https://voila.readthedocs.io/)

### VS Code

There is an extension by Microsoft for working with Jupyter notebooks in VS Code: [marketplace.visualstudio.com/items?itemName=ms-toolsai.jupyter](https://marketplace.visualstudio.com/items?itemName=ms-toolsai.jupyter)

## dotnet (C#, F#) and PowerShell support.

Install dotnet interactive

```
dotnet tool install --global Microsoft.dotnet-interactive
```

Setup for Jupyter

```
dotnet interactive jupyter install
```

## TypeScript / JavaScript

Via 'deno', unstable.

```
deno jupyter --unstable
```

Using `tslab`.

```
npm install -g tslab
```

```
tslab install
```

## Other languages

Other language kernels are also available, there is a list of some of them on the Jupyter GitHub wiki: [jupyter/jupyter/wiki/Jupyter-kernels](https://github.com/jupyter/jupyter/wiki/Jupyter-kernels)


# Converting notebooks

You can use `nbconvert` to convert to different formats. Converting to formats other than Markdown and HTML have additional dependencies.  
[Using as a command line tool](https://nbconvert.readthedocs.io/en/latest/usage.html)

```
jupyter nbconvert .\notebook.ipynb --to markdown
```

```
jupyter nbconvert .\notebook.ipynb --to html
```