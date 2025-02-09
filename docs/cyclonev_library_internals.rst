Mistral CycloneV library internals
==================================

Structure
---------

A large part of the library is generated code from information in the
data directory.  The exception is the routing data that is converter
to compressed binary and put in the gdata directory.  All the
conversions are done with python programs and shell scripts in the
tools directory.


Routing data
------------

The routing data is stored in bzip2-compressed text files named
<die>-r.txt.bz2.  Each line describes a routing mux.

A mux description looks like that:

.. code-block::

    H14.000.032.0003 4:0024_2832 0:GIN.000.032.0005 1:GIN.000.032.0004 2:GIN.000.032.0001 3:GIN.000.032.0000

That line describes the mux for the rnode H14.000.032.0003.  It uses
the pattern 4 as position (24, 2832) and has four inputs connected to
four GIN rnodes.

The chip uses a limited number of mux types, with a specific bit
pattern in the cram controlling a fixed number of inputs and of bit
set/unset values selecting them.  There is a total of 70 different
patterns, currently only described as C++ code in cv-rpats.cc.  An
additional 4 are added to store the variations of pattern 6 where the
default is different.

The special case of pattern 6 looks like:

.. code-block::

    SCLK.014.000.0025 6.3:1413_0638 0:GCLK.000.008.0009 1:RCLK.000.004.0011 4:RCLK.000.004.0003

The ".3" indicates that the default is on slot 3, e.g. value 0x08 or pattern 70+3.

The python script routes-to-bin.py loads this file and generated a
compressed binary version in gdata which matches the rmux structure.
The script mkroutes.sh generates it for all die types.


Block muxes
-----------

The lists of block muxes and options muxes are independant of the
dies.  They're in the block-mux.txt files.  Each mux is described in
these files using the following syntax:


.. code-block::

    g dft_mode m:3 21.42 20.40 20.43
      0 off
      1 on !
      7 dft_pprog

"g" indicates the subtype of mux, which is block-dependant, here
"global".  'm' indicates a symbolic mux, 3 is the number of bits.  It
is followed by the bits coordinates, LSB first.  Here it's an inner
block, so the coordinates are 2D.  Options are also 2D, and peripheral
blocks are 1D.

In such a case of symbolic mux it is followed by the indented possible
values of the mux (in hex) with the exclamation point indicating the
default.

A numeric mux is similar but the type is 'n' and labels on the right
have to be numeric.

Boolean muxes look like this:

.. code-block::

    g clk0_inv               b-   6.45

The 'b' indicates boolean, and '-' indicates the default is false,
otherwise it is '+' for true.  The boolean can be multi-bits, such as
in the following example.  Then all bits are set or unset.

.. code-block::

    g pr_en              b-:2 0.61 0.67

Finally ram muxes look like:

.. code-block::

    g cvpcie_mode                      r-:2    2.21 2.22
    g clkin_0_src                      r2:4  760 761 762 763

In the second case the '2' between r and : indicates that the default
value is 2.

Instanciated muxes can take two forms.  For instance in fpll muxes of
subtype 'c' are instanciated on the counter number, hence have 9
values.  The mux is written as:

.. code-block::

    c cnt_in_src                       r2:2  600 601 | 602 603 | 604 605 | 606 607 | 608 609 | 610 611 | 612 613 | 614 615 | 616 617
    c dprio0_cnt_hi_div                r1:8
      * 8 9 10 11 12 13 14 15
      * 24 25 26 27 28 29 30 31
      * 40 41 42 43 44 45 46 47
      * 56 57 58 59 60 61 62 63
      * 72 73 74 75 76 77 78 79
      * 88 89 90 91 92 93 94 95
      * 104 105 106 107 108 109 110 111
      * 120 121 122 123 124 125 126 127
      * 136 137 138 139 140 141 142 143

Either the bits are indicated on the same line separated by '|', or
they're set as one set per line start with an indented '*'.

The lab, mlab, m10k, mlab and hps_clocks target bits in the 2D cram by
offsetting from a base position computed from the tile position (see
the method pos2bit).  opt targets bits in the oram.  All the others
with the exception of pma3-c target bits in the pram from a position
found in <die>-pram.txt.  pma3-c targets bits in the cram from the
tables in pma3-cram.txt

mux_to_source.py enum <datadir> generates the file cv-bmuxtypes.ipp
while mux_to_source.py mux <datadir> generates the file
cv-bmux-data.cc.  mkmux.sh does both calls.


Logic blocks
------------

Blocks come from two sources, the files <die>-pram.txt indicates all
the peripheral blocks with their pram address.  The files
<die>-<block>.txt where bock is cmux, ctrl, fpll, hmc, hps or iob has
the information of the connections between the blocks and neighbouring
blocks and the routing grid.

blocks_to_source.py generates the cvd-<die>-blk.cc file for a given
die, abd mkblocks.sh calls it for every die.


Inverters
---------

The list of inverters, their cram position and their default value
(always 0 at this point) is in <die>-inv.txt.
inv_to_source.py/mkinv.sh takes care of generating the
cvd-<die>-inv.cc files.


Forced-1 bits
-------------

Five of the seven dies seem to have bits always set to 1.  They are
listed in the files <die>-1.txt.  blocks_to_source.py takes care of
it.


Packages
--------

The file <die>-pkg.txt lists the packages and the pins of each package
for each die.  pkg_to_source.py/mkpkg.sh take cares of generating the
cvd-<die>-pkg.cc files.


Models
------

models.txt includes all the information on variants and models.  The
cv-models.cc file is generated by models_to_source.py called by
mkmodels.sh.


