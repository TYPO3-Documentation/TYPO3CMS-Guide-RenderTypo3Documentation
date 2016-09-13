
.. include:: ../Includes.txt


=====================================
At the servers commandline
=====================================

TCT is the Toolchain Tool. The actual name on the commandline is `tct`.

`RenderDocumentation` is a toolchain that is run by TCT.



Login to the server.

Run TCT::

   user@srv123:~$  tct
   bash: tct: command not found

This is exactly what you should expect since TCT is installed in a 'virtualenv'.
Source the activation file to set up the necessary environment::

   # ~/venvs               a place to keep virtual environments
   # ~/venvs/tct           the virtual we are using for TCT
   # ~/venvs/tct/venv      'venv' is the common name
   # ~/venvs/tct/venv/bin  the usual place for executables

   user@srv123:~$  source ~/venvs/tct/venv/bin/activate
   (venv)user@srv123:~$

   # Yeah!

Run TCT. This time it should work and look somehow like::

   user@srv123:~$  tct
   Usage: tct [OPTIONS] COMMAND [ARGS]...

     tct, the toolchain tool, is a command line tool that travels a toolchain
     folder alphabetically and topdown and runs each tool it finds.

     Tools are executable files with a name starting with 'run_'. Files are run
     first. Then processing continues with the next (sub)folder. When a tool
     fails (exitcode != 0) processing stops for the current folder and its
     subfolders. It continues with the next folder in order.

     Use --help with the subcommands.

   Options:
     --toolchains-home PATH  Root folder holding toolchains
     --temp-home PATH        Root folder for tempfiles
     -c, --config KEY VALUE  Define or override config key-value pair
                             (repeatable)
     -v, --verbose           Enable verbose mode.
     -D, --dump-params       Dump parameters and exit.
     --version               Show the version and exit.
     --help                  Show this message and exit.

   Commands:
     clean   Clean the temp folder.
     config  Handle the USER configuration file...
     list    List available toolchains.
     run     Run a toolchain.


What toolchains do we have? ::

   (venv)user@srv123:~$ tct list
   RenderDocumentation
   (venv)user@srv123:~$

   # ok, there's only one, named 'RenderDocumentation'



Settings
========

What are the global settings?

   $ cat ~/.tctconfig | less

   (venv)user@srv123:~$ tct config list

      [general]
      toolchains_home = /home/user/Toolchains
      temp_home = /tmp/TCT

      [RenderDocumentation]
      email_admin = martin.bless@gmail.com
      webroot_abspath = /home/user/public_html
      latex_contrib_typo3_folder = /home/user/HTDOCS/github.com/TYPO3-Documentation/latex.typo3
      htaccess_template_show_latest = /home/user/scripts/config/_htaccess
      email_user_receivers_exlude_list = documentation@typo3.org,kasperYYYY@typo3.org,kasperYYYY@typo3.com,info@typo3.org,francois@typo3.org
      url_of_webroot = https://docs.typo3.org
      email_user_send_extra_mail_to_admin = 1
      webroot_part_of_builddir = /home/user/public_html
      lockfile_name = lockfile.json



Logging
=======

Cleaning will happen automatically. The N most recent builds are kept for
inspection. N is a configurable value. Find out what recently happened::

   ls -la /tmp/TCT/RenderDocumentation

   drwxr-xr-x 33 user user 4096 Sep 13 12:06 .
   drwxr-xr-x  4 user user 4096 Sep  4 11:58 ..
   drwxr-xr-x 19 user user 4096 Sep 13 11:58 2016-09-13_11-58-12_664769
   drwxr-xr-x 19 user user 4096 Sep 13 11:58 2016-09-13_11-58-18_141930
   drwxr-xr-x 19 user user 4096 Sep 13 11:58 2016-09-13_11-58-41_141289
   drwxr-xr-x 19 user user 4096 Sep 13 11:58 2016-09-13_11-58-44_990298
   drwxr-xr-x 19 user user 4096 Sep 13 11:58 2016-09-13_11-58-49_437418
   drwxr-xr-x 19 user user 4096 Sep 13 11:59 2016-09-13_11-58-54_140979
   drwxr-xr-x 19 user user 4096 Sep 13 11:59 2016-09-13_11-59-13_729523
   drwxr-xr-x 19 user user 4096 Sep 13 11:59 2016-09-13_11-59-17_223291
   drwxr-xr-x 19 user user 4096 Sep 13 11:59 2016-09-13_11-59-21_269917
   drwxr-xr-x 19 user user 4096 Sep 13 11:59 2016-09-13_11-59-24_921175
   drwxr-xr-x 19 user user 4096 Sep 13 11:59 2016-09-13_11-59-28_874855
   drwxr-xr-x 19 user user 4096 Sep 13 11:59 2016-09-13_11-59-32_599972
   drwxr-xr-x 19 user user 4096 Sep 13 11:59 2016-09-13_11-59-36_013213
   drwxr-xr-x 19 user user 4096 Sep 13 11:59 2016-09-13_11-59-39_580416
   drwxr-xr-x 19 user user 4096 Sep 13 12:05 2016-09-13_12-05-02_547883
   drwxr-xr-x 19 user user 4096 Sep 13 12:05 2016-09-13_12-05-23_045668
   drwxr-xr-x 19 user user 4096 Sep 13 12:05 2016-09-13_12-05-26_947207
   drwxr-xr-x 19 user user 4096 Sep 13 12:05 2016-09-13_12-05-32_560999
   drwxr-xr-x 19 user user 4096 Sep 13 12:05 2016-09-13_12-05-36_496683
   drwxr-xr-x 19 user user 4096 Sep 13 12:05 2016-09-13_12-05-40_493718
   drwxr-xr-x 19 user user 4096 Sep 13 12:05 2016-09-13_12-05-44_580121
   drwxr-xr-x 19 user user 4096 Sep 13 12:05 2016-09-13_12-05-48_693320
   drwxr-xr-x 19 user user 4096 Sep 13 12:05 2016-09-13_12-05-52_604264
   drwxr-xr-x 19 user user 4096 Sep 13 12:06 2016-09-13_12-05-56_644457
   drwxr-xr-x 19 user user 4096 Sep 13 12:06 2016-09-13_12-06-00_682575
   drwxr-xr-x 19 user user 4096 Sep 13 12:06 2016-09-13_12-06-04_457984
   drwxr-xr-x 19 user user 4096 Sep 13 12:06 2016-09-13_12-06-08_198774
   drwxr-xr-x 19 user user 4096 Sep 13 12:06 2016-09-13_12-06-12_243568
   drwxr-xr-x 19 user user 4096 Sep 13 12:06 2016-09-13_12-06-16_351784
   drwxr-xr-x 19 user user 4096 Sep 13 12:06 2016-09-13_12-06-20_102410
   drwxr-xr-x 19 user user 4096 Sep 13 12:06 2016-09-13_12-06-24_030296


Why are there so many project remaining?
Well, that's what we get from the command "clean but keep last 30"::

   (venv)user@srv123:~/scripts/bin$  tct run RenderDocumentation --clean-but 30

To remove all::

   (venv)user@srv123:~/scripts/bin$  tct run RenderDocumentation --clean-but 0


We are seeing 30 because that's the way it's configured:::

   (venv)user@srv123:~/scripts/bin$ cat cron_rebuild-RenderDocumentation.sh

   #!/bin/bash

   source ~/venvs/tct/venv/bin/activate
   MAKEDIR=$(cd "$(dirname "$0")" && echo $PWD)
   if [ ! -r "$MAKEDIR/REBUILD_REQUESTED" ]; then
     exit 0
   fi

   echo

   tct \
     run RenderDocumentation \
     -c makedir "$MAKEDIR" --clean-but 30

   tct \
     run RenderDocumentation \
       -c makedir "$MAKEDIR" \
       -c email_user_to martin.bless@gmail.com \
       -c talk 1

   rm "$MAKEDIR/REBUILD_REQUESTED" >/dev/null 2>&1

   echo


Locking
=======

Only a single instance of the toolchain `RenderDocumentation` should be running at a given time.
The lockfile :file:`/tmp/TCT/RenderDocumentation/lockfile.json` indicates that a job is running.
The job should remove the lockfile in the end. A very old lockfile will be disregarded anyway.


Unlock manually
---------------

If a job fails and doesn't remove the lockfile you can enforce removal from the commandline::

   (venv)user@srv123:~/scripts/bin$ tct run RenderDocumentation -T unlock
   # -------- RenderDocumentation 2016-09-13 13:02:04 159229



Prepare a render job
====================


Provide the project
-------------------

::

   git clone \
      https://github.com/TYPO3-Documentation/TYPO3CMS-Guide-RenderTypo3Documentation.git \
      ~/TYPO3CMS-Guide-RenderTypo3Documentation.git

   cd ~/TYPO3CMS-Guide-RenderTypo3Documentation.git
   git checkout latest
   git pull


Create :file:`makedir` folder
-----------------------------

The `RenderDocumentation` toolchain expects you to set up a file:`makedir` folder. Example::

   # go home
   (venv)user@srv123:~$ cd

   # create makedir
   (venv)user@srv123:~$ mkdir ~/TYPO3CMS-Guide-RenderTypo3Documentation.git.make

   # go there
   (venv)user@srv123:~$ cd ~/TYPO3CMS-Guide-RenderTypo3Documentation.git.make

   # symlink the conf.py into that folder
   (venv)user@srv123:~/TYPO3CMS-Guide-RenderTypo3Documentation.git.make$ \
      ln -s /home/user/scripts/bin/conf-2015-10.py conf.py

   # create a buildsettings file.
   touch buildsettings.sh



Edit :file:`buildsettings.sh`
-----------------------------

The file is sourced by bash.

The file is read as ini file too.

.. code-block:: cfg

   # This is a real life example of 'buildsettings.sh'

   # Tip: Prefer absolute paths! It's less error prone.

   # absolute path to the master_doc, without suffix (.rst or .md)
   # or relative path from conf.py's folder to master_doc
   MASTERDOC=/home/user/TYPO3CMS-Guide-RenderTypo3Documentation.git/Documentation/Index

   # Absolute path or relative path from conf.py's folder
   # Not required on the server.
   # toolchain RenderDocumentation does not care about this value
   LOGDIR=.

   # The name of the project. Appears top left on pages. Gets overriden by Settings.cfg
   PROJECT=RenderTYPO3DocumentationGuide

   # The version of th project. Appears top left on pages. Gets overriden by Settings.cfg
   VERSION=latest

   # Where to publish documentation
   # The webroot folder is: /home/user/public_html
   BUILDDIR=/home/user/public_html/typo3cms/RenderTYPO3DocumentationGuide/latest

   # The folder with the project source
   GITDIR=/home/user/TYPO3CMS-Guide-RenderTypo3Documentation.git

   # If GITURL is empty then GITDIR is published unmodified, that is, "as it is"
   # GITURL=

   # If GITURL is given then a `git checkout $GITBRANCH; git pull $GITURL --force`
   # will be done first
   GITURL=https://github.com/TYPO3-Documentation/TYPO3CMS-Reference-Typoscript.git
   GITBRANCH=latest

   # Path to the documentation within the Git repository
   T3DOCDIR=/home/user/TYPO3CMS-Guide-RenderTypo3Documentation.git/Documentation/Index

   # Packaging information

   # Set to 0 or 1. If set, a zip archive will be produced.
   PACKAGE_ZIP=1

   # Name of the zip file
   PACKAGE_KEY=typo3cms.manual.RenderT3Docs

   # Use 'default' for English
   PACKAGE_LANGUAGE=default

   # Is this a TER extension? Set to 0 or 1
   # If set, the folder with the highest version number like '1.2.3' will automatically
   # be treated a 'stable', which is what gets shown when the url of the project is given
   # without version number.
   # If set to 0, the symlink 'stable' needs to be manually created.
   TER_EXTENSION=0

   # If empty, the default language of the manual is rendered.
   LOCALIZATION=

   # Otherwise, for example: If there is a PROJECT/Documentation/Localization.fr_FR/ section
   # set value 'fr_FR':
   # LOCALIZATION=fr_FR




.. write about:
   (venv)user@srv123:~/HTDOCS/github.com/TYPO3-Documentation/TYPO3/Guide/RenderTypo3Documentation.git.make$ ln -s /home/user/scripts/bin/cron_rebuild-RenderDocumentation.sh cron_rebuild.sh
   (venv)user@srv123:~/HTDOCS/github.com/TYPO3-Documentation/TYPO3/Guide/RenderTypo3Documentation.git.make$
