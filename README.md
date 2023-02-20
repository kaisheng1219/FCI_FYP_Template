# FCI FYP Template

This is an *unofficial* template for FCI FYP Report. 

This current version is based on the [FCI FYP Guideline from 2022/23 session](https://github.com/kaisheng1219/FCI_FYP_Template/blob/master/reportGuideline.pdf). Please check the latest guideline for potential changes in copyright, declaration, formattings, and etc.

*This template is modified from FCI FYP Template. (Credit to: Dr. Poo Kuan Hoong)*

## Overleaf or Local LaTeX Environment

Although Overleaf is recommended by most students, the basic version of it has a compilation timeout issue. If you are expecting yourself inserting many high reso images into your report, then it is not recommended to use Overleaf. Set up the LaTeX environment on your pc as this allows you to compile faster and has no limitations on whatsoever.

## Setting Up LaTeX Environment 

### For Windows and MacOS

1. Install TexLive from (https://www.tug.org/texlive/windows.html)
2. Install Visual Studio Code from (https://code.visualstudio.com/download)
3. Open up Visual Studio Code and install LaTeX Workshop extension
4. Press Ctrl + Shift + P for Windows or Cmd + Shift + P for MacOS
5. Go to the bottom and insert the following json codes, make sure there is a comma before you paste the codes
```json
"latex-workshop.latex.tools": [
    {
        "name": "pdflatex",
        "command": "pdflatex",
        "args": [
            "-synctex=1",
            "-interaction=nonstopmode",
            "-file-line-error",
            "-output-directory=%OUTDIR%",
            "%DOC%"
        ]
    },
    {
        "name": "bibtex",
        "command": "bibtex",
        "args": [
            "%DOCFILE%"
        ],
        "env": {}
    }
],
"latex-workshop.latex.recipes": [
    {
        "name": "pdflatex", 
        "tools": [
            "pdflatex",
            "bibtex",
            "pdflatex",
            "pdflatex"
        ]
    }
]
```
7. Open and edit thesis.tex file. Edit the `\author`, `\title`, `\submissionyear`, `\submissionmonth`, `\degree`, `\major`, `\session` accordingly.
8. Edit the rest of the files accordingly.
9. To include a new chapter, simply create a new `.tex` file and make sure you include the link to the file to `thesis.tex` by including the command `\include{newchapter}`

## For Debian/Ubuntu

1. Install texlive-full with apt-get (approx 3GB) and [TexMaker] (http://www.xm1math.net/texmaker/download.html#linux):

  ```
  $ sudo apt-get install texlive-full
  $ sudo apt-get install texmaker
  ```

## Compiling with Makefile

Provided you have CMake and pdflatex + bibtex commands properly installed. You can run `make` in the directory and it will generate `thesis.pdf`.

On Mac, it will open the PDF upon completion. Sublime Text users can just build it inside the editor (cmd + b for mac).

  ```
  $ cd path/to/your-tex-project
  $ make
  ```
