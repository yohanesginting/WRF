# WRF

**About**

The Weather Research and Forecasting (WRF) Model is a cutting-edge mesoscale numerical weather prediction system that may be used for atmospheric research as well as operational forecasting. It has two dynamic cores, a data assimilation system, and a software architecture supporting parallel computation and system extensibility. For more information see here:
https://www.mmm.ucar.edu/models/wrf

**Installing WRF Version 4.5.1**

This script has undergone slight modifications based on the script created by Jamal Khan (https://gist.github.com/jamal919/5498b868d34d5ec3920f306aaae7460a#file-install_wrf41-sh).

_A. Prerequisites_
1) Tested in Win10/Win11 system
2) WSL2 has been installed
3) Latest verion of Ubuntu (22.04.2 LTS) has been installed
4) Hard disk capacity must be greater than 50GB

_B. Basic Package Managment_

Open your Ubuntu terminal (bash) and run this commands:

     sudo apt update
  
     sudo apt upgrade
  
     sudo apt install gcc gfortran g++ libtool automake autoconf make m4 grads default-jre csh
  
For Jasper, Domain Wizard:

     sudo apt install unzip

_C. Directory Listing_

     export HOME=`cd;pwd`
  
     mkdir $HOME/WRF
  
     cd $HOME/WRF
  
     mkdir Downloads
     
     mkdir Library

_D. Downloading the Latest Version of each Library Package_

     cd Downloads

     wget -c https://www.zlib.net/zlib-1.3.tar.gz
     
     wget -c https://support.hdfgroup.org/ftp/HDF5/releases/hdf5-1.14/hdf5-1.14.3/src/hdf5-1.14.3.tar.gz
     
     wget -c https://downloads.unidata.ucar.edu/netcdf-c/4.9.2/netcdf-c-4.9.2.tar.gz
     
     wget -c https://downloads.unidata.ucar.edu/netcdf-fortran/4.6.1/netcdf-fortran-4.6.1.tar.gz
     
     wget -c https://www.mpich.org/static/downloads/4.1.2/mpich-4.1.2.tar.gz
     
     wget -c https://download.sourceforge.net/libpng/libpng-1.6.37.tar.gz
     
     wget -c https://www.ece.uvic.ca/~frodo/jasper/software/jasper-1.900.1.zip

_E. Compilers_

     export DIR=$HOME/WRF/Library
     
     export CC=gcc
     
     export CXX=g++
     
     export FC=gfortran
     
     export F77=gfortran

_F. Extract and Install each Library Package_

#### ZLIB (Zip Compression Library)

     cd $HOME/WRF/Downloads
     
     tar -xvzf zlib-1.3.tar.gz
     
     cd zlib-1.3/
     
     ./configure --prefix=$DIR
     
     make
     
     make install

#### HDF5 (Hierarchical Data Format version 5) Library for NetCDF4 Functionality

     cd $HOME/WRF/Downloads
     
     tar -xvzf hdf5-1.10.5.tar.gz
     
     cd hdf5-1.10.5
     
     ./configure --prefix=$DIR --with-zlib=$DIR --enable-hl --enable-fortran
     
     make check
     
     make install
     
     export HDF5=$DIR
     
     export LD_LIBRARY_PATH=$DIR/lib:$LD_LIBRARY_PATH

     
####  NetCDF (Network Common Data Form) C Library

     cd $HOME/WRF/Downloads
     
     tar -xvzf netcdf-c-4.9.0.tar.gz
     
     cd netcdf-c-4.9.0/
     
     export CPPFLAGS=-I$DIR/include 
     
     export LDFLAGS=-L$DIR/lib
     
     ./configure --prefix=$DIR --disable-dap
     
     make check
     
     make install
     
     export PATH=$DIR/bin:$PATH
     
     export NETCDF=$DIR

#### NetCDF (Network Common Data Form) Fortran Library

     cd $HOME/WRF/Downloads
     
     tar -xvzf netcdf-fortran-4.6.0.tar.gz
     
     cd netcdf-fortran-4.6.0/
     
     export LD_LIBRARY_PATH=$DIR/lib:$LD_LIBRARY_PATH
     
     export CPPFLAGS=-I$DIR/include 
     
     export LDFLAGS=-L$DIR/lib
     
     export LIBS="-lnetcdf -lhdf5_hl -lhdf5 -lz" 
     
     ./configure --prefix=$DIR --disable-shared
     
     make check
     
     make install
     
#### MPICH (Message Passing Interface Chameleon)

     cd $HOME/WRF/Downloads
     
     tar -xvzf mpich-3.3.1.tar.gz
     
     cd mpich-3.3.1/
     
     ./configure --prefix=$DIR
     
     make
     
     make install
     
     export PATH=$DIR/bin:$PATH

 #### LIBPNG (Library for Portable Network Graphics)

     cd $HOME/WRF/Downloads
     
     export LDFLAGS=-L$DIR/lib
     
     export CPPFLAGS=-I$DIR/include
     
     tar -xvzf libpng-1.6.37.tar.gz
     
     cd libpng-1.6.37/
     
     ./configure --prefix=$DIR
     
     make
     
     make install

     
 #### JASPER

     cd $HOME/WRF/Downloads
     
     unzip jasper-1.900.1.zip
     
     cd jasper-1.900.1/
     
     autoreconf -i
     
     ./configure --prefix=$DIR
     
     make
     
     make install
     
     export JASPERLIB=$DIR/lib
     
     export JASPERINC=$DIR/include

_G. Download and Install WRF v.4.5.1 and WPS v.4.5_

#### WRF v.4.5.1

     cd $HOME/WRF/Downloads
     
     wget -c https://github.com/wrf-model/WRF/releases/download/v4.5.1/v4.5.1.tar.gz
     
     tar -xvzf v4.5.1.tar.gz -C $HOME/WRF
     
     cd $HOME/WRF/WRFV4.5.1
     
     ./clean
     
     ./configure # 34, 1 for gfortran and distributed memory
     
     ./compile em_real
     
     export WRF_DIR=$HOME/WRF/WRFV4.5.1

 #### WPS v.4.5

     cd $HOME/WRF/Downloads
     
     wget -c https://github.com/wrf-model/WPS/archive/refs/tags/v4.5.tar.gz
     
     tar -xvzf v4.5.tar.gz -C $HOME/WRF
     
     cd $HOME/WRF/WPS-4.5
     
     ./configure #3
     
     ./compile

 

## WRF Domain Wizard

https://jiririchter.github.io/WRFDomainWizard/









