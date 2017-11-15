Data format
===========

XML format
----------
We take XML format files as the standard input and output configuration files. 
The XML files can contain coordinates, types, masses, velocities, bond connections, angles, dihedrals and so on.
Here is an example of the XML file of a single molecule system. The molecule consisting of four particles is depicted in following picture. 

.. image:: xml-config.png
    :width: 250 px
    :align: center
    :alt: Principle of dihedral torsion

The data in a line of XML file corresponds to a particle and all particles are given in sequence. 
For example, the coordinate of a particle in x, y, and z directions is written in a line and three columns in XML files. 
However, this rule does not include topological relevant information, including bonds, angles and dihedrals.

   Particles coordinates, Velocities, Types, Masses ... ::
   
      <?xml version="0.2" encoding="UTF-8"?>
      <galamost_xml>
      <configuration time_step="0">
      <box units="sigma"  Lx="10" Ly="10" Lz="10"/>
      <position units="sigma">
      -1 2 -1
      -2 3 0
      -1 4 1
      -1 5 2
      </position>
      <velocity units="sigma/tau">
      1 2 3
      1 0 0
      3 -2 1
      0 1 1
      </velocity>
      <type>
      A
      B
      B
      A
      </type>
      <mass>
      1.0
      2.1
      1.0
      1.0
      </mass>
      </configuration>
      </galamost_xml>

   Bonds, Angles, Dihedrals ... ::  
   
      <bond>
      polymer 0 1
      polymer 1 2
      polymer 2 3
      </bond>
      # As above example, each bond connection should be given in one line (bond type, 
      # particle i and particle j). In addition to bond connection, angle and dihedral information 
      # also should be given explicitly in XML as following format, if they are needed.
      <angle>
      theta 0 1 2
      theta 1 2 3
      </angle>
      <dihedral>
      phi 0 1 2 3
      </dihedral>
   
   
   
   