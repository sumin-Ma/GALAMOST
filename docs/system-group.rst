Particle set
============

.. py:class:: ParticleSet(all_info, keyword)

   The constructor of particle set object with keyword.
  
   :param AllInfo all_info: The system information.
   :param str keyword: The candidates of keyword are “all”, “body”, “non_body”, “charge”, and the string of particle type.

  
.. py:class:: ParticleSet(all_info, min, max)

   The constructor of particle set object with keyword.
  
   :param AllInfo all_info: The system information.
   :param int min: The particle index range from min to max.
   :param int max: The particle index range from min to max.  

.. py:class:: ParticleSet(all_info, members_list)

   The constructor of particle set object with python object.
  
   :param AllInfo all_info: The system information.
   :param PyObject* members_list: The Python object. Note: multiple keywords and particle index can be included in Python object 
      
.. py:class:: ParticleSet(all_info, member_tags)

   The constructor of particle set object with a vector of particle tags.
  
   :param AllInfo all_info: The system information.
   :param vector<unsigned_int> member_tags: A vector of particle tags	  
  
   .. py:function:: ParticleSet combine(ParticleSet group1, ParticleSet group2)
   
      combines two particle groups into one.	  
   
   Example::
   
      groupC = galamost.ParticleSet(all_info,'C')
      # initializes a particle set object by the particle type.
	  
      groupB = galamost.ParticleSet(all_info,'body')
      # initializes a particle set object of body particles by 'body'.
	  
      group_e = galamost.ParticleSet(all_info,'charge')
      # initializes a particle set object of nonbody particles by 'non_body'.
	  
      groupC = galamost.ParticleSet(all_info,'all')
      # initializes a particle set object of all particles by 'all'.
	  
      group= galamost.ParticleSet(all_info, ['A', 12, 'body'])
      # initializes a particle set object of charged particles by 'charge'.
	  
      groupAB= galamost.ParticleSet.combine (groupA,groupB)
      # combines two particle sets into one set.
   
   
   
   