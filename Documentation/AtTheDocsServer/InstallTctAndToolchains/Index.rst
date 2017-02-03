
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

Setup virtual environment

#. `cd ~/venvs/tct` - go to project folder
#. `virtualenv venv` - setup a local Python environment
#. `source venv/bin/activate` - activate
#. `deactivate`- reset shell to normal environment

Install with PIP

#. `cd ~` - go somewhere - it doesn't matter
#. `source ~/venvs/tct/venv/bin/activate` - activate the environment
#. `(venv) pip install --upgrade git+https://github.com/aaronsw/html2text.git` -
   install Python package directly from Git repository
#. `UNTESTED not ready yet`
   `(venv) pip install --upgrade git+https://github.com/marble/TCT.git` 


Test

Is the html to text converter installed? ::

   html2text --help


Keep this notes:

Install toolchain updates::

   cd ~/Toolchains/RenderDocumentation
   git pull

 
