# Jupyter Notebook (jnb)

- IPython (short for Interactive Python) was started in 2001 by Fernando Perez as an enhanced Python interpreter, and has since grown into a project aiming to provide, in Perez's words, "Tools for the entire life cycle of research computing." If Python is the engine of our data science task, you might think of IPython as the interactive control panel.

- jnb is built on IPython

- Install jnb using CLI `pip install jupyterlab` "jupyterlab" is recent version of jnb

- after installing open jnb by `jupeter notebook` . This will start a (local) jupyter-server and will serve the jnb-app (with aview of folder/directory initially) on port 8888 which can be viewed on any browswer. You can close server and release port 8888 by ctrl+C in terminal

- if you want to run "jupyter lab" instead of "jupyter notebook" then run `jupyter lab` command

- .ipynb is the extension for a jnb file, e.g. my-notebook.ipynb

- a jnb is consists of two types of cells

  1. Markdown cells
  2. Code cells

- shift+Enter runs current cell and goes to next cell

- ctrl+Enter runs current cell and stays in the same cell so that you may edit it again and see results

- Esc key takes you out of the cell (without running it). Now you may use J and K keys to move forward and backward in code cells

- after using Esc in cell quikly clicking A or B keys adds a new cell "above" or "below" that cell.

- quickly pressing D key twice (DD) will delete that cell.

- Unlike script files, in a jnb the code cells are not required to run in a top-to-bottom manner. It's one of the real powerful things about Jupyter lab and Jupyter notebooks. But it also allows for some bad practices where you can make a notebook that doesn't actually run end to end.

- It's important to go through once you're saving off your notebook and to make sure it actually can run all the way from the top to the bottom. Or else you're really going to confuse yourself (or other users of that notebook) later.

- Instead of local you can develop jnbs on clouds as well:

  1. Google colab
  2. Kaggle notebooks

- f you have Google account the go to Google colab at `https://colab.research.google.com/` or `https://colab.research.google.com/notebooks/`
