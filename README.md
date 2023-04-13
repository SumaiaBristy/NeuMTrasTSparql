#NeuMTrasTSparql (Translating Natural language To SPARQL Using Neural Network)
The paper explores the use of SPARQL as a query language for Linked Data resources and Knowledge Graphs, highlighting the need for expertise in domain entities and language syntax and semantics. To bridge this knowledge gap for average or non-technical web users, develop a neural machine translation model that can convert natural language into SPARQL queries, allowing users to interact with RDF data in a more natural and intuitive way. Eight NMT models are evaluated, with emphasis placed on high-quality datasets for training. The results show a CNN-based architecture to be the most effective, achieving high BLEU scores of up to 98 and accuracy up to 94%. However, NMT models are utilized here since despite the success of deep learning methods in other natural language processing tasks, there has been limited exploration of their potential in the field of translating natural language to SPARQL queries. This paper helps to fill this gap by evaluating eight NMT models for the specific task of translating natural language to the structured query language SPARQL. Through this evaluation, the paper highlights the potential benefits of using deep learning techniques in this area and contributes to the growing body of research on natural language processing and SPARQL generation. Overall, this research provides insight into the challenges and potential solutions for translating natural language to SPARQL queries and demonstrates a promising approach using deep learning methods

Referrenced Paper
Title: Neural Machine Translating from Natural Language to SPARQL
Authors: Dr. Dagmar Gromann, Prof. Sebastian Rudolph and Xiaoyu Yin
my paper: link
Course: 5P30 (Graph Data mining)
supervisor: Renata Queiroz Dividino

#The result of the referrenced paper is partially reproduced here for the CONVS2S model to have a deeper understanding of the work proposed in this paper, discover existing issues and so as to utilize my knowledge in the future, targetting to develop more convenient system for user fixing these issues. At the same time, allowing myself enough time to configure my system to handle this massive project that requires high- configuration experimetal set up, as demostrated in the referenced paper that is not currently available and thus limit myself to test for all the models this time.

# The results can be reporduced in two ways viz that to perform natural lanuage to SPARQL translation, we can follow two steps:- 
     1. clone this project and run specific file to see the expected translation
     2. clone this project and create a virtual environment to test translation with a web interface
These two steps are detailed in the following. However, the whole process can be divided into two module i.e dataset generation and training. During dataset generation the placeholder in manually crafted template-query pairs are replaced by corresponding entities and their english labels that is retrieved thorugh execution of an assistant SPARQL query on a DBpedia endpoint. For example,check the follwoing picture.
![image](https://user-images.githubusercontent.com/28555115/231785910-16127b33-31a6-4afb-8b37-b6c99b0f0d46.png)
given a template pair in Table 1, where <A> belongs to the class dbo:Monument in DBpedia, one can then retrieve a list of entities and their corresponding
English labels to replace <A> by executing an assistant SPARQL query on a DBpedia endpoint. An example is shown in Table 2. To be noted, The range of entities in this dataset is restricted to the instances of the specific class dbo:Monument, which is why we call it the Monument dataset.

PDF is available

@article{DBLP:journals/corr/abs-1906-09302,
  author    = {Xiaoyu Yin and
               Dagmar Gromann and
               Sebastian Rudolph},
  title     = {Neural Machine Translating from Natural Language to {SPARQL}},
  journal   = {CoRR},
  volume    = {abs/1906.09302},
  year      = {2019},
  url       = {http://arxiv.org/abs/1906.09302},
  archivePrefix = {arXiv},
  eprint    = {1906.09302},
  timestamp = {Thu, 27 Jun 2019 18:54:51 +0200},
  biburl    = {https://dblp.org/rec/journals/corr/abs-1906-09302.bib},
  bibsource = {dblp computer science bibliography, https://dblp.org}
}

Datasets
Downloads (Google drive)
Monument
Monument80
Monument50
LC-QUAD
DBNQA
Usages
The files ended with *.en (e.g. dev.en, train.en, test.en) contain English sentences, *.sparql files contain SPARQL queries. The ones with the same prefix name have 1-1 mapping that was used in the training as a English-SPARQL pair. vocab.* or dict. are vocabulary files. fairseq has its own special requirement of input files, therefore aforementioned files were not used directly by it but processed into binary formats stored in /fairseq-data-bin folder of each dataset.

Sources
The datasets used in this paper were originally downloaded from Internet. I downloaded them and have split them into the way I needed to train the models. The sources are listed as follows:

Neural SPARQL Machines Monument dataset
LC-QUAD (v2.0 is released! but we used 1.0)
DBpedia Neural Question Answering (DBNQA) dataset
Experimental Setup
Dataset splits and hyperparameters
see in paper

Hardware configuration
hardware

Results
Raw data
We kept the inference translations of each model and dataset which was used to generate BLEU scores, accuracy, and corresponding graphs in below sections. The results are saved in the format of dev_output.txt (validation set) & test_output.txt (test set) version and available here (compat version).

Full version containing raw output of frameworks is also available

Training
Plots of training perplexity for each models and datasets are available in a separate PDF here.

Test results
Table of BLEU scores for all models and validation and test sets Bleu scores

Table of Accuracy (in %) of syntactically correct generated SPARQL queries | F1 score accuracy

Please find more results and detailed explanations in the research paper and the thesis.

Trained Models
Because some models were so space-consuming (esp. GNMT4, GNMT8) after training for some sepecific datasets (esp. DBNQA), I didn't download all the models from the HPC server. This is an overview of the availablity of the trained models on my drive:

.	Monument	Monument80	Monument50	LC-QUAD	DBNQA
NSpM	yes	yes	yes	yes	yes
NSpM+Att1	yes	yes	yes	yes	yes
NSpM+Att2	yes	yes	yes	yes	yes
GNMT4	no	yes	no	no	no
GNMT8	no	no	no	no	no
LSTM_Luong	yes	yes	yes	yes	no
ConvS2S	yes	yes	yes	yes	no
Transformer	yes	yes	yes	yes	no
One More Thing
This paper and thesis couldn't have been completed without the help of my supervisors (Dr. Dagmar Gromann, Dr. Dmitrij Schlesinger and Prof. Sebastian Rudolph) and those great open source projects. I send my sincere appreciation to all of the people who have been working on this subject, and hopefully we will show the world its value in the near future.

Neural SPARQL Machines
LC-QUAD
DBNQA
fairseq
nmt
