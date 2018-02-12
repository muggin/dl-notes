## Professor Forcing: A New Algorithm for Training Recurrent Networks
_Authors:_ Alex Lamb, Anirudh Goyal, Ying Zhang, Saizheng Zhang, Aaron Courville, Yoshua Bengio    
_Publishing Year:_ 2016    
_Link:_ https://arxiv.org/abs/1610.09038    

#### Summary
The authors propose an alternative technique of training sequential neural models, called _Professor Forcing_. The main goal is to address the problem of the _Teacher Forcing_ training strategy, where the models is fed tokens from different distributions during training and inference time, which in turn yield suboptimal performance of the model. The main intution of the new technique is to explicitly make the generative-behavior (sampling) and the teacher-forced behavior match as closely as possible. The authors use the GAN framework, with the Discriminator trying to distinguish between teacher-forced and free-running generative behaviors based on the dynamics of the Generators outputs and hidden states. Both the Generator and Discriminator are RNNs, so the model can operate on variable length sequences.

#### Key points
- The Generator `G` is the task-specific generative recurrent model that is being trained
- The Discriminator `D` is a bi-directional RNN with GRU units and a MLP classifier (shared across time) on top of it 
- `D` operates on the outputs and hidden states (before tanh operation) of the Generator
- Training objective of `D` is to correctly classify which sequences were teacher-forced and which freely-running
- Training objective of `G` has three components (`NLL + C_f + C_t`)
  - The usual _Teacher Forcing_ goal of minimizing the negative loglikelihood (`NLL`)
  - Matching the free-running and teacher-forced behaviors, using `D`s scoring (`C_f`)
  - Making the teacher-forced indistinguishable from the free-running behvarior, also using `D`s scoring (`C_t`)
- Gradients are only back-propagated from `D` to `G` only when `D`s accuracy is between 75 and 99%
- The benefits of _Professor Forcing_ are mainly visible when modeling long-term dependencies
- Method also works as a regularizer
- Matching the models behavior at training and test time helps to better model long-term dependencies and robustly generate sequences with length beyond that which was seen at training

#### Experiments
Experiments conducted on three tasks:
- Character-level LM
- Sequential MNIST
- Handwiring Generation 
- Music Synthesis

#### Other notes
- Paper strongly inspired by Adversarial Domain Adaptation research
