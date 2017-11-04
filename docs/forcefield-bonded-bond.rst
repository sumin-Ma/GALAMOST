Bond stretching
---------------

Harmonic bond potential
^^^^^^^^^^^^^^^^^^^^^^^

   Description:

    .. math::
        :nowrap:

        \begin{eqnarray*}
        V_{\mathrm{bond}}(r) = \frac{1}{2}k\left( r - r_{0} \right)^{2}
        \end{eqnarray*}

    Coefficients:

    - :math:`k` - spring constant ``k`` (in units of energy/distance^2)
    - :math:`r_0` - equilibrium length ``r0`` (in distance units)

   Constructor::
   
      BondForceHarmonic(boost::shared_ptr<AllInfo> all_info)
      # initializes a harmonic bond interaction object with system information.
	  
   Functions::
   
      void setParams(string& type, Real k, Real r0)
      # specifies the bond interaction parameters with bond type, 
      # spring constant, and equilibrium length.

   Example::
   
      bondforce = galamost.BondForceHarmonic(all_info)
      bondforce.setParams('polymer', 1250.000, 0.470)
      app.add(bondforce)

FENE bond potential
^^^^^^^^^^^^^^^^^^^

   Description:

    .. math::
        :nowrap:

        \begin{eqnarray*}
        V_{\mathrm{bond}}(r)=-\frac{1}{2}k {r_{m}}^{2}\log \left[ 1-\frac{\left(r - r_{0} -\Delta \right)^{2}}{r_{m}^{2}} \right]
        \end{eqnarray*}

        \begin{eqnarray*}
           V_{\mathrm{WCA}}(r)=&4 \varepsilon \left[ \left( \frac{\sigma }{r-\Delta } \right)^{12}-\left( \frac{\sigma }{r-\Delta } \right)^{6} \right] + \varepsilon 
		                       & ,(r - \Delta)<\sigma^{1/6}  \\
                            = & 0 & ,(r - \Delta) \ge \sigma^{1/6}  \\
        \end{eqnarray*}
		
    Coefficients:

    - :math:`k` - attractive force strength ``k`` (in units of energy/distance^2)
    - :math:`r_0` - equilibrium length ``r0`` (in distance units)
      - *optional*: defaults to 0.0
    - :math:`r_m` - maximum bond length ``rm`` (in distance units)
    - :math:`\varepsilon` - *epsilon* (in energy units)
    - :math:`\sigma` - *sigma* (in distance units)
    - :math:`\Delta = (d_{i} + d_{j})/2 - 1.0` - (in distance units); :math:`d_{i}` and :math:`d_{j}` are the diameter of particle :math:`i` and :math:`j` which can be input from XML file.	
    
    Note:
        :math:`\Delta` only will be considered (default value is 0.0) by calling the function ``setConsiderDiameter(True)`` 	
	
   Constructor::
   
      BondForceFene(boost::shared_ptr<AllInfo> all_info)
      # initializes a FENE bond interaction object with system information.
	  
   Functions::
   
      void setParams(string& type, Real k, Real rm)
      # specifies the FENE bond force parameters with bond type, 
      # spring constant, and the maximum length of the bond.
	  
      void setParams(string& type, Real k, Real rm, Real r0)
      # specifies the FENE bond force parameters with bond type, 
      # spring constant, maximum length, and equilibrium length.
	  
      void setParams(string& type, Real k, Real rm, Real epsilon, Real sigma)
      # specifies the FENE+LJ bond parameters with bond type, spring constant, 
      # maximum length of the bond, epsilon, sigma (the latter two parameters 
      # for LJ force between two bonded particles ).

      void setConsiderDiameter(bool con_dia)
      # the diameter of particles will be considered or not

   Example::
   
      bondforcefene = galamost.BondForceFene(all_info)
      bondforcefene.setParams('polymer', 10, 1.2)
      app.add(bondforcefene)

Polynominal bond potential
^^^^^^^^^^^^^^^^^^^^^^^^^^

   Description:

    .. math::
        :nowrap:

        \begin{eqnarray*}
        V_{\mathrm{bond}}(r)=k_{1}\left( r - r_{0} \right)^{2}+k_{2}\left( r - r_{0} \right)^{4}
        \end{eqnarray*}

    Coefficients:

    - :math:`k_1` - spring constant ``k1`` (in units of energy/distance^2)
    - :math:`k_2` - spring constant ``k2`` (in units of energy/distance^4)	
    - :math:`r_0` - equilibrium length ``r0`` (in distance units)

	
   Constructor:: 
   
      BondForcePolynomial(boost::shared_ptr<AllInfo> all_info)
      # initializes a polynomial bond interaction object with system information.
	  
   Functions::
   
      void setParams(string &type, Real k1, Real k2, Real r0)
      # specifies the polynomial bond force parameters with bond type, spring constant k1,
      # spring constant k2, and equilibrium bond length r0.
	  
   Example::
   
      bondforce_polynomial = galamost.BondForcePolynomial(all_info)
      bondforce_polynomial.setParams('polymer', 10.0, 100.0, 1.2)
      app.add(bondforce_polynomial)

	
Morse bond potential
^^^^^^^^^^^^^^^^^^^^

   Description:

    .. math::
        :nowrap:

        \begin{eqnarray*}
        V_{\mathrm{bond}}(r)=&k\left[ 1-e^{-\alpha \left( r-r_{0} \right)} \right]^{2} & r < r_{\mathrm{m}} \\
                            = & 0 & r \ge r_{\mathrm{m}} \\		
        \end{eqnarray*}

    Coefficients:

    - :math:`k` - well depth ``k`` (in units of energy)
    - :math:`\alpha` - controls the 'width' of the potential ``alpha`` (he smaller :math:`\alpha` is, the larger the well)	
    - :math:`r_0` - equilibrium length ``r0`` (in distance units)
    - :math:`r_m` - maximum interaction range ``rm`` (in distance units)
	
   Constructor::
   
      BondForceMorse(boost::shared_ptr<AllInfo> all_info)
      # initializes a Morse bond interaction object and system information.
	  
   Functions::
   
      void setParams(string& name, Real k, Real alpha, Real r0, Real rm)
      # specifies the Morse bond force parameters with bond type, spring constant, alpha 
      # controls the 'width' of the potential, equilibrium bond length, maximum interaction range.
	  
   Example::
   
      bondforce_morse = galamost.BondForceMorse(all_info)
      bondforce_morse.setParams('polymer', 10.0, 1.0, 1.0, 2.0)
      app.add(bondforce_morse)

	  
