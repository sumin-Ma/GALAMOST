Space constraint
================

Bounce back condition
---------------------

.. py:class:: BounceBackConstrain(boost::shared_ptr<AllInfo> all_info, boost::shared_ptr<ParticleSet> group)

   initializes a bounce back wall object with a group of particles with system information and particle group.
   
   :param AllInfo all_info: The system information.
   :param ParticleSet group: The group of charged particles.     
   

   .. py:function:: addWall(float o_x, float o_y, float o_z, float d_x, float d_y, float d_z)
   
      add wall with original point(o_x, o_y, o_z) and normal direction(d_x, d_y, d_z).
	  
   .. py:function:: addCylinder(float o_x, float o_y, float o_z, float d_x, float d_y, float d_z, float r)
   
      add cylinder with original point (o_x, o_y, o_z) , axis direction (d_x, d_y, d_z) and radius.
	  
   .. py:function:: addSphere(float o_x, float o_y, float o_z, float r)
   
      sphere with center point(o_x, o_y, o_z) and radius.
   
   Example::
   
      bbc = galamost.BounceBackConstrain(all_info,group)
      bbc.addwall(0.0, 10.0, 0.0, 0.0, 1.0, 0.0)
      bbc.addwall(0.0, -10.0, 0.0, 0.0, 1.0, 0.0)
      app.add(bbc)


LJ surface force
----------------
 
.. py:class:: LjConstrainForce(all_info, group, r_cut)

   initializes a LJ interaction surface object for a group of particles with system information, particle set, and cut-off radius.

   :param AllInfo all_info: The system information.
   :param ParticleSet group: The group of charged particles. 
   :param float r_cut: The cut-off radius.	   
   
   .. py:function:: setParams(string type, float epsilon, float sigma, float alpha)
   
      sets the interaction parameters of particle type for LJ surface.
	  
   .. py:function:: addWall(float o_x, float o_y, float o_z, float d_x, float d_y, float d_z)
   
      adds wall with original point(o_x, o_y, o_z) and normal direction(d_x, d_y, d_z) 
	  
   .. py:function:: addCylinder(float o_x, float o_y, float o_z, float d_x, float d_y, float d_z, float r)
   
      adds cylinder with original point(o_x, o_y, o_z) ,axis direction(d_x, d_y, d_z), and radius.
	  
   .. py:function:: addSphere(float o_x, float o_y, float o_z, float r)
   
      adds sphere with center point(o_x, o_y, o_z) and radius.
	  
   Example::
   
      ljc = galamost. LjConstrainForce (all_info, group, 1.0)
      ljc.addWall(0.0, 10.0, 0.0, 0.0, 1.0, 0.0)
      ljc.addWall(0.0, -10.0, 0.0, 0.0, 1.0, 0.0)
      app.add(ljc)


