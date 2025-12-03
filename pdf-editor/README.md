# Introduction

```
Is there anything better than Only Office for Editing and modifying PDF documents on Linux?
```
Source: https://discourse.ubuntu.com/t/pdf-editor/71573

How about [Pandoc](https://pandoc.org/)?

```
If you need to convert files from one markup format into another, pandoc is your swiss-army knife.
```

Source: https://pandoc.org/

Back in 2008, I had to learn how to type up mathematical proofs in LaTeX for Advanced Calculus homeworks with [Prof. King](https://squash.1gainesville.com/info.jksched.html) at the University of Florida. Years later, I continued to use it in graduate school to write [my dissertation](https://repository.lib.fsu.edu/islandora/object/fsu:254496) and several published journal articles. LaTeX with pdflatex has all the capabilities needed to edit PDF documents, but it is a typeset language. It is not a GUI like Adobe.

When I entered the workforce, they wanted me to use `.docx` format so that people could edit the file to make it fit a particular template. For years, I straddled document versions. At one point I made my own javascript text editor using MathJax because I could more easily convert the LaTeX math equations. I learned to type up my technical write-ups as `.docx` files and lived a bit subdued for a while. Every time I handed it off to someone else, they broke all the referenced equations, tables, and figures. I had to fix them manually. This problem is exactly what LaTeX is made to solve.

Then I learned about Markdown and Pandoc. Guess what, this `README.md` file is written in markdown and github renders it to display it for you. The `.md` extension stands for markdown (I think), but it is just a plain text document with some very intuitive human readable syntax.

- You can make lists
- *You can emphasize groups of words* 
- **You can make bold statements**
- You can use inline latex math equations $\frac{1}{n}\sum_{i=1}^ny_i$
- You can use block latex math equations 
$$
\begin{align*}
\frac{1}{n}\sum_{i=1}^ny_i
\end{align*}
$$
(sometimes)
- You can include images ![yaupon](./images/yaupon.jpeg)
- You can include links [yaupon](https://www.inaturalist.org/observations/28146000)
- You can even make tables that you can read as plain text

| column 1 | column 2|
|----------|---------|
|r1 c1     |r1 c2    |
|r2 c1     |r2 c2    |

You can even include code blocks

``` python
import numpy as np
```

If you combine this with pandoc, then you can convert your markdown into `html`,`.odt`, `.docx` (ms-word),`pptx` (powerpoint), and many more.

Here are the basic steps:

- [Install Pandoc](https://pandoc.org/installing.html)
    - Basically you download a `.deb` file and unpack it, or you could use apt.
``` bash
sudo apt update
sudo apt install pandoc
```
- Install LaTeX with pdflatex
```bash
sudo apt update
sudo apt install texlive-latex-base
sudo apt-get install texlive-latex-extra
```
- Create a markdown file
    - I made one for you called `first-markdown.md`

- Use the commands found in the [demos page](https://pandoc.org/demos.html)

```bash
mkdir -p artifacts
# You can make a webpage with markdown and pandoc
pandoc first-markdown.md -o artifacts/first-markdown.html
# You can make a OpenDocument Text
pandoc first-markdown.md -o artifacts/first-markdown.odt
# You can output docx ms-word
pandoc -s first-markdown.md -o artifacts/first-markdown.docx
# pdf
pandoc first-markdown.md -o --toc artifacts/first-markdown.pdf
# Beamer Slides
pandoc -t beamer first-markdown.md -o artifacts/first-markdown-beamer.pdf
```


You can see some example outputs [here](./artifacts)
