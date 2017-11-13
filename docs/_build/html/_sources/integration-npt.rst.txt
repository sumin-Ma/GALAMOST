NPT ensemble
============

Andersen barostat
-----------------

   Constructor::
   
      Npt(AllInfo all_info, ParticleSet group, ComputeInfo comp_info_group, 
      ComputeInfo comp_info_all, Real T, Real P, Real tauT, Real tauP)
      # initializes a NPT thermostat object for a group of particles with system information, 
      # particle group, information computation for a group particles, information computation 
      # for all particles, temperature, pressure, tauT, tauP.
	  
   Functions::
   
      void setP(Real P) 
      # specifies the pressure with a constant value.
	  
      void setT(Real T)
      # specifies the temperature with a constant value.
	  
      void setT(boost::shared_ptr<Variant> vT)
      # specifies the temperature with a varying value by time step.
	  
   Example::
  
      npt =galamost.Npt(all_info, group, comp_info, comp_info, 1.0, 0.2, 0.5, 0.1)
      app.add(npt)

NPT for rigid body
------------------

   Constructor::
   
      NptRigid(AllInfo all_info, ParticleSet group, ComputeInfo comp_info_group, 
      ComputeInfo comp_info_all, Real T, Real P, Real tauT, Real tauP)
      # initializes a NPT thermostat object for rigid bodies with system information, particle group, 
      # information computation for the group particles, information computation for all particles, 
      # temperature, pressure, tauT, and tauP.
	  
   Functions::
   
      void setT(Real T)
      # specifies the temperature with a fixed value.
	  
      void setT(Variant vT)
      # specifies the temperature with a varying value by time step.
	  
      void setP(Real P)
      # specifies the pressure with a fixed value.
	  
   Example::
   
      group = galamost.ParticleSet(all_info,'all')
      comp_info = galamost.ComputeInfo(all_info, group)
	  
      bgroup = galamost.ParticleSet(all_info, 'body')
      comp_info_b = galamost.ComputeInfo(all_info, bgroup)
	  
      rigidnpt = galamost.NptRigid(all_info, bgroup, comp_info_b, comp_info, 1.0, 0.1, 1.0, 1.0)
      app.add(rigidnpt)
