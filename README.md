# ubuntu_setup
This is how I setup my computer for bioinformatics and personal usage.

Current: Ubuntu 18.04 4.18.0-25-generic

## Installing Git, Synaptic package manager, htop monitor and Gdebi installation manager
```
sudo apt-get install git
sudo apt install synaptic
sudo apt install gdebi-core
sudo apt install htop
```
## Install Java Development Kit builds
```
sudo apt-get install openjdkXXXXXXXXXXXXXXXXXXXXX
```

## Install media codecs and addons
```
sudo apt install ubuntu-restricted-extras
sudo apt install ubuntu-restricted-addons
sudo apt install vlc
```

## Intel(R) Graphics Compute Runtime for OpenCL(TM) drivers
```
add-apt-repository ppa:intel-opencl/intel-opencl
apt-get update
apt-get install intel-opencl-icd
```

## NVidia_GTX_1050 driver
```
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt update
sudo apt install nvidia-XXX  #current 390
```

## Installing R (current 3.6.1)
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E298A3A825C0D65DFD57CBB651716619E084DAB9
sudo add-apt-repository 'deb https://cloud.r-project.org/bin/linux/ubuntu bionic-cran35/'
sudo apt update
sudo apt install r-base r-base-dev
```

Installing packages and dependencies for genetic analyses on Ubuntu 18.04, recomended by [Grunwald lab](https://grunwaldlab.github.io/)

Install *devtools* and *bioconductor* packages
```
sudo apt install build-essential libcurl4-gnutls-dev libxml2-dev libssl-dev
sudo -i R
> install.packages(*devtools*)
> if (!requireNamespace("BiocManager", quietly = TRUE))
    install.packages("BiocManager")
> BiocManager::install()
```
[*units* package](https://github.com/r-quantities/units)
```
sudo apt-get install libudunits2-dev
```
[*sf* package](https://github.com/r-spatial/sf)
```
sudo add-apt-repository ppa:ubuntugis/ubuntugis-unstable
sudo apt-get update
sudo apt-get install libudunits2-dev libgdal-dev libgeos-dev libproj-dev 
```
Installing packages
```
sudo -i R
> require(devtools)
> install.packages('units')
> install.packages('sf')
# After installing this packages, other dependencies will install automatically.
> install.packages('adegenet')
> install_github(repo = "grunwaldlab/poppr", build_vignettes = TRUE)
> install_github("dwinter/mmod")
```

Download RStudio (IDE)
```
cd ~/Downloads
sudo gdebi rstudio-XXX.deb
```
## Install VCFTools
```
git clone https://github.com/vcftools/vcftools.git
cd vcftools
./autogen.sh
./configure
make
make install
```
## Install ANGSD
```
git clone https://github.com/samtools/htslib.git
git clone https://github.com/ANGSD/angsd.git 
cd htslib;make;cd ../angsd ;make HTSSRC=../htslib
```

## Install iPyrad
Follow the instructions at [iPyrad.docs](https://ipyrad.readthedocs.io/en/latest/3-installation.html).

## Install Stacks
Download [Stacks](http://catchenlab.life.illinois.edu/stacks/) and extract.
```
tar xfvz stacks-2.xx.tar.gz
cd stacks-2.xx
./configure
make -j 8 #number of processors available 
sudo make install

```
## Install samtools, bcftools and htslib (following [Biostars](https://www.biostars.org/p/328831/) tutorial)

```
sudo apt-get update
sudo apt-get install gcc
sudo apt-get install make
sudo apt-get install libbz2-dev
sudo apt-get install zlib1g-dev
sudo apt-get install libncurses5-dev 
sudo apt-get install libncursesw5-dev
sudo apt-get install liblzma-dev
```
# Install HTSLIB
```
cd /usr/bin
wget https://github.com/samtools/htslib/releases/download/1.9/htslib-1.9.tar.bz2
tar -vxjf htslib-1.9.tar.bz2
cd htslib-1.9
make
```
# Install SAMTOOLS
```
cd ..
wget https://github.com/samtools/samtools/releases/download/1.9/samtools-1.9.tar.bz2
tar -vxjf samtools-1.9.tar.bz2
cd samtools-1.9
make
```
# Install BCFTools
```
cd ..
wget https://github.com/samtools/bcftools/releases/download/1.9/bcftools-1.9.tar.bz2
tar -vxjf bcftools-1.9.tar.bz2
cd bcftools-1.9
make
```
```
Export To Path And Refresh
export PATH="$PATH:/usr/bin/bcftools-1.9"
export PATH="$PATH:/usr/bin/samtools-1.9"
export PATH="$PATH:/usr/bin/htslib-1.9"
source ~/.profile
```

## Install [VSEARCH](https://github.com/torognes/vsearch)
```
wget https://github.com/torognes/vsearch/archive/vXXXXXXXX.tar.gz
tar xzf vXXXXXXXX.tar.gz
cd vsearch-vXXXXXXXX
./autogen.sh
./configure
make
make install  # as root or sudo make install
```

## Install QGIS LTR 
```
sudo sh -c 'echo "deb http://qgis.org/ubuntu-ltr bionic main" >> /etc/apt/sources.list'
sudo sh -c 'echo "deb-src http://qgis.org/ubuntu-ltr bionic main" >> /etc/apt/sources.list'

wget -O - https://qgis.org/downloads/qgis-2019.gpg.key | gpg --import
gpg --fingerprint 51F523511C7028C3
gpg --export --armor 51F523511C7028C3 | sudo apt-key add -

sudo apt-get update
sudo apt-get install qgis qgis-plugin-grass

```

## Install Zotero reference manager

Download [Zotero](https://www.zotero.org/download/) and extract.

```
sudo mv Zotero_linux-x86_64 /opt
sudo ln -s /opt/Zotero_linux-x86_64/zotero /usr/bin/zotero
sudo add-apt-repository ppa:smathot/cogscinl
sudo apt-get update 

```
To add Zotero on Applications tab
```
sudo ln -s /opt/Zotero-5.0.76_linux-x86_64/Zotero_linux-x86_64/zotero.desktop /usr/share/applications/zotero.desktop

```
Open as root
```
sudo zotero
```
# to install [qnotero](http://www.cogsci.nl/qnotero)

## Install Tweak tools for  
```
sudo add-apt-repository universe
sudo apt install gnome-tweak-tool
```
# Install Steam from official package
```
sudo dpkg --add-architecture i386
sudo apt update
sudo apt install wget gdebi-core libgl1-mesa-dri:i386 libgl1-mesa-glx:i386
wget http://media.steampowered.com/client/installer/steam.deb
sudo gdebi steam.deb
```

## Install programs via Snap
> Skype, spotify, whatsapp.desktop, Discord, etc.. check the list.

