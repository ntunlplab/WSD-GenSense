# GenSense: A Generalized Sense Retrofitting Model
# Introduction
With the aid of recently proposed word embedding algorithms, the study of semantic similarity has progressed and advanced rapidly. However, many natural language processing tasks need sense level representation. To address this issue, some researches propose sense embedding learning algorithms. In this paper, we present a generalized model from existing sense retrofitting model. The generalization takes three major components: semantic relations between the senses, the relation strengths and the semantic strengths. In the experiment, we show that the generalized model can outperform previous approaches in three types of experiment: semantic relatedness, contextual word similarity and semantic difference.

# Requirements
1. Python3
2. Numpy
# Data
#### 1. Word vector file
A file containing a pre-trained word vector model. In word vector model, each line has a word vector as follows : the -1.0 0.1 0.2

You can download pre-trained word vector in [Word2Vec](https://code.google.com/archive/p/word2vec/) or [GloVe](https://nlp.stanford.edu/projects/glove/).
#### 2. Lexicon file (provided in [lexicon](https://github.com/y95847frank/GenSense/tree/master/lexicon)/)
It's an ontology file that contains words and its' synonyms. Each line represents a word and all it's synonyms. The format is : <wordsense><weight> <neighbor-1><weight> <neighbor-2><weight> ...

[Thesaurus-API](https://github.com/Manwholikespie/thesaurus-api) is used for parsing the ontology.

#### 3. Word similarity evaluation dataset (provided in [eval_data](https://github.com/y95847frank/GenSense/tree/master/eval_data)/)
# Usage
#### 1. General usage
```
$ python all-joint_retrofit.py -i word_vec_file -s synonym_lexicon_file -a antonym_lexicon_file -n num_iter -o out_vec_file
$ python synonym-joint_retrofit.py -i word_vec_file -s synonym_lexicon_file -n num_iter -o out_vec_file
$ python antonym-joint_retrofit.py -i word_vec_file -a antonym_lexicon_file -n num_iter -o out_vec_file
```
-i : path of word vectors input file  
-s : path of synonym ontology file  
-a : path of antonym ontology file  
-n : number of iterations (default : n=5)  
-o : path of output file  
#### 2. Example
```  
$ python all-joint_retrofit.py -i glove.txt -s lexicon/synonym_ontology.txt -a lexicon/antonym_ontology.txt -n 5 -o out.txt
```
#### 3. Evaluation
```
$ python we_sensesim.py word_vec_file
```
This program will show the cosine similarity score of the word vector on each dataset. In eval_data/ directory, there are MEN, MTurk, RW, WS353 datasets. You can add more evaluation dataset to test your word vector on your own.

# Download
Please go to [resources page](http://nlg.csie.ntu.edu.tw/nlpresource/GenSense/) to access resources.
 
  
# How to cite this resource
Please cite the following [paper](http://aclweb.org/anthology/C18-1141) when referring to GenSense in academic publications and papers.

Yang-Yin Lee, Ting-Yu Yen, Hen-Hsen Huang, Yow-Ting Shiue, and Hsin-Hsi Chen. 2018. GenSense: A Generalized Sense Retrofitting Model. In Proceedings of the 27th International Conference on Computational Linguistics (COLING 2018), August 20-26, 2018, Santa Fe, New Mexico, USA.
