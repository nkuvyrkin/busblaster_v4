BusBlaster v4
=============

CPLD designs for the `BusBlaster v4`_ from Dangerous Prototypes.

The buffer logic for the KT-Link is described the KT-Link_-Documentation.

.. _BusBlaster v4: http://dangerousprototypes.com/docs/Minouche_:_Bus_Blaster_v4
.. _KT-Link: http://kristech.eu/sites/default/files/KT-LINK-UM-ENG.pdf


Download and install urJTAG
---------------------------

To program the CPLD a newer version of urJTAG is needed. See the description in the loa-repository for instructions on how to build and install urJTAG (see https://github.com/dergraaf/loa/blob/master/fpga/jtag.markdown).


Program the CPLD
----------------

Load the ISE 13.3 project (project file: `ktlink/ise/busblaster_v4_ktlink.xise`) and click *Generate Programming File*. This will generate `ktlink/ise/toplevel.jed`. At the first time you will have to use *Process > Rerun All* to build everything a second time, otherwise ISE will complain about missed timing specs.

Then go to the `ktlink` folder and type::

    make program

This will load iMPACT to generate an SVF file and then load this SVF file via urJTAG into the CPLD. Make sure that the BusBlaster mode jumper is set to *Update Buffer*.


OpenOCD
-------

An OpenOCD interface description can be found in the xpcc repository (see https://github.com/roboterclubaachen/xpcc/blob/develop/tools/openocd/busblaster-ktlink.cfg).
