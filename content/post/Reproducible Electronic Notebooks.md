+++
Categories = ["Jupyter", "IPython"]
Description = ""
Tags = ["Electronic Notebooks", "Jupyter", "IPython"]
date = "2015-04-24T10:22:32-07:00"
menu = "main"
title = "Reproducible Electronic Notebooks"

+++

# The Jupyter Notebook

The practice of reproducible/open science makes every step of the scientific process for particular publication easily accessible, repeatable, and open for discussion. This implies that the procedure, the raw data, the processing code, and the plot-generating code are freely available, commented for understanding, and polished for sanity. Anyone interested in reviewing your material should easily follow your pipeline and be able to reproduce your output.

This sounds like a ton of overhead work. Most of the time, the analysis of data is a bit half-hazard. We do a quick hack to plot results ASAP, so we can begin thinking about our interpretations and publication. We certainly do not want anyone else to see that ugly script we wrote in R to parse some files. And, we definitely do not want them to try and use it! And, we do not have the time to go back and clean up all these files and scripts we used for that one paper three years ago. Its not laziness; its trully the lack of time. We need a solution that will help us practice reproducibility on the fly; a tool where we can still hack, but others can still follow along.

The Jupyter Notebook project (previously called IPython) provides an impressive solution. The Jupyter Notebook is stable, language agnostic electronic notebook. There have been a few attempts at creating an electronic notebook in recent years, none stand up the IPython Community. [Try it out for yourself!](https://try.jupyter.org)

## How does an electronic notebook need?

This section compiles a list of things that are necessary for an electronic notebook to be helpful. 

1. Low costs for a lab
2. Run code within notebook (but what language?)
3. Word processor or Mark-up text for publications or notes.
4. Equations in the text. (After all, this is a science notebook.)
5. Plots in the notebook, below the code that generated it?
6. Easy to use
7. Conversion to blogs, PDF, slides, etc.
8. Easy to share with anyone
9. Run on remote server
10. Standardize across a lab
11. Secure 

## Jupyter's performance as an electronic notebook?

1. Low cost? How about **free**? Jupyter notebook is completely free and open source for anyone to use. Simply download here. As a bonus, the open source community around the Jupyter Notebook is highly active and passionate about the project, so it is getting better everyday. 

2. Originally called IPython Notebook (the "I" standing for **Interactive** Python notebook), the Jupyter notebook is, first and foremost, an interactive computing environment. It is comprised of *cells* that enable the user to write chunks of code and run them separately from the rest of the notebook. What language? You choose! The notebook is a language-agnostic frontend that runs code cells through kernels connecting it to any backend. In fact, the rename to **Jupyter** Notebook was in acknowledgement of this agnosticism, highlighting the three core languages (Julia, Python, and R). However, many other kernels exist (such as Matlab, Octave, Javascript, etc.); see the list here. This means, you only need to learn one interface/frontend no matter how many languages you know. 

3. The cells mentioned above can also be **text** cells, rendered by Markdown. This is a lightweight mark-up language used in many blogging circles. Its **very** easy to use and is explained further here. This almost makes the notebook a worthy blogging editor. 

4. Equations can be written in Markdown cells using Latex syntax (via MathJax). Write a latex formula between double dollars signs to render the equation.

5. The notebook plots figures inline with text and code. This might be one of the most attractive features of electronic notebooks in general. To enable this feature in the Jupyter notebook, one simply needs to run the following line of code: 

    ```%matplotlib inline```

6. The notebook is easy to install (site), intuitive to use, and includes many tutorials on the web. If you want example notebooks, you can flip through exampe notebooks here.

7. The Jupyter notebook comes with a internal conversion API, called NBConvert. This allows you to output your notebooks as Latex/PDF documents, HTML pages, *interactive* presentation slides (through reveal.js), and stand-alone scripts.  

8. The Notebook can be saved into a lightweight format, called JSON, that makes sharing notebooks (even large ones) easy. If you want a notebook to be READ-ONLY, you can share the notebook using the NBViewer application online.

9. There are a few different ways to run the notebook on a remote server. The stable solution is to use **Jupyterhub**. This allows you to set up a Jupyterhub server and allow users to connect through a password protected sign-in page (using server credentials or Github credentials). 

10. The Jupyterhub provides a great way to standardize your lab's electronic notebooks. This implementation allows multiple users on a single server. No one *has* to download the notebook or any dependencies locally on their machines. All these dependencies can be installed and loaded in one location, on a remote server, and everyone has access to the same programming environment.

11. The Jupyter Notebook has a large, active community constantly improving its performance. Chances are, if any bug exists, it will be fixed immediately. If you find a point of vulnerability or annoyance, you can post an issue to the community, and it will be fixed quickly!

## How does it work?

The Jupyter notebook is an web-application and interactive programming shell. That means, the frontend is hosted in a browser, written entirely in HTML, Javascript, and CSS. This is advantageous to the notebook's design, providing nearly endless possibilities for future development and allowing the notebook to access libraries like MathJax (Latex rendering), D3 (data visualization library), etc. It also enables users to embed notebooks in blogs (simple HTML), share notebooks is a lightweight format (JSON data), run notebooks remotely through HTTP protocols (or the stable Jupyterhub, described below), add custom extensions easily, and build browser widgets for GUI interaction with data. Though the frontend is Javascript, the notebook server is entirely Python. This server manages the architecture of the notebook and handles all messaging between the frontend and code-executing **kernel**. The kernel is the main machinery for executing the code (in its native language) written by a user. Amazingly, the Jupyter team designed the Notebook such that the kernel could be any language, making the Notebook language agnostic. 

## Above and beyond: more Jupyter Notebook features

1. **Widgets**: the Notebook includes many interactive widgets, like slidebars, accordians, user input, etc. that allow one to interact with plots using these GUIs. You can also easily design your own widget. 

2. **Terminal**: the Notebook includes a terminal in the web-application that allows your to navigate the local filesystem using your local terminal environment. You can even launch an IPython terminal within an IPython Notebook!

3. **VIM and Emacs Shortcuts**: the notebook has two modes, edit and command mode, which allow you to quickly navigate notebook editing through shortcuts like VIM and Emacs.

4. **Google Drive**: recently, the Jupyter team integrated the Notebook with Google Drive. Now you can share and run notebooks on Google Drive using this extension. 

