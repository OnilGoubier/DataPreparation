Node A preparation
==================

Node A processing:

* Check and validate FDSN code
* validate campaign and network file
* transform yaml files to json format
* create and validate metadata stationXML file(s)
* check and validate data (mseed)
* create miniseeds corrected
* transform miniseeds to SDS
* create images
* validate data and metadata using Web application
* deliver data and metadata to RESIF

The package contains the scripts to prepare data in the Node A, before sending the to RESIF (Node B).

.. toctree::

   stationXMLCreateAndValid
   mseedNodeAValidation
   mseedTimeCorrection
   mseed2SDS
   imageCreations
   webValidation
   dataDelivery
