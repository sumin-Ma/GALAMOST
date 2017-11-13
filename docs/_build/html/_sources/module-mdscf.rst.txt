MD-SCF
======

   Constructor::
   
      MdScfForce(AllInfo all_info, unsigned int nx , unsigned int ny, unsigned int nz, Real comp)
      # initializes an object of MD-SCF force with system information, 
      # grid number in x, y, z, direction, and compressibility.
	  
   Functions::
   
      void setParams(string type1, string type2, Real chi)
      # specifies the MD-SCF interaction parameters by pair types with type1, type2, chi parameter.
	  
      void setNewVersion(bool switch)
      # switches the function of newly developed method of implementation.
	  
   Example::
   
      scf = galamost.MdScfForce(all_info, 22, 22, 22, 0.100)
      scf.setParams('N', 'N',0.000)
      scf.setParams('N', 'P',-1.500)
      scf.setParams('P', 'P',0.000)
      scf.setPeriodScf(1,300)
      # sets parameters by computing period of density field, updating period of density field.
      scf.setNewVersion(True)
      # switches to newly developed version.
      app.add(scf)	
      # adds this object to the application.
