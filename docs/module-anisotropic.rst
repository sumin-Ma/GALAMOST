Anisotropic particle
====================

Gay-Berne model
---------------

GB interaction
^^^^^^^^^^^^^^

   Constructor::
   
      GBForce(AllInfo all_info, Neighbor List nlist, Real r_cut)
      # initializes a method of Gay-Berne force with system information, 
      # neighbor list, and cut-off radius.
	  
   Functions::
   
      void setParams(string type1, string type2, Real epsilon0, Real sigma0, Real nu, Real mu,
      Real sigma_e, Real sigma_s, Real epsilon_e, Real epsilon_s, Real Ps)
      # specifies the GB force parameters with type1, type2, epsilon0, sigma0, nu, mu, 
      # end-to-end length (sigma_e), side-by-side length (sigma_s), end-to-end energy (epsilon_e), 
      # side-by-side energy (epsilon_s), Ps.
	  
   Example::
   
      gb = galamost.GBForce(all_info, neighbor_list, 10.0)
      gb.setParams('A', 'A' , 1.5, 1.5, 1.0, 2.0,3.0, 1.0, 0.5, 3.0, 1.0)
      # sets parameters: type1, type2, epsilon0, sigma0, nu, mu, sigma_e, 
      # sigma_s, epsilon_e, epsilon_s, Ps.
      app.add(gb)
	  
Bond Force of GB particles
^^^^^^^^^^^^^^^^^^^^^^^^^^

   Constructor::
   
      BondForceAni(AllInfo all_info)
      # initializes a method of bond force of anisotropic particles with system information.
      
   Functions::
   
      void setParams(string bondtype, Real Kbond, Real rbond, Real Kangle, Real dangle)
      # specifies the bond force parameters with bond type, bond spring constant, 
      # end-to-end length of GB particle, angle spring constant, equilibrium angle degree.
	  
   Example::
   
      bondani = galamost.BondForceAni(all_info)
      bondani.setParams('A-A', 100.0 , 4.498, 30.0, 0.0)
      app.add(bondani)

Soft anisotropic model
----------------------

Interaction
^^^^^^^^^^^

   Constructor::
   
      LzwForce(AllInfo all_info, NeighborList nlist, Real r_cut)
      initializes a method of LZW force with system information, neighbor list, and cut-off radius.
	  
   Functions::
   
      void setParams(string type1, string type2, Real alphaR, Real mu, Real nu, Real alphaA, Real beta)
      # specifies the LZW force parameters with type1, type2, alphaR, mu, nu, alphaA, and beta.
	  
      void setMethod(string method)
      # chooses a method of 'Disk', 'Janus', ABAtriJanus', 'BABtriJanus'.
	  
   Example::
   
      lzw = galamost.LzwForce(all_info, neighbor_list, 1.0)
      lzw.setParams('A', 'A' , 396.0, 1.0, 0.5, 88.0,60.0/180.0*3.1415926)
      lzw.setMethod('ABAtriJanus')
      # sets method with the choice of ABAtriJanus.
      app.add(lzw)

Thermostat
^^^^^^^^^^

   Constructor::
   
      BerendsenAniNvt(AllInfo all_info, ParticleSet group, ComputeInfo comp_info, Real T, 
      Real tauT, Real tauR)
      # initializes a Berendsen NVT thermostat for anisotropic particles with system information, 
	  # particle group, information computation, temperature, tauT, and tauR.
	  
   Functions::
   
      void setTau(Real tauT, Real tauR)
      # specifies the Berendsen NVT thermostat with tauT and tauR.
	  
      void setT(Real T)
      # specifies the temperature with a constant value.
	  
      void setT(Variant vT)
      # specifies the temperature with a varying value by time step.
	  
   Example::
   
      bere = galamost.BerendsenAniNvt(all_info, group, comp_info, 1.0, 0.3, 0.1)
      app.add(bere)
