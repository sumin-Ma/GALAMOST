NVT ensemble
============

Nose Hoover thermostat
----------------------

.. py:class:: NoseHooverNvt(all_info, group, comp_info, T, tauT)

   The constructor of a NVT NoseHoover thermostat object for a group of particles.
	  
   :param AllInfo all_info: The system information.
   :param ParticleSet group: The group of particles.	
   :param ComputeInfo comp_info: The object of calculation of collective information.	   
   :param float T: The temperature.  
   :param float tauT: The thermostat coupling.		  

   .. py:function:: setT(float T)
   
      specifies the temperature with a constant value.
	  
   .. py:function:: setT(Variant vT)
   
      specifies the temperature with a defined varying value by time step.
	  
   Example::
   
      group = galamost.ParticleSet(all_info, 'all')
      comp_info = galamost.ComputeInfo(all_info, group)
      nh = galamost.NoseHooverNvt(all_info, group, comp_info, 1.0, 0.5)
      app.add(nh)


Berendsen thermostat
--------------------

.. py:class:: BerendsenNvt(all_info, group, comp_info, T, tauT)

   The constructor of a NVT Berendsen thermostat object for a group of particles.
	 
   :param AllInfo all_info: The system information.
   :param ParticleSet group: The group of particles.	
   :param ComputeInfo comp_info: The object of calculation of collective information.	   
   :param float T: The temperature.  
   :param float tauT: The thermostat coupling parameter.	

   .. py:function:: setT(float T)
   
      specifies the temperature with a constant value.
      
   .. py:function:: setT(Variant vT)
   
      specifies the temperature with a varying value by time steps.
   
   
Andersen thermostat
-------------------

.. py:class:: AndersenNvt(all_info, group, T, gamma, seed)

   The constructor of a NVT Andersen thermostat object for a group of particles.
	  
   :param AllInfo all_info: The system information.
   :param ParticleSet group: The group of particles.	
   :param float T: The temperature.  
   :param float gamma: The collision frequency.		  
   :param int seed: The seed of random number generator.	

   .. py:function:: setT(float T)
   
      specifies the temperature with a constant value.
	  
   .. py:function:: setT(Variant vT)
   
      specifies the temperature with a varying value by time steps.
	  
   Example::
   
      an = galamost.AndersenNvt(all_info,group,1.0,10.0, 12345)
      app.add(an)

Brownian dynamic thermostat
---------------------------

.. py:class:: BdNvt(all_info, group, T, seed)

   The constructor of a Brownian NVT thermostat object for a group of particles.
	  
   :param AllInfo all_info: The system information.
   :param ParticleSet group: The group of particles.	
   :param float T: The temperature.    
   :param int seed: The seed of random number generator.		  

   .. py:function:: setGamma(float gamma)
   
      specifies the gamma with a constant value.
	  
   .. py:function:: setGamma(string type, float gamma)
   
      specifies the gamma of a particle type.
	  
   .. py:function:: setT(float T)
   
      specifies the temperature with a constant value.
	  
   .. py:function:: setT(Variant vT)
 
      specifies the temperature with a varying value by time step.
	  
   Example::
   
      group = galamost.ParticleSet(all_info, 'all')
      bdnvt = galamost.BdNvt(all_info, group, 1.0, 123)
      app.add(bdnvt)



NVT for rigid body
------------------

.. py:class:: NvtRigid(AllInfo all_info, ParticleSet group, float T, float tauT)

   The constructor of a NVT thermostat object for rigid bodies.
	  
   :param AllInfo all_info: The system information.
   :param ParticleSet group: The group of particles.	
   :param float T: The temperature.    
   :param float tauT: The thermostat coupling parameter.  

   .. py:function:: setT(float T)
   
      specifies the temperature with a fixed value.
	  
   .. py:function:: setT(Variant vT)
   
      pecifies the temperature with a varying value by time step.
	  
   Example::
   
      bgroup = galamost.ParticleSet(all_info, 'body')
      rigidnvt = galamost.NvtRigid(all_info, bgroup, 1.0, 10.0)
      app.add(rigidnvt)

Brownian dynamic for rigid body
-------------------------------

.. py:class:: BdNvtRigid(all_info, group, T, seed)

   The constructor of a Brownian NVT thermostat object for rigid bodies.
	  
   :param AllInfo all_info: The system information.
   :param ParticleSet group: The group of particles.	
   :param float T: The temperature.    
   :param int seed: The seed of random number generator.		  

   .. py:function:: setGamma(float gamma)
   
      specifies the gamma of Brownian method with a constant value.
	  
   .. py:function:: setGamma(const std::string & type, float gamma)
   
      specifies the gamma of Brownian method of a particle type.
	  
   .. py:function:: setT(float T)
   
      specifies the temperature with a constant value.
	  
   .. py:function:: setT(Variant vT)
   
      specifies the temperature with a varying value by time step.
	  
   Example::
   
      bgroup = galamost.ParticleSet(all_info, 'body')
      bdrigidnvt = galamost.BdNvtRigid(all_info, bgroup, 1.0, 123)
      app.add(bdrigidnvt)
