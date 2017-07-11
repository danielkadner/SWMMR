SWMMR - Modify inputs and read SWMM outputs from R
==================================================

_SWMMR_ is an R package to interface the EPA Storm Water Management
Model (SWMM). It can modify SWMM input files, run SWMM, and read SWMM
binary output files.


## Installation from Github

1. Install `devtools` (type in the R command line)
```
install.packages("devtools")
```

3. Install SWMMR (type in the R command line)
```
library(devtools)
install_github("scheidan/SWMMR")
```


## Usage

This is a minimal example, see the package help for more options.
```R
library(SWMMR)

## Run SWMM
runSWMM <- function(inputfile = "input.inp",
                    reportfilename="report.rpt",
                    outputfilename="output.out",
                    SWMMexe="swmm5.exe")

## Read output file
result <- openSWMMOutput("output.out")

result    # print summary

readSubcatchments(ff, names=c("S1", "S2", "S3"), variables=c("rainfall", "runoff"))

readNodes(ff, names="Nod1")               # read all varbles for node "Nod1"

readLinks(ff, names=NULL, variables=NULL) # read all variables for all links

readSystem(ff)                            # read all system variables
```

## Alternatives
An alternative is the \code{swmmr} package by dleutnant \url{https://github.com/dleutnant/swmmr}.
It should be faster (due to C++ reader), the interface is a more low-level compared to _SWMMR_.

## Acknowledgments
This package is based on [this](https://github.com/PeterDSteinberg/RSWMM) work of Peter Steinberg.