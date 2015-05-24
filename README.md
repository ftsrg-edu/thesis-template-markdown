thesis-template-markdown
========================

[![Build status](https://travis-ci.org/FTSRG/thesis-template-markdown.svg?branch=master)](https://travis-ci.org/FTSRG/thesis-template-markdown)

Markdown template for thesis works in the Budapest University of Technology and Economics. **This is an experimental work** and is only recommended for users experienced with _both Markdown and LaTeX_.

Tested on Linux Mint 17.

### Requirements

* Pandoc 1.12.4.2 with pandoc-citeproc (see http://johnmacfarlane.net/pandoc/installing.html#all-platforms). Ubuntu 14.04 only provides version 1.12.2.1 which does not produce proper cross references in the HTML output.
* TeX Live (`texlive-full`)

### Usage

* Clone this repository:
  ```bash
  git clone git@github.com:FTSRG/thesis-template-markdown.git
  ```
  
* Use `make pdf`, `make html`, `make epub` to generate the thesis in your desired output format.
