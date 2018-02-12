## Scheduled Sampling for Sequence Prediction with Recurrent Neural Networks
_Authors:_ Samy Bengio, Oriol Vinyals, Navdeep Jaitly, Noam Shazeer      
_Publishing Year:_ 2015    
_Link:_ https://arxiv.org/abs/1506.03099   

#### Summary
The authors propose a technique for training sequential neural networks called _Scheduled Sampling_. The main goal is to address the problem of _Teacher Forcing_ training, which is the descrepancy between how the model is trained and used at inference time. The intuition behind the idea is to expose the model to its own errors during training, with hope to teach it how to handle possible errors that it makes. The authors proposed to use a "coin flip" independently for each token, to decided whether the target or sampled token should be fed as input to the network. The probability of using target tokens decreases with the length of the training procedure (based on mini-batch iterations). The authors suggest starting with a high probability of using target tokens and gradually decreasing it to 0.

#### Key points
- Curriculum learning procedure, the probability of using "sampled" token grows with the length of training
- Training the model only with sampled tokens significantly decreases the performance after training
- Three curriculums proposed for probability of using target (`epsilon`), linear, exponential, inverse sigmoidal 
- The authors propose back-propagating through sampled tokens as future work 

#### Experiments
Experiments in three domains:
- Image Captioning
- Constituency Parsing
- Speech Recognition

#### Other notes
- Technique has been criticized by Ferenc Huszar [link](http://www.inference.vc/scheduled-sampling-for-rnns-scoring-rule-interpretation/)
