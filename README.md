# Knowledge-graphs
Research project exploring the use of LLMs and TaskLang to generate knowledge graphs in Neo4j from recipe data.

# Recipe Knowledge Graph with LLMs and TaskLang

This project explores the use of Large Language Models (LLMs) to extract structured data from recipes and construct knowledge graphs using Neo4j.

## 🎯 Objectives
- Investigate prompt engineering strategies for generating RDF.
- Evaluate the consistency and quality of knowledge graphs with and without TaskLang.
- Test reverse generation: producing recipes from RDF graphs.

## 📁 Structure
- **`AIs evaluation/`**  
  Contains the graphs and images generated by each LLM (**ChatGPT**, **Claude**, **Mistral**, and **Perplexity**) during the evaluation phase that compared how each model interpreted the same recipe.
- **`Tasklang evaluation/`**  
  Includes both versions of the **TaskLang prompt** used in the project. You’ll also find the RDF scripts generated *with* and *without* TaskLang.  
  > 📌 The `claude/` subfolder contains all test outputs from **Claude** after it was chosen as the main LLM. It includes RDF scripts and corresponding graph screenshots — note that this folder is somewhat unorganized, as it reflects the iterative testing process.
- **`graphs print/`**  
  Visual representations (images) of the knowledge graphs created and exported from **Neo4j**.
- **`recipes used/`**  
  Text files of all the recipes used throughout the project.
- **`ttl scripts/`**  
  Turtle (`.ttl`) RDF scripts used to generate the graphs shown in `graphs print/`.
- **`25-Ingredients-50-Meals-Print-Friendly-Final-1.pdf`**  
  The source book of recipes used for the project.
- **`Cypher_Queries.txt`**  
  A set of **Cypher** queries used to initialize and manipulate the graphs within Neo4j.

## 🛠 Tools Used
- Neo4j (for graph creation and visualization)
- OpenAI ChatGPT, Claude, Mistral, Perplexity (for generation)
- TaskLang (prompt templating language)

