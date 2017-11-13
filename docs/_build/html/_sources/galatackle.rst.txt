GalaTackle
==========

Usage
-----

The "galaTackle" is a plugin of GALAMOST to obtain some important statistical information by analyzing the output configuration files. 
You can use this tool by running the following 

   Command::
   
      galaTackle particle.xml
      galaTackle particle0.xml particle1.xml
      galaTackle *.xml
	  
The "galaTackle" plugin supports the configuration files with XML and DCD formats. 
The XML files can be tackled independently. However, a DCD trajectory file has to be tackled along with 
a XML file for particle attributes and topological information, 

   Such as::
   
      galaTackle particle.xml trajectory.dcd
	  
The "galaTackle" can be found in the installed "bin" folder and the XML configuration files should be put in current directory. 
After the executing of above command, a menu of many options will be listed. You can choose one or several functions by 
input the number index separated by blank and press enter to execute them.


Functions
---------

   Function list::
   
      -------------------------------------------------------------
      1  Rg^2              2  Ed^2             3  RDF              
      4  bond_distri       5  angle_distri     6  dihedral_distri  
      7  stress tensor     8  density          9  unwrapping       
      10 MSD               11 RDF-CM           12 MSD-CM           
      13 ents              14 strfac           15 domain size      
      16 dynamic strfac    17 config check     18 RDF between types
      19 XML conversion 
      -------------------------------------------------------------

Function 1:
^^^^^^^^^^^

   Description:
      To calculate the mean square of gyration radius and output result to ``rg2.log``.

Function 2:	  
^^^^^^^^^^^
   
   Description:
      To calculate the mean square of end to end distance and output result to ``ed2.log``.
	  
Function 3:	  
^^^^^^^^^^^
   
   Description:
      To calculate the radial distribution function of all particles and output result to ``*.rdf`` and ``rdf.log``.
	  
   Parameters:
      :maxbin=100|gpu=0|rmax=Lx/2|bondex=false|angleex=false|molex=false
	  
Function 4:	  
^^^^^^^^^^^
   
   Description:
      To calculate the distribution of bond lengths and output result to ``bond_distr.log``.
	  
   Parameters:
      :npot=2001

Function 5:	  
^^^^^^^^^^^
   
   Description:
      To calculate the distribution of angle degrees and output result to ``angle_distr.log``.
	  
   Parameters:
      :npot=2001
	  
Function 6:	  
^^^^^^^^^^^
   
   Description:
      To calculate the distribution of dihedral degrees and output result to ``dihedral_distr.log``.
	  
   Parameters:
      :npot=2001
	  
Function 7:	  
^^^^^^^^^^^
   
   Description:
      To calculate the stress tensor by inputing the parameters of force calculation and output result to ``stress_tensor.log``.
	  
   Parameters:
      :bondex=true|bodyex=true|diameter=true 

Function 8:	  
^^^^^^^^^^^
   
   Description:
      To calculate the real density (g/cm^3) with basic units [amu] and [nm] and output result to ``density.log``.
	  
Function 9:	  
^^^^^^^^^^^
   
   Description:
      To unwrap or shift molecules by changing the image information
	  
   Parameters:
      :unwrap_molecule=true|label_free_particle=particle type| molecule_center_in_box=false|shiftx=0.0|shifty=0.0|remove_image=false| convert_constraint_to_bond=false

	  
Function 10:	  
^^^^^^^^^^^^
   
   Description:
      To compute mean square displacement of all particles and output result to ``msd.log``.

	  
Function 11:	  
^^^^^^^^^^^^
   
   Description:
      To calculate the radial distribution function of the mass center of molecules and output result to ``rdf_cm.log``.
	  
   Parameters:
      :maxbin=100|gpu=0|rmax=Lx/2	  
	  
Function 12:	  
^^^^^^^^^^^^
   
   Description:
      To compute mean square displacement of the mass center of molecules and output result to ``msd_cm.log``.
	  
Function 13:	  
^^^^^^^^^^^^
   
   Description:
      To analyze the entanglements of polymers and output result to ``ents.log``.
	  
Function 14:	  
^^^^^^^^^^^^
   
   Description:
      To calculate the structure factor of particles and output result to ``*.strf`` and ``strf.log``.
	  
   Parameters:
      :kmax=80|gpu=0|qbin=2pi/L

Function 15:	  
^^^^^^^^^^^^
   
   Description:
      To calculate the domain size of components in mixtures and output result to ``domsize.log``.
	  
   Parameters:
      :kmax=20|qc=0.4690|gpu=0

Function 16:	  
^^^^^^^^^^^^
   
   Description:
      To calculate the dynamic structure factor of particles and output result to ``dstrf.log``.
	  
   Parameters:
      :kmax=20|q=7.0

Function 17:	  
^^^^^^^^^^^^
   
   Description:
      To check the configuration including the minimum distance of particles, and the Maximum and minimum length of bonds, etc. and output result to ``config_check.log``.

   Parameters:
      :bondex=true|angleex=true|dihedralex=true|bodyex=true|rcut=2.0


Function 18:	  
^^^^^^^^^^^^
   
   Description:
      To compute the radial distribution function between types and output result to ``*.type.rdf`` and ``rdf_by_type.log``.
	  
   Parameters:
      :maxbin=100|gpu=0|rmax=Lx/2|bondex=false|angleex=false|molex=false


Function 19:	  
^^^^^^^^^^^^
   
   Description:
      To convert XML files into other formats
	  
   Parameters:
      :lammps=false|gromacs=false
  
	  
 	  