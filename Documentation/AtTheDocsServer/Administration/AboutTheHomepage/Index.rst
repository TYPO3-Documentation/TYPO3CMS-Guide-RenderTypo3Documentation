
.. include::   ../../../Includes.txt
.. highlight:: shell

=====================================
About the Homepage
=====================================

by Martin Bless, 2017-02-12, updated 2018-11-06

A repository for the "glue pages"
=================================

In general the documentation server is presenting a collection of individual
documentation projects. Each project starts within its own rootfolder.

To present the contents of the server nicely we need some kind of homepage
and other pages that present and connect the individual manuals. We've coined
the term "glue pages" for that.

As a quick solution we have created a special "manual" for this purpose at
https://github.com/TYPO3-Documentation/DocsTypo3Org-Homepage

Changes pushed to that repository should appear a few minutes later in the
drafts area at https://docs.typo3.org/typo3cms/drafts/github/TYPO3-Documentation/DocsTypo3Org-Homepage/


Normal manual - special use
===========================

The idea of the "glue pages" is that we on one hand just use a normal manual
but on the other hand pay attention to the intended special usage. The homepage
repo is meant to fill the gaps between the other manuals. So we need to pay attention
to what folders and filenames we use. If somebody messes things up the homepage
could be lost or parts of the other manuals could be overwritten.


Manual intervention needed
==========================

There's no fully automatical method to update the homepage at the moment (2017-02).
The procedure of publishing new homepage content is:

#. SSH into docs.typo3.org
#. Switch user: `sudo su mbless`
#. Go to the 'make'-folder of the homepage: `mbless@srv123:$ cd ~/HTDOCS/github.com/TYPO3-Documentation/DocsTypo3Org-Homepage.git.make`

   Read the name `HTDOCS` as `Repositories` - that's what it actually means.

#. Run bash script one: `./1.sh`
#. Have an eye on the output to make sure that there aren't (severe) errors
#. Understand: This first script renders the glue pages to the drafts area as a '0.0' version. It can be seen here:
   https://docs.typo3.org/typo3cms/drafts/github/TYPO3-Documentation/DocsTypo3Org-Homepage/0.0/

#. If the result of script one looks good please run the second script to actually publish the new homepage:
   `./2.sh`

#. Script two simply copies the `0.0` version to the homepage location.

Running `./1sh` and `./2.sh` can be done at any time and happens very fast.

*Tip, convenience calls:* ::

   # from a remote machine:
   ssh mbless@srv123.typo3.org HTDOCS/github.com/TYPO3-Documentation/DocsTypo3Org-Homepage.git.make/1.sh
   ssh mbless@srv123.typo3.org HTDOCS/github.com/TYPO3-Documentation/DocsTypo3Org-Homepage.git.make/2.sh


.. attention::

   To actually see the changes in the browser don't forget to clear the browser cache.
   Then reload the homepage.






