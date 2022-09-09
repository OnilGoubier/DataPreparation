Original data processing
========================

Inputs
------

Data in lcheapo format, file names with extension  *\*.orig.lch*

Initial repository
------------------

This repository contains original lcheapo files, extracted directly from OBS, and original metadata files in yaml format:: 

 initial-repository/<EXPERIMENT>/<CAMPAIGN>/                                         
     <CAMPAIGN>.campaign.yaml
     <NETWORK>.network.yaml
     <STATION>/
         *.orig.lch

Outputs
-------

Data files with extension *.raw.lch*

Processing : Context, environment, tools
----------------------------------------

A campaign can include a number of parks. Each park prepare and process original data (*.orig.lch*) and meta data (*.network.yaml*) files. A campaign meta data file (*.campaign.yaml*) is prepared by the reference scientist of this campaign.
The reference scientist of a campaign checks and processes original data using the following tools:
 
1. lcinfo
2. lccut, if data is damaged  and some parts of data still can be collected and usable.
3. lcfix

Lcfix
-----

**Lcfix** will fix some problems that may exist in L-CHEAPO files. This step is nécessary to make data ready for the next processing (normalisation)

Inputs
^^^^^^

Lcheapo data files *\*.raw.lch*

Processing and Parameters
^^^^^^^^^^^^^^^^^^^^^^^^^

Example of of how **lcfix** command

.. code-block:: console

   $ lcfix BBo5a_22.raw.lch  -d /MyDirectory/Tests/MarinAPark/normalized-repository/EMSO-MOMAR/2007-2008.MOMAR_A/LSV5A -i /MyDirectory/Tests/MarinAPark/suitable-repository/EMSO-MOMAR/2007-2008.MOMAR_A/LSV5A -o /MyDirectory/Tests/MarinAPark/suitable-repository/EMSO-MOMAR/2007-2008.MOMAR_A/LSV5A/lcheapo_fixed

Outputs
^^^^^^^

The processing outputs are files, also in format lcheapo with extension *\*.raw.lch* ready for the next processing (mini-seed creation). They will be stored in the Suitable structure / directories.

Suitable repository
-------------------

This repository contains lcheapo files ready to be transform to miniseed format. It includes also metadata files :campaign and network files in yaml, and infodump files::

   suitable-repository/<EXPERIMENT>/<CAMPAIGN>/ 
       <CAMPAIGN>.campaign.yaml
       <NETWORK>.network.yaml
       infodump/
           networkGraph.dump.json
       <STATION>/
           *.raw.lch

         
       
