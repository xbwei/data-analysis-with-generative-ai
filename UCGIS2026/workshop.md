# UCGIS 2026 Workshop

## Advancing Social Media Analytics in Neo4j: Multimodal Embeddings and AI Agents with Knowledge Graphs

**Instructor**: Dr. Wei Xu ([LBSocial](https://www.lbsocial.net/))  
**Workshop Description**: [View on Sched](https://ucgissymposium2026.sched.com/event/2KN6D/advancing-social-media-analytics-in-neo4j-multimodal-embeddings-and-ai-agents-with-knowledge-graphs)

Welcome to the UCGIS 2026 Workshop! This hands-on tutorial will guide you through the process of integrating social media data with Neo4j Knowledge Graphs and leveraging Generative AI (Gemini) to build powerful analytical tools and AI agents.

---

### 📚 Prerequisite Tutorials
To get the most out of this workshop, we recommend reviewing these foundational tutorials:
1. [Neo4j Agent: Free No-Code GraphRAG](https://www.lbsocial.net/post/neo4j-agent-free-no-code-graphrag)
2. [Geo-GraphRAG Tutorial: Neo4j & Gemini](https://www.lbsocial.net/post/geo-graphrag-tutorial-neo4j-gemini)
3. [Neo4j Tutorial: Cypher, Generative AI & Dashboard](https://www.lbsocial.net/post/neo4j-tutorial-cypher-generative-ai-dashboard)
4. [Social Media Knowledge Graph: Python & Neo4j](https://www.lbsocial.net/post/social-media-knowledge-graph-python-neo4j)

---

### 🗺️ Step-by-Step Workshop Guide

#### Step 1: Set Up Your Free Neo4j Database
First, we need a graph database to store our social media data.
1. Go to [Neo4j Aura](https://neo4j.com/cloud/aura/) and sign up / log in.
2. ⚠️ **CRITICAL STEP**: Do **NOT** create the default trial instance (it is not free). 
3. When prompted, select **"Skip, I'll create an instance later"** or click on the **"Create a free instance"** button as shown below (No credit card required).

![Neo4j Free Instance Setup](neo4j_free_instance.png)
*(Note: Please remember to upload the `neo4j_free_instance.png` image to this UCGIS2026 folder on GitHub, otherwise the image link will be broken).*

#### Step 2: Obtain API Keys
We will use Google's Gemini for Generative AI capabilities.
1. Go to [Google AI Studio](https://aistudio.google.com/).
2. Sign in and generate your own **free Gemini API Key**.
3. Keep this key handy as we will need it in our Python code.

#### Step 3: Build the Knowledge Graph (Python ETL)
We will extract dummy tweets and ingest them into Neo4j as a knowledge graph.
1. Open the code notebook: [Social_Media_ETL_Neo4j_Python.ipynb](https://github.com/lbsocial/data-analysis-with-generative-ai/blob/main/Social_Media_ETL_Neo4j_Python.ipynb)
2. Run through the cells to connect to your Neo4j instance and process the dummy tweets.
3. This step will create nodes (e.g., Users, Tweets) and relationships (e.g., POSTED, MENTIONS) in your graph.

#### Step 4: Querying the Graph with AI
Now that our data is in Neo4j, let's explore it!
1. Open your Neo4j Workspace.
2. We will use the built-in **AI Query** feature to ask natural language questions about our graph data.
3. Observe how Neo4j translates your questions into Cypher queries automatically.

#### Step 5: Embeddings & GraphRAG
Next, we will implement Graph Retrieval-Augmented Generation (GraphRAG).
1. Open the second code notebook: [GraphRAG_Social_Media_Neo4j.ipynb](https://github.com/lbsocial/data-analysis-with-generative-ai/blob/main/GraphRAG_Social_Media_Neo4j.ipynb)
2. We will generate embeddings for our text data and store them in the graph.
3. Then, we will use Python to perform GraphRAG, combining the structural context of the graph with the generative power of Gemini.

#### Step 6: Create a Neo4j Graph Agent
Finally, let's build an autonomous AI agent that can navigate our graph!
1. Set up a free **Neo4j Graph Agent** within your environment.
2. 💡 **Important Tip**: The agent's performance relies heavily on its instructions. You will need to provide **specific prompts** detailing the graph schema and the types of questions it should answer.

---

### 📌 Additional Learning: Multimodal Embeddings
Please note that we will **not** be covering text-to-image or image embeddings in today's workshop. 
However, if you are interested in exploring multimodal AI, please check out this comprehensive guide:
- [Build a Multimodal Search Engine with Python](https://www.lbsocial.net/post/build-multimodal-search-engine-python)
