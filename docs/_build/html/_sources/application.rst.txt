Application
===========

.. py:class::  Application(all_info, dt)

   The constructor of an application object.
	  
   :param AllInfo all_info: The system information
   :param float dt: The integration time step	   

   .. py:function:: add(boost::shared_ptr<*> object)
   
      adds an object to the application.
	  
   .. py:function:: remove(boost::shared_ptr<*> object)
   
      removes an added object.
	  
   .. py:function:: clear()
   
      removes all objects from the application.
	  
   .. py:function:: run(unsigned int N)
   
      runs the simulation for N time steps.
	  
   Example::
   
      dt = 0.001
      app = galamost.Application(all_info, dt)
      # builds up an application.
      app.run(10000)
      # runs the simulation for 10000 time steps.


