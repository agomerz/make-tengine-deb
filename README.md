make-tengine-deb
===
## Instructions
Retrieve and extract tengine

    wget http://tengine.taobao.org/download/tengine-1.5.2.tar.gz
    tar -zxf tengine-1.5.2.tar.gz  

Clone this repository to the debian folder       

    cd tengine-1.5.2   
    git clone https://github.com/dmsimard/make-tengine-deb.git debian
    cd debian; git checkout 1.5.2; cd ..

Install compilation dependencies  

    apt-get install  build-essential debhelper make autoconf automake patch dpkg-dev  fakeroot pbuilder gnupg dh-make libssl-dev libpcre3-dev
    export DEB_BUILD_OPTIONS=nocheck; dpkg-buildpackage -rfakeroot -uc -b     

## Installing the debian package
Install the compiled package    

    sudo dpkg -i tengine_1.5.2-1_amd64.deb

## Notes
  The packaging rules and layout is taken directly from Ubuntu's nginx repository.
  In this particular fork, some defaults are taken from Ubuntu's own nginx packaging such
  as the usage of sites-available and sites-enabled.
