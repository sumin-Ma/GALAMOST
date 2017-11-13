Particle list
=============

Neighbor list
-------------

.. py:class:: NeighborList(all_info, r_cut, r_buffer)

   The constructor of neighbor list object
  
   :param AllInfo all_info: The system information
   :param float r_cut: The cut-off radius
   :param float r_buffer: The buffer distance

   Functions::
   
      setRCut(Real r_cut, Real r_buffer)
      # specifies the cut-off and buffer distance.
	  
      setNsq()
      # switches on the method of searching all particle to build up list.
	  
      setDataReproducibility()
      # switches on the data reproducibility.
	  
      addExclusionsFromBonds()
      # add 1-2 exclusion into exclusion list.
	  
      addExclusionsFromAngles()
      # add 1-3 exclusion into exclusion list.
	  
      addExclusionsFromDihedrals()
      # add 1-4 exclusion into exclusion list.
	  
      addExclusionsFromBodys()
      # add body exclusion into exclusion list.
	  
      setFilterDiameters()
      # consider the radius of particle in neighbor list which includes the particles 
      # within r_cut + (diameter_i + diameter_j)/2.
   
   Example::
   
      neighbor_list = galamost.NeighborList(all_info, 3.0 ,0.4)

Cell list
---------

.. py:class:: CellList(all_info)

   The constructor of cell list object

   :param AllInfo all_info: The system information

   Functions::
   
      setNominalWidth(Real width)
      # specifies the length of cell.
	  
      setNominalDim(unsigned int x, unsigned int y, unsigned int z)
      # specifies the dimensions of grid in x, y, z directions.
	  
      setDataReproducibility()
      # switches on data reproducibility function.
	  
   Example::
   
      cell_list = galamost.CellList(all_info)

