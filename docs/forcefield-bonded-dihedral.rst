Dihedral torsion
----------------
**Overview**

Dihedrals impose forces on specific quadruplets of particles to model the rotation about chemical bonds.
The dihedrals are specified in :ref:`xml-format` configuration file with the format::

   <dihedral>
   dihedral_type(str)  particle_i(int)  particle_j(int)  particle_k(int)  particle_l(int)
   ...
   </dihedral>
   
By themselves, dihedrals do nothing. Only when you specify a dihedral force in script(i.e. :py:class:`DihedralForceHarmonic`), are forces actually calculated between the listed particles.

=================================   ===================================
:ref:`harmonic-dihedral`            :py:class:`DihedralForceHarmonic`
:ref:`harmonic-dihedral-improper`   :py:class:`DihedralForceHarmonic`
:ref:`opls-dihedral`                :py:class:`DihedralForceOplsCosine`
=================================   ===================================

.. image:: dihedral.png
    :width: 250 px
    :align: center
    :alt: Principle of dihedral torsion

.. _harmonic-dihedral:	

Harmonic dihedral potential
^^^^^^^^^^^^^^^^^^^^^^^^^^^

Description:

    .. math::
        :nowrap:

        \begin{eqnarray*}
        V_{\mathrm{dihedral}}(\varphi)=k\left[ 1+f\cos \left( \varphi-\delta \right) \right]		
        \end{eqnarray*}

    Coefficients:

    - :math:`k` - multiplicative constant ``k`` (in units of energy)
    - :math:`\delta` - phase shift angle ``delta`` (in radians)
    - :math:`f` - factor ``f`` (unitless)	
      - *optional*: defaults to `-1.0`		
	
    .. note::
	    The dihedral angles set in script are in the unit of degree, and the program will convert them into radian automatically.

.. py:class:: DihedralForceHarmonic(all_info)

   The constructor of dihedral harmonic interaction object.
 
   :param AllInfo all_info: The system information.

   .. py:function:: setParams(string name, float k, float delta)
   
      specifies the dihedral harmonic force parameters with dihedral type, multiplicative constant, and phase shift angle.	

   .. py:function:: setCosFactor(float f)
   
      specifies the dihedral harmonic force parameters with factor.		  
	  
   Example::
   
      dihedralforce = galamost.DihedralForceHarmonic(all_info)
      dihedralforce.setParams('A-B-B-A', 10.0, 0.0)
      app.add(dihedralforce)
	  
.. _harmonic-dihedral-improper:	
	  
Harmonic dihedral(improper) potential
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Description:

    .. math::
        :nowrap:

        \begin{eqnarray*}
        V_{\mathrm{dihedral}}(\varphi)=k\left( \varphi-\delta \right)^2		
        \end{eqnarray*}

    Coefficients:

    - :math:`k` - potential constant ``k`` (in units of energy/radians^2)
    - :math:`\delta` - phase shift angle ``delta`` (in radians)

    .. note::
	    The dihedral angles set in script are in the unit of degree, and the program will convert them into radian automatically.	

.. py:class:: DihedralForceHarmonic(all_info)

   The constructor of dihedral harmonic interaction object.
 
   :param AllInfo all_info: The system information.

   .. py:function:: setParams(string name, float k, float delta)
   
      specifies the dihedral harmonic force parameters with dihedral type, potential constant, and phase shift angle.	  
	  
   Example::
   
      dihedralforce = galamost.DihedralForceHarmonic(all_info)
      dihedralforce.setParams('A-B-B-A', 10.0, 0.0, galamost.DihedralForceHarmonic.Prop.improper)
      app.add(dihedralforce)

.. _opls-dihedral:	  
	  
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
    - :math:`\delta` - phase shift angle ``delta`` (in radians)
	
    .. note::
	    The dihedral angles set in script are in the unit of degree, and the program will convert them into radian automatically.

.. py:class:: DihedralForceOplsCosine(all_info)

   The constructor of dihedral OPLS cosine interaction object.
 
   :param AllInfo all_info: The system information.

   .. py:function:: setParams(string name, float k1, float k2, float k3, float k4, float delta)
   
      specifies the dihedral OPLS cosine force parameters with dihedral type, k1, k2, k3, k4, and phase shift angle.
	  
   Example::
   
      dihedralforce = galamost.DihedralForceOplsCosine(all_info)
      dihedralforce.setParams('C_33-C_32-C_32-C_32', 0.0, 2.95188, -0.566963, 6.57940, 0.0)
      app.add(dihedralforce)


