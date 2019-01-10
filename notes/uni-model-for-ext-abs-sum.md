## A Unified Model for Extractive and Abstractive Summarization using Inconsistency Loss
_Authors:_ Wan-Ting Hsu, Chieh-Kai Lin, Ming-Ying Lee, Kerui Min, Jing Tang, Min Sun   
_Publishing Year:_ 2018   
_Link:_ https://arxiv.org/abs/1805.06266   

#### Summary
The authors propose a unified model for text summarization that combines abstractive and extractive summarization techniques.
The task is achieved using two models, an _extractor_ that analyzes the input article and returns a sentence-level attention, and an _abstractor_ that generates the summary using both sentence- and word-level attention.
The intuition is to use global, sentence-level attention to modulate word-level attention in each timestep.
In addition to the unified model, the authors also propose an inconsistency loss that is used to penalize the model for inconsitencies between the two levels of attention.


#### Key points
- Utilize both extractive and abstractive summarization:
	- Extractor - find salient parts of the input article, return sentence-level attention
	- Abstractor - generate summary using additional insight coming from extractor
- Independent pre-training phase:
	- Create supervised training set for extractor - pick most important sentences from input article as targets (using ROUGE-base heuristic) 
	- Train extractor as binary classifier using sigmoid cross-entropy loss using created data
	- Train abstractor using target data from extractor training
- Combined training phase:
	- Two-step - treats extractor output as hard-attention and filter out input sentences that fall below certain threshold (only abstractor fine-tuned)
	- End-to-end - treats extractor output as soft-attention and multiply it with word-level attention during decoding (both models fine-tuned)
- Inconsistency loss penalized models for inconsistent attention scores - word-level attention should be high when sentence-level is high


#### Experiments
- End-to-end fine-tuning phase achieves better performance than two-stage fine-tuning
- Inconsistency loss consistently improve performance of models


#### Other notes
- Try augmenting the hierarchical GRU extractor with self-attention modules?
- When doing human study add trap question that will allow to filter out biased answers
