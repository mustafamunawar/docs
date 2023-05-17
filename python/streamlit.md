# Streamlit (st)

- `pip install streamlit`

- `import streamlit as st`

- A simple st code:

```python
import streamlit as st
st.title('This is a title')
# the text is displayed as Github-Markdown (ghmd). Syntax information can be found at: https://github.github.com/gfm.
# in ghmd text between "_" rendered in italics, :colorname[text] rendered in color and :emojishortcode: gives emoji
st.title('A title with _italics_ :blue[colors] and emojis :sunglasses:')
st.header('A header with _italics_ :blue[colors] and emojis :sunglasses:')
st.subheader('A subheader with _italics_ :blue[colors] and emojis :sunglasses:')
```

- st emojis shortcodes are at https://streamlit-emoji-shortcodes-streamlit-app-gwckff.streamlit.app

- Other text commands include `st.caption`, `st.write`, `st.markdown`, `st.title`, `st.title`, `st.title`, `st.title`, `st.title`,

- `st.write()` is the Swiss Army knife of Streamlit commands: it does different things depending on what you throw at it. Unlike other Streamlit commands, write() has some unique properties:

  1. You can pass in multiple arguments, all of which will be written.
  2. Its behavior depends on the input types as follows.
  3. It returns None, so its "slot" in the App cannot be reused.

- `st.write()` signature : `st.write(*args, unsafe_allow_html=False, **kwargs)`

- args are one or many objects to print to the App. Following list explain arg types:

  - write(string) : Prints the formatted Markdown string, with support for LaTeX expression, emoji shortcodes, and colored text.
  - write(data_frame) : Displays the DataFrame as a table.
  - write(error) : Prints an exception specially.
  - write(func) : Displays information about a function.
  - write(module) : Displays information about the module.
  - write(class) : Displays information about a class.
  - write(dict) : Displays dict in an interactive widget.
  - write(mpl_fig) : Displays a Matplotlib figure.
  - write(altair) : Displays an Altair chart.
  - write(keras) : Displays a Keras model.
  - write(graphviz) : Displays a Graphviz graph.
  - write(plotly_fig) : Displays a Plotly figure.
  - write(bokeh_fig) : Displays a Bokeh figure.
  - write(sympy_expr) : Prints SymPy expression using LaTeX.
  - write(htmlable) : Prints _repr_html_() for the object if available.
  - write(obj) : Prints str(obj) if otherwise unknown.

- Magic commands are a feature in Streamlit that allows you to write almost anything (markdown, data, charts) without having to type an explicit command at all. Just put the thing you want to show on its own line of code, and it will appear in your app. Here's an example:

```python
# Draw a title and some text to the app:
'''
# This is the document title

This is some _markdown_.
'''
import pandas as pd
df = pd.DataFrame({'col1': [1,2,3]})
df  # 👈 Draw the dataframe

x = 10
'x', x  # 👈 Draw the string 'x' and then the value of x

# Also works with most supported chart types
import matplotlib.pyplot as plt
import numpy as np

arr = np.random.normal(1, 1, size=100)
fig, ax = plt.subplots()
ax.hist(arr, bins=20)

fig  # 👈 Draw a Matplotlib chart
```
