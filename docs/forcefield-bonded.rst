Bonded interactions
===================

The bonded forces generally include the bond, angle, and torsion forces. 
Because of the execution mode of SIMD in GPU, it is efficient that a thread calculates and sums the bond, angle, and torsion forces of a particle in the kernel functions. 
Therefore, we can employ the thread whose number is equal to the number of particle to calculate the bonded forces of each particle independently. 
Although the force of a bond will be computed twice (three times for an angle and four times for a torsion) on device, 
it casts the computation well into parallel mode for separated threads of GPUs and is efficient for data copy between host and device memories. 
The common bonded potential energy functions in GALAMOST:

.. toctree::
    :maxdepth: 3

    forcefield-bonded-bond
    forcefield-bonded-angle
    forcefield-bonded-dihedral
