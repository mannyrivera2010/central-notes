Python3 Installation    
How to compile python 3.x in Debian-Based Linux    
1) Download Preq    
```shell
$ sudo apt-get install libpq-dev python-dev libssl-dev openssl libsqlite3-dev     
```
2) Download Python From Website    
https://www.python.org/downloads/    

3) Compile Python Source
```shell
$ ./configure --prefix=/home/{user}/sources/compiled/python3.4_dev --with-ensurepip=install
$ make
```
    
Debugging Help    
http://stackoverflow.com/questions/22592686/compiling-python-3-4-is-not-copying-pip
