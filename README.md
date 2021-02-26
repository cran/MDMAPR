
<!-- README.md is generated from README.Rmd. Please edit that file -->

# MDMAPR

<!-- badges: start -->

<!-- badges: end -->

<img src="images/mdmaprlogo.png" width=400>

The MDMAPR is a Shiny web application that is able to merge raw qPCR fluorescence data and metadata together to facilitate the spatial visualization of species presence/absence detections. The application also has the ability to visualize qPCR fluorescence curves and standard curves to evaluate data quality. 

The MDMAPR shiny application has the option to be connected to a custom developed MySQL database in order to populate the applications interface with data. Data can also be uploaded directly on the application for analysis. The MDMAPR 2.0 is built using R shinydashboard which is an open-source R package for web application development.

To learn how to set up a MDMAPR MySQL database to run with the MDMAPR Shiny application please refer to the [wiki](https://github.com/AlkaBenawra/MDMAPR/wiki).

## Installation

You can install the released version of MDMAPR from
[CRAN](https://CRAN.R-project.org) with:

``` r
install.packages("MDMAPR")
```

## Example on how to run MDMAPR without database connection: 
``` r
library(MDMAPR)

#Set dbInstance to no
dbInstance("No")

#Launch app to run application
launchApp()
```


## Example on how to run MDMAPR with database connection
``` r
library(MDMAPR)

#Set dbInstance to yes
dbInstance("Yes")

#Enter database connection details in dbVariables (Note: the entries for each variable are examples. Please ensure the variables you enter in the dbVariables function reflect your database instance.)
dbVariables(user = "root", password = "Test23!", dbname = 'MDMap_2.0', host = "127.0.0.1")

#Launch app to run application
launchApp()

```


## Mapping Dashboard

<kbd><img src="images/mapping_dashboard.png" width=600></kbd>

The Mapping Dashboard is used to perform geospatial analysis on qPCR run
samples. On this page, an interactive map displays location markers for
qPCR run sample collection locations and allows for filtering of markers
by Cq intensity, date, location, taxon details, machine type, project,
and assay. Hovering above a certain marker will display a pop-up menu
that shows information about the specific marker. As well, the page
contains a data table which shows detailed information about the markers
on the map. The data table will update based on the used filters. A copy
of the data table can be downloaded as a CSV by pressing the ‘Download
Mapped Markers Metadata’ button.

## Data Overview Page

<kbd><img src="images/data_overview.png" width=600></kbd>

The Data Overview page is used to analyze individual tube/well samples
and facilitates the quality control inspection of data. The page has
four tabs, which include the ‘Presence/Absence Samples’, ‘Amplification
Plot’, ‘Standard Curve Data Overview’, and ‘Standard Curve Plot’. The
‘Presence/Absence Samples’ tab displays a table which indicates if a
target sequence was detected in a tube/well based on its Cq Value. The
‘Amplification Plot’ shows the amplification curve associated with a
specific well sample from the ‘Presence/Absence Samples’ tab. The
‘Standard Curve Data Overview’ tab displays a table with information
related to the standard curve used for the samples in the
‘Presence/Absence Samples’ tab. Lastly, the ‘Standard Curve Plot’ tab
shows the plotted standard curve.

## Data Submission page

<kbd><img src="images/data_submission.png" width=600></kbd>

The Data Submission page is used to format raw qPCR fluorescence data
and associated metadata into a format that is acceptable to be added to
the MDMAPR 2.0 database for storage. On this page, a raw qPCR
experimental fluorescence file, a raw standard curve fluorescence file,
and the filled in MDMAPR 2.0 metadata file are required. The Data
Submission tool will parse the data into 13 CSV files. A preview of the
tables is viewable on the page. A zipped file of the CSVs can be
downloaded by pressing the ‘Download Data Submission Files’ button.
NOTE: Before you can upload the generated CSV data files into their
respective tables in the MDMAPR 2.0 database, the ID columns (projectID,
geographicRegionID, siteID, stationID, replicateID, extractID, assayID,
runID, pcrChemistryID, resultID, standardCurveID, and SCresultID) must
be manually changed from alphabetical characters to unique numeric IDs.
