**NeuMTrasTSparql (Translating Natural language To SPARQL Using Neural Network)**

The paper explores the use of SPARQL as a query language for Linked Data resources and Knowledge Graphs, highlighting the need for expertise in domain entities and language syntax and semantics. To bridge this knowledge gap for average or non-technical web users, develop a neural machine translation model that can convert natural language into SPARQL queries, allowing users to interact with RDF data in a more natural and intuitive way. Eight NMT models are evaluated, with emphasis placed on high-quality datasets for training. The results show a CNN-based architecture to be the most effective, achieving high BLEU scores of up to 98 and accuracy up to 94%. However, NMT models are utilized here since despite the success of deep learning methods in other natural language processing tasks, there has been limited exploration of their potential in the field of translating natural language to SPARQL queries. This paper helps to fill this gap by evaluating eight NMT models for the specific task of translating natural language to the structured query language SPARQL. Through this evaluation, the paper highlights the potential benefits of using deep learning techniques in this area and contributes to the growing body of research on natural language processing and SPARQL generation. Overall, this research provides insight into the challenges and potential solutions for translating natural language to SPARQL queries and demonstrates a promising approach using deep learning methods

**Referrenced Paper vs My Paper**

Title: Neural Machine Translating from Natural Language to SPARQL
Authors: Dr. Dagmar Gromann, Prof. Sebastian Rudolph and Xiaoyu Yin
My Name: Sumaia Aktar
My Paper: link
Institution: Brock University
Department: Computer Science
Course: 5P30 (Graph Data mining)
supervisor: Renata Queiroz Dividino

**Target of this work**

The result of the referrenced paper is partially reproduced here for the CONVS2S model to have a deeper understanding of the work proposed in this paper, discover existing issues and so as to utilize my knowledge in the future, targetting to develop more convenient system for user fixing these issues. At the same time, allowing myself enough time to configure my system to handle this massive project that requires high- configuration experimetal set up, as demostrated in the referenced paper that is not currently available and thus limit myself to test for all the models this time.
Results can be regenerated in two ways viz that to perform natural lanuage to SPARQL translation, we can follow two steps i.e:  
     1. clone this project and run specific file to see the expected translation
     
     2. clone this project and create a virtual environment to test translation with a web interface
These two steps are detailed in the following. However, the whole process can be divided into two module i.e dataset generation and training. During dataset generation the placeholder in manually crafted template-query pairs are replaced by corresponding entities and their english labels that is retrieved thorugh execution of an assistant SPARQL query on a DBpedia endpoint. For example,check the follwoing picture.
![image](https://user-images.githubusercontent.com/28555115/231785910-16127b33-31a6-4afb-8b37-b6c99b0f0d46.png)
given a template pair in Table 1, where <A> belongs to the class dbo:Monument in DBpedia, one can then retrieve a list of entities and their corresponding
English labels to replace <A> by executing an assistant SPARQL query on a DBpedia endpoint. An example is shown in Table 2. To be noted, The range of entities in this dataset is restricted to the instances of the specific class dbo:Monument, which is why we call it the Monument dataset.

**Downloads(Google drive)**
- Monument ([https://drive.google.com/drive/folders/1ibgd3pGtQZJ8lPTOCJ7vf6lzz2MxKa-0](url))
- Monument80
- Monument50
- LC-QUAD
- DBNQA
     
**Usages**
The files ended with *.en (e.g. dev.en, train.en, test.en) contain English sentences, *.sparql files contain SPARQL queries. The ones with the same prefix name have 1-1 mapping that was used in the training as a English-SPARQL pair. vocab.* or dict. are vocabulary files. fairseq has its own special requirement of input files, therefore aforementioned files were not used directly by it but processed into binary formats stored in /fairseq-data-bin folder of each dataset.

**Trained Models**
Because most of the models were so space-consuming (esp. GNMT4, GNMT8) after training for some sepecific datasets (esp. DBNQA), all the models could not be downloaded  from the HPC server. However, trained models are already shared as requested from author that can be downloaded from here [https://drive.google.com/drive/folders/1VuZrbFl3hgK-qWwGV_zI68qtZWKAKbTv]
     
**One More Thing**
This regeneration of work has been really helpful for me specially having a deeper understanding of the 
