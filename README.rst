This is the French Translation of the Python Documentation
==========================================================

Documentation Contribution Agreement
------------------------------------

NOTE REGARDING THE LICENSE FOR TRANSLATIONS: Python's documentation is
maintained using a global network of volunteers. By posting this
project on Transifex, Github, and other public places, and inviting
you to participate, we are proposing an agreement that you will
provide your improvements to Python's documentation or the translation
of Python's documentation for the PSF's use under the CC0 license
(available at
`https://creativecommons.org/publicdomain/zero/1.0/legalcode`_). In
return, you may publicly claim credit for the portion of the
translation you contributed and if your translation is accepted by the
PSF, you may (but are not required to) submit a patch including an
appropriate annotation in the Misc/ACKS or TRANSLATORS file. Although
nothing in this Documentation Contribution Agreement obligates the PSF
to incorporate your textual contribution, your participation in the
Python community is welcomed and appreciated.

You signify acceptance of this agreement by submitting your work to
the PSF for inclusion in the documentation.


TODO
----

- Patch `docsbuild-scripts
  <https://github.com/python/docsbuild-scripts/>`_ to build
  translations too.


Translation Progression
-----------------------

============  =====  =====  =====
          ..    2.7    3.5    3.6
============  =====  =====  =====
    about.po   100%   100%   100%
     bugs.po   100%   100%   100%
       c-api     9%    12%    11%
 contents.po   100%   100%   100%
copyright.po   100%   100%   100%
distributing   100%   100%   100%
   distutils    32%    33%    33%
   extending    21%    24%    24%
         faq    29%    33%    32%
 glossary.po    85%   100%   100%
       howto     7%     6%     6%
     install    45%    46%    43%
  installing   100%   100%    66%
     library    16%    20%    19%
  license.po   100%   100%   100%
   reference     5%     5%     5%
   sphinx.po   100%   100%   100%
    tutorial   100%   100%   100%
       using    31%    21%    19%
    whatsnew     6%    41%     7%
     ~total~    19%    25%    19%
============  =====  =====  =====


Contributing to the Translation
-------------------------------

Your help is welcome, you can start with easy tasks like reviewing
fuzzy entries to help keeping the documentation up to date.  You can
also proofread already translated entries, and finally translate
untranslated ones.


How to Contribute
~~~~~~~~~~~~~~~~~

You can either contribute on `transifex/python-doc/public
<https://www.transifex.com/python-doc/public/>`_, or by simply openning an
issue on this repository, or by editing the ``po`` files.

To modify those files you first have to fork this project and follow
github instructions to clone it.

Next, to edit the files, you can use an editor of your choice, there's many:

- Highly recommended: `poedit <http://www.poedit.net/>`_
- gted
- gtranslator
- lokalize
- betterpoeditor
- vim or emacs with an appropriate mode
- Vé on Android
- Probably many others

Finally, once your contribution is done, do a ``pull request`` so we
can review and merge it.


What to translate
~~~~~~~~~~~~~~~~~

- Prioritize the higher version, identical strings between version can
  automatically be reused.
- Do not translate content of ``:ref:...`` and ``:term:...``
- Put english words, if you have to use them, in *italics* (surrounded
  by stars).
- ``::`` at the end of some paragraphs have to be translated to ``:
  ::`` in French to place the space before the column.


Where to get help
~~~~~~~~~~~~~~~~~

The coordinator for this translation is `mdk <https://mdk.fr/>`_.

Feel free to ask your questions on ``#python-fr`` on `freenode
<https://webchat.freenode.net/>`_.


Priorities
----------

The ``tutorial/`` directory has a high priority as translations aim
for newcomers, then here are files most read in the original version:

- library/functions.po
- library/stdtypes.po
- library/string.po
- library/re.po
- library/datetime.po
- library/csv.po
- library/os.po
- library/random.po
- library/json.po
- library/subprocess.po


Translation Resources
---------------------

- `Le Grand Dictionnaire Terminologique <http://gdt.oqlf.gouv.qc.ca/>`_
- IRC channel `#python-fr <irc.lc/freenode/python-fr>`_ on freenode.
- The `liste traductions <http://lists.afpy.org/mailman/listinfo/traductions>`_
- `Glossaire traduc.org <http://glossaire.traduc.org>`_
- `Glossaires et Dictionnaires of traduc.org
  <https://traduc.org/Glossaires_et_dictionnaires>`_
- glossary.po, as it's already translated.


Glossary
--------

For consistency in our translations, here are some propositions and
reminders for frequent terms you'll have to translate, don't hesitate
to open an issue if you disagree.

- double quote: *guillemet*
- simple quote: *guillemet simple*, *apostrophe* (*apostrophe* is to glue,
  *guillemet* is to surround, use when appropriate)
- -like: *-compatible* (when appropriate)
- abstract data type: *type abstrait*
- argument: *argument* (Don't mix with parameter)
- parameter: *paramètre*
- backslash: *antislash*, *backslash* (in italics)
- bound: *lier*
- bug: *bogue*, *bug* (in italics)
- debugging: *débogage*
- built-in: *primitive*, *native*
- identifier: *identifiant*
- immutable: *immuable*
- interpreter: *interpréteur*
- library: *bibliothèque*
- list compréhension: *liste en compréhension*
- mutable: *variable*
- prompt: *invite*
- regular expression: *expression rationnelle*, *expression régulière*
- socket: *socket* (in italics)
- statement: *instruction*
- underscore: *tiret bas*, *underscore* (in italics)
- little-endian, big-endian: `petit-boutise, gros-boutiste
  <https://fr.wikipedia.org/wiki/Endianness>`_


Project History
---------------

This project was started `around 2012
<https://github.com/AFPy/python_doc_fr/commit/b77bdff59036b6b5a4804d5f519ce3ea341e027c>`_
by `afpy <https://www.afpy.org/>`_ members, in 2017 this project
became the official french Python documentation translation thanks to
`PEP 545 <https://www.python.org/dev/peps/pep-0545/>`_.


Maintenance
-----------

Find fuzzy strings:

.. code-block:: bash

  grep -c fuzzy **/*.po | grep -v ':1$\|:0$'


Merge pot files from cpython doc:

.. code-block:: bash

  VERSION=3.6
  git clone --depth 1 --branch $VERSION https://github.com/python/cpython.git /tmp/cpython/
  (cd /tmp/cpython/ && sphinx-build -Q -b gettext -D gettext_compact=0 Doc pot/)
  POT_PATH="/tmp/cpython/pot/"
  PO_PATH="./"

  find "$POT_PATH" -name '*.pot' |
      while read -r POT
      do
          PO="$PO_PATH/$(echo "$POT" | sed "s#$POT_PATH##; s#\.pot\$#.po#")"
          mkdir -p "$(dirname "$PO")"
          if [ -f "$PO" ]
          then
              msgmerge --backup=off --force-po -U "$PO" "$POT"
          else
              msgcat -o "$PO" "$POT"
          fi
      done
