percolation
===========


This branch refactors the original honeycomb lattice to (hopefully) facilitate extensions to more general lattices.

All such lattices now derive from an abstract base class called Lattice which contains all the logic necessary to determine if a long-range connected component exists. General lattices that derive from this are responsible for two things:

1. Constructing the lattice
2. Implementing percolate(const double& p, const double& q) 

Constructing the lattice naturally involves adding vertices and edges, but must also label extremities that a long-range connected component must include. For this the VertexT includes a field 'traverse' which can be either START, MIDDLE, or END. The is\_crossable routine essentially tries to traverse from a START vertex to an END one. 

The ostream&lt;&lt;operator produces something called a MDL Molfile, which can be viewed in cheap-and-cheerful 3d with webgl/viewer.html. This uses the excellent ChemDoodle web-components library, so you'll need the js and css files available <a href="http://web.chemdoodle.com/installation/5ownload">here</a>. (Note as usual if you're running this from a local filesystem you'll need to allow cross-origin requests, e.g google-chrome -–allow-file-access-from-files).


For background on such thresholds see for example <a href="http://en.wikipedia.org/wiki/Percolation_threshold">here</a> and see <a href="http://arxiv.org/abs/quant-ph/0605014">quant-ph/0605014</a> for their significance in quantum computing.
