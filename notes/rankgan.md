## Adversarial Ranking for Language Generation
_Authors:_ Kevin Lin, Xiaodong He, Zhengyou Zhang, Dianqi Li, Ming-Ting Sun   
_Publishing Year:_ 2017   
_Link:_ https://arxiv.org/abs/1705.11001    

#### Summary
In the paper, the authors propose a novel architecture for training Language Generation models using the Adversarial training framework. Most of the architecture and training procedures are analogous to the work described in the [SeqGAN](seqgan.md) publication by Yu et al., the main contribution is replacing the binary-classification Discriminator with a Ranking module. The idea was inspired by the "Learning to Rank" framework from Information Retrieval. The goal of the Ranker is to order a set of sequences by their similary to a provided reference sequence. The reference sequence is always sampled from the ground-truth data, out of the ranked sequences one comes from the Generator/datset and the rest is sampled from the data/Generator. The authors claim that the signal coming from the Ranker allows to train the Generator to produce sequences with a richer structure. Training is also done using Policy Gradient methods.

#### Key points
- Training done Policy Gradient because of discrete outputs from the Generator
- In experiments both Discriminator and Generator are LSTM-based
- Discriminator first encodes sequence into fixed size, vector representation before ranking them
- Ranker can use any similarity metric between two vectors, in experiments cosine similairity was used
- Sofmax layer is used on top of similarity function to yield the final ordering
- Monte Carlo rollouts used to obtain per-token reward

#### Experiments
Experiments on different tasks
- Synthetic Sequence generation
- Text generation - Chinese poem dataset and COCO image captioning dataset

#### Other notes
