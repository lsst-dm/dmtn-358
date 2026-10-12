.. image:: https://img.shields.io/badge/dmtn--358-lsst.io-brightgreen.svg
   :target: https://dmtn-358.lsst.io
.. image:: https://github.com/lsst-dm/dmtn-358/workflows/CI/badge.svg
   :target: https://github.com/lsst-dm/dmtn-358/actions/

############################################
Using LLMs to Port a Large C Library to Rust
############################################

DMTN-358
========

In 2026 large language model coding agents such as Codex and Claude have developed rapidly and changed the face of software development. They can be used for debugging, performance optimization, and adding features to existing codebases. As the tooling improved we decided to see if we could use these systems to port a large C library to Rust. The library we chose was the Starlink AST library, a library that consists of 200,000 lines of C (not including comments or blank lines) that has been in development for over 30 years and contains some very specific fixes for very rare combinations of FITS headers.

In this paper I will tell the story of agents getting confused (but also agents improving), agents cutting corners and hoping I wouldn't notice, agents finding bugs in the original code but then making sure the Rust had the same bugs, eye-watering token costs, and how the real lesson from this journey is that your ported code is only as good as the test suite of your original library.

Links
=====

- Live drafts: https://dmtn-358.lsst.io
- GitHub: https://github.com/lsst-dm/dmtn-358

Build
=====

This repository includes lsst-texmf_ as a Git submodule.
Clone this repository::

    git clone --recurse-submodules https://github.com/lsst-dm/dmtn-358

Compile the PDF::

    make

Clean built files::

    make clean

Updating acronyms
-----------------

A table of the technote's acronyms and their definitions are maintained in the `acronyms.tex` file, which is committed as part of this repository.
To update the acronyms table in ``acronyms.tex``::

    make acronyms.tex

*Note: this command requires that this repository was cloned as a submodule.*

The acronyms discovery code scans the LaTeX source for probable acronyms.
You can ensure that certain strings aren't treated as acronyms by adding them to the `skipacronyms.txt <./skipacronyms.txt>`_ file.

The lsst-texmf_ repository centrally maintains definitions for LSST acronyms.
You can also add new acronym definitions, or override the definitions of acronyms, by editing the `myacronyms.txt <./myacronyms.txt>`_ file.

Updating lsst-texmf
-------------------

`lsst-texmf`_ includes BibTeX files, the ``lsstdoc`` class file, and acronym definitions, among other essential tooling for LSST's LaTeX documentation projects.
To update to a newer version of `lsst-texmf`_, you can update the submodule in this repository::

   git submodule update --init --recursive

Commit, then push, the updated submodule.

.. _lsst-texmf: https://github.com/lsst/lsst-texmf
