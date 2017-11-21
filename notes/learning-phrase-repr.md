### Learning Phrase Representations using RNN Encoder-Decoder for Statistical MT
_Authors:_ K. Cho, B. van Merrienboer, C. Gulcehre, D. Bahdanau, F. Bougares, H. Schwenk, Y. Bengio   
_Publishing Year:_  2014   
_Link:_ https://arxiv.org/abs/1406.1078    

#### Summary
The authors propose a novel neural architecture called the RNN Encoder-Decoder. The network consists of two recurrent module, the Encoder, which encodes the input sequence into a single, fixed-size representation, and the Decoder, which decodes the fixed-sized representation into an output sequence. The models is specifically good for transduction problems since it can handle inputs and output sequences of varying length. The authors used their solution as a component in a larger, conventional Statistical Machine Translation system, in order to rescore the phrase translation tables created by the translation module. Apart from the architecture, the authors also proposed a new Recurrent unit called the Gated Recurrent Unit (GRU), which can be seen as a simplified version of the LSTM units.

#### Key points
- Encoder learns a continuous space representation of phrases that preserves their semantic and syntactic structure
- At inference the Decoder can be used for two purposes
  - Synthesizing new sequences conditioned - Decoder output from `t-1` fed as input at time `t`
  - Scoring target sequences - tokens of the target sequence fed to Decoder, score based on output probabilities
- At each step of decoding, the models is conditioned on the hidden state of the Decoder and the summary vector
- GRU consists of element-wise, parametrized (learned) _reset_ and _update_ gates
- Max-out layer used as networks output

#### Experiments
- Model trained on the English-French WMT '14 task (Europarl, UN, news commentary datasets)
  - Vocabulary limited to 15k most popular tokens in each language
- Apart from rescoring the phrase table authors also successfully tried to generate translated phrases
- The model encoded single words and short phrases in a way that preserved their semantic meaning
  
#### Other notes
- Authors proposed replacing the SMT with a end-to-end Encoder-Decoder model, later explored by Sutskever
