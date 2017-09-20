
# info-mb: Infographics for Monterey Bay

This is a simplified demonstration of how to use the [`infographiq`](https://github.com/marinebon/infographiq) package to create your own interactive infographics. This repository contains everything needed to generate the static html website hosted by github in the `./docs` folder.

## getting started

To get started making your own infographic you can use this repository as a starting point. Simply clone or download the repository, start editing, and building your site using `infographiq::create_info_site(site_title = "Monterey Bay Infographics", render_modals = T)`.

## overview

A basic overview of the functionality is given below. It is recommended that you browse both the code and the resulting website (at https://marinebon.github.io/info-mb/) as you read through this overview. Also see the Flordia Keys site, info-fk, for more examples.

Using the data in this repo, the website is generated into the `./docs` folder by running `create_info_site.R`. Github can then host the website from within the `./docs` directory.

We create 2 infographics here: 1. Kelp Forest 2. Pelagic. Images for these infographics are in the `./svg` directory and can be opened using inkscape.

The two svg files are refrenced by name in `svg_elements.csv`. In this file we define species that we want to make interactive, i.e.  Phytoplankton and Pinnipeds. The `svg_id` in this file must match the element id set in the svg file (under object properties in inkscape). 

For phytoplankton, we want to include some text in the "modal" popup window which appears when the parrotfish silhoutte is clicked. To do this we created a file in markdown format at `./captions/phytoplankton.md` and give this value in the `svg_elements.csv` column `modal text`.

For the plots that show within a modal popup, we use `plot_indicators.csv`. In this file we give the `svg_id` that matches with the ids in the svg file(s) and in `svg_elements.csv`, along with the details to create the plot.

# infographiq
R library for creation of interactive infographics for data-driven storytelling

# usage overview

1. Define your infographic by creating the following files:

* `./svg_elements.csv`
* `./plot_indicators.csv`
* `./svg/*.svg`

For example files see [the info-demo repository](https://github.com/marinebon/info-demo), or one of the following regional infographics that have been generated using the infographiq package:

* [Florida Keys infographics](https://github.com/marinebon/info-fk/)
* [Monterey Bay Infographics](https://github.com/marinebon/info-mb)

2. Use infographiq from an R console to generate the website:

```R
# install
install.packages(c("tidyverse", "stringr", "rmarkdown", "dygraphs", "xts", "lubridate", "geojsonio", "RColorBrewer", "leaflet", "crosstalk", "servr", "roxygen2", "futile.logger"))

if (!require('devtools')) install.packages('devtools')
devtools::install_github('marinebon/infographiq')

# load
library(infographiq)

# run i.e.
create_info_site(site_title = "Monterey Bay Infographics", render_modals = T)
```

# dev workflow

```R
# to test your infographic generation with a local copy of infographiq
# you must install from local source
require('devtools')
install_local('../infographiq')
```
