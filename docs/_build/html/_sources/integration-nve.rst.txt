NVE ensemble
============

NVE thermostat
--------------

.. py:class:: Nve(all_info, group)

   initializes a NVE thermostat object for a group of particles with system information and particle group.

   :param AllInfo all_info: The system information.
   :param ParticleSet group: The group of particles.

   .. py:function:: setZeroForce(bool switch) 
   
      switches the function of making all force to be zero (the default is False).
   
   Example::
   
      group = galamost.ParticleSet(all_info,'all')
      thermo = galamost.Nve(all_info,group)
      app.add(thermo)

NVE for rigid body
------------------

.. py:class:: NveRigid(all_info, group)

   initializes a NVE thermostat object for rigid bodies with system information and particle group.
   
   :param AllInfo all_info: The system information.
   :param ParticleSet group: The group of particles.
   
   Example::
   
      bgroup = galamost.ParticleSet(all_info, 'body')
      rigidnve = galamost.NveRigid(all_info, bgroup)
      app.add(rigidnve)
	  
NVE for rigid body with tunable freedoms
----------------------------------------

.. py:class:: TranRigid(all_info, group)

   initializes a NVE thermostat object for rigid bodies for defined freedoms with system information and particle group.
   
   :param AllInfo all_info: The system information.
   :param ParticleSet group: The group of particles.	  

   .. py:function:: setTraDimension(bool x, bool y, bool z)
   
      switches the freedoms of translocation in x y z directions.
	  
   .. py:function:: setRotDimension(bool x, bool y, bool z)
   
      switches the freedoms of rotation in x y z directions.
	  
   Example::
   
      bdrigidnvt = galamost.TranRigid (all_info, bgroup)
      bdrigidnvt.setTraDimension(True, True, True)
      bdrigidnvt.setRotDimension(True, True, True)
      app.add(bdrigidnvt)
	  
