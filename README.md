# Thesis

### Resources
[Markdown language](https://medium.com/@saumya.ranjan/how-to-write-a-readme-md-file-markdown-file-20cb7cbcd6f ) \
[Lenz repo](https://github.com/ReCAP-UTR/Argument-Graph-Retrieval)

---
### Glossay
CA = computational argumentation \
CBR = case based reasoning \
IR = information retrieval \
AIF = Argument Interchange Format 

---

### Main concepts:
* [AIF](https://en.wikipedia.org/wiki/Argument_Interchange_Format) 
* Case Based reasoning (Data Mining notes 4, pag 2/3)
* MAC/FAC approach

---
### Tasks Idea:
The idea is to find a faster and (hopefully) equally capable alternative to a structural retrieval (i.e., creating a mapping between a query and a case).

1.  literature research for word/sentence embeddings that are either of high quality or fast to compute. \
[Transformers](https://towardsdatascience.com/transformers-89034557de14): 
    * [Repo](https://github.com/huggingface/transformers)
    * [Explenation](https://www.pinecone.io/learn/sentence-embeddings/)
    * [Sentence-transformers](https://github.com/UKPLab/sentence-transformers):


    Sentence embeddings repos:
    * https://separius.github.io/awesome-sentence-embedding/
    * https://www.sbert.net/docs/pretrained_models.html
        1. fast:
            * Smooth Inverse Frequency [SIF](https://towardsdatascience.com/fse-2b1ffa791cf9)
            * [mini-mpnet](https://huggingface.co/sentence-transformers/all-MiniLM-L6-v2)
            * [Fast sentence embeddings](https://github.com/oborchers/Fast_Sentence_Embeddings)(Gensim)
            * Elmo would allow easier transiction to sms
        2. precise:
            * [all-mpnet](https://huggingface.co/sentence-transformers/all-mpnet-base-v2)

2. literature research for similarity methods that can be applied to these embeddings (apart from the cosine similarity). [Comparison](http://nlp.town/blog/sentence-similarity/).\
Candidates:
    * [Sentence Mover's similarity](https://homes.cs.washington.edu/~nasmith/papers/clark+celikyilmaz+smith.acl19.pdf) \
    [Paper](https://homes.cs.washington.edu/~nasmith/papers/clark+celikyilmaz+smith.acl19.pdf)\
    [Code](https://github.com/eaclark07/sms) -> needs adaption to be used (only Elmo and glove available):
        * [Word Mover’s Distance for Text Similarity](https://www.datastunt.com/post/word-mover-s-distance-for-text-similarity):
            * [Paper](http://www.cs.cornell.edu/~kilian/papers/wmd_metric.pdf)
    * [17 types of similarity and dissimilarity measures used in data science.](https://towardsdatascience.com/17-types-of-similarity-and-dissimilarity-measures-used-in-data-science-3eb914d2681)
3. research graph-to-text generation to create a purely text-based representation of the argument graphs
    * GPT-3
4. perform a retrieval using the three techniques mentioned above

---


### Notes:
An **argument graph** is composed by many nodes. \
Each node can be either an **I-node** or an **S-node**. I-nodes contain claims and premisis, whereas S-nodes connect premises to claims. \
Each **arg. graph** is a tuple 
```
G =  (N, E, tao, lambda, t) 

N = set of nodes
E = set of edges
tao = function assignin a node type (I-node or S-node)
lambda = textual content + tentual embedding
t = concateneted textual content of all I-nodes and their vector representation
```
Given our data we create a case-base. In the case-base argument graphs are stored. \
Whenever we perform a query a **MAC/FAC** approach is used:
1. The MAC phase applies a filter to the entire case-base -> fast filer with many possibly wrong results.
2. In the FAC phase a more precise (and slower) approach is performed.

---

### Quality measures
* Presicion (P) 
* Avg Precision (AP) 
* Normilized Discounted Cumulative Gain (NDCG): assesses that elements with high relevance appear at the beginning 
* Completeness (CP): measures the % of pairs of the reference ranking that are included in the produced ranking (the pair I think is (appear, rank_coincide)) 
* Correctness (CR): measures concordance/discordance of the ordering of those pairs 

---

### Questions
My understanding of the task is:
* ingest data creating the graph structure
* data does not contain embeddings -> "enrich" the arg graph with the "new varialbe(s)" "embedding" 
* research on possible similarity measures (given the results from Lenz)
* use the A* alg to find the best document to retrieve given the previously defined sim measure
* quality assessment
1. Are the data in the form of IFA graphs? Or do I have to create graphs from text? 
2. g2t: we want to create a text out of a single argument graph?
3. the word mover's distance requires word embeddings -> 


