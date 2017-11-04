Coulomb interaction
===================

Ewald summation theory
----------------------

The Coulomb interaction between two charge particles is given by:

   .. math::
       :nowrap:
   
       \begin{eqnarray*}
	   U\left( r \right)=f\frac{q_{i} q_{j}}{\varepsilon_{r}r}
       \end{eqnarray*}
	   
where electric conversion factor :math:`f= 1/4\pi \varepsilon_0=138.935\text{ }kJ\text{ }mol^{-1}\text{ }nm\text{ }e^{-2}`.
The total electrostatic energy of N particles and their periodic images is given by

   .. math::
       :nowrap:
   
       \begin{eqnarray*}
        V=\frac{f}{2}\sum\limits_{n}\sum\limits_{i}^{N}{\sum\limits_{j}^{N}{\frac{{q}_{i}{q}_{j}}{\left| {r}_{ij}+n \right|}}}
       \end{eqnarray*}

The electrostatic potential is practically calculated in GALAMOST by

   .. math::
       :nowrap:
   
       \begin{eqnarray*}
	   U\left( r \right)=f\frac{q_{i} q_{j}}{r}
       \end{eqnarray*}
	   
The electric conversion factor and relative dielectric constant are considered in the reduced charge. 
For example, if the mass, length, and energy units are [amu], [nm], and [kJ/mol], respectively, the reduced charge is
:math:`\sqrt{f/{\varepsilon }_{r}}` with :math:`f = 138.935`.

The calculation of Coulomb interaction is splitted into two parts, short-range part and long-range part.
The short-range part can employ Ewald summation and long-range part can employ PPPM or ENUF method. 

Ewald (short-range part)
-------------------------------------

   Constructor::
   
      EwaldForce(boost::shared_ptr<AllInfo> all_info, boost::shared_ptr<NeighborList> nlist,
      boost::shared_ptr<ParticleSet> group, Real r_cut)
      # initializes an Ewald force object for a group of charged particles with system information,
      # neighbor list, particle set, and cut-off radius.
	  
   Functions::
   
      void setParams(string& type0, string& type1, Real kappa)
      # specifies the force parameters with kappa.
	  
      void setParams(Real kappa)
      # specifies the force parameters for all particle types with kappa.
	  
   Example::
   
      group = galamost.ParticleSet(all_info, "charge")
      kappa=0.8
      ewald = galamost.EwaldForce(all_info, neighbor_list, group, 3.0)
      ewald.setParams(kappa)
      app.add(ewald)
	  
PPPM (long-range part)
----------------------

   Constructor::
   
      PPPMForce(boost::shared_ptr<AllInfo> all_info, boost::shared_ptr<NeighborList> nlist,
      boost::shared_ptr<ParticleSet> group)	  
      # initializes a PPPM force object for a group of charged particles with system information,
      #  neighbor list, and particle group.
	  
   Functions::
   
      void setParams(int nx, int ny, int nz, int order, Real r_cut)
      # specifies the PPPM force with the number of grid points in x, y, and z direction, 
      # the order of interpolation, and the cutoff radius of direct force.
	  
      Real getKappa()
      # return the kappa calculated by PPPM force.
	  
   Example::
   
      group = galamost.ParticleSet(all_info, "charge")
      pppm = galamost.PPPMForce(all_info, neighbor_list, group)
      pppm.setParams(32, 32, 32, 5, 3.0)
      app.add(pppm)
	  
ENUF (long-range part)
----------------------

   Constructor::
   
      ENUFForce(boost::shared_ptr<AllInfo> all_info, boost::shared_ptr<NeighborList> nlist,
      boost::shared_ptr<ParticleSet> group)	  
      # initializes an ENUF force object for a group of charged particles with system information,
      # neighbor list, and particle group.
	  
   Functions::
   
      void setParams(Real alpha, Real sigma, int precision, int Nx, int Ny, int Nz)
      # specifies the ENUF force with alpha, hyper sampling factor sigma, 
      # precision determine the order of interpolation (precision*2+2), 
      # and the number of grid points in x, y, and z direction.	
	  
   Example::
   
      group = galamost.ParticleSet(all_info, "charge")
      kappa=0.8
      enuf = galamost.ENUFForce(all_info, neighbor_list, group)
      enuf.setParams(kappa, 2.0, 2, 32, 32, 32)
      app.add(enuf)

	   