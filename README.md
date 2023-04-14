**NeuMTrasTSparql (Translating Natural language To SPARQL Using Neural Network)**

The paper explores the use of SPARQL as a query language for Linked Data resources and Knowledge Graphs, highlighting the need for expertise in domain entities and language syntax and semantics. To bridge this knowledge gap for average or non-technical web users, develop a neural machine translation model that can convert natural language into SPARQL queries, allowing users to interact with RDF data in a more natural and intuitive way. Eight NMT models are evaluated, with emphasis placed on high-quality datasets for training. The results show a CNN-based architecture to be the most effective, achieving high BLEU scores of up to 98 and accuracy up to 94%. However, NMT models are utilized here since despite the success of deep learning methods in other natural language processing tasks, there has been limited exploration of their potential in the field of translating natural language to SPARQL queries. This paper helps to fill this gap by evaluating eight NMT models for the specific task of translating natural language to the structured query language SPARQL. Through this evaluation, the paper highlights the potential benefits of using deep learning techniques in this area and contributes to the growing body of research on natural language processing and SPARQL generation. Overall, this research provides insight into the challenges and potential solutions for translating natural language to SPARQL queries and demonstrates a promising approach using deep learning methods.

**Referrenced Paper vs My Paper**

Title: Neural Machine Translating from Natural Language to SPARQL <br>
Authors: Dr. Dagmar Gromann, Prof. Sebastian Rudolph and Xiaoyu Yin<br>
My Name: Sumaia Aktar<br>
My Paper: would be attached after completion <br>
Institution: Brock University<br>
Department: Computer Science<br>
Course: 5P30 (Graph Data mining)<br>
My Supervisor: Renata Queiroz Dividino<br>

**Target of this work** <br>
  
  **Natural language question :** What is the common area of expertise of Sam Loyd and Eric Schiller? (as represented by their "knownFor" properties in DBpedia?)<br>

   **Correspondig SPARQL :** ![image](https://user-images.githubusercontent.com/28555115/231902643-606d4a0e-b4bb-47d7-8e47-edbe76d7deea.png) <br>

As it can be seen in the picture above, there's a natural language question and its corresponding SPARQL translation which is actually the target of our work. The encoded form of SPARQL is also shown to get familiar with the formalities of encoding. To understand the necessity of encoding, please see the 'SPARQL encoding' section in the paper. However, to sum up, the result of the referrenced paper is partially reproduced here for the CONVS2S model to have a deeper understanding of the work proposed in this paper, discover existing issues and so as to utilize my knowledge in the future, targetting to develop more convenient system for user fixing these issues. At the same time, allowing myself enough time to configure my system to handle this massive project that requires high- configuration experimetal set up, as demostrated in the referenced paper that is not currently available and thus limit myself to test for all the models this time.
Results can be regenerated in two ways viz that to perform natural lanuage to SPARQL translation, we can follow two steps i.e:  

     1. clone this project and run specific file to see the expected translation (self machine/environment)
     2. clone this project and create a virtual environment to test translation with a web interface (vritual environment)
     
These two steps are detailed in the following.However, the whole process can be divided into two module i.e dataset generation and training. During dataset generation the placeholder in manually crafted template-query pairs are replaced by corresponding entities and their english labels that is retrieved thorugh execution of an assistant SPARQL query on a DBpedia endpoint. For example,check the following picture.
![image](https://user-images.githubusercontent.com/28555115/231785910-16127b33-31a6-4afb-8b37-b6c99b0f0d46.png). 

Given a template pair in Table 1, where <A> belongs to the class dbo:Monument in DBpedia, one can then retrieve a list of entities and their corresponding
English labels to replace <A> by executing an assistant SPARQL query on a DBpedia endpoint. An example is shown in Table 2. To be noted, The range of entities in this dataset is restricted to the instances of the specific class dbo:Monument, which is why we call it the Monument dataset.

**1. Translation in self machine** <br>
**Experimental set up of my machine**  
- CPU @ 2.30GHZ
- 8GB RAM
- conda 23.3.1
- Python 3.9.13
- torch 1.13.1 <br>
Project needs all these libraries to be installed as prerequisites. Aprt from this, in case of any error during the execution of any code blocks regarding installation, just try installing the libraries as suggested by the error dialog, following under conda environment and it should work! For myself it worked that way and should not be that much tough! isn't it? lets give a try!
     
For manual dataset generation and training, please follow this file here: https://github.com/SumaiaBristy/NeuMTrasTSparql/blob/main/kmst.py [**kmst.py**]. For each of the method there is documentation along with it regarding how it works so that it would be easier for user to understand how all the module like preprocessing, encoding,decoding, attention mechanism, training, evaluation works and reasons behind writing this way. Aftr going through this file, the first and formeost step is to prepare dataset for training and evaluation. You can check the available following datasets shared by author through their drive in the 'datasets' paragraph here. However, for the convenience of training, I have gathered the available *.en and *.sparql files(those are 1-1 mapped that can be checked from the given drive link here) to one file  named monument.csv that can be retrieved by unzipping this file 'https://github.com/SumaiaBristy/NeuMTrasTSparql/blob/main/monument_300.zip'[monument_300.zip]. After that, this csv file will input the templates (english question, SPARQL pairs) as shown above in table:1 to 'generate.py' [https://github.com/SumaiaBristy/NeuMTrasTSparql/blob/main/generator.py] and output will be split to 3 files (train.txt,test.txt and dev.txt) with an updated template pairs containing the English Sentence and corresponding SPARQL where the placeholders are replaced as per the aforemenioned method like this <br>
![image](https://user-images.githubusercontent.com/28555115/231900050-6117ba66-d55e-4db7-acf9-e34d58099351.png) <br>
Lastly, you are ready for your first training! For the training and evaluation use this file 'https://github.com/SumaiaBristy/NeuMTrasTSparql/blob/main/encode-decode-train.ipynb' [encode-decode-train.ipynb] that can be run for so many epocs with the dataset taken as input after the dataset generation and split as shown above. I ran it for 1000 epocs that output like the following <br>
![image](https://user-images.githubusercontent.com/28555115/231887893-bdbba436-f841-4021-9942-df14703b5df7.png) <br>
     
As it can be seen in the picture, it ended up with perplexity score at maximum of 1.1311% for the monument300 dataset and Seq2Seq model and took approximately 4 hours as myself having a 8GB RAM only!


**2. Translation creating virtual Environment using an web interface**

To translate a natural language question to SPARQL query with an interactive web based interface, one need to follow the following steps:-<br>
  
**Installation guide for spacey**
- pip install -U spacey 
- python -m venv .env
- source .env/bin/activate (linux)
- .\venv\Scripts\activate (windows)
- pip install spacey
  
**Installation guide for flask** <br>
- mkdir myproject
- cd myproject
- python3 -m venv venv
- .\venv\Scripts\activate (windows)
- source .env/bin/activate (linux)
- pip install Flask
  
**Data preparation**<br>
To generate the training data, execute the following commands
- mkdir data/monument_300
- python generator.py --templates data/annotations_monument.csv  --output data/monument_300

**Training**
Now go back to the initial directory and launch train.sh to train the model. The first parameter is the prefix of the data directory and the second parameter is the number of training epochs.The following command will create a model directory called data/monument_300_model and would take nearly 4 hours for 20 epochs.
- sh train.sh data/monument_300 20

**Inference**
Predict the SPARQL sentence for a given question with a given model. In this, we wil run back.py. After that go to http://localhost:5000/result on any web browser. This has front end. Enter your query and sparql sentence will be generated in next page.

**Execution of the application**
- Run back.py and then go to http://localhost:5000/ . <br>
After implementing all these steps in my machine i have come up with th following results:- <br>
input: <br>
![image](https://user-images.githubusercontent.com/28555115/231916241-e6ff3e59-f258-43af-94f4-a5a6f582af89.png)<br>
 output:  <br>
![image](https://user-images.githubusercontent.com/28555115/231916196-cb442170-72f3-4368-b70c-af1831af941a.png)<br>
![image](https://user-images.githubusercontent.com/28555115/231916323-7d18fdba-83e6-42b1-b921-ad8e3fde488a.png)<br>
![image](https://user-images.githubusercontent.com/28555115/231916414-b72af6dd-377b-445f-b9ae-82e31570e06b.png)<br>
  
**Datasets(Google drive)**
- Monument (https://drive.google.com/drive/folders/1ibgd3pGtQZJ8lPTOCJ7vf6lzz2MxKa-0)
- Monument80 (https://drive.google.com/drive/folders/18QF3avTHU8rD9C-hWAnD56QlP4yxhKDy)
- Monument50(https://drive.google.com/drive/folders/1C-vFYKpEvxCN06bjUvrqZBUb7hXeM145)
- LC-QUAD (https://drive.google.com/drive/folders/1LGk7a5aRKFQXWVsrdISz3jzzRD5TcdWb)
- DBNQA (https://drive.google.com/drive/folders/1sSiwVn7aBUezYvM4u226zzq5MqhbaxIw)
     
**Usages**
The files ended with *.en (e.g. dev.en, train.en, test.en) contain English sentences, *.sparql files contain SPARQL queries. The ones with the same prefix name have 1-1 mapping that was used in the training as a English-SPARQL pair. vocab.* or dict. are vocabulary files.

**Trained Models**
Because most of the models were so space-consuming (esp. GNMT4, GNMT8) after training for some sepecific datasets (esp. DBNQA), all the models could not be downloaded  from the HPC server. However, trained models are already shared as requested from author that can be downloaded from here [https://drive.google.com/drive/folders/1VuZrbFl3hgK-qWwGV_zI68qtZWKAKbTv]
     
**One More Thing**
This regeneration of work has been really helpful for me having a deeper understanding of the neural models and all the three architectures as mentioned in the paper. I had to face challenges regarding machine configuration and differnet package installation that in turn helped to find out so many things and hence enrich my knowledge that migh surely help me to research more in the related filed. Special thanks to my course supervisor Renata Queiroz Dividino. I found her so cordial and cooperative always that motivated me to give my best to work on this project. 
