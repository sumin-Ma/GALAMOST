Application
===========

Modules management
------------------

GALAMOST is a modular program. Application manages and calls modules and run simulation.
Usually, we only define an application object in the context of script. The modules can be 
added ``add()`` into or removed ``remove()`` from the application before runing ``run()`` the simulation. 

.. py:class::  Application(all_info, dt)

   The constructor of an application object.
	  
   :param AllInfo all_info: system information
   :param float dt: integration time step	   

   .. py:function:: add(boost::shared_ptr<*> object)
   
      adds an object to the application.
	  
   .. py:function:: remove(boost::shared_ptr<*> object)
   
      removes an added object.
	  
   .. py:function:: clear()
   
      removes all objects from the application.
	  
   .. py:function:: setDt(float dt)
   
      sets integration time step.	  
	  
   .. py:function:: run(unsigned int N)
   
      runs the simulation for N time steps.
	  
   Example::
   
      dt = 0.001
      app = galamost.Application(all_info, dt)
      # builds up an application.
      app.run(10000)
      # runs the simulation for 10000 time steps.


Multi-stage simulation 
----------------------

An application can have single or multiple stage simulations. The commands in the context of script are executed sequentially.
Every stage simulation is achieved with ``run()``.  Before a stage of simulation, the modules and parameters can be adjusted.
New modules can be added into the applicaitons by ``add()``. The added modules at last stage can be removed from the application, 
otherwise they will be kept. For example:

* First stage simulation::

   dt = 0.001
   app = galamost.Application(all_info, dt)
   app.add(lj)
   app.add(nvt)
   app.add(xml)
   app.run(1000)
  
* Second state simulation::

   app.remove(lj)
   app.remove(nvt)
   app.add(harmonic)
   app.add(npt)
   app.run(1000)
  