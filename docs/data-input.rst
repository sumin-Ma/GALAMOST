Data input
==========

.. py:class:: Reader

   The basic class of :py:class:`XmlReader` and :py:class:`BinaryReader`.


XML reader
----------

.. py:class:: XmlReader(filename)

   The constructor of XML file parser object.
	  
   :param str filename: The input XML file name.

   Example::
   
      filename = 'dppc.xml'
      # sets the name of input XML file.
      build_method = galamost.XmlReader(filename)
      # builds up a parser object for the input XML file.
   
Binary reader
-------------

.. py:class:: BinaryReader(filename)

   The constructor of GALAMOST binary file parser object.
	  
   :param str filename: The input binary file name.
  
   Example::
   
      filename = 'initial.bin'
      # sets the name of GALAMOST binary file.
	  
      build_method = galamost.BinaryReader(filename)
      # builds up a reading object for input GALAMOST binary file.
   
   
   