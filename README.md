# SeaFlow_cruise_report
This repository consists of a knitR file and supporting documents to build an R and LaTeX cruise report for SeaFlow data.

In a bash shell, use R to knit a LaTeX .tex file:

```
Rscript -e "library(knitr); knit('SeaFlow_cruise_report_template.Rnw')"
```

Build the pdf from the LaTeX file.  You may need to do this 3 times sequentially to get all the labels and references complete:

```
pdflatex SeaFlow_cruise_report_template.tex
```

To get the bibliography, use BibTeX:

```
bibtex SeaFlow_cruise_report_template
```

Then LaTeX the .tex file again once or thrice as above.
