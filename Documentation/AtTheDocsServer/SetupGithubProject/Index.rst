.. include:: ../Includes.txt
.. highlight:: shell

==================================================
How to set up a Github Docs Project on the Server
==================================================


To be explained:

   # mb, 2016-09-22, 2016-09-22

   umask 2


   # settings
   builddir=/home/mbless/public_html/typo3cms/drafts/github/typo3-themes/themes/latest
   gitdir=/home/mbless/HTDOCS/github.com/typo3-themes/themes.git
   makedir=/home/mbless/HTDOCS/github.com/typo3-themes/themes.git.make
   builddir_parent=/home/mbless/public_html/typo3cms/drafts/github/typo3-themes/themes/

   # webfolder
   mkdir -p $builddir
   ln -s /home/mbless/scripts/config/_htaccess-2016-08.txt $builddir_parent/.htaccess
   ln -s $builddir_parent  $builddir_parent/latest

   # repository
   mkdir -p $makedir
   ln -s /home/mbless/scripts/bin/request_rebuild.php                  $makedir/request_rebuild.php
   ln -s /home/mbless/scripts/bin/conf-2015-10.py                      $makedir/conf.py
   ln -s /home/mbless/scripts/bin/cron_rebuild-RenderDocumentation.sh  $makedir/cron_rebuild.sh
   touch  $makedir/buildsettings.sh
   # vim $makedir/buildsettings.sh


   # enable Github hook
   vim /home/mbless/public_html/services/known-github-manuals.txt

   # include into cronjob
   vim /home/mbless/HTDOCS/git.typo3.org/Documentation/cron_rebuild_included.sh


-----------------

# https://github.com/mindshape-GmbH/mindshape_seo

GITHUB_USER=mindshape-GmbH
GITHUB_REPO=mindshape_seo
GITHUB_USER_REPO=${GITHUB_USER}/${GITHUB_REPO}

umask 2

# settings
builddir=/home/mbless/public_html/typo3cms/drafts/github/${GITHUB_USER_REPO}/latest
gitdir=/home/mbless/HTDOCS/github.com/${GITHUB_USER_REPO}.git
makedir=/home/mbless/HTDOCS/github.com/${GITHUB_USER_REPO}.git.make
builddir_parent=/home/mbless/public_html/typo3cms/drafts/github/${GITHUB_USER_REPO}/

# webfolder
mkdir -p $builddir
ln -s /home/mbless/scripts/config/_htaccess-2016-08.txt $builddir_parent/.htaccess

# repository
mkdir -p $makedir
ln -s /home/mbless/scripts/bin/request_rebuild.php                  $makedir/request_rebuild.php
ln -s /home/mbless/scripts/bin/conf-2015-10.py                      $makedir/conf.py
ln -s /home/mbless/scripts/bin/cron_rebuild-RenderDocumentation.sh  $makedir/cron_rebuild.sh
touch  $makedir/buildsettings.sh
# vim $makedir/buildsettings.sh


# enable Github hook
vim /home/mbless/public_html/services/known-github-manuals.txt

# include into cronjob
vim /home/mbless/HTDOCS/git.typo3.org/Documentation/cron_rebuild_included.sh


------------------

# https://github.com/TYPO3-Documentation/TYPO3CMS-Code-Examples

GITHUB_USER=TYPO3-Documentation
GITHUB_REPO=TYPO3CMS-Code-Examples
GITHUB_USER_REPO=${GITHUB_USER}/${GITHUB_REPO}

umask 2

# settings
builddir=/home/mbless/public_html/typo3cms/drafts/github/${GITHUB_USER_REPO}/latest
gitdir=/home/mbless/HTDOCS/github.com/${GITHUB_USER_REPO}.git
makedir=/home/mbless/HTDOCS/github.com/${GITHUB_USER_REPO}.git.make
builddir_parent=/home/mbless/public_html/typo3cms/drafts/github/${GITHUB_USER_REPO}/

# webfolder
mkdir -p $builddir
ln -s /home/mbless/scripts/config/_htaccess-2016-08.txt $builddir_parent/.htaccess

# repository
mkdir -p $makedir
ln -s /home/mbless/scripts/bin/request_rebuild.php                  $makedir/request_rebuild.php
ln -s /home/mbless/scripts/bin/conf-2015-10.py                      $makedir/conf.py
ln -s /home/mbless/scripts/bin/cron_rebuild-RenderDocumentation.sh  $makedir/cron_rebuild.sh
touch  $makedir/buildsettings.sh
# vim $makedir/buildsettings.sh


### # buildsettings.sh
###
### # absolute path, or relative to conf.py, without suffix (.rst)
### MASTERDOC=../Public-Info-000.git/Documentation/Index
###
### # absolute path, or relative to conf.py
### LOGDIR=.
###
### PROJECT=Public-Info-000
### VERSION=master
###
### #TER_EXTENSION=
### #LOCALIZATION=
###
### # Where to publish documentation
### BUILDDIR=/home/mbless/public_html/typo3cms/drafts/github/T3DocumentationStarter/Public-Info-000/latest
###
### # If GITURL is empty then GITDIR is expected to be "ready" to be processed
### GITURL=https://github.com/T3DocumentationStarter/Public-Info-000.git
### GITDIR=/home/mbless/HTDOCS/github.com/T3DocumentationStarter/Public-Info-000.git
### GITBRANCH=master
###
### # Path to the documentation within the Git repository
### T3DOCDIR=$GITDIR/Documentation
###
### # Packaging information
### PACKAGE_ZIP=0
### PACKAGE_KEY=unused
### PACKAGE_LANGUAGE=default






# enable Github hook
vim /home/mbless/public_html/services/known-github-manuals.txt

# include into cronjob
vim /home/mbless/HTDOCS/git.typo3.org/Documentation/cron_rebuild_included.sh



