Numerical interaction
=====================

The numerical non-bonded, bond, angle, and torsion potentials can be derived from IBI or reverse Monte Carlo method. 
With IBI method, the procedure starts with the potentials of mean force as guessed potentials and then optimizes 
the potentials iteratively by mapping the structural distributions (i.e., radial distribution function, RDF) onto 
the ones obtained either from atomistic simulations or from experiments. The resulting numerical potentials usually 
take the form as a table in which the potential values at discrete grid points of distance are given. 
In the treatment of tabulated potentials, the initial inputted potential tables on grid points of r are 
transformed to the tables (arrays) on grid points of :math:`z = r^2`. With this trick, the :math:`r = SQRT(r^2)` in the inner 
loop of force calculation is avoided, and the force is then calculated by

   .. math::
       :nowrap:
   
       \begin{eqnarray*}
       F=-r\frac{\partial V(r)}{\partial r}\frac{1}{r}=-2r\frac{\partial V(z)}{\partial z}
       \end{eqnarray*}

Within each interval between the grid points, potentials are fitted to a cubic spline function, 
more specifically, for each :math:`x_i< x < x_{i+1}`, let :math:`δ = x - x_i`, :math:`V(x)` is represented by	   

   .. math::
       :nowrap:
   
       \begin{eqnarray*}
       V(x)=C_{0}+C_{1}\delta +C_{2}{\delta}^{2}+C_{3}{\delta}^{3}
       \end{eqnarray*}

where :math:`x` corresponds to :math:`z`, :math:`\theta`, and :math:`\varphi` for particle-particle distance square, bending angle, 
and torsion angle, respectively. :math:`i` is the index of the grid point and :math:`C_0` is the starting potential value of each grid point. 
Other parameters :math:`C_1`, :math:`C_2`, and :math:`C_3` are chosen to make the values of the first derivative and the second derivative 
at both ends of interval :math:`x_i` and :math:`x_{i+1}` equal to the correct values of function V. 
The potentials can be read from two columns in a file by function ``setPotential()`` with the formats, such as for pair interactions

   Example::

      <PairPotential>
      r  potential
      </ PairPotential >
	  
The distance points in first column should be in equal interval and the potentials at the distance points are given in second column. 
The other node names for bond, angle and dihedral are ``BondPotential``, ``AnglePotential``, and ``Dihedralpotential``.

The interaction parameters :math:`(C_0, C_1, C_2, C_3)` can be read directly from four columns in a file by function ``setParams()``
with the formats, such as pair interactions with

   Example::
   
      <PairForcePoints>
      C0  C1  C2  C3
      </PairForcePoints>
	  
The other node names for bond, angle and dihedral are ``BondForcePoints``, ``AngleForcePoints``, and ``DihedralForcePoints``.
	  
Non-bonded interaction
----------------------

   Constructor::
   
      PairForceTable(AllInfo all_info, NeighborList nlist, unsigned int npot)
      # initializes an object of numerical pair force with system information, neighbor list,
      # and the number of potential points.
	  
   Functions::
   
      void setParams(string type1, string type2, Real r_cut, string& filename, int scol, int ecol)
      # specifies the numerical interaction parameters(C0,C1,C2,C3) with type1, type2, cut-off, 
      # inputting file name, start column, end column
	  
      void setPotential(string type1, string type2, std::vector<Real2> potential)
      # specifies the numerical potential with type1, type2, potential array(r, potential)
	  
      void setPotential(string type1, string type2, string& filename, int scol,int ecol)
      # specifies the numerical potential with type1, type2, inputting file name,
      # start column, end column.
	  
   Example::
   
      pair = galamost.PairForceTable(all_info, neighbor_list, 1.3, 2000)
      pair.setParams('A', 'A', 1.3, "table.dat", 0, 3)
      app.add(pair)
	  
Bond interaction
----------------

   Constructor::
   
      BondForceTable(AllInfo all_info, unsigned int npot)
      # initializes an object of numerical bond force with system information 
      # and the number of potential points.
	  
   Functions::
   
      void setParams(string type, Real r_cut, string filename, int scol, int ecol)
      # specifies the numerical bond interaction parameters(C0,C1,C2,C3) with bond type,
      # cut-off, inputting file name, start column, end column.
	   
      void setPotential(string type, std::vector<Real2> potential)
      # specifies the numerical potential with bond type and the array of potential.
	  
      void setPotential(string type, string filename, int scol, int ecol)
      # specifies the numerical potential with bond type, inputting file name,
      # start column, and end column.
	  
   Example::
   
      bond = galamost.BondForceTable(all_info, 2000)
      bond.setParams('1_1', 2.0, "table.dat", 0, 3)
      app.add(bond)
	  
Angle interaction
-----------------

   Constructor::
   
      AngleForceTable(AllInfo all_info, unsigned int npoint)
      # initializes a method of numerical angle force with system information
      # and the number of potential points.
	  
   Functions::
   
      void setParams(string type, string file name, int scol, int ecol)
      # specifies the numerical angle force parameters(C0,C1,C2,C3) with angle type, 
      # inputting file name, start column, and end column.
	  
      void setPotential(string type, std::vector<Real2> potential)
      # specifies the numerical potential with angle type and the array of potential(r, potential).
	  
      void setPotential(string type, string filename, int scol, int ecol)
      # specifies the numerical potential with angle type, inputting file name, 
      # start column, and end column.	  
	  
   Example::
   
      angle = galamost.AngleForceTable(all_info, 500)
      angle.setParams('111', "table.dat", 0, 3)
      app.add(angle)
	  
Dihedral interaction
--------------------

   Constructor::
   
      DihedralForceTable(AllInfo all_info, unsigned int npot)
      # initializes an object of numerical dihedral force with system information 
      # and the number of potential points.
	  
   Functions::
   
      void setParams(string type, string filename, int scol, int ecol)
      # specifies the numerical dihedral force parameters(C0,C1,C2,C3) with dihedral type,
      # inputting file name, start column, end column.
	  
      void setPotential(string dihedral_type, std::vector<Real2> potential)
      # specifies the numerical potential with dihedral type and the array of potential(r, potential).
	  
      void setPotential(string dihedral_type, string file, int scol, int ecol)
      # specifies the numerical potential with dihedral type, inputting file name,
      # start column, end column.	  
	  
   Example::
   
      dihedral = galamost.DihedralForceTable (all_info, 500)
      dihedral.setParams('111', "table.dat", 0, 3) 
      app.add(dihedral)







	  
	  

