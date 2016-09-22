
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

   Learn about settings:
   ((`normal <https://github.com/marble/typo3-docs-typo3-org-resources/blob/master/TemplatesForCopying/ExampleFiles/Settings-minimal.cfg>`__,
   `extensive <https://github.com/marble/typo3-docs-typo3-org-resources/blob/master/TemplatesForCopying/ExampleFiles/Settings-extensive.cfg>`__,
   `example files <https://github.com/marble/typo3-docs-typo3-org-resources/tree/master/TemplatesForCopying/ExampleFiles>`__,
   `about ini files <http://mbless.de/blog/2015/10/24/a-new-task-for-an-old-server.html#ini-files>`__))


Step 2: Notify the documentation server
=======================================

At the moment it's more the documentation TEAM you have to notify. Send an email to documentation@typo3.org
providing this information:

1. The **url** of your Github repository
2. The **branch** that should be used
3. The **desired folder name** or your publication

Add any information you want, for example what complete url you'd like to see.

Example 1::

   Please publish: https://github.com/TYPO3-Documentation/TYPO3CMS-Guide-RenderTypo3Documentation
   branch:         master
   as:             RenderTYPO3DocumentationGuide
   preferably at:  https://docs.typo3.org/typo3cms/RenderTYPO3DocumentationGuide/

Example 2::

   Please publish: https://github.com/georgringer/news
   branch:         master
   as:             news
   preferably at:  https://docs.typo3.org/typo3cms/extensions/news/

.. What does "Is it a TER extension?" mean? The documentation of a TER extension
   is automatically rendered and published with a url that ends with the version number
   like :file:`typo3cms/extensions/EXTKEY/1.2.3/`. It is the contents of the
   documentation with the highest version number that you see when you visit the
   url without the version number like in :file:`typo3cms/extensions/EXTKEY/`.

That's it.


Step 3: Add a webhook at Github
===============================

1. Copy the following payload, 67 characters, starting wiht `https` and ending with `.php`:
   `https://docs.typo3.org/services/handle_github_post_receive_hook.php`

2. Go to the settings of your Github project:

   .. figure:: 001.png
      :class: with-border

3. Choose "Webhooks":

   .. figure:: 002.png

4. Add the webhook like this:

   .. figure:: 003.png
