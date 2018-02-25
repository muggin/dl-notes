## SeqGAN: Sequence Generative Adversarial Nets with Policy Gradient
_Authors:_ Lantao Yu, Weinan Zhang, Jun Wang, Yong Yu   
_Publishing Year:_ 2017   
_Link:_ https://arxiv.org/abs/1609.05473   

#### Summary
The authors propose a novel approach to training neural models for Language Generation using the Adversarial training framework. The model proposed in the paper consists of an RNN based Generator and a CNN-based Discriminator. The Discriminator was expected to discriminate between fake and real sequences, the Generator was expected to output high quality sequences that would consistently trick the Discriminator. Because the outputs of the Generator are discrete, the signal coming from the Discriminator could not be passed using backpropagation back to the Generator. The authors proposed using Policy Gradient methods to overcome this issue. To solve the problem of Credit Assignment the authors proposed using Monte Carlo roll-outs to approximate the rewards on a per-token basis.

#### Key points
- Both the Generator and Discriminator require pretraining using the MLE regime
- Using an RNN Generator and CNN Discriminator allowed the model to work with variable length sequences

#### Experiments
Experiment conducted on different tasks:
- Synthetic Sequence Generation with LSTM-based oracle
- Text Generation - Chinese poem generation and President speech generation
- Music Generation


#### Other notes
- No model outputs were presented, why?
- Authors proposed using Value networks to better guide the training process (used in MaskGAN?)
- Authors proposed a more complex roll-out strategy such as Monte Carlo Tree Search
