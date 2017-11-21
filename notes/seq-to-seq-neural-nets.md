## Sequence to Sequence Learning with Neural Networks
_Authors:_ Ilya Sutskever, Oriol Vinyals, Quoc V. Le    
_Publishing Year:_ 2014   
_Link:_ https://arxiv.org/abs/1409.3215   

#### Summary
The authors propose a general end-to-end architecture for sequence learning that makes minimal assumptions on the sequence structure. The architecture, called RNN Encoder-Decoder, mimics the one presented by [Cho et al](notes/learning-phrase-repr.md). The authors used this solution on the task of Machine Translation, and showed that end-to-end solution can yield satisfying results. Another important contribution from the authors was that reversing the order of words in all source sequences significantly improved the performance of the model.

#### Key points
- Reversing the order of input sequences introduces many short term dependencies between source and target seqs
- The LSTM-based network did not suffer on long sequences after the source order was reversed
- Deep LSTMs significantly outperform shallow LSTMs (4 layers used to train model)
- The fixed-size, summary vector places similar phrases close to each other in the continuous vector space

#### Experiments
- Model trained on the WMT '14 English-French dataset
- Vocabulary was limited to 80k most popular words in both languages
- Best BLEU score 34.81 points.
- Model heavily parallelized, trained on 8GPUs
