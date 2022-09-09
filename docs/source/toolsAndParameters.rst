Tools and Parameters
====================

Data preparation need tools that can be executed with some parameters. The tools are programs or online commands that will process data. For each step of data preparation, one or more tools will be used.

The parameters are not only about directories and files, but also includes some metadata, such as the name of a network, the stations which are parts of a network and the channels of a station. These metadata is stored in a json format in an infodump file.

Infodump
--------

There are 2 kinds of infodump files used during data preparation.

* infodump file for network, containing information on the network, the stations and the channels, corresponds to a campaign
* infodump file for experiment, containing infotmation on the experiment name, responsible, campaigns included in this experiment, validation methods for each campaign, ...

Each kind of these files is in json format with  well defined schema. 

Sdpchain
--------

Sdpchain consists of programs that transform data to a formalized / normalized format such as miniseeds and SDS (SeisComp3 Data Structure). These programs include also time correction. Sdpchain programs / tools create a file that record the trace of the execution steps in json format (process-steps.json). The tools are :

* lc2ms : transform data from lcheapo format to miniseed format
* mscat : concatenate miniseed files
* msdrift : handle a clock drift correction
* ms2sds : transform data from miniseed format to SDS format

Other Tools
-----------

Some other tools are also used, such as :

* msi
* obsinfo
* msmod
