Markdown-eszközök {#markdown-eszkozok}
=================

<div id="markdown-logo">
![A Markdown nyelv logója\label{markdown-logo}](img/markdown-logo.png)

</div>

A dokumentum lefordítása Linux alatt
------------------------------------

A dokumentum fordításához szükséges a Pandoc és a \TeX Live \LaTeX-disztribúció telepítése:

```bash
sudo apt-get install texlive-base pandoc pandoc-citeproc
```

A diplomaterv a `make` parancssal fordítható le, a konfigurációt a `Makefile` állomány tartalmazza.

Alapadatok megadása
-------------------

A diplomaterv alapadatait (cím, szerző, konzulens, konzulens titulusa) a `Makefile` fájlban lehet megadni a változók módosításával:

```
AUTHOR=...
TITLE=...
```

Az alapértelmezett kimenet a PDF, de különböző kimeneteket is megadhatunk a `make` parancs céljának változatásával:

```bash
make pdf
make html
make mobi
```
