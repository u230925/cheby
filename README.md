# Cheby

[![Build Status](https://travis-ci.org/lerwys/cheby.svg)](https://travis-ci.org/lerwys/cheby)

The Cheby project aims at defining a file format to describe the HW/SW
interface (the memory map), and a set of tools to generate HDL,
drivers, documentation... from these files.

The Cheby project is the successor of the Cheburashka and Wbgen tools.

## Version 0.2

This version offers backward compatiblity with wbgen files, and
provides an setup.py installer.

To install cheby:

    $  python setup.py install [--user]

Add `--user` to install in user directory instead of a system wide
installation.

You can use the `wbgen2cheby` tool to convert from wbgen.

    Usage: wbgen2cheby FILE.wb > FILE.cheby

The tool generates on the standard output a cheby file that contains
extensions for wbgen compatibility.  You can then generate a VHDL file
from this cheby file:

    $ cheby --gen-wbgen-vhdl FILE.cheby > FILE.vhdl

## Version 0.1

The purpose of this version is to handle the Cheburashka files, to
generate HDL, and to understand all the features available.
Currently there is no real packaging.

Two tools are available:

* gena2cheby

    Usage: gena2cheby FILE

Convert the Cheburashka/Gena file to the Cheby file format.  The
result is sent to the standard output.  All valid files are supported,
all the tags and attributes for generating HDL are converted.  Some attributes
are currently ignored; the next step is to define how they will be converted.

Note that included submaps are not converted (but the name extension
is changed from .xml to .cheby).

The result follows the Cheby file format but many extensions (under
the 'x_gena' name) are created to support features not defined in the
Cheby core format.

* cheby

    Usage: cheby --gen-gena-memmap FILE

Generate a VHDL memory map file from FILE.  The result is sent to the
standard output.  The generated file is equivalent to the output of gena.py -m.

    Usage: cheby --gen-gena-regctrl FILE

Generate a VHDL regctrl file from FILE.  The result is sent to the standard
output.  The generated file is equivalent to the output of gena.py

    Usage: cheby --print-memmap FILE
    Usage: cheby --print-simple FILE

Display a textual description of the memory map described by FILE.
