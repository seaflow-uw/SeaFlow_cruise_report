# SeaFlow_cruise_report
This repository consists of a knitR file and supporting documents to build an R and LaTeX cruise report for SeaFlow data.  To customise the report for your cruise:
* Ensure you are connected to the Seaflow-OPP drive.  Otherwise, change `path` to a local directory containing the database, OPP files, and VCT files for the cruise.
* Update `cruise`. 
* Cruise identifiers will be pulled from a Google sheets file.  To authorize R to access this worksheet, copy the link provided in your terminal and paste it in a browser.
* Tweak the identification of temperature and salinity outliers in the `hydro` block.

In a bash shell, use R to knit a LaTeX .tex file:

```
Rscript -e "library(knitr); knit('SeaFlow_cruise_report_template.Rnw')"
```

Build the pdf from the LaTeX file.  You may need to do this 3 times sequentially to get all the labels and references complete.

WARNING:  The "--shell-escape" option allows a shell to download files from our GitHub repository required to build the LaTeX file.  Double check that these are all files you trust.    

```
pdflatex --shell-escape SeaFlow_cruise_report_template.tex
```

To get the bibliography, use BibTeX:

```
bibtex SeaFlow_cruise_report_template
```

Then LaTeX the .tex file again once or thrice as above.
