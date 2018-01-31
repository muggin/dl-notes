## Twin Networks: Matching The Future For Sequence Generation
_Authors:_ Dmitriy Serdyuk, Nan Rosemary Ke, Alessandro Sordoni, Adam Trischler, Chris Pal, Yoshua Bengio   
_Publishing Year:_ 2018   
_Link:_ https://arxiv.org/abs/1708.06742    

#### Summary
The authors introduce a simple regularization technique that is applicable to generative sequential models that encourages them to plan ahead. Along with any regular model, an additional _backward_ recurrent network is trained that generates the output sequence in reverse order. The regularizer (loss penalty) forces the hidden states of the original _forward_ network to be close to the co-temporal states of the _backward_ network with the hope that the _forward_ network will learn to contain more meaningful information from the past in its hidden state. This would allow it to generate long-term dependencies and increase coherence of the output sequences. The regularization term can be a simple Euclidean distance between the co-temporal hidden states or a learned metric involving an affine transformation. After the training procedure, the _backward_ network is discarded. 

#### Key points
- To provide a more stable learning signal, the gradient from the penalty term is only propagated to the _forward_ net
- This technique almost doubles the training computational complexity (because it adds a second network)
- Twin module can be plugged into existing architectures with minor changes

#### Experiments
Experiments conducted in multiple domains:
- Speech Recognition (WSJ dataset)
  - Baseline - Test CER 6.8, WER: 9.0
  - TwinNet - Test CER: 6.2, WER: 8.4
- Image Captioning (MSCOCO dataset)
  - Baseline - B1: 73.2, B2: 56.3, B3: 41.4, B4: 30.1, METEOR: 25.3, CIDEr: 96.6
  - TwinNet - B1: 73.8, B2: 56.9, B3: 42.0, B4: 30.6, METEOR: 25.2, CIDEr: 97.3
- Language Generation (PTB)
  - Baseline - Test Perp: 61.2, Valid Perp: 58.5
  - TwinNet - Test Perp: 61.0, Valid Perp: 58.3

#### Other notes
- Very simple and intuitive idea
