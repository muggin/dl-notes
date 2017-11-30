## Abstractive Sentence Summarization with Attentive Recurrent Neural Networks
_Authors:_ Sumit Chopra, Michael Auli, Alexander M. Rush    
_Publishing Year:_ 2016    
_Link:_ http://nlp.seas.harvard.edu/papers/naacl16_summary.pdf       

#### Summary
The authors propose a neural architecture for abstractive text summarization with a novel Convolutional attention-based Encoder. The solution can be seen as a simplified version of the Encoder-Decoder network proposed by [Bahdanau et al.](jointly-learn-to-align-and-translate.md), or as an extension of a Feedforward network proposed by [Rush et al](neural-attn-abs-sent-summ.md). The Encoder computes 'aggregate vectors' (annotations) of the input sequence using convolution operations on the augmented vector representations of the input tokens. The aggregate vectors are used to find the soft-alignment over the input. The Decoder is a standard RNN that produces output based on its previous state and the context vector returned by the Encoder. The work compares two types of recurrent units in the decoder, an LSTM and an Elman (standard) unit. The authors achieve state-of-the-art performance on the DUC-2004 task.

#### Key points
- The input is kept as a matrix with each column being a full (augmented) vector representation of the token 
- Full word vectors are a sum of the words embedding and its positions embedding (position explicitly encoded)
- Aggregate vectors are created by the Convolutional layer and used to compute the soft-alignment
- Context vectors are a weighted average of ONLY the word embeddings (no position info, etc.)
- Authors used a convolution of width 5, with zero-padding on both ends

#### Experiments
- Model trained on the Gigaword 4M article dataset
- Model tested on the DUC-2003 and DUC-2004 benchmark
- The Elman unit outperformed the LSTM unit in tests, it is also much more computationally efficient

#### Other notes
- Model is called Recurrent Attentive Summarizer (RAS)
