## Show, Attend and Tell: Neural Image Caption Generation with Visual Attention
_Authors:_ Kelvin Xu, Jimmy Ba, Ryan Kiros, Kyunghyun Cho, Aaron Courville, Ruslan Salakhutdinov, Richard Zemel, Yoshua Bengio  
_Publishing Year:_ 2015  
_Link:_ https://arxiv.org/abs/1502.03044  

#### Summary
The authors presented an attention-based, end-to-end neural solution for the Image Captioning task. The proposed model uses an Encoder-Decoder architecture, similar to the one proposed by [Vinyals](show-and-tell.md). In this work, the Encoder generates a sequence of fixed-size annotation vectors that summarize different parts of the image, instead of a single vector that summarizes the entire image. The Decoder, at each decoding step, looks back into those annotations and chooses the most important ones on which the next prediciton will be conditioned. The authors proposed two types of attention mechanisms, soft attention, where the context vector used for decoding is a weighted sum of all annotations of the image, and hard attention, where the context vector is equal to a single, chosen annotation. Intuitively, in the former case the Decoder partially focuses on all the parts of the image, in the later case the Decoder chooses only one part of the image to focus on.

#### Key points
- Using single vector (output of FC layer) to summarize the entire image may cause less detailed descirptions
- Annotations (summary vectors) were unrolled feature maps from an early Convolutional layer of the Encoder
- VGGNet used as Encoder network, LSTM-based RNN used as Decoder network
- Similarity function between previous hidden state and the annotions implemented as a Perceptron
- Normalized similarity is used in two different way when creating the context vector:
  - Soft-attention - as the weights in the sum of annotations
  - Hard-attention - as parameters of a Mutlinoulli distribution from which a single annotation is sampled
- Attention component can be visualized to provide additional insights into the model

#### Experiments
- Evaluated on 3 data sets:
  - Flickr8k - 7k train/1k test examples - 67 BLEU-1 points, 21.3 BLEU-4 points
  - Flickr30k - 28k rain/1k test examples - 66.9 BLEU-1 points, 19.9 BLEU-4 points
  - MSCOCO - 82k train/40k test examples - 71.8 BLEU-1 points, 25 BLEU-4 points

#### Other notes
