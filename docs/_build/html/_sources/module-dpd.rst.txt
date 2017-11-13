Dissipative particle dynamics
=============================

DPD force
^^^^^^^^^

   Constructor::
   
      DpdForce(AllInfo all_info, NeighborList nlist, Real r_cut, Real temperature, unsigned int rand_num)
      # initializes a DPD interaction object with system information, neighbor list, cut-off radius, 
      # temperature, and RNG seed.
	  
      DpdForce(AllInfo all_info, NeighborList nlist, Real r_cut, unsigned int rand_num)
      # initializes a DPD interaction object with system information, neighbor list, cut-off of radius, 
      # and RNG seed. The default temperature is 1.0.
	  
   Functions::
   
      void setParams(string type1, string type2, Real alpha, Real sigma)
      # specifies the DPD interaction parameters with type1, type2, alpha, sigma.
	  
      void setT(Real T)
      # specifies the temperature with a constant value.
	  
      void setT(Variant vT)
      # specifies the temperature with a varying value by time step.
	  
      void setDPDVV()
      # calls the function to enable DPDVV method (the default is GWVV).
	  
   Example::
   
      dpd = galamost.DpdForce(all_info, neighbor_list, 1.0, 12345)
      dpd.setParams('A', 'A', 25.0, 3.0)
      app.add(dpd)
	  
GWVV integration
^^^^^^^^^^^^^^^^

   Constructor:: 
   
      DpdGwvv(AllInfo all_info, ParticleSet group)
     # initializes a GWVV NVT thermostat for a group of DPD particles with 
     # system information and particle group

   Functions::
   
      void setLamda(Real lamda)	
      # specifies lamda.	  
	  
   Example::

      gwvv = galamost.DpdGwvv(all_info, group)
      app.add(gwvv)
	  
