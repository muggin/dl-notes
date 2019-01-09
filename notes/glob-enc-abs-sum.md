## Global Encoding for Abstractive Summarization  
_Authors:_ Junyang Lin, Xu Sun, Shuming Ma, Qi Su   
_Publishing Year:_ 2018    
_Link:_ https://arxiv.org/abs/1805.03989   

#### Summary
The authors propose adding a global encoding module to standard seq2seq architectures with attention for abstractive summarization.
The hope is to refine the hidden state of the Encoder so that they better resemble the global information present in the input document.
The global encoding is applied by filtering the hidden state of the Encoder by using a gating mechanism.
The inputs to the gating unit comes from a Convolutional layer that works on the hidden states of the Encoder followed by a single layer of self-attention.


#### Key points
- Abstractive summarization is more concerned with global information present in the summarized document
- Filter hidden states of Encoder to remove local and strengthen global information of the encoded document
- Use per-timestep gating mechanism - Convolutional Gated Unit
- Pass each hidden state through a Convolutional and self-attention layer to obtain input to gating mechanism
- Convolutional layer should find information about ngrams and local structure
- Self-attention should find correlated information across longer segments of the input


#### Experiments
- The technique shows minor improvements over other baseline models

#### Other notes
- Badly written paper - authors offer little detail about the mechanism apart from a high level description
