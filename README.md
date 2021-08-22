# r-codespaces

# https://cran.r-project.org/
To install R

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

# Packages
To install R packages

```R
# sudo rm -rf /home/codespace/R/x86_64-pc-linux-gnu-library/4.1/devtools
# sudo apt-get install libxml2-dev -y
install.packages("devtools")

# https://irkernel.github.io/installation/
install.packages('IRkernel')
IRkernel::installspec()
install.packages('IRdisplay')
```
