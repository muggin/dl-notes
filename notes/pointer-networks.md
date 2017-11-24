## Pointer Networks
_Authors:_ Oriol Vinyals, Meire Fortunato, Navdeep Jaitly    
_Publishing Year:_ 2015    
_Link:_ https://arxiv.org/abs/1506.03134    

#### Summary
The authors propose a neural architecture that learn the conditional probability of an output sequence with elements that are discrete tokens corresponding to position in an input sequence. In this setting, the vocabulary/dictionary of the decoder is of variable length, equivalent to the length of the input. The main idea of the solution is to treat the "attention mask" over the hidden states as the output distribution of the Decoder at each step of decoding. The Decoder is fed the values from the the input sequence that correspond to the prediced indices. The authors test their solution on three combinatorial problems: planar convex hulls, Delaunay triangulation and planar TSP. Results show that the network can produce good approximate solutions.

#### Key points
- In Pointer-Networks the size of the output vocabulary does not need to be known a prior
- The complexity of the inference process `O(n^2)`, with `n` being the length of the input 
- Pointer solutions can be applied to other neural architectures, i.e. Memory Networks, Neural Turing Machines

#### Other notes
- Pointer Networks could be used for sorting, but their complexity is worse than many comparison-based sorts
