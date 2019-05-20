
.. include::   ../Includes.txt
.. highlight:: shell

==================
Projects On Github
==================

With proper setup the documentation of a Github project will be automatically
rebuild on the docs server whenever a new push is made to the repository.

Examples of projects are TYPO3 CMS extensions, manuals in general, drafts
of something new and upcoming where you want to concentrate on compiling the
actual docs and leave all rendering problems to the server.

Drafts are publicly available at https://docs.typo3.org/typo3cms/drafts
and thus need to be compliant with legal rules. But they don't have to be
"ready" in any way. It's just the other way round: If you're planning
a new piece of text have the rendering setup BEFORE you start writing.
It simplifies things and boosts motivation that you can write a few sentences,
do a push and shortly after that find the result of your efforts nicely rendered.

Remember, it's not core code: push early, push often.

What needs to be done to get your documentation project rendered on https://docs.typo3.org\?
Read on!

Step 1: Make your project compatible
====================================

Two files are required at the minimum:

-  The master document (master_doc): :file:`https://github.com/USERNAME/PROJECT/Documentation/Index.rst`

-  A settings file with metadata: :file:`https://github.com/USERNAME/PROJECT/Documentation/Settings.cfg`

- A composer.json file that requires `typo3/csm-core`.

   Learn about settings:
   ((`normal <https://github.com/marble/typo3-docs-typo3-org-resources/blob/master/TemplatesForCopying/ExampleFiles/Settings-minimal.cfg>`__,
   `extensive <https://github.com/marble/typo3-docs-typo3-org-resources/blob/master/TemplatesForCopying/ExampleFiles/Settings-extensive.cfg>`__,
   `example files <https://github.com/marble/typo3-docs-typo3-org-resources/tree/master/TemplatesForCopying/ExampleFiles>`__,
   `about ini files <http://mbless.de/blog/2015/10/24/a-new-task-for-an-old-server.html#ini-files>`__))


Step 2: Notify the documentation server
=======================================

To trigger documentation rendering you should add `https://docs-hook.typo3.org/` as a webhook to your
public repository. Make sure to set the content type to `application-json`.

That's it.
