# Install R

```bash
sudo apt update && sudo apt upgrade -y

# update indices
sudo apt update -qq

# install two helper packages we need
sudo apt install --no-install-recommends software-properties-common dirmngr -y

# add the signing key (by Michael Rutter) for these repos
# To verify key, run gpg --show-keys /etc/apt/trusted.gpg.d/cran_ubuntu_key.asc 
# Fingerprint: 298A3A825C0D65DFD57CBB651716619E084DAB9
wget -qO- https://cloud.r-project.org/bin/linux/ubuntu/marutter_pubkey.asc | sudo tee -a /etc/apt/trusted.gpg.d/cran_ubuntu_key.asc

# add the R 4.0 repo from CRAN -- adjust 'focal' to 'groovy' or 'bionic' as needed
sudo add-apt-repository "deb https://cloud.r-project.org/bin/linux/ubuntu $(lsb_release -cs)-cran40/" -y
sudo apt install --no-install-recommends r-base -y
sudo add-apt-repository ppa:c2d4u.team/c2d4u4.0+ -y
```

# Notebook
Install R packages

```R
# sudo rm -rf /home/codespace/R/x86_64-pc-linux-gnu-library/4.1/devtools
# sudo apt-get install libxml2-dev -y
install.packages("devtools")

# https://irkernel.github.io/installation/
install.packages('IRkernel')
IRkernel::installspec()
install.packages('IRdisplay')
```

# GIS specific purposes

## GDAL on Linux

```bash
# https://mothergeo-py.readthedocs.io/en/latest/development/how-to/gdal-ubuntu-pkg.html
sudo add-apt-repository ppa:ubuntugis/ppa
sudo apt-get update
sudo apt-get install gdal-bin -y
export CPLUS_INCLUDE_PATH=/usr/include/gdal
export C_INCLUDE_PATH=/usr/include/gdal

# https://stackoverflow.com/questions/64826887/install-r-cran-rgdal-on-ubuntu-20-04
# https://stackoverflow.com/questions/12141422/error-gdal-config-not-found-while-installing-r-dependent-packages-whereas-gdal
sudo apt install r-cran-rgdal libudunits2-dev gfortran libgdal-dev libjq-dev libv8-dev libprotobuf-dev protobuf-compiler -y
```

## R Packages

```R
# https://geocompr.robinlovelace.net/
remotes::install_github("geocompr/geocompkg", dependencies=TRUE)
```

# Uninstall all packages except base

```bash
# https://stackoverflow.com/questions/16382647/remove-all-packages-that-do-not-come-with-r
cd ~/R/x86_64-pc-linux-gnu-library/
rm -rf 4.1/
```