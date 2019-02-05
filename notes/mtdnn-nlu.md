## Multi-Task Deep Neural Networks for Natural Language Understanding
_Authors:_ Xiaodong Liu, Pengcheng He, Weizhu Chen, Jianfeng Gao   
_Publishing Year:_ 2019  
_Link:_ http://arxiv.org/abs/1901.11504    

#### Summary
The authors propose an architecture for learning representation across multiple NLU tasks.
The Multi-task Deep Neural Network (MT-DNN) builds on top of the BERT architecture.
The primarily contribution, is replacing the single-task fine-tuning step used by BERT, with a multi-task fine-tuning procedure.
In the multi-task setting, the BERT architecture is shared across tasks, and light architectures are used per task group, with 4 groups in total.
The model outperforms outher representation learning architecture when measured on downstream tasks, and allows significantly faster domain adaptation at a fraction of the necessary data.


#### Key points
- Combines strenghts of LM pre-training with multi-task training for NLU tasks
- BERT used to build context-aware token representations with light, task-specific layers on top 
- Model trained in two phases:
	- Pre-training as language model, using Masked LM training and next sentence prediction
	- Fine-tune in multi-task setting with 9 auxiliary tasks from the GLUE benchmark
	- Auxiliary tasks group by output type: single sentence classification, text similarity, pairwise text classification, and sentence ranking.
- Multiple tasks work as a regularizer for the model, allowing it to achieve better generalizability
- Model converges much fast in comparison to regular BERT in case of domain adaptation
- MT-DNN uses BERT_LARGE for its initial layers


#### Experiments
- Scores on GLUE benchmark significantly outperform earlier models
- Domain adaptation requires much less samples, with very good results with as little as 500 samples


#### Other notes
- Big Bird paper
