## A Deep Reinforced Model for Abstractive Summarization
_Authors:_ Romain Paulus, Caiming Xiong, Richard Socher   
_Publishing Year:_ 2017   
_Link:_ https://arxiv.org/abs/1705.04304   

#### Summary
The authors propose a novel attentional Encoder-Decoder architecture for the task of Abstractive Text Summarization. The model extends the base architecture by using intra-temporal attention and a hybrid Supervised-Reinforced learning procedure. The goals of the method was to improve the coherence of generated sequences and prevent the network from repeating its output when working with longer sequences. The intra-attention means that there are separate context vectors created for the Encoder and Decoder. The Encoder context vector has the usual task of summarizing pieces of the input so that the Decoder can work on specific parts of the input at a time. Encoder context vectors use temporal attention, which is normalized by the sum of all the previous attention distributions. In the case of the Decoder, the context vector summarizes summarize the pieces of the output that was already generated, the goal is to prevent the Decoder from repeating itself. Hybrid learning combines regular supervised learning, that minimizes the negative log-likelihood, with a self-critic policy gradient algorithm that directly optimizes the ROGUE score. The model also used pointing mechanisms to handle OOV.

#### Key points
- Encoder uses temporal attention to prevent it from attending the same parts of the input multiple times
- Decoder attention significantly reduces the repetition problem
- Self-critic is a twist on the REINFORCE algo where the baseline is created by the same network that is optimized
- Optimizing only log-likelihood does not yield optimal ROGUE scores
- Optimizing only ROGUE score does not yield naturaly sounding sequences
- Optimizing mix of log-likelihood and ROGUE yields high quality, human readable sequences

#### Experiments
- Experiments conducted on two datasets:
  - CNN/DailyMail ([Nalapatti et al.](abstractive-text-sum-rnns-beyond.md))
    - ROGUE-1 41.16, ROGUE-2 15.75, ROGUE-L 39.08
  - New York Times
    - ROGUE-1 47.22, ROGUE-2 30.51, ROGUE-L 43.27
- Training only with RL procedure gave best ROGUE scores, the output was of poor quality
- Mixed training gave high ROGUE scores and readable output sequences

#### Other notes
- Finally somebody used readable notations to distinguish between the encoder and decoder hidden states
