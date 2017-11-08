### Google's Neural Machine Translation System: Bridging the Gap between Human and MT
_Authors:_ Yonghui Wu, Mike Shuster, Zhifeng Chen, Quoc Le, Mohammad Norouzi  
_Publishing Year:_ 2016  
_Link:_ https://arxiv.org/abs/1609.08144

#### Summary
The authors propose an end-to-end neural model for NMT which is an extension of the Encoder-Decoder architecture. The architecture consists of deep, LSTM-based, recurrent layers combined with attention mechanisms and residual connections between the layers. To improve the models performance on rare words, training was performed on a set of common sub-word units both for the source and target sequences.

#### Key points
- 8 stacked recurrent layers in the Encoder and Decoder
- First layer of the Encoder was bi-directional, all other layers were uni-directional
- Simple stacking of LSTM units works up to 4 layers, then performance decreases (vanishing/expoding gradients)
- Residual connections allow stacking more than 4 layers (improve the gradient flow in backward pass)
- Bahdanau-style attention, with Perceptron similarity function between hidden state and annotations
- Attention connects top layer of Encoder with bottom layer of Decoder (only)
- Sub-word units give the flexibility of character-based models and the efficiency of word-based models
- Data parallelism - 10 model replicas trained at the same time making async updates to parameters
- Model parallelism - each layer of Encoder and Decoder kept on separate GPU, softmax on dedicated GPUs

#### Experiments


#### Other notes
