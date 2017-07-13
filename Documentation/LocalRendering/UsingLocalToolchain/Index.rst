
.. include::   ../../Includes.txt
.. highlight:: shell

=====================================
Using Local Toolchain
=====================================

((to be written))



Installing with PIP
===================

Install
=======
...


Upgrade
=======

How to upgrade all::

   pip freeze --local | grep -v '^\-e' | cut -d = -f 1  | xargs pip install -U

Readings:
`one <http://mikegrouchy.com/blog/2014/06/pro-tip-pip-upgrade-all-python-packages.html>`__,
`two <http://stackoverflow.com/questions/2720014/upgrading-all-packages-with-pip/3452888#3452888>`__,
`Google <https://www.google.de/search?q=python+pip+upgrade+all>`__

