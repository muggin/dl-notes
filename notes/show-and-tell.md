## Show and Tell: A Neural Image Caption Generator
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
  - Pascal VOC 2008 - no train/1k test examples - 59 BLUE-1 points
  - Flickr8k - 6k train/1k test examples - 66 BLUE-1 points
  - Flickr30k - 28k train/1k test examples - 63 BLUE-1 points
  - MSCOCO - 82k train/40k test examples - 27.7 BLEU-4 points
  - SBU - 1M train/no test examples - 28 BLEU-1 points
- 80% of Top-1 generated captions were in the training set (network memorized them?)
- 50% of Top-15 generated captions were in the training set

#### Other notes
