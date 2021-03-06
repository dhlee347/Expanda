expanda.ext.wikipedia
=====================

Introduction
------------
**Wikipedia** ([#]_) is one of the most famous datasets in NLP. It has an
enormous scale of text and contains diverse categories. Also, Wikipedia has
multi-lingual versions of articles. It is frequently used to pretrain NLP
models (especially language model).

The data structure of Wikipedia is based on *MediaWiki* ([#]_) which is a free
and open-source wiki engine. All Wikipedia contents are written in *MediaWiki*
grammar. There are many nested structures and messy components in raw contents.
Thanks to mwparserfromhell_, MediaWiki-formatted contents would be parsed and
each component would be altered to plain texts.

Simply, this extension extracts plain texts from Wikipedia dump file. It
supports multi-core processing to enhance extracting speed. Too short sentences
would be dropped from the corpus.

.. caution::
    To extract Wikipedia dump file in parallel, the partitions in temporary
    directory would be used. Please be careful not to delete the temporary
    files when using this extension.

Details
-------
.. code:: console

    $ expanda show expanda.ext.wikipedia
    Extension [expanda.ext.wikipedia]
    Name             : wikipedia dump extractor
    Version          : 1.0
    Description      : extract wiki dump file.
    Author           : expanda
    Parameters
        num-cores    : int    (default: -1)
        min-length   : int    (default: 50)
        max-length   : int    (default: 1000)
        split-sent   : str    (default: true)

Configuration Example
---------------------
.. code:: ini

    # ...

    [expanda.ext.wikipedia]
    num-cores           = 8
    min-length          = 100
    max-length          = 1000
    split-sent          = false

    # ...

References
----------
.. [#] https://en.wikipedia.org/wiki/Wikipedia
.. [#] https://en.wikipedia.org/wiki/MediaWiki
.. _mwparserfromhell: https://github.com/earwig/mwparserfromhell
