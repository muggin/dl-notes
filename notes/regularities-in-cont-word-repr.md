## Linguistic Reglarities in Continuous Space Word Representations
_Authors:_ Tomas Mikolov, Wen-tau Yih, Geoffrey Zweig  
_Link:_  https://www.aclweb.org/anthology/N13-1090

#### Summary
Authors explore the vector-space representations of words learned by the input (projection) layer weights of a neural network.
These representations encode semantic and syntactic regularities of the language.
The authors found that the regularities are characterized by constant vector offsets between pairs of words that share a regularity. 
The paper introduces the classic example v(king) - v(man) + v(woman) ~ v(queen).

#### Key points
- Word representations created using RNNLM (80/320/640/1600 dim)
- Created syntactic analogy questions dataset: _a_ is to _b_ as _c_ is to __?
- To answer analogy question, find vector that is closest to y = x_b - x_a + x_c, (using cosine sim) 
- Trained using maximal likelihood criterion

#### Experiments
- Trained on Broadcast News data - 320M words, 82k vocabulary
- Compared against LSA and Log-Bilinear model
- Beat most models in semantic and syntactic test
- Achieves (nearely) 40% correctness on syntactic tasks


#### Other notes
- Semantic regularities: v(berlin) - v(germany) + v(france) ~ v(paris)
- Syntactic regularities: v(biggest) - v(big) + v(small) ~ v(smallest) 
- Authors don't mention the trianing time of the RNNLM model?
