## A Neural Attention Model for Abstractive Sentence Summarization
_Authors:_ Alexander M. Rush, Sumit Chopra, Jason Weston     
_Publishing Year:_  2015     
_Link:_ https://arxiv.org/abs/1509.00685     

#### Summary
The authors propose a fully data-driven approach to abstractive sentence summarization, based on a (feedforward) Neural Network Language Model architecture. The model utilizes attention mechanisms to generate words conditioned on the input sequence. The publication presented a very general version of the model, where the Encoder could be treated as an easily replaceable black-box module. The authors proposed three types of Encoder modules, Bag-of-Word Encoder, Convolutional Encoder, and Attention-based Encoder. To solve the OoV/rare-word problem, the authors proposed an extension to the where additional features were used that allowed to control the trade-off between abstractive and extractive summarization.

> To be explicit, compared to Bahdanau et al. (2014) our model uses an NNLM instead of a target-side LSTM, source-side windowed averaging instead of a source-side bi-directional RNN, and a weighted dot-product for alignment instead of an alignment MLP.

#### Key points
- Bag-of-Words Encoder simply averaged the input sequence embeddings with equal weight
- Convolutional Encoder extended the BoW Encoder by allowing interactions between neighboring tokens
- Attention-based Encoder replaces the uniform distribution of BoW with a learned soft alignment
- Model used fixed-sized output context vector (Decoder memory)
- Beam-search decoding utilized to produce final summary
- Both Attention and Convolution Encoders create new input representations by averaging (smoothing) neighboring embeddings - has similar effect as using a bi-directional RNN to create the hidden states

#### Experiments
- Model trained on the Gigaword 4M article dataset
- Model tested on the DUC-2003 and DUC-2004 benchmark

#### Other notes
- Very interesting way of implementing a Encoder-Decoder network using only Feedforward units
- Pretty unreadable notation
