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
<!-- ### Bergmann paper
Create a case base containing graphs and then use it. Retrieve relevant text using graph similarity -->

---
### Tasks Idea:
The idea is to find a faster and (hopefully) equally capable alternative to a structural retrieval (i.e., creating a mapping between a query and a case).

1.  literature research for word/sentence embeddings that are either of high quality or fast to compute. [Sentence embeddings repo](https://separius.github.io/awesome-sentence-embedding/).
2. literature research for similarity methods that can be applied to these embeddings (apart from the cosine similarity)
3. research graph-to-text generation to create a purely text-based representation of the argument graphs
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


