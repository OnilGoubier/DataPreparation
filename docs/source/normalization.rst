Normalization : miniseed creation
=================================

Inputs
------

* Data files in lcheapo format with *.raw.lch* extension
* Metadata files : campaign.yaml, network.yaml and infodump files
* process-steps.json, if it exists

All these files are found in the suitable repository.

Outputs
-------

Miniseed files that will be stored in the normalized repository

Normalized repository
^^^^^^^^^^^^^^^^^^^^^

This repository contains data and metadata files after having been converted to the standard format miniseed::

   normalized-repository/<EXPERIMENT>/<CAMPAIGN>/ 
       <CAMPAIGN>.campaign.yaml
       <NETWORK>.network.yaml
       <NETWORK>.station.xml
       infodump/
           networkGraph.dump.json
       <STATION>/
           miniseed_basic/
               *.mseed
           miniseed_corrected/
               *.mseed
           process-steps.json

Processing steps
----------------

The main tools used are **lc2ms** and **mscat**.

Lc2ms
^^^^^

**lc2ms** converts lcheapo files to miniseed format. 
The following example shows how to run **lc2ms**. 

.. code-block:: console

   $lc2ms BBo6a_21.fix.lch -d /MyDirectory/Tests/MarinAProcesses/normalized-repository/EMSO-MOMAR/2007-2008.MOMAR_A/LSV6A -i /MyDirectory/Tests/MarinAProcesses/normalized-repository/EMSO-MOMAR/2007-2008.MOMAR_A/LSV6A/lcheapo_fixed -o /MyDirectory/Tests/MarinAProcesses/normalized-repository/EMSO-MOMAR/2007-2008.MOMAR_A/LSV6A/ -m :%E.%S.00.%C.%Y.%D.%T.mseed --experiment 4G --sitename LSV6A --obstype BBOBS1 --sernum 21 -p /opt/sdpchain2/config/lc2ms.properties

Some parameters such as the name of experiment, the name of site / station, the type of statio  as well as the seial number can be obtained from a network infodump file. 

To get more information, run the following command

.. code-block:: console

   $lc2ms -h

Some remarks

* Before running the program make sure that the output directry is empty
* Currently data quality of an miniseed file created by lc2ms is still *Q*, weneed to change this quality later in the nex processing

Mscat
^^^^^

When there are more than one file for a channel of a station, the files can be concatenated using **mscat**.

.. code-block:: console

   $mscat 4G.LSVSA.00.BH2.2007.206.120000.mseed 4G.LSVSA.00.BH2.2007.230.104615.mseed -d /MyDirectory/normalized-repository/EMSO-MOMAR/2007-2008.MOMAR_A/LSVSA -i /MyDirectory/normalized-repository/EMSO-MOMAR/2007-2008.MOMAR_A/LSVSA/miniseed_basic -o /MyDirectory/normalized-repository/EMSO-MOMAR/2007-2008.MOMAR_A/LSVSA/miniseed_concat

For more information :

.. code-block:: console

   $mscat -h

Change network and data quality
-------------------------------

Currently, lc2ms creates miniseed files with data quality code Q instead of D, and the network code is **NN** instead of a network code such as **4G**. To fixe this matter **msmod** is used after the creation of miniseed files.

.. code-block:: console

   $msmod -i 4G.LSVWA.00.BDH.2007.203.150000.mseed 4G.LSVWA.00.SH2.2007.203.150000.mseed 4G.LSVWA.00.SH1.2007.203.150000.mseed 4G.LSVWA.00.SH3.2007.203.150000.mseed --net 4G --quality D

Use the following command for more information 

.. code-block:: console

   $msmod -h
