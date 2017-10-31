## Neural Machine Translation by Jointly Learning To Align and Translate
_Authors:_ Dzmitry Bahdanau, KyungHyun Cho, Yoshua Bengio  
_Publishing Year:_ 2014  
_Link:_ https://arxiv.org/abs/1409.0473

#### Summary
Authors propose an extension of the Encoder-Decoder architecture that solves the problem of modeling long sequences. Instead of using the Encoder to create a single, fixed-size summary vector of the source sequence, a sequence of vectors (annotations) is created. This solution allows the Decoder to look back into the source sequence and adaptively choose which parts of it are relevant at each decoding step. The summary vectors on which the predictions are conditioned are computed at each step as a weighted sum of all annotations created by the Encoder. The weight is computed as a similarity function between the given annotation and the previous hidden state of the Decoder. 

#### Key points
- Encoder is a single layer bi-directional recurrent network with GRU units
  - Hidden states of the forward and backward layers are concatenated
  - Allows to summarize past and future contexts of a given word
- Decoder is a single layer uni-directional recurrent network with GRU units
- Similarity function between annotation and hidden state implemented as one layer Perceptron
- All components (including Perceptron) trained jointly to maximize prob of target given source
- Method allows modeling non-monotonic alignments between source and target sequences
- Annotation weights can be visualized to show the alignment between source and targer sequences

#### Experiments
- Trained on WMT '14 data set - 348M tokens (reduced), 30k German & English vocabulary (limited)
- Models trained/tested on sequences limited to 30 and 50 tokens
- Attention-based models perform much better on long sequences when compared to basic Encoder-Decoder
- Best model achieved 28.45 BLEU points
- Qualitative experiments showed non-trivial, non-monotonic alignments between sequences

#### Other notes
- First publication on attention models in NMT
