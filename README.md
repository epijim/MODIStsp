
-   [MODIStsp](#modistsp)
    -   [Important News ! MODIStsp content migrated to our new website !](#important-news-modistsp-content-migrated-to-our-new-website)
    -   [Problems and Issues](#problems-and-issues)
    -   [<i class="fa fa-desktop" aria-hidden="true"></i> System Requirements](#system-requirements)
    -   [<i class="fa fa-windows" aria-hidden="true"></i> Installing on Windows](#installing-on-windows)
    -   [<i class="fa fa-linux" aria-hidden="true"></i> Installing on Linux Systems](#installing-on-linux-systems)

[![](https://www.r-pkg.org/badges/version-ago/MODIStsp)](http://cran.rstudio.com/web/packages/MODIStsp/index.html) [![](http://cranlogs.r-pkg.org/badges/grand-total/MODIStsp?color=red)](http://cran.rstudio.com/web/packages/MODIStsp/index.html) [![Travis-CI Build Status](https://travis-ci.org/lbusett/MODIStsp.svg?branch=master)](https://travis-ci.org/lbusett/MODIStsp) [![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.290683.svg)](https://doi.org/10.5281/zenodo.290683) [![Coverage Status](https://img.shields.io/codecov/c/github/lbusett/MODIStsp/master.svg)](https://codecov.io/github/lbusett/MODIStsp?branch=master)

MODIStsp
========

MODIStsp is a "R" package devoted to automatizing the creation of time series of rasters derived from MODIS Land Products data. MODIStsp allows to perform several preprocessing steps (e.g., download, mosaicing, reprojection and resize) on MODIS data available within a given time period. Users have the ability to select which specific layers of the original MODIS HDF files they want to process. They also can select which additional Quality Indicators should be extracted from the aggregated MODIS Quality Assurance layers and, in the case of Surface Reflectance products, which Spectral Indexes should be computed from the original reflectance bands. For each output layer, outputs are saved as single-band raster files corresponding to each available acquisition date. Virtual files allowing access to the entire time series as a single file can be also created. All processing parameters can be easily selected with a user-friendly GUI, although non-interactive execution exploiting a previously created Options File is possible. Stand-alone execution outside an "R" environment is also possible, allowing to use scheduled execution of MODIStsp to automatically update time series related to a MODIS product and extent whenever a new image is available.

*MODIStsp is developed and maintained by L.Busetto and L.Ranghetti, from the Institute of Remote Sensing of Environment - National Research Council - Italy (CNR-IREA)*

Important News ! MODIStsp content migrated to our new website !
---------------------------------------------------------------

-   25/07/2017 - As of today, **most of the content related to MODIStsp has been moved to our new website at [lbusett.github.io/MODIStsp](http://lbusett.github.io/MODIStsp/)**, which provides a much better user interface and ease of access to MODIStsp-related information. From now on, please **consult the new website for detailed and updated information on the package**.

-   Also our previous FAQ page on github containing info for solving common installation, downloading and processing problems and issues was discontinued and **migrated at [lbusett.github.io/MODIStsp/articles/faq.html](http://lbusett.github.io/MODIStsp/articles/faq.html)**.

Problems and Issues
-------------------

-   Please **report any issues** you may encounter in our [issues page on github <i class="fa fa-github-square" aria-hidden="true"></i>](https://github.com/lbusett/MODIStsp/issues).

<i class="fa fa-desktop" aria-hidden="true"></i> System Requirements
--------------------------------------------------------------------

`MODIStsp` requires [R](https://cran.r-project.org) v &gt;= 3.2.1 and [GDAL](http://www.gdal.org) (Geospatial Data Abstraction Library) v &gt;= 1.11.1 **with support for HDF4 raster format** to be installed in your system. Brief instructions for installing R and GDAL can be found [HERE](http://lbusett.github.io/MODIStsp/articles/installation.html#installing-r-and-gdal).

------------------------------------------------------------------------

<i class="fa fa-windows" aria-hidden="true"></i> Installing on Windows
----------------------------------------------------------------------

You can install the stable version of `MODIStsp` from CRAN:

`install.packages("MODIStsp")`

, or the development version (containing the latest improvements and bug fixes) from github:

``` r
library(devtools)
install_github("lbusett/MODIStsp")
```

Note that **if the `GTK+` library is not already installed on your system, installation may fail**. In that case, please install and load the `gWidgetsRGtk2` library beforehand:

``` r
install.packages("gWidgetsRGtk2")
library(gWidgetsRGtk2)
```

Upon loading `gWidgetsRGtk2`, an error window will probably appear. This signals that library "GTK+" is not yet installed on your system or is not on your PATH. To install itpress "OK". A new window dialog window will appear, asking if you want to install "GTK+". Select "Install GTK" and then "OK" . Windows will download and install the GTK+ library. When it finishes, the RSession should be restarted and you should be ready to go !

In case RStudio doesn't automatically restart or continuously asks to install GTK+ again, kill it form "Task Manager" (or restart the R session from RStudio "Session" menu), reload RStudio and the try to reload `gWidgetsRGtk2`. If it loads correctly, you should be ready to go.

If it still fails, try downloading the GTK+ bundle from:

<http://ftp.gnome.org/pub/gnome/binaries/win64/gtk+/2.22/gtk+-bundle_2.22.1-20101229_win64.zip> (OR <http://ftp.gnome.org/pub/gnome/binaries/win32/gtk+/2.22/gtk+-bundle_2.22.1-20101227_win32.zip> if on Win32)

, unzip the archive on a folder of your choice (e.g., `C:\\Program Files\\GTK+`), then add the path to its "bin" subfolder (e.g., `C:\\Program Files\\GTK+\\bin\\` to your system PATH environment variable.

Restart your system and try loading again `gWidgetsRGtk2`: if it loads ok, you should be ready to install `MODIStsp`

<i class="fa fa-linux" aria-hidden="true"></i> Installing on Linux Systems
--------------------------------------------------------------------------

To install `MODIStsp` on Linux, you have to first install the following required dependencies:

-   `Cairo` &gt;= 1.0.0, `ATK` &gt;= 1.10.0, `Pango` &gt;= 1.10.0, `GTK+` &gt;= 2.8.0, `GLib` &gt;= 2.8.0 (required by package `RGtk2`)
-   `Curl` (required by package `curl`)
-   `GDAL` &gt;= 1.6.3, `PROJ.4` &gt;= 4.4.9 (required by package `rgdal`)

On *Debian and Ubuntu-based* systems, to install those packages open a terminal and type:

``` bash
sudo apt-get install r-cran-cairodevice r-cran-rgtk2 libcairo2-dev libatk1.0-dev libpango1.0-dev 
libgtk2.0-dev libglib2.0-dev libcurl4-openssl-dev libgdal-dev libproj-dev
```

On *rpm-base systems*, to install packages open a terminal and type:

``` bash
sudo yum install libcairo2-devel libatk1.0-devel libpango1.0-devel gtk2 gtk2-devel 
glib2-devel libcurl-devel gdal-devel proj proj-devel proj-epsg proj-nad
```

Then, you can install the stable version of MODIStsp from CRAN:

``` r
install.packages("MODIStsp")
```

, or the development version (containing the latest improvements and bug fixes) from github;

``` r
library(devtools)
install_github("lbusett/MODIStsp")
```
