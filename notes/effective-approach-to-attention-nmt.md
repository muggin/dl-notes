## Effective Approaches to Attention-based Neural Machine Translation
_Authors:_ Minh-Thanh Luong, Hieu Pham, Christopher Manning   
_Publishing Year:_  2015   
_Link:_ https://arxiv.org/abs/1508.04025   

#### Summary
The authors propose two novel approaches to implementing attention mechanisms in Neural Machine Translation models. These solutions are heavily based on the architecture proposed by [Bahdanau et al.](jointly-learn-to-align-and-translate.md) and further increased the performance of the model and shortened inference time. The global approach to attention, which resembles the mentioned work, allows the network to consider all summary vectors (annotations) produced by the Encoder at each step of decoding, and uses a very function to score the similarity between the hidden state of the Decoder and the annotations. The other approach is local attention which allows the Decoder to place attention only a small subset of the source sequence in search for meaningful information for each target word. The location of the subset can be found directly, given the current position in the target sequence (assuming monotonic alignment), or using a predictive component trained jointly with the rest of the model (no alignment assumptions). The authors also propose input-feeding, where the Decoder is fed the input together with the previous attention vector. This gives the network information about past alignment decisions.

#### Key points
- Uses uni-directional, multi-layered LSTM as the Encoder
- Dot-product used as scoring function of annotations and hidden state
- Global attention is computationally expensive and may be impractical to use for longer sequences
- Local attention is computationally efficient and is blend between hard and soft attention (differentiable)
- The subset of annotations in local attenion must to map to a continuous substring of the source sequence
- The size of the subset in local attention is selected empirically

#### Experiments
- Trained on WMT '14 English-German data set - 226M tokens (reduced), 50k German & English vocabulary (limited)
- Models trained/tested on sequences limited to 50 tokens
- Encoder had 4-layers of LSTM units with a 1000-dim hidden state
- Attention-based models perform much better on long sequences when compared to basic Encoder-Decoder
- Best model achieved 20.9 BLEU points (23.0 BLEU points for 8-model ensemble)
- Qualitative experiments showed non-trivial, non-monotonic alignments between sequences

#### Other notes
- Local attention inspired by [Xu 2015](https://arxiv.org/abs/1502.03044)
