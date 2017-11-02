## Title
_Authors:_ Oriol Vinyals, Alexander Toshev, Samy Bengio, Dumitru Erhan  
_Publishing Year:_  2015  
_Link:_ https://arxiv.org/abs/1411.4555  

#### Summary
Authors proposed a fully neural architecture for image captioning called Neural Image Caption (NIC). The architecture is inspired by the Encoder-Decoder models proposed by Sustkever and Cho for NMT. Similarly to NMT, in Image Captioning the input to the model, an image, should be compressed into a fixed-size format which is then used to generate the textual output. In NIC, the RNN-based Encoder network was replaced with a deep CNN, and the LSTM-based Decoder network was RNN unchanged. The architecture was trained jointly with the goal to minimize the negative log likelihood of each correct word in the target sequence. 


#### Key points
- Google Inception used as Encoder CNN
- CNN pretrained on ImageNet increased performance
- Context vector (image summary) taken as the output of the fully contected layer of the CNN
- Context vector passed into the Decoder only once, at the first step of the decoding

#### Experiments
- Evaluated on 5 different datasets
  - Pascal VOC 2008 - no training examples/1k testing examples
  - Flickr8k - 6k training examples/1k testing examples 
  - Flickr30k - 28k training examples/1k testing examples
  - MSCOCO - 82k training examples/40k testing examples
  - SBU - 1M training examples/no testing examples
- 80% of Top-1 generated captions were in the training set (network memorized them?)
- 50% of Top-15 generated captions were in the training set

#### Other notes
