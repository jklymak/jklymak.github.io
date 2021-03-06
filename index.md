---
layout: default
title: Home
---

# Uvic Ocean Physics software page

This is a list of useful software we may need.

## [git](github.com)

git is the version control system we use.  Some of our stuff is kept on [github](github.com), which is a public repository of our code.  See [http://jklymak.github.com]().

    brew install git

You probably want to set up a github account.

## [jekyll](http://jekyllrb.com)

    sudo gem install jekyll

jekyll is the site generator for these webpages, and how we will serve the documentation for each project.  Github runs it automatically if you follow the directions at [http://jklymak.github.io/projtemplate]().  However, if you want to preview the webpage locally before committing and pushing it, then you can run

    jekyll serve --baseurl ''

and you will be able to see it at [http://localhost:4000/]().  

## [brew](http://brew.sh)

If `brew` is not already on your computer, see Install Homebrew at [http://brew.sh]() and follow the prompts.  Brew is the unix package manager for OS X, and it largely has what we want.  However, note that a lot of things that I used to use brew for are now available by anaconda, and using one packaged manager is better than a lot.  



## Editors and Document Preparation:

For general editing, I use [Atom](https://atom.io).  

For formal document preparation, I keep a Latex files.  For OS X use [MacTeX](https://tug.org/mactex/) and it will install TexShop and BibDesk

For [LaTeX](http://www.latex-project.org) I use [TexPad](https://www.texpadapp.com).  

For my bibliographies, I use [bibtex](http://www.bibtex.org) and [Bibdesk](http://bibdesk.sourceforge.net).  

## Data Analysis

For data analysis I almost exclusive use python now.  All the libraries I use can be installed from [Anaconda](https://store.continuum.io/cshop/anaconda/).  

### Python libraries

Most libraries not included with [Anaconda](https://store.continuum.io/cshop/anaconda/) can be included by running

    conda update
    conda install newlib

Many cutting edge libraries are at [conda-forge](https://conda-forge.org/#about)
So I do

    conda config --add channels conda-forge
    conda config --set channel_priority strict

to make sure it is included in the search paths for installs.

My usual minimal install is:

    conda install matplotlib scipy xarray dask netcdf4 seawater jupyter


### [jupyter notebook](http://jupyter.org)

I run [jupyter notebook](http://jupyter.org) for most of my analysis.  To get this running I type:

    % jupyter-notebook


Then, you need to open [Firefox](www.mozilla.org/en-US/firefox/new/), to [http://localhost:9999/](http://localhost:9999/) and your notebook will appear.  You can start entering python code and running it.  The result will be saved in `Notebookname.ipynb` in the directory you are working in (where you choose the `Notebookname`).  

You can enable some cool extensions for the notebook:

     conda install -c conda-forge jupyter_contrib_nbextensions

I particularly like `toc2` (table of contents) and `Snippets` (pre-filled cells).
