Dihedral torsion
----------------

Harmonic dihedral potential
^^^^^^^^^^^^^^^^^^^^^^^^^^^

   Description:

    .. math::
        :nowrap:

        \begin{eqnarray*}
        V_{\mathrm{dihedral}}(\varphi)=k\left[ 1-\cos \left( \varphi-\delta \right) \right]		
        \end{eqnarray*}

    Coefficients:

    - :math:`k` - multiplicative constant ``k`` (in units of energy)
    - :math:`\delta` - phase shift angle ``delta`` (in degrees)

   Constructor::
   
      DihedralForceHarmonic(boost::shared_ptr<AllInfo> all_info)
      # initializes a dihedral harmonic interaction object with system information.
	  
   Functions::
   
      void setParams(string& name, Real k, Real delta)
      # specifies the dihedral harmonic force parameters with dihedral type,
      # multiplicative constant, and phase shift angle.	  
	  
   Example::
   
      dihedralforce = galamost.DihedralForceHarmonic (all_info)
      dihedralforce.setParams('A-B-B-A', 10.0, 0.0)
      app.add(dihedralforce)

OPLS dihedral potential
^^^^^^^^^^^^^^^^^^^^^^^

   Description:

    .. math::
        :nowrap:

        \begin{eqnarray*}
        V_{\mathrm{dihedral}}(\varphi)=k_{1}+k_{2}\left[ 1+\cos \left( \varphi-\delta \right) \right]+k_{3}\left[ 1-\cos \left( 2\varphi-2\delta \right) \right]+k_{4}\left[ 1+\cos \left( 3\varphi-3\delta\right) \right]
        \end{eqnarray*}

    Coefficients:

    - :math:`k_1, k_2, k_3, k_4` - multiplicative constant ``k1, k2, k3, k4`` (in units of energy)
    - :math:`\delta` - phase shift angle ``delta`` (in degrees)

   Constructor::
   
      DihedralForceOplsCosine(boost::shared_ptr<AllInfo> all_info)
      # initializes a dihedral OPLS cosine interaction object with system information.
	  
   Functions::
   
      void setParams(string& name, Real k1, Real k2, Real k3, Real k4, Real delta)
      # specifies the dihedral OPLS cosine force parameters with dihedral type, 
      # k1, k2, k3, k4, and phase shift angle.
	  
   Example::
   
      dihedralforce = galamost.DihedralForceOplsCosine(all_info)
      dihedralforce.setParams('C_33-C_32-C_32-C_32', 0.0, 2.95188, -0.566963, 6.57940, 0.0)
      app.add(dihedralforce)


