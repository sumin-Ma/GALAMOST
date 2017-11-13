Application
===========

   Constructor::
 
      Application(AllInfo all_info, Real dt)
      # initializes an application object with system information 
      # and integration time step.
	  
   Functions::
   
      void add(boost::shared_ptr<*> object)
      # adds an object to the application.
	  
      void remove(boost::shared_ptr<*> object)
      # removes an added object.
	  
      void clear()
      # removes all objects from the application.
	  
      void run(unsigned int N)
      # runs the simulation for N time steps.
	  
   Example::
   
      dt = 0.001
      app = galamost.Application(all_info, dt)
      # builds up an application.
      app.run(10000)
      # runs the simulation for 10000 time steps.


