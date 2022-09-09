Overview
========


OBS data and metadata have to be prepared before delivering them to the RESIF. The data preparation includes :

* transform data from lcheapo format to miniseed format
* transform metadata from yaml to station xml format
* process time correction on data
* validate data and metadata

This documentaion is about all the steps needed to prepare data and metadata, with tools and scripts that can be downloaded from. It's based on `obspy <https://github.com/obspy/obspy/ wiki>`_.

Structure and processing flow
-----------------------------

 .. figure:: images/OBSDataProcessingFlow_En.png
   :scale: 50%

   Processing flow

OBS data from a campaign, are initially processed in an OBS park (marina-park). These data are then sent to NodeA (marina-node) for the next processing needed before being sent to the RESIF.

Tools and parameters
--------------------

Tools / programs from sdpchain (

