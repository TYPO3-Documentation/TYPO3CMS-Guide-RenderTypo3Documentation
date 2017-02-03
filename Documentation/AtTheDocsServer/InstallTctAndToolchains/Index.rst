
.. include::   ../../Includes.txt
.. highlight:: shell

=====================================
Install TCT and toolchains
=====================================


... heavily under construction ...

Installation
============

Provide basics

#. SSH to server as the user who will do the rendering.
#. `python --version` - verify you have Python 2.7.x
#. `sudo pip install --upgrade pip` - use the Python packet manager to upgrade itself
#. `cd` - go home
#. `mkdir venvs` - create folder for virtual environments
#. `mkdir venvs/tct` - create folder for ToolChainTool

Install with PIP

#. `cd ~/venvs/tct` - go to project folder
#. `pip install --upgrade git+https://github.com/aaronsw/html2text.git` -
   install Python package directly from Git repository
#. ...

Test

Is the html to text converter installed? ::

   html2text --help


Keep this notes:

Install toolchain updates::

   cd ~/Toolchains/RenderDocumentation
   git pull

 
