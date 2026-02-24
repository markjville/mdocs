# Install Printer on CentOS 7

1. Install foomatic drivers
   `sudo yum install foomatic`
   
2. Add the printer through gui, like CUPS or System Settings

An example for installing a printer, Samsung CLX-3175:
```
wget -O foo2zjs.tar.gz http://foo2zjs.rkkda.com/foo2zjs.tar.gz

tar zxf foo2zjs.tar.gz

cd foo2zjs

sudo make install

sudo make cups
```
