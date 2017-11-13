Information
===========

Perform configuration
---------------------

.. py:class:: PerformConfig(gpu_list)

   The constructor of perform configuration object.
	  
   :param PyObject* gpu_list: The gpu list.

   Example::
   
      global _options
      parser = OptionParser()
      parser.add_option('--gpu', dest='gpu',help='GPU on which to execute')
      (_options, args) = parser.parse_args()
	  
      perform_config = galamost.PerformConfig(_options.gpu)



All information
---------------

.. py:class:: AllInfo(reader, perf_conf)
   
   The constructor of all information object.
   
   :param Reader reader: The file parser   
   :param PerformConfig perf_conf: The perform configuration  
	  
   Functions::
   
      setNDimensions(unsigned int nds);
      # set the number of dimensions
	  
      addParticleType(string ptype)
      # add a particle type to system
	  
      addBondType(string bondtype)
      # add a bond type to system     
      
      addAngleType(string angletype)
      # add a angle type to system     
      
      addBondTypeByPairs()
      # add bond types to system according to particle types      
      
      addAngleTypeByPairs()
      # add angle types to system according to particle types 
   
   Example::
   
      filename = 'PE-1000.xml'
      build_method = galamost.XmlReader(filename)
      perform_config = galamost.PerformConfig(_options.gpu)
      all_info = galamost.AllInfo(build_method,perform_config)


