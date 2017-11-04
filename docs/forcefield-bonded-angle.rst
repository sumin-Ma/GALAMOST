Angle bending
-------------

Harmonic angle potential
^^^^^^^^^^^^^^^^^^^^^^^^

   Description:

    .. math::
        :nowrap:

        \begin{eqnarray*}
        V_{\mathrm{angle}}(\theta) = \frac{1}{2}k\left( \theta -\theta_{0} \right)^{2}
        \end{eqnarray*}

    Coefficients:

    - :math:`k` - potential constant ``k`` (in units of energy/radians^2)
    - :math:`\theta_{0}` - equilibrium angle ``theta0`` (in degrees)

   Constructor::
   
      AngleForceHarmonic(boost::shared_ptr<AllInfo> all_info)
      # initializes an angle harmonic interaction object with system information.
	  
   Functions::
   
      void setParams(string& type, Real k, Real theta0)
      # specifies the angle harmonic force parameters with angle type, 
      # potential constant, and equilibrium angle degree.
	  
   Example::
   
      angleforce = galamost.AngleForceHarmonic(all_info)
      angleforce.setParams('P-G-G', 25.000, 120.000)
      app.add(angleforce)

Cosine harmonic angle potential
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

   Description:

    .. math::
        :nowrap:

        \begin{eqnarray*}
        V_{\mathrm{angle}}(\theta)=\frac{1}{2}k\left[\cos \left( \theta \right)-\cos \left( \theta_{0} \right)\right]^{2}	
        \end{eqnarray*}

    Coefficients:

    - :math:`k` - potential constant ``k`` (in units of energy)
    - :math:`\theta_{0}` - equilibrium angle ``theta0`` (in degrees)

   Constructor::
   
      AngleForceHarmonicCos(boost::shared_ptr<AllInfo> all_info)
      # initializes an angle cosine harmonic interaction object with system information.
	  
   Functions::
   
      void setParams(string& type, Real k, Real theta0)
      # specifies the angle cosine harmonic force parameters with angle type, 
      # potential constant, and equilibrium angle degree.
	  
   Example::
   
      angleforce = galamost.AngleForceHarmonicCos(all_info)
      angleforce.setParams('P-G-G',25.000, 120.000)
      app.add(angleforce)
	  
Cosine angle potential
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

   Description:

    .. math::
        :nowrap:

        \begin{eqnarray*}
        V_{\mathrm{angle}}(\theta)=k\left[ 1-\cos \left( \theta - {\theta}_{0} \right) \right]		
        \end{eqnarray*}

    Coefficients:

    - :math:`k` - potential constant ``k`` (in units of energy)
    - :math:`\theta_{0}` - equilibrium angle ``theta0`` (in degrees)

   Constructor::
   
      AngleForceCos(boost::shared_ptr<AllInfo> all_info)
      # initializes an angle cosine interaction object with system information.
	  
   Functions::
   
      void setParams(string& type, Real k, Real theta0)
      # specifies the angle cosine force parameters with angle type, 
      # spring constant, and equilibrium angle degree.
	  
   Example::
   
      angleforce = galamost.AngleForceCos(all_info)
      angleforce.setParams('P-G-G', 25.000, 120.000)
      app.add(angleforce)
  
	  