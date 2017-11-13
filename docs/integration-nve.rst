NVE ensemble
============

NVE thermostat
--------------

   Constructor::
    
      Nve(AllInfo all_info, ParticleSet group)
      # initializes a NVE thermostat object for a group of particles 
      # with system information and particle group.
	  
   Functions::
   
      void setZeroForce(bool switch) 
      # switches the function of making all force to be zero (the default is False).
   
   Example::
   
      group = galamost.ParticleSet(all_info,'all')
      thermo = galamost.Nve(all_info,group)
      app.add(thermo)

NVE for rigid body
------------------

   Constructor::
   
      NveRigid(AllInfo all_info, ParticleSet group)
      # initializes a NVE thermostat object for rigid bodies with system 
      # information and particle group.
	  
   Example::
   
      bgroup = galamost.ParticleSet(all_info, 'body')
      rigidnve = galamost.NveRigid(all_info, bgroup)
      app.add(rigidnve)
	  
NVE for rigid body with tunable freedoms

   Constructor::
   
      TranRigid(AllInfo all_info, ParticleSet group)
      # initializes a NVE thermostat object for rigid bodies for defined 
      # freedoms with system information and particle group.
	  
   Functions::
   
      void setTraDimension(bool x, bool y, bool z)
      # switches the freedoms of translocation in x y z directions.
	  
      void setRotDimension(bool x, bool y, bool z)
      # switches the freedoms of rotation in x y z directions.
	  
   Example::
   
      bdrigidnvt = galamost.TranRigid (all_info, bgroup)
      bdrigidnvt.setTraDimension(True, True, True)
      bdrigidnvt.setRotDimension(True, True, True)
      app.add(bdrigidnvt)
	  
