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


  


3) For Jasper, Domain Wizard:
   
   sudo apt install unzip

_C. Directory Listing_

     export HOME=`cd;pwd`
  
     mkdir $HOME/WRF
  
     cd $HOME/WRF
  
     mkdir Downloads
     
     mkdir Library

_D. Downloading the latest version of each library package_

 





