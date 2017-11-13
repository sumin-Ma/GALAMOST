NVT ensemble
============

Nose Hoover thermostat
----------------------

   Constructor::
   
      NoseHooverNvt(AllInfo all_info, ParticleSet group, ComputeInfo comp_info, Real T, Real tauT)
      # initializes a NVT NoseHoover thermostat object for a group of particles with system information, 
      # particle group, information computation, temperature, and tauT.
	  
   Functions::
   
      void setT(Real T)
      # specifies the temperature with a constant value.
	  
      void setT(Variant vT)
      # specifies the temperature with a defined varying value by time step.
	  
   Example::
   
      group = galamost.ParticleSet(all_info, 'all')
      comp_info = galamost.ComputeInfo(all_info, group)
      nh = galamost.NoseHooverNvt(all_info, group, comp_info, 1.0, 0.5)
      app.add(nh)


Berendsen thermostat
--------------------

   Constructor::
    
      BerendsenNvt(AllInfo all_info, ParticleSet group, ComputeInfo comp_info, Real T, Real tauT)
      # initializes a NVT Berendsen thermostat object for a group of particles with system information, 
      # particle set, information computation, temperature, and tauT.
	  
   Functions::
   
      void setT(Real T)
      # specifies the temperature with a constant value.
      
      void setT(Variant vT)
      # specifies the temperature with a varying value by time steps.
   
   
Andersen thermostat
-------------------

   Constructor::
   
      AndersenNvt(AllInfo all_info, ParticleSet group, Real T, Real gamma, unsigned int seed)
      # initializes a NVT Andersen thermostat object for a group of particles with system information, 
      # particle set, temperature, collision frequency, and RNG seed.
	  
   Functions::
   
      void setT(Real T)
      # specifies the temperature with a constant value.
	  
      void setT(Variant vT)
      # specifies the temperature with a varying value by time steps.
	  
   Example::
   
      an = galamost.AndersenNvt(all_info,group,1.0,10.0, 12345)
      app.add(an)

Brownian dynamic thermostat
---------------------------

   Constructor::
   
      BdNvt(AllInfo all_info, ParticleSet group, Real T, unsigned int seed)
      # initializes a Brownian NVT thermostat object with system information, 
      # particle group, temperature, and RNG seed.
	  
   Functions::
   
      void setGamma(Real gamma)
      # specifies the gamma with a constant value.
	  
      void setGamma(string type, Real gamma)
      # specifies the gamma of a particle type.
	  
      void setT(Real T)
      # specifies the temperature with a constant value.
	  
      void setT(Variant vT)
      # specifies the temperature with a varying value by time step.
	  
   Example::
   
      group = galamost.ParticleSet(all_info, 'all')
      bdnvt = galamost.BdNvt(all_info, group, 1.0, 123)
      app.add(bdnvt)



NVT for rigid body
------------------

   Constructor::
   
      NvtRigid(AllInfo all_info, ParticleSet group, Real T, Real tauT)
      # initializes a NVT thermostat object for rigid bodies with system information, 
      # particle group, temperature, and tauT.
	  
   Functions::
   
      void setT(Real T)
      # specifies the temperature with a fixed value.
	  
      void setT(Variant vT)
      # specifies the temperature with a varying value by time step.
	  
   Example::
   
      bgroup = galamost.ParticleSet(all_info, 'body')
      rigidnvt = galamost.NvtRigid(all_info, bgroup, 1.0, 10.0)
      app.add(rigidnvt)

Brownian dynamic for rigid body
-------------------------------
   Constructor::
   
      BdNvtRigid(AllInfo all_info, ParticleSet group, Real T, unsigned int seed)
      # initializes a Brownian NVT thermostat object for rigid bodies with system information, 
      # particle group, temperature, and RNG seed.
	  
   Functions::
   
      void setGamma(Real gamma)
      # specifies the gamma of Brownian method with a constant value.
	  
      void setGamma(const std::string & type, Real gamma)
      # specifies the gamma of Brownian method of a particle type.
	  
      void setT(Real T)
      # specifies the temperature with a constant value.
	  
      void setT(Variant vT)
      # specifies the temperature with a varying value by time step.
	  
   Example::
   
      bgroup = galamost.ParticleSet(all_info, 'body')
      bdrigidnvt = galamost.BdNvtRigid(all_info, bgroup, 1.0, 123)
      app.add(bdrigidnvt)
