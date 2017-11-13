Data output
===========

Collective information
----------------------

   Constructor::
   
      DumpInfo(AllInfo all_info, ComputeInfo comp_info, string filename)
      # initializes an information dump object of a group of particles with system information,  
      # information computation, and output file name.
   
   Functions::
   
      void dumpAnisotropy()
      # switches on the dump of information related to anisotropic particles.
	  
      void dumpVirialEnergy(Force force)
      # switches on the dump of energy and virial of inputting force object.
   
   Example::
   
      dinfo = galamost.DumpInfo(all_info, comp_info, 'data.log')
      dinfo.setPeriod(200)
      app.add(dinfo)

MOL2 dump
---------
   Constructor::
   
      Mol2Dump(AllInfo all_info, string filename)
      # initializes a dump object of mol2 files with system information and file name.
	  
   Functions::

      void setChangeFreeType(string type)
      # specifies the type of free particles which will be changed to be 'F' in output file.
	  
      void deleteBoundaryBond(bool switch)
      # switches on the function of not displaying the bonds across the box.
	  
   Example::
   
      mol2 = galamost.Mol2Dump(all_info, 'particles')
      mol2.setPeriod(100000)
      mol2.deleteBoundaryBond(True)
      app.add(mol2)

XML dump
--------
   Constructor::
   
      XmlDump(AllInfo all_info, string filename)
      # initializes a dump object of XML files with system information and base file name.
	  
      XmlDump(AllInfo all_info, ParticleSet group, string filename)
      # initializes a dump object of XML files with system information, particle set, and base file name.
	  
   Functions::
   
      void setOutput (PyObject* out_put_list)
      # indicate the output data type.
	  
      void setOutputPosition(bool switch)
      # switches the function of output position (the default is true).
	  
      void setOutputType (bool switch)
      #switches the function of output type (the default is true).
	  
      void setOutputImage(bool switch)
      # switches the function of output image.
	  
      void setOutputVelocity(bool switch)
      # switches the function of output velocity.
	  
      void setOutputMass(bool switch)
      # switches the function of output mass.
	  
      void setOutputCharge(bool switch)
      # switchesthe function of output charge.
	  
      void setOutputDiameter(bool switch)
      # switches the function of output diameter.
	  
      void setOutputBody(bool switch)
      # switches the function of output body.
	  
      void setOutputVirial(bool switch)
      # switches the function of output virial.
	  
      void setOutputForce(bool switch)
      # switches the function of output force.
	  
      void setOutputOrientation(bool switch)
      # switches the function of output orientation.
	  
      void setOutputQuaternion(bool switch)
      # switches the function of output quaternion.
	  
      void setOutputRotation(bool switch)
      # switches the function of output rotation velocity.
	  
      void setOutputTorque(bool switch)
      # switches the function of output torque.
	  
      void setOutputInert(bool switch)
      # switches the function of output inert tensor.
	  
      void setOutputInit(bool switch)
      # switches the function of output initiator indication.
	  
      void setOutputCris(bool switch)
      # switches the function of output cris.
	  
      void setOutputBond(bool switch)
      # switches the function of output bond.
	  
      void setOutputAngle(bool switch)
      # switches the function of output angle.
	  
      void setOutputDihedral(bool switch)
      # switches the function of output dihedral.
   
   Example::
   
      xml = galamost.XmlDump(all_info, 'particles')
      xml.setOutput(['image', 'bond '])
      xml.setPeriod(100000)
      app.add(xml)

DCD trajectory dump
-------------------

   Constructor::
   
      DcdDump(AllInfo all_info, string filename, bool overwrite)
      # initializes a dump object of DCD file with system information, file name, 
      # and if overwrite former data.
	  
      DcdDump(AllInfo all_info, ParticleSet group, string filename, bool overwrite)
      # initializes a dump object of DCD file with system information, particle set, 
      # file name, and if overwrite former data.
	  
   Functions::
   
      void unpbc(bool switch)
      # switches the function of outputing the particle position without the application 
      # of PBC, the default value is false.
	  
      void unwrap(bool switch)
      # switches the function of unwrapping the molecules across box boundary due to 
      # PBC condition, the default value is false.
	  
   Example::
   
      dcd = galamost.DcdDump(all_info, 'particles',True)
      dcd.unwrap(True)
      dcd.setPeriod(100000)
      app.add(dcd)

GALAMOST binary dump
--------------------

   Constructor::
   
      BinaryDump(AllInfo all_info, string filename)
      # initializes a dump object of GALAMOST binary file with system information and file base name.
	  
   Functions::
   
      void setOutputAll()
      # switches on the function of output all data.
	  
      void setOutputForRestart()
      # switches on the function of output data needed for restarting.
	  
      void enableCompression(bool switch)
      # switches the function of compressing output file.
	  
   Example::
   
      binary = galamost.BinaryDump(all_info, 'particle')
      binary.setOutput(['image', 'bond'])
      binary.setPeriod(10000)
      app.add(binary)


