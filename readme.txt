
TEMA - Model Based Online Testing Tool
======================================


* Getting started

** Installing tema-tg and temagui

Most of the current users use TEMA at Ubuntu Linux environment.  Full
set of installation packages, including .debs, can be downloaded from
the project home page at http://tema.cs.tut.fi/.

Extract the files from the archive, goto (cd) into the directory,
where debian packages are and give following commands:

sudo apt-get update
sudo apt-get upgrade
sudo dpkg -i tema-tg_3.2_all.deb
sudo apt-get -f install
sudo apt-get install sqlite3
sudo dpkg -i temagui_3.2.1_all.deb
sudo apt-get -f install

(Commands "sudo apt-get -f install" are needed because dpkg do not
install dependences.  The commands "sudo apt-get update" and "sudo
apt-get upgrade" are optional and used to ensure that the Ubuntu
installation is up to date.)


** Fixing broken temagui installation

The most often experienced symptom of broken temagui installation is,
that test generation can not be started in temagui.  In order to fix
this, one have to manually clean the system before re-installation
attempt:

First remove the installed TEMA packages:

sudo apt-get --purge remove temagui tema-tg
sudo apt-get --purge autoremove

(See file INSTALL in temagui-3.2.1.tar.gz for uninstall instructions,
if you tried to install manually from the tar archives)


The most likely reasons for the described fault is that the contents
of the directory /var/lib/temagui is messed up.  So, be sure, that the
directory is removed.  Its contents is set up when temagui is
installed again.  All the temagui related data, temagui accounts, test
configurations, uploaded models, logs, etc. are lost, though.

sudo rm -rf /var/lib/temagui


Then one have to be sure, that the right programs are called.

sudo rm -f /usr/local/bin/tema*


And check that temagui is not referenced from configuration files
under /etc.

egrep -R temagui /etc/*

If any references are found in Apache configuration, remove them. The
directory /etc/temagui have to be deleted, if it exists

sudo rm -rf /etc/temagui


When installing from tar archives, some of the installed files are
under /usr/local.  In order to keep system clean, following two
directories should be removed, if they exists.

sudo rm -rf /usr/local/var/temagui
sudo rm -rf /usr/local/temagui


After these cleaning actions, the installation actions described above
should be carried out.


** Models

In directory TEMA-Toolset-3.2.1/Models there are some model packages
which can be used when experimenting with TEMA tool.  Those zip-files
can be uploaded into temagui or test generation can be started with
program tema.runmodelpackage from command line.  Example models for
Android platform are part of the NG_Models library.


** Modelling

Models can be constructed with ModelDesigner.  It is installed like
any other Debian package file.  (There is a separate package for 64
bit system, ...amd64.deb)

For 32 bit computer system:

sudo dpkg -i tema-modeldesigner_3.2_i386.deb
sudo apt-get -f install

See /usr/share/doc/tema-modeldesigner/README.gz for very brief
introduction how ModelDesigner is used.
