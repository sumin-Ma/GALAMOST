Dissipative particle dynamics
=============================

DPD force
^^^^^^^^^

.. py:class:: DpdForce(AllInfo all_info, NeighborList nlist, float r_cut, float temperature, unsigned int rand_num)

   initializes a DPD interaction object with system information, neighbor list, cut-off radius, temperature, and RNG seed.
	  
   :param AllInfo all_info: The system information.
   :param NeighborList nlist: The neighbor list.  
   :param float r_cut: The cut-off radius.
   :param float temperature: The temperature.
   :param int rand_num: The seed of random number generator.   
   
.. py:class:: DpdForce(AllInfo all_info, NeighborList nlist, float r_cut, unsigned int rand_num)

   initializes a DPD interaction object with system information, neighbor list, cut-off of radius, and RNG seed. The default temperature is 1.0.
	  
   :param AllInfo all_info: The system information.
   :param NeighborList nlist: The neighbor list.  
   :param float r_cut: The cut-off radius.
   :param int rand_num: The seed of random number generator.	  
	  
   Functions::
   
   .. py:function:: setParams(string type1, string type2, float alpha, float sigma)
   
      specifies the DPD interaction parameters with type1, type2, alpha, sigma.
	  
   .. py:function:: setT(float T)
   
      specifies the temperature with a constant value.
	  
   .. py:function:: setT(Variant vT)
   
      specifies the temperature with a varying value by time step.
	  
   .. py:function:: setDPDVV()
   
      calls the function to enable DPDVV method (the default is GWVV).
	  
   Example::
   
      dpd = galamost.DpdForce(all_info, neighbor_list, 1.0, 12345)
      dpd.setParams('A', 'A', 25.0, 3.0)
      app.add(dpd)
	  
GWVV integration
^^^^^^^^^^^^^^^^

.. py:class:: DpdGwvv(AllInfo all_info, ParticleSet group)

   initializes a GWVV NVT thermostat for a group of DPD particles with system information and particle group

   :param AllInfo all_info: The system information.
   :param ParticleSet group: The group of particles.	   

   .. py:function:: setLamda(float lamda)
   
      specifies lamda.	  
	  
   Example::

      gwvv = galamost.DpdGwvv(all_info, group)
      app.add(gwvv)
	  
