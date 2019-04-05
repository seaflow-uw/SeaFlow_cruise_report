# SeaFlow_cruise_report
This repository consists of a knitR file and supporting documents to build an R and LaTeX cruise report for SeaFlow data.  To customise the report for your cruise:
* Download all the files (except README) in this repository and put them in the same directory.
* Ensure you are connected to the SeaFlow-OPP drive.  Otherwise, change `path` to a local directory containing the database, OPP files, and VCT files for the cruise.
* Update `cruise`. 
* Cruise identifiers will be pulled from the Google sheets file "SeaFlow instrument log."  To authorize R to access this worksheet, copy the link provided in your terminal during your first `knitr` run and paste it in a browser. You should only have to do this once.
* Tweak the outlier detection for temperature and salinity in the `hydro` block.

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
