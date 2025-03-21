# RStudio
RStudio DWR-Next NLA

    Some handy setup-tips when using RStudio.
    Current version of RStudio Desktop in DWR-Next env. is (as of 2025/03/21) RStudio 2024.12 "Kousa Dogwood":
    RStudio-2024.12.0-467 : ( https://s3.amazonaws.com/rstudio-ide-build/electron/windows/RStudio-2024.12.0-467.exe ) 
    R 4.4.2 'Innocent and Trusting' : ( https://cran.r-project.org/bin/windows/base/old/4.2.2/ )

Install packages faster by skipping compilation

    # Use latest R 4.4.2 binaries repository and you don't have to compile.
    # The windows-binaries repository is managed by Posit software.
    # To add windows-binary-4.4.2 and set as default repository, run following:
    setRepositories(addURLs = c(PRAN_R442="https://packagemanager.posit.co/cran/2025-02-27"),ind=0)

    # Test package install and see how much faster everything is without compilation.
    install.packages("shiny") #this installs shiny 1.7.3 with all dependencies takes 2 minutes
    install.packages("tidyverse") #this installs tidyverse 1.3.2 with all dependencies takes 4 minutes   

Alternative way to install packages via list

    # Create package list, Create already installed package list, and install new packages
    packages <- c( "htmlwidgets","DT","shiny","leaflet","dplyr" )
    installed_packages <- packages %in% rownames(installed.packages())
    if (any(installed_packages == FALSE)) {
      install.packages(packages[!installed_packages]) }


You can still install older packages via version number and CRAN

    # To download and compile older versions of packages from CRAN, you need the 'remotes' package.
    install.packages("remotes") 
    # To install older version, looks like following command:
    install_version("shiny", version = "0.10.1", repos = "http://cran.us.r-project.org") 

