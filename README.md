# Data x Model x Theory

A novel tool for exploring the interpretability of LLMs by comparing the LLM embeddings with linguistic frameworks.

The proposed algorithm is the following:

## Step 1: Extract LLM embeddings and construct the graph

**Input**: input sentence to be processed (str)

**Output**: graph representation of the embeddings

**Example usage**

```
embeddings = llm_model.get_embeddings(text)
llm_graph = Graph(embeddings)
```

[See the implementation..](https://github.com/vifirsanova/llm-dmt/blob/main/get_embeddings.ipynb)

## Step 2: Obtain BNF description of a linguistic framework

**Input**: linguistic_framework - object representing a linguistic framework

**Output**: bnf_description - BNF description of the framework

**Example usage**

```
bnf_description = linguistic_framework.get_bnf_description
```

[See the implemetation..](https://github.com/vifirsanova/llm-dmt/blob/main/get_rules.ipynb)

## Step 3: Convert BNF to graph representation

**Input**: bnf_description - BNF description of the linguistic framework from step 2

**Output**: bnf_graph - graph representation of the BNF description


**Example usage**

```
bnf_graph = Graph(bnf_description)
```

[See the implementation..](https://github.com/vifirsanova/llm-dmt/blob/main/get_graph.ipynb)

# Steps 4-5: Search for intersections between graphs and calculate similarity

**Input**: llm_graph - graph from embeddings, bnf_graph - graph from BNF

**Output**: intersections - list of matching nodes between the graphs

**Example usage**

```
if match_nodes(llm_graph, bnf_graph):
    intersections.append(llm_node.id, bnf_node.id)

node_ratio = intersections / (llm_graph.node_count, bnf_graph.node_count)
edge_ratio = intersections / (llm_graph.edge_count, bnf_graph.edge_count)

similarity_score = (node_ratio + edge_ratio) / 2
```

[See the implementation..](https://github.com/vifirsanova/llm-dmt/blob/main/get_scores.ipynb)
