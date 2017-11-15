Anisotropic particle
====================

Gay-Berne model
---------------

GB interaction
^^^^^^^^^^^^^^

.. py:class:: GBForce(all_info, nlist, r_cut)

   The constructor of a method of Gay-Berne force.
   
   :param AllInfo all_info: The system information.
   :param NeighborList nlist: The neighbor list.  
   :param float r_cut: The cut-off radius.	  

   .. py:function:: setParams(string type1, string type2, float epsilon0, float sigma0, float nu, float mu, float sigma_e, float sigma_s, float epsilon_e, float epsilon_s, float Ps)
   
      specifies the GB force parameters with type1, type2, epsilon0, sigma0, nu, mu, end-to-end length (sigma_e), side-by-side length (sigma_s), end-to-end energy (epsilon_e), side-by-side energy (epsilon_s), Ps.
	  
   Example::
   
      gb = galamost.GBForce(all_info, neighbor_list, 10.0)
      gb.setParams('A', 'A' , 1.5, 1.5, 1.0, 2.0,3.0, 1.0, 0.5, 3.0, 1.0)
      # sets parameters: type1, type2, epsilon0, sigma0, nu, mu, sigma_e, 
      # sigma_s, epsilon_e, epsilon_s, Ps.
      app.add(gb)
	  
Bond Force of GB particles
^^^^^^^^^^^^^^^^^^^^^^^^^^

.. py:class:: BondForceAni(all_info)

   The constructor of a method of bond force calculation of anisotropic particles.
   :param AllInfo all_info: The system information.   

   .. py:function:: setParams(string bondtype, float Kbond, float rbond, float Kangle, float dangle)
   
      specifies the bond force parameters with bond type, bond spring constant, end-to-end length of GB particle, angle spring constant, equilibrium angle degree.
	  
   Example::
   
      bondani = galamost.BondForceAni(all_info)
      bondani.setParams('A-A', 100.0 , 4.498, 30.0, 0.0)
      app.add(bondani)

Soft anisotropic model
----------------------

Interaction
^^^^^^^^^^^

.. py:class:: LzwForce(all_info, nlist, r_cut)

   The constructor of a method of LZW force calculation.
	  
   :param AllInfo all_info: The system information.
   :param NeighborList nlist: The neighbor list.  
   :param float r_cut: The cut-off radius.	  

   .. py:function:: setParams(string type1, string type2, float alphaR, float mu, float nu, float alphaA, float beta)
   
      specifies the LZW force parameters with type1, type2, alphaR, mu, nu, alphaA, and beta.
	  
   .. py:function:: setMethod(string method)
   
      chooses a method of 'Disk', 'Janus', ABAtriJanus', 'BABtriJanus'.
	  
   Example::
   
      lzw = galamost.LzwForce(all_info, neighbor_list, 1.0)
      lzw.setParams('A', 'A' , 396.0, 1.0, 0.5, 88.0,60.0/180.0*3.1415926)
      lzw.setMethod('ABAtriJanus')
      # sets method with the choice of ABAtriJanus.
      app.add(lzw)

Thermostat
^^^^^^^^^^

.. py:class:: BerendsenAniNvt(AllInfo all_info, ParticleSet group, ComputeInfo comp_info, float T, float tauT, float tauR)

   The constructor of a Berendsen NVT thermostat for anisotropic particles.
	  
   :param AllInfo all_info: The system information.
   :param ParticleSet group: The group of particles.	
   :param ComputeInfo comp_info: The object of calculation of collective information.	   
   :param NeighborList nlist: The neighbor list.  
   :param float r_cut: The cut-off radius.	 	  

   .. py:function:: setTau(float tauT, float tauR)
   
      specifies the Berendsen NVT thermostat with tauT and tauR.
	  
   .. py:function:: setT(float T)
   
      specifies the temperature with a constant value.
	  
   .. py:function:: setT(Variant vT)
   
      specifies the temperature with a varying value by time step.
	  
   Example::
   
      bere = galamost.BerendsenAniNvt(all_info, group, comp_info, 1.0, 0.3, 0.1)
      app.add(bere)
