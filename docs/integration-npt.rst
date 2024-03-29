NPT ensemble
============

**Overview**

===================   ====================
:ref:`andersen-npt`   :py:class:`Npt`
:ref:`npt-rigid`      :py:class:`NptRigid`
===================   ====================

.. _andersen-npt:

Andersen barostat
-----------------

Reference: H. C. Andersen, J. Chem. Phys., 1980, 72(4), 2384-2393.

.. py:class:: Npt(all_info, group, comp_info_group, comp_info_all, T, P, tauT, tauP)

   The constructor of a NPT thermostat object for a group of particles.

   :param AllInfo all_info: The system information.
   :param ParticleSet group: The group of particles.	
   :param ComputeInfo comp_info_group: The calculation of collective information of group particles.
   :param ComputeInfo comp_info_all: The calculation of collective information of all particles.   
   :param float T: The temperature.  
   :param float P: The pressure.     
   :param float tauT: The thermostat coupling.
   :param float tauP: The barostat coupling.

   .. py:function:: setP(float P) 
   
      specifies the pressure with a constant value.
	  
   .. py:function:: setT(float T)
   
      specifies the temperature with a constant value.
	  
   .. py:function:: setT(Variant vT)
   
      specifies the temperature with a varying value by time step.
	  
   Example::
  
      npt =galamost.Npt(all_info, group, comp_info, comp_info, 1.0, 0.2, 0.5, 0.1)
      app.add(npt)

.. _npt-rigid:  
	  
NPT for rigid body
------------------

.. py:class:: NptRigid(all_info, group, comp_info_group, comp_info_all, T, P, tauT, tauP)

   The constructor of a NPT thermostat object for rigid bodies.
	  
   :param AllInfo all_info: The system information.
   :param ParticleSet group: The group of particles.	
   :param ComputeInfo comp_info_group: The calculation of collective information of group particles.
   :param ComputeInfo comp_info_all: The calculation of collective information of all particles.   
   :param float T: The temperature.  
   :param float P: The pressure.     
   :param float tauT: The thermostat coupling.
   :param float tauP: The barostat coupling.	  

   .. py:function:: setT(float T)
   
      specifies the temperature with a fixed value.
	  
   .. py:function:: setT(Variant vT)
   
      specifies the temperature with a varying value by time step.
	  
   .. py:function:: setP(float P)
   
      specifies the pressure with a fixed value.
	  
   Example::
   
      group = galamost.ParticleSet(all_info,'all')
      comp_info = galamost.ComputeInfo(all_info, group)
	  
      bgroup = galamost.ParticleSet(all_info, 'body')
      comp_info_b = galamost.ComputeInfo(all_info, bgroup)
	  
      rigidnpt = galamost.NptRigid(all_info, bgroup, comp_info_b, comp_info, 1.0, 0.1, 1.0, 1.0)
      app.add(rigidnpt)
	  
Martyna-Tobias-Klein barostat
-----------------------------

Reference: G. J. Martyna, D. J. Tobias, and M. L. Klein, J. Chem. Phys., 1994, 101(5), 4177-4189.

.. note::

    GALAMOST v4.0.0's function

.. py:class:: NPTMTK(all_info, group, comp_info_group, comp_info_all, T, P, tauT, tauP)

   The constructor of a NPTMTK thermostat object for a group of particles.
	  
   :param AllInfo all_info: The system information.
   :param ParticleSet group: The group of particles.	
   :param ComputeInfo comp_info_group: The calculation of collective information of group particles.
   :param ComputeInfo comp_info_all: The calculation of collective information of all particles.   
   :param float T: The temperature.  
   :param float P: The pressure.     
   :param float tauT: The thermostat coupling.
   :param float tauP: The barostat coupling.	  

   .. py:function:: setT(float T)
   
      specifies the temperature with a fixed value.
	  
   .. py:function:: setT(Variant vT)
   
      specifies the temperature with a varying value by time step.
	  
   .. py:function:: setSemiisotropic(float pressxy, float pressz)
   
       specifies the pressure with fixed values for XY and Z directions, respectively.  

   .. py:function:: setSemiisotropic(float pressxy, Variant vpressz)
   
       specifies the pressure with a fixed value for XY direction and a varying value for Z direction, respectively.     
		
   .. py:function:: setAnisotropic(float pressx, float pressy, float pressz)

       specifies the pressure with fixed values for X, Y and Z directions, respectively.    
	 
   Example::

      group = galamost.ParticleSet(all_info,'all')
      comp_info = galamost.ComputeInfo(all_info, group)   
   
      npt = galamost.NPTMTK(all_info, group, comp_info, comp_info, 1.0, 0.1, 0.5, 1.0)
      npt.setSemiisotropic(0.1, 0.1)
      app.add(npt)
	  
Martyna-Tobias-Klein barostat for rigid body
--------------------------------------------

Reference: G. J. Martyna, D. J. Tobias, and M. L. Klein, J. Chem. Phys., 1994, 101(5), 4177-4189.

.. note::

    GALAMOST v4.0.0's function

.. py:class:: NPTMTKRigid(all_info, group, comp_info_group, comp_info_all, T, P, tauT, tauP)

   The constructor of a NPTMTK thermostat object for rigid bodies.
	  
   :param AllInfo all_info: The system information.
   :param ParticleSet group: The group of particles.	
   :param ComputeInfo comp_info_group: The calculation of collective information of group particles.
   :param ComputeInfo comp_info_all: The calculation of collective information of all particles.   
   :param float T: The temperature.  
   :param float P: The pressure.     
   :param float tauT: The thermostat coupling.
   :param float tauP: The barostat coupling.	  

   .. py:function:: setT(float T)
   
      specifies the temperature with a fixed value.
	  
   .. py:function:: setT(Variant vT)
   
      specifies the temperature with a varying value by time step.
	  
   .. py:function:: setSemiisotropic(float pressxy, float pressz)
   
       specifies the pressure with fixed values for XY and Z directions, respectively.  

   .. py:function:: setSemiisotropic(float pressxy, Variant vpressz)
   
       specifies the pressure with a fixed value for XY direction and a varying value for Z direction, respectively.     
		
   .. py:function:: setAnisotropic(float pressx, float pressy, float pressz)

       specifies the pressure with fixed values for X, Y and Z directions, respectively.    
	 
   Example::

      group = galamost.ParticleSet(all_info,'all')
      comp_info = galamost.ComputeInfo(all_info, group)   

      bgroup = galamost.ParticleSet(all_info, 'body')
      comp_info_b = galamost.ComputeInfo(all_info, bgroup)	  
	  
      npt = galamost.NPTMTK(all_info, groupb, comp_infob, comp_info, 1.0, 0.1, 0.5, 1.0)
      npt.setSemiisotropic(0.1, 0.1)
      app.add(npt)	  
