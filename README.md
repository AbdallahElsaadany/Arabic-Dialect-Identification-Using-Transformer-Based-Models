# Arabic-Dialect-Identification-Using-Transformer-Based-Models

The identification of Arabic dialects using deep learning models is a rapidly evolving field in computational linguistics, driven by the increasing digital communication in the Arab world. Arabic dialect identification is crucial due to the significant linguistic variations between dialects and Modern Standard Arabic (MSA). MSA, the formal language of media and education across the Arab world, differs considerably from colloquial dialects in terms of syntax, vocabulary, and pronunciation. These dialects, which are often region-specific, are prevalent in everyday communication and social media, presenting a unique challenge for natural language processing systems. In this paper, we compare 5 different transformer-based models on a specific Arabic dialect corpus and analyze the results of each of them.

### 1-Data Pre-Processing and Analysis
We used the https://huggingface.co/datasets/Abdelrahman-Rezk/Arabic_Dialect_Identification dataset, which comprises texts and their
corresponding dialects, specifically 18 different country-level dialects as shown in the figure below.

![diall](https://github.com/y0usefadel/Arabic-Dialect-Identification-Using-Transformer-Based-Models/assets/67977986/40578a40-f08b-464e-9535-7e7c8d808de2)

To minimize data redundancy, we eliminated duplicate entries. A standardization technique was employed, transforming all instances of \<ي> to \<ى> among other modifications, and we also removed punctuation as well as the hashtags "@" and similar redundant characters. Most importantly, stop-word removal was applied to remove the redundancy of each text record. This preprocessing was applied across the entire dataset, including training, validation, and testing phases. Additionally, we converted labels like "EG" into numerical representations, such as "3," to enhance model prediction accuracy. Moreover, due to the high number of classes, we grouped certain dialects into the same class. The data exhibited class imbalance, as depicted in the figure. We handled the imbalance in the corpus by taking the minimum number of class instances and reducing the number of other class instances to the number of the minimum class instances. Also, we took a sample of only 55\% due to computation and time limitations. As shown in Table below, the dialects transformed from 18 classes to 5 labels based on the vocabulary similarity, to minimize the number of distinct classes and make it easier for the model to predict.

![image](https://github.com/y0usefadel/Arabic-Dialect-Identification-Using-Transformer-Based-Models/assets/67977986/08af9251-95cb-498f-bb22-9a2e45396373)

### 2-Transformer-Based Models
We experimented with various transformer-based models on this corpus to evaluate and compare their performance.

The first model, "MARBERTv2," is an extensive pre-trained masked language model tailored for both Dialectal Arabic (DA) and MSA. It underwent training on a random sample of 1 billion Arabic tweets from a larger dataset containing approximately 6 billion tweets. The architecture of "MARBERTv2" mirrors that of BERT-base, with 12 attention layers, each featuring 12 attention heads and 768 hidden dimensions. It includes a vocabulary of 100,000 WordPieces and comprises roughly 163 million parameters. The maximum text length processed by its tokenizer is 60.

The second model we utilized is "AraBERTv2," an Arabic pre-trained language model developed based on Google's BERT architecture. This model adheres to the BERT-Base configuration, maintaining consistency with the first model in terms of model and tokenizer hyperparameters. This alignment in configuration underscores the systematic approach employed in our comparative analysis of different language models.

The third model in our study is termed "Multi-Dialect-Bert-Base-Arabic." This model commenced with the foundational weights of "Arabic-BERT" and underwent subsequent fine-tuning using a corpus of 10 million Arabic tweets. These tweets were sourced from the unlabeled data segment of the Nuanced Arabic Dialect Identification (NADI) shared task, offering a robust foundation for dialect analysis and model enhancement.

The fourth model utilized in our research is "bert-base-arabic-camelbert-mix," a BERT-based model specifically pre-trained on a diverse array of Arabic texts. This model encompasses a blend of both dialectal Arabic and Modern Standard Arabic (MSA), enabling it to effectively process and understand a wide range of textual sizes and variants within the Arabic language spectrum.

The concluding model in our analysis is designated as "AraBERTv02-base-twitter." This model, tailored for Arabic dialects and tweets, underwent an extended pre-training phase using the Masked Language Model (MLM) task on approximately 60 million Arabic tweets, which were selectively curated from a larger pool of 100 million tweets. "AraBERTv02-base-twitter" adheres to the standard BERT-Base architecture and configurations, demonstrating its alignment with established deep learning frameworks for language processing.

### 3-Results and Discussion
The experiment was done for this study on Kaggle online free computational resources (GPU T4 x2) and applied few-shot learning for five epochs only for each model due to time and computational constraints. The following following table illustrates the results of the five different models, including training/validation loss of the last training epoch, the accuracy score,  precision score, recall score, and F1 score on the held-out-set to fairly evaluate the model's performance on the dataset. We used multiple classification metrics to accurately evaluate the model's performance on the given dataset.

![image](https://github.com/y0usefadel/Arabic-Dialect-Identification-Using-Transformer-Based-Models/assets/67977986/84a92804-d5c1-4c21-bf9a-2d78481d0a12)

As shown in the Table above, the five models achieved similar results. However, MARBERTv2 model achieved slightly better results than its competitors. This could be justified because this model is mainly pre-trained on numerous Arabic tweets which contain various types of dialects with the existence of the MSA. So, the model performed better due to the similarity between the data pre-trained on and the data applied few-shot learning on.

##### NOTE: There is no ethical conflict in our Experiments.
