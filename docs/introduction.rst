Introduction
============

GALAMOST is a versatile molecular simulation package which is designed to utilize computational power of graphics processing units (GPUs) as much as possible. 
In addition to common features of molecular dynamics programs, it is developed specially for coarse-graining simulation of soft matter systems by encompassing some latest techniques, 
such as hybrid particle-field molecular dynamics, iterative Boltzmann inversion numerical potential method, soft anisotropic particle model, and chain-growth polymerization model. 
   
By continuously optimizing the algorithms, each method implemented on a single GPU by GALAMOST has gained a good performance. Some biomolecules and polymers can be modeled in coarse-grained MD (CGMD) 
simulations implemented by GALAMOST. The CGMD has become a powerful tool, accounting for the problems related to self-assembly, phase separation, and other phenomena of soft matter systems.
Especially, a hybrid particle field MD technique (MD-SCF) for calculating intermolecular interactions has been incorporated to accelerate simulations. 
With this technique, the most computational time-consuming parts in MD, i.e., the intermolecular pair interactions, are replaced by interactions of particles 
with density fields. It will greatly speed up some slowly evolving collective processes in MD simulations, such as micro-phase separation and self-assembly of polymeric systems. 

In addition to analytical potentials, a numerical potential method can be used in GALAMOST by reading the potential tables derived from, such as iterative Boltzmann inversion (IBI) method or other 
structure-based coarse-graining methods by mapping the structural distributions onto the ones obtained either from atomistic simulations or from experiments. With the bottom-up coarse-graining scheme, 
the derived coarse-grained numerical potentials can be applied in larger systems, but under the same thermodynamic conditions. The numerical potential can describe not only non-bonded interactions,
but also the bonded interactions, including stretching, angle bending and dihedral torsion interactions. With this mothed, you can freely design your force field.

Besides some basic functions of general MD, such as CGMD, Brownian dynamics (BD), and dissipative particle dynamics(DPD), GALAMOST also encompasses several tailor-made modules: 
a soft anisotropic particle model has been incorporated for modeling some kinds of anisotropic particles and a stochastic chain-growth polymerization reaction model has been developed 
specially for the studies related to polymerization.
 
In summary, by using these advanced simulation techniques on the GPU, GALAMOST enriches the routes for researchers to investigate soft matter systems via computer simulations. 
