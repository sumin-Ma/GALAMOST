Data output
===========

Collective information
----------------------

.. py:class:: DumpInfo(all_info, comp_info, filename)

   initializes an information dump object of a group of particles with system information, information computation, and output file name.
   
   :param AllInfo all_info: The system information.	
   :param ComputeInfo comp_info: The object of calculation of collective information.	   
   :param str filename: The output file name.  

   .. py:function:: dumpAnisotropy()
   
      switches on the dump of information related to anisotropic particles.
	  
   .. py:function:: dumpVirialEnergy(Force force)
   
      switches on the dump of energy and virial of inputting force object.
   
   Example::
   
      dinfo = galamost.DumpInfo(all_info, comp_info, 'data.log')
      dinfo.setPeriod(200)
      app.add(dinfo)

MOL2 dump
---------

.. py:class:: Mol2Dump(all_info, filename)

   initializes a dump object of mol2 files with system information and file name.
	  
   :param AllInfo all_info: The system information.   
   :param str filename: The output file name. 	  

   .. py:function:: setChangeFreeType(string type)
   
      specifies the type of free particles which will be changed to be 'F' in output file.
	  
   .. py:function:: deleteBoundaryBond(bool switch)
   
      switches on the function of not displaying the bonds across the box.
	  
   Example::
   
      mol2 = galamost.Mol2Dump(all_info, 'particles')
      mol2.setPeriod(100000)
      mol2.deleteBoundaryBond(True)
      app.add(mol2)

XML dump
--------

.. py:class:: XmlDump(all_info, filename)

   initializes a dump object of XML files with system information and base file name.

   :param AllInfo all_info: The system information.   
   :param str filename: The output file name. 

	  
.. py:class:: XmlDump(all_info, group, filename)

   initializes a dump object of XML files with system information, particle set, and base file name.

   :param AllInfo all_info: The system information.
   :param ParticleSet group: The group of particles.	
   :param str filename: The output file name.

   .. py:function:: setOutput (PyObject* out_put_list)
   
      indicate the output data type.
	  
   .. py:function:: setOutputPosition(bool switch)
   
      switches the function of output position (the default is true).
	  
   .. py:function:: setOutputType (bool switch)
   
      switches the function of output type (the default is true).
	  
   .. py:function:: setOutputImage(bool switch)
   
      switches the function of output image.
	  
   .. py:function:: setOutputVelocity(bool switch)
   
      switches the function of output velocity.
	  
   .. py:function:: setOutputMass(bool switch)
   
      switches the function of output mass.
	  
   .. py:function:: setOutputCharge(bool switch)
   
      switchesthe function of output charge.
	  
   .. py:function:: setOutputDiameter(bool switch)
   
      switches the function of output diameter.
	  
   .. py:function:: setOutputBody(bool switch)
   
      switches the function of output body.
	  
   .. py:function:: setOutputVirial(bool switch)
   
      switches the function of output virial.
	  
   .. py:function:: setOutputForce(bool switch)
   
      switches the function of output force.
	  
   .. py:function:: setOutputOrientation(bool switch)
   
      switches the function of output orientation.
	  
   .. py:function:: setOutputQuaternion(bool switch)
   
      switches the function of output quaternion.
	  
   .. py:function:: setOutputRotation(bool switch)
   
      switches the function of output rotation velocity.
	  
   .. py:function:: setOutputTorque(bool switch)
   
      switches the function of output torque.
	  
   .. py:function:: setOutputInert(bool switch)
   
      switches the function of output inert tensor.
	  
   .. py:function:: setOutputInit(bool switch)
   
      switches the function of output initiator indication.
	  
   .. py:function:: setOutputCris(bool switch)
   
      switches the function of output cris.
	  
   .. py:function:: setOutputBond(bool switch)
   
      switches the function of output bond.
	  
   .. py:function:: setOutputAngle(bool switch)
   
      switches the function of output angle.
	  
   .. py:function:: setOutputDihedral(bool switch)
   
      switches the function of output dihedral.
   
   Example::
   
      xml = galamost.XmlDump(all_info, 'particles')
      xml.setOutput(['image', 'bond '])
      xml.setPeriod(100000)
      app.add(xml)

DCD trajectory dump
-------------------

.. py:class:: DcdDump(all_info, filename, overwrite)

   initializes a dump object of DCD file with system information, file name, and if overwrite former data.
	  
   :param AllInfo all_info: The system information.	
   :param str filename: The output file name.
   :param bool overwrite: If overwrite the existed DCD file.   
	  
.. py:class:: DcdDump(all_info, group, filename, overwrite)

   initializes a dump object of DCD file with system information, particle set, file name, and if overwrite former data.
	  
   :param AllInfo all_info: The system information.
   :param ParticleSet group: The group of particles.	
   :param str filename: The output file name. 
   :param bool overwrite: If overwrite the existed DCD file.    

   .. py:function:: unpbc(bool switch)
   
      switches the function of outputing the particle position without the application of PBC, the default value is false.
	  
   .. py:function:: unwrap(bool switch)
   
      switches the function of unwrapping the molecules across box boundary due to PBC condition, the default value is false.
	  
   Example::
   
      dcd = galamost.DcdDump(all_info, 'particles',True)
      dcd.unwrap(True)
      dcd.setPeriod(100000)
      app.add(dcd)

GALAMOST binary dump
--------------------

.. py:class:: BinaryDump(all_info, filename)

   initializes a dump object of GALAMOST binary file with system information and file base name.
	  
   :param AllInfo all_info: The system information.
   :param str filename: The output file name. 	  

   .. py:function:: setOutputAll()
   
      switches on the function of output all data.
	  
   .. py:function:: setOutputForRestart()
   
      switches on the function of output data needed for restarting.
	  
   .. py:function:: enableCompression(bool switch)
   
      switches the function of compressing output file.
	  
   Example::
   
      binary = galamost.BinaryDump(all_info, 'particle')
      binary.setOutput(['image', 'bond'])
      binary.setPeriod(10000)
      app.add(binary)


