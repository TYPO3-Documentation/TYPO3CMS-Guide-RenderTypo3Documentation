
.. include::   ../../Includes.txt
.. highlight:: shell

======================================
The Makedir of a Documentation Project
======================================

The Makedir
===========

The renderer (toolchain) expects as input the path to a `makedir`.

See this example folder: :file:`~/HTDOCS/github.com/T3DocumentationStarter/Public-Info-000.git.make`


File buildsettings.sh
---------------------

Needed: :file:`buildsettings.sh`

Carries the individual settings for this project.

Example:

.. code-block:: ini

   # buildsettings.sh

   # absolute path, or relative to conf.py, without suffix (.rst)
   MASTERDOC=../Public-Info-000.git/Documentation/Index

   # absolute path, or relative to conf.py
   LOGDIR=.

   PROJECT=Public-Info-000
   VERSION=master

   #TER_EXTENSION=0
   #TER_EXTENSION=1

   #LOCALIZATION=
   #LOCALIZATION=en_US
   #LOCALIZATION=de_DE
   #LOCALIZATION=fr_FR

   # Where to publish documentation
   BUILDDIR=/home/mbless/public_html/typo3cms/drafts/github/T3DocumentationStarter/Public-Info-000/latest

   # If GITURL is empty then GITDIR is expected to be "ready" to be processed
   GITURL=https://github.com/T3DocumentationStarter/Public-Info-000.git
   GITDIR=/home/mbless/HTDOCS/github.com/T3DocumentationStarter/Public-Info-000.git
   GITBRANCH=master

   # Path to the documentation within the Git repository
   T3DOCDIR=$GITDIR/Documentation

   # Packaging information
   PACKAGE_ZIP=1
   PACKAGE_KEY=typo3cms.drafts.Plublic-Info-000
   PACKAGE_LANGUAGE=default


Additional general files
------------------------

These are all the same for all projects::

   # cd $makedir
   ln -s /home/mbless/scripts/bin/cron_rebuild-RenderDocumentation.sh cron_rebuild.sh
   ln -s /home/mbless/scripts/bin/request_rebuild.php                 request_rebuild.php
   ln -s /home/mbless/scripts/bin/conf-2015-10.py                     conf.py


You can find a complete reference of what settings :file:`conf-2015-10.py` understands
like this::

   # cd $makedir
   cp /home/mbless/scripts/bin/conf-2015-10.Reference.Settings.cfg  Defaults.cfg


How to run cron_rebuild.sh
--------------------------

Set the "flag file". Without that file nothing will be done::

   cd $makedir
   touch REBUILD_REQUESTED

Remove the checksum file, if you want to force a rebuild::

   cd $makedir
   rm build.checksum

**To finally run the toolchain:**

1. If it's a makedir the server doesn't know::

      # cd $makedir
      ./cron_rebuild.sh

2. If it's a makedir the server does know, let the cronjob take action::

      # cd $makedir
      php request_rebuild.php


Where to put a makedir
----------------------

Note, that - afair right now - the toolchain keeps a white list of places where
makedirs may exist. One of those is :file:`~/HTDOCS/...`. So create your makedir
somewhere there.


Logs: What happened during the build?
-------------------------------------

The toolchain creates a lot of detailed logs what happened when and where.
The data of the last build is copyied to :file:`$makedir/temp_lastrun_RenderDocumentation`.

.. tip::

   If you want to understand the whole story of a rendering, look at the
   temp folder at :file:`/tmp/TCT/RenderDocumentation/...` and study the data
   while it's there. Only N jobs are kept there.


Explanations
============

.. note::

   The new toolchain will always try to render a PDF automatically.
   All necessary parameter are calculated from the given settings.
   You may however define your own in :file:`Settings.cfg` if you
   are the project owner or in :file:`$makedir/Overrides.cfg` if
   you are the server admin.

All temporary files are placed at :file:`/tmp/TCT/RenderDocumentation/...`.

The last N projects (20 or so) are kept there for inspection.
