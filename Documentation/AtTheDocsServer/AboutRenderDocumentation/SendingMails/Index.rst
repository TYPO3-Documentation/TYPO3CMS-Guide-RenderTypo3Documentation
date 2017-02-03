
.. include::   ../../../Includes.txt
.. highlight:: shell

=====================================
Sending Mails
=====================================


Templating
==========

#. As a starting point we are using the
   `Foundation Responsive Email Templates. <http://foundation.zurb.com/emails/email-templates.html>`__
   See `ZURB's email template and their README. <https://github.com/zurb/foundation-emails-template>`__

#. Our repository is `TYPO3-Documentation/t3SphinxThemeRtdEmail at Github.
   <https://github.com/TYPO3-Documentation/t3SphinxThemeRtdEmail>`__
   It is mostly a plain Foundation Sass project as described on their website.
   The purpose is to develop :file:`t3docs.html` in there. It is our html template.

#. Once you cloned the repository and made the tools work that Foundation requires
   you can build the effective template from the source.

#. Common commands::

       cd ~/Repositories
       git clone https://github.com/TYPO3-Documentation/t3SphinxThemeRtdEmail TYPO3-Documentation/t3SphinxThemeRtdEmail
       cd ~/Repositories/TYPO3-Documentation/t3SphinxThemeRtdEmail
       foundation watch
       cp example.config.json config.json
       gedit config.json
       npm run mail

#. Sources are in :file:`src/`, the result is in :file:`dist/`.

#. You need to run then `npm run mail` command to get the final result file.

#. We develop the HTML version of our template. Various html tags have special id-attributes that we freely invent.
   So we can manipulate those items later.


Deploy the template
===================

Once we are satisfied with the template we copy and paste it manually into the respective toolchain.


Using the template
==================

#. We are using `Beautiful Soup <https://www.crummy.com/software/BeautifulSoup/bs4/doc/>`__
   to parse and manipulate the html structure of the template according to our needs.

#. To fill in variables we use the normal Python string interpolation procedure (`result = template % D`).

#. As final result we produce :file:`mailcontents.html` which is to be sent as html part of the mail.



Composing the mail
==================

#. Mails should contain a pure text part first. So we use `html2text <https://github.com/aaronsw/html2text>`__,
   a commandline tool, that seems to do the job. As a result we get :file:`mailcontents.txt`.

#. Both parts are added to the mail as *alternative* parts with the pure text version being first.


Double use
==========

The html version is well suited to be shown as a standalone webpage and will be used for that purpose.
