
.. include:: ../../Includes.txt

.. highlight:: none

========
Warnings
========



Warnings about highlighting
===========================

.. _Pygments: http://pygments.org/

Pygments_ is the machinery responsible for syntax highlighting.
Visit that page and play around with the lexer.
[...]


.. rst-class:: panel panel-default

Could not lex
-------------

Why
   do I get `path/to/file.rst:181: WARNING: Could not lex literal_block as "html".
   Highlighting skipped.` for this code?

   .. figure:: 001.png
      :class: with-border


Because
   the code contains a syntax error:

   .. figure:: 002.png
      :class: with-border

What
   the lexer at the Pygments_ page says:

   .. figure:: 003.png
      :class: with-border

Indeed,
   there is an error:

   .. figure:: 004.png
      :class: with-border



