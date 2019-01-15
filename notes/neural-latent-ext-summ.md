## Neural Latent Extractive Document Summarization
_Authors:_ Xingxing Zhang, Mirella Lapata, Furu Wei, Ming Zhou   
_Publishing Year:_ 2018   
_Link:_ https://arxiv.org/abs/1808.07187   

#### Summary
The authors propse a latent variable, neural extractive model for text summarization.
The extractive model has three modules - a sentence encoder, document encoder, and document decoder.
Treating this problem as a sequence classification problem, the last module predicts whether each sentence should be extracted into the summary.
The authors treat the outputs of the extractive model as a latent vector, thus there is no need for sentence-level target labels.
To provide training signal, a sentence-compression model is used to estimate the likelihood of each summary sentence given the chosen input sentence.
The model is trained using the REINFORCE algorithm, where the reward is a weighted sum of precision and recall scores based on the outputs from the compression model.


#### Key points
- Three module extractive model:
	- biLSTM sentence encoder, with averaging word-level hidden states
	- biLSTM document encoder, using embedded sentences
	- LSTM document decoder, per sentence binary classification
- Attention-based sentence-compression model:
	- Predict probability of (input sentence, summary sentence) pair
	- Generated training data by finding pairs that maximize ROUGE between input and summary sentences
- Instead of obtaining per sentence target labels using heuristics, treat prediction vector as latent variable
- Train extractive model using REINFORCE algorithm:
	- Single sample to estimate expected value
	- Reward from weighted _recall_ and _precision_ scores between extracted sentences and human written summary
	- Sentence-compression model to obtain _recall_ and _precision_ scores


#### Experiments
- Extractive model architecture outperforms baseline models in standard training procedure (with labels from a heuristic)
- Latent extractive model outperforms baselines and traditionally trained architecture
- Using sentence-compression model to paraphrase extracted sentences significantly drops overall performance


#### Other notes
- Still uses heuristic to find similar (input, summary) sentence pairs 
- Short paper
