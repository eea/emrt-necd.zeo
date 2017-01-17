# ZEO Server buildout for EMRT-NEC

## System requirements

This buildout is intended to run on Linux/Unix-based operating systems and has been used and tested on CentoOS 7. The following system libraries must be installed on the server before you run the buildout. These must be globally installed by the server administrator.

    $ sudo yum install gcc python-devel

## Installation

We'll have to create a new user and use this user for deployment:

    $ sudo bash
    $ useradd -u 500 -g 500 -m -s /bin/bash zope-www
    $ groupadd -g 500 zope-www
    $ mkdir -p /var/local/zeoserver
    $ mkdir -p /var/zeodb/
    $ chown -R 500:500 /var/local/zeoserver /var/zeodb/
    # sudo su - zope-www

Now get the source code:

    $ cd /var/local/zeoserver
    $ git clone https://github.com/eea/esdrt.nec.zeo.git
    $ cd esdrt.nec.zeo

and run buildout:

    $ python bootstrap.py --buildout-version=2.2.1 --setuptools-version=7.0
    $ ./bin/buildout

## Start the server

Start the ZEO server in foreground:

    $ cd /var/local/zeoserver
    # ./bin/zeoserver fg
