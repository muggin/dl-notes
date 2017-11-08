### Google's Neural Machine Translation System: Bridging the Gap between Human and MT
_Authors:_ Yonghui Wu, Mike Shuster, Zhifeng Chen, Quoc Le, Mohammad Norouzi  
_Publishing Year:_ 2016   
_Link:_ https://arxiv.org/abs/1609.08144   

#### Summary
The authors propose an end-to-end neural model for NMT which is an extension of the Encoder-Decoder architecture. The architecture consists of deep, LSTM-based, recurrent layers combined with attention mechanisms and residual connections between the layers. To improve the models performance on rare words, training was performed on a set of sub-word units (wordpieces) common for the source and target languages. The wordpieces were created using a fully data-driven approach. The target sequence was decoded using a modified version of Beam search that includes a coverage penalty and length normalization. During training and inference data and model parallelism was utilized.

#### Key points
- 8 stacked recurrent layers in the Encoder and Decoder
- First layer of the Encoder was bi-directional, all other layers were uni-directional
- Simple stacking of LSTM units works up to 4 layers, then performance decreases (vanishing/expoding gradients)
- Residual connections allow stacking more than 4 layers (improve the gradient flow in backward pass)
- Bahdanau-style attention, with Perceptron similarity function between hidden state and annotations
- Attention connects top layer of Encoder with bottom layer of Decoder (only)
- Wordpieces give the flexibility of character-based models and the efficiency of word-based models 
- Wordpieces shared for source and target languages to allow model to learn when to copy input to output
- Beam search decoding modified to address the shortcomings of other NMT:
  - Coverage penalty - encourages model to create translation that covers all word in the input sequence
  - Length normalization - to discourage beam search from penalizing longer output sequences
- Data parallelism - 10 model replicas trained at the same time making async updates to parameters
- Model parallelism - each layer of Encoder and Decoder kept on separate GPU, softmax on dedicated GPUs

#### Experiments
- Trained on two data sets:
  - WMT '14 English-French data set - 36M sentence pairs
  - WMT '14 English-German data set - 5M sentence pairs
- Best model scores:
  - English-French - 38.95 BLEU points (model using wordpieces) - 40.35 in ensemble of 8 models
  - English-German - 24.61 BLEU points (model usind wordpieces) - 26.20 in ensemble of 8 models
- Trained for 6 days on 96 NVidia K80 GPUs
  
#### Other notes
