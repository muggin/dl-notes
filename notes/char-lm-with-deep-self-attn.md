## Character-Level Language Modeling with Deeper Self-Attention
_Authors:_ Rami Al-Rfou, Dokook Choe, Noah Constant, Mandy Guo, Llion Jones   
_Publishing Year:_ 2018  
_Link:_ https://arxiv.org/abs/1808.04444 

#### Summary
The authors propose applying the Transformer architecture to character-level language modeling.
The hope is that several layers of self-attenion modules will be able to address the shortcomings of RNN-based models, such as using long-term context.
The proposed model uses 64 self-attention layers to predict the next character based on a context of 512 previous characters.
During training, the model is augmented with auxiliary losses that enable faster convergence and regularize the model.


#### Key points
- Self-attention-based LMs should outperform RNN-based models in utilizing long-term dependencies
- The LM-based model uses 64 self-attention layers (which yields 5x model paramters in comparison to RNNs)
- Auxiliary losses are added to the total lose to improve convergence and regularize the model:
	- Multiple positions - adding prediction task to each position in final layer (predict $t1$ from $t0$, $t2$ from $t1$, etc.)
	- Intermedial Layer losses - adding predictions from each position in all intermediate layers
	- Multiple targets - at each position predicting and and two future characters (predict $t1$ and $t2$ from $t0$, etc.)
	- Positional embeddings - add learned, per-layer positional embeddings that are added before each self-attention layer
- Auxiliary losses add parametrized prediction heads that are only used during training (smaller number of parameters during inference)
- Auxiliary losses are decayed (using a schedule) as training proceeds 
- No state is passed between predictions, computations must be done from scratch


#### Experiments
- Models with 12 and 64 layers, both outperform SOTA in perplexity, 64 layer version by a significant margin.
- Ablation study examined contribution of each auxiliary loss:
	- Predicting from multiple positions gives highest gains
	- Predicting from intermediate layer gives second highest gains
	- Predicting multiple targets gives insignificant gains
- Model is able to find long-term dependencies (>430 tokens apart)
- Model doesn't work well in word-level LM setting, significant gap between SOTA and Transformer


#### Other notes
- 64 layer version has 5x the number of paramters of regular RNN-based model
- 12 layer version has similar amount of paramters to regular RNN-based model
