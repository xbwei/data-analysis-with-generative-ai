# UCGIS 2025 Workshop: Advancing Social Media Analytics with AI

**Instructor:** Xuebin Wei  
**Associate Professor, School of Integrated Science, James Madison University**  
**Email:** weixx@jmu.edu  
**Website:** www.lbsocial.net  
**Textbook:** [Social Data Analytics in the Cloud with AI](https://www.taylorfrancis.com/books/mono/10.1201/9781003437611/social-data-analytics-cloud-ai-xuebin-wei-xinyue-ye)  
**Demo Code:** https://github.com/xbwei/data-analysis-with-generative-ai  

---

## Introduction

This hands-on workshop explores AI-powered social media analytics, focusing on Twitter (X) data collection, analysis, and visualization. Participants will learn to use MongoDB for scalable storage, generative AI for text and image processing, and retrieval-augmented generation (RAG) for enhanced data insights. These techniques are critical for researchers and professionals working in fields such as public sentiment analysis, misinformation detection, disaster response, and urban studies.

---

## Set Up Cloud Resources

### Twitter Free API

Twitter recently updated its policy to allow the free Twitter API to collect 100 Tweets per month.

1. Register for a Twitter account at https://x.com if you don’t already have one.
2. Apply for a FREE Twitter developer account at https://developer.x.com/en using your Twitter account.
3. A short video demo is available here: https://www.youtube.com/shorts/GBmR_bnqrOs.
4. Log in to your Twitter developer account. Under **Projects & Apps**, you will find your default app.
5. Click **Keys and tokens**, and generate a **Bearer Token**.
6. Copy the Bearer Token and save it to your local computer, such as a text file.

> If you can’t create a Twitter API, you can use the provided demo Tweet data.

---

### MongoDB Cluster

MongoDB is the most popular NoSQL database and offers a free M0 cluster in its Atlas service.

1. You should have received an invitation from MongoDB. Please accept the invitation and register your account at https://www.mongodb.com.
2. Once you log in, create a new project. You can name your project with your name. Each participant has complete control over their project.
3. In your project, create a cluster — a group of database instances. You can create only one free cluster per project.
4. On the next page, create a database user. This user is different from your MongoDB account and is used in Python to access your database.

> While it is not the best practice, to simplify the workshop, let’s all use the same username and password:  
> Username: `demo`  
> Password: `UCGIS2025`

5. While the cluster is being created, change the network access settings:
    - Under **Security**, click **Network Access**, then click **Edit**.
    - Best practice is to restrict access by IP address, but for the workshop, allow access from anywhere.

6. Locate the MongoDB connection string:
    - Go to **Clusters** > **Connect**.
    - Choose **Drivers/Python**, copy the connection string, and save it locally.

7. To easily manage and query the data, download and install **MongoDB Compass**:
    - Visit https://www.mongodb.com/try/download/compass.
    - Download the version for your operating system.
    - Start Compass, add a new connection, and paste in your connection string.
    - Make sure you change the password to `UCGIS2025`.

8. You should now be able to see your cluster on the left side of the Compass interface.

---

### AWS Academy Lab

AWS Academy offers free credits to students using AWS services including coding, machine learning, AI, storage, and other cloud computing tasks.

1. You should have received an invitation to an AWS Academy Learner Lab.
2. Accept the invitation and set your password.
3. Once your account is created, log in at https://awsacademy.instructure.com/login/canvas.
4. After logging in, open **Modules** and click **Launch AWS Academy Learner Lab**.
5. For first-time users, you’ll need to accept the terms. Click **Start Lab** and wait until your lab environment is ready.

> When the AWS dot becomes green, click the AWS link to open the AWS console.

---

### Store Credentials in AWS Secrets Manager

We will use **AWS Secrets Manager** to securely store credentials for use in the SageMaker notebooks.

1. In the AWS Console, search for and open **Secrets Manager**.
2. Choose **Store a new secret**.
3. Choose **Other type of secret**, then enter the key-value pair for your Twitter API:

    - Key: `bearer_token`  
      Value: your bearer token  
      Secret name: `twitter_api`

4. Accept all other default settings and store the secret.

Repeat the above process for your MongoDB and OpenAI credentials:

- **MongoDB**  
  - Key: `connection_string`  
  - Value: your connection string (make sure to replace the password)  
  - Secret name: `mongodb`

- **OpenAI**  
  - Key: `api_key`  
  - Value: your OpenAI API key (from email)  
  - Secret name: `openai`

---

### Set Up Jupyter Notebook on SageMaker

1. In the AWS Console, search for **Amazon SageMaker** and open it.
2. Click **Notebooks**, then choose **Create notebook instance**.
3. Provide a notebook instance name.
4. Under **Git repositories**, choose to clone a public Git repository.
5. Use the following GitHub repository URL:  
   `https://github.com/xbwei/data-analysis-with-generative-ai.git`
6. Leave all other settings at their default values and click **Create instance**.

> It may take 1–2 minutes for the notebook instance to become ready. We can take a short break now. Feel free to ask the instructor if you have questions.

---
## Collect Twitter Data

Once your Jupyter notebook instance is ready and running, you can begin collecting real Twitter data.

1. Open **JupyterLab** from your SageMaker instance.
2. Navigate to the notebook file named `Collect_Twitter_Data.ipynb`.
3. Open the notebook. Select the first cell, and press **Shift + Enter** to execute it.
4. Continue executing all cells from top to bottom one by one.

> The notebook is designed to use the Twitter API to collect up to **100 tweets**, which is the current limit for the free tier.

### Customize the Query

- In the cell that defines the data collection query, you will see a `query` string.
- You may modify the keyword in the query to reflect your own research interests or any current topic.
- For example, instead of `"generative AI"`, you might use `"climate change"` or `"cybersecurity"`.

```python
query = "generative AI"
```

> You can change `"generative AI"` to any keyword or hashtag you want to collect tweets about.

### After Collection

Once the data has been collected:
- Open **MongoDB Compass**.
- Refresh your database by clicking the circular arrow icon.
- You should see a new collection appear with your tweet data.
- Browse through the documents to view tweet content, metadata, and other fields.

---

### Optional: If You Can’t Use Twitter API

If your Twitter API setup did not work or if you’ve already hit the 100 tweet/month limit, use the demo dataset instead:

1. Open **MongoDB Compass**.
2. Click **Create Database**.
   - Name the database: `demo`
   - Name the collection: `tweet_collection`

3. Once the collection is created, click **Import Data**.
4. Select the demo tweet JSON file that you received from the instructor via email.
5. After importing, you’ll be able to see the same kind of tweet data as if you had collected it via API.

---

## Analyze Tweet Text with OpenAI

In this section, you will use OpenAI's API to process and analyze the tweet texts.

1. Open the notebook named `Analyze_Twitter_Data.ipynb`.
2. Execute each cell from top to bottom.
3. This notebook connects to your MongoDB collection, fetches the tweet text, and sends each tweet to the OpenAI API.

The analyses performed include:

- **Sentiment Analysis**: Determine if the tweet is positive, negative, or neutral.
- **Language Translation**: Translate tweets into English (if necessary).
- **Emotion Detection**: Identify emotions like anger, joy, surprise, or fear.
- **Entity Extraction**: Extract named entities such as people, organizations, and locations.
- **Summarization**: Generate a short summary for each tweet.

Each result is saved back into MongoDB as additional fields within the tweet document.

> For example, you will see new fields such as `"sentiment"`, `"emotions"`, `"entities"`, and `"summary"` appended to the original tweet records.

### Tips

- Ensure your OpenAI API key is correctly stored in **Secrets Manager** and is accessible by your notebook.
- If you encounter errors (e.g., rate limit or authentication), double-check your API key or try reducing the number of tweets processed.

---

## Analyze Tweet Images with OpenAI

This advanced notebook lets you extract, classify, and manipulate tweet images using OpenAI’s image models.

1. Open the notebook titled `Twitter-Image-Classification-Recreation-Editing.ipynb`.
2. From the kernel menu (top-right), select the `conda_pytorch` environment.
3. Execute all the cells one by one.

### What This Notebook Does

- **Extracts Tweets with Images**: Filters out tweets that contain media files.
- **Analyzes Image Content**: Sends each image to OpenAI’s vision model to get a textual description.
- **Selects One Random Image**: Displays a single image along with its AI-generated description.
- **Recreates Images from Prompts**: You provide a text prompt and the model generates new images based on the original content.
- **Applies a Mask with PyTorch**: Optionally applies a mask to selectively regenerate parts of the image.

### Customizing Image Prompts

In the final cell of the notebook, you will be prompted to type a new instruction for generating an image:

```python
prompt = "turn the image into a watercolor painting of a futuristic city"
```

> Edit this prompt to explore different transformations or styles.

### If the Mask Fails

- Sometimes the notebook won’t be able to generate a mask for an image.
- In that case, simply re-run the code cell that selects a random image. Try another one.

## Vector Database and RAG System

In this part of the workshop, we will use a Jupyter notebook to create a vector database from your tweet embeddings and implement a RAG (Retrieval-Augmented Generation) system using MongoDB and OpenAI.

1. Open the notebook named `Exploring-Twitter-Data-with-Vector-Databases-and-RAG-Systems.ipynb`.
2. Execute each cell from top to bottom.

---

### What This Notebook Does

- **Embeds tweet text**: Each tweet will be transformed into a numerical vector using OpenAI's embedding model.
- **Stores embeddings in MongoDB**: The resulting vectors are saved as part of each tweet document in your MongoDB collection.
- **Builds a vector index**: This enables similarity search between queries and tweet content.
- **Implements a RAG system**: A chatbot-style interface is enabled that lets you ask questions and receive AI-generated responses, grounded in your tweet data.

---

### Viewing Embeddings in Compass

After running the embedding steps:

1. Open **MongoDB Compass**.
2. Refresh the collection where you stored your tweets.
3. Each document (tweet) should now contain an additional field — usually named `"embedding"` — which holds the numerical vector representing the semantic content of the tweet.

---

### Using the RAG Chatbot

Toward the end of the notebook, you’ll find cells that let you ask questions like:

```python
"Tell me about the most discussed AI topics in these tweets."
"What do people say about deep learning?"
"Are there any concerns mentioned about AI safety?"
```

The system works as follows:

1. Your natural language query is embedded into a vector.
2. The MongoDB vector search finds the top N similar tweet vectors.
3. Those results are passed into the OpenAI language model with your prompt.
4. OpenAI responds based on the tweet content — not the internet — making this a grounded, private RAG system.

> You are welcome to ask the chatbot any questions that relate to your tweet dataset, such as AI news, public sentiment, or named entities.

---

## Query Twitter Data in Compass

Now that we have collected tweets and analyzed them using OpenAI, we can explore the results using **MongoDB Compass**.

Compass allows two types of queries:

1. **Document query and aggregation pipeline** — traditional MongoDB syntax.
2. **Natural Language Query (NLQ)** — powered by MongoDB Atlas with AI assistance.

---

### Using Traditional Query Methods

1. Open **MongoDB Compass**.
2. Select your database and collection (e.g., `demo.tweet_collection`).
3. Click the **Filter** bar or go to the **Aggregation** tab to build complex queries.
4. You can manually query for fields like sentiment, emotion, or specific keywords in tweets.

Example filter (find positive sentiment tweets):

```json
{ "sentiment": "Positive" }
```

---

### Using Natural Language Queries

MongoDB Atlas Compass supports AI-powered querying in plain English.

1. Click **Generate Query** in Compass.
2. You will be asked to **log in with your Atlas account** if you're not already logged in.
3. Once logged in, return to Compass and try typing a question in the prompt box.

Examples:

- `"Which tweets have the most likes?"`
- `"Show me tweets with negative sentiment."`
- `"How many tweets mention OpenAI?"`

4. MongoDB will convert your question into either:
   - A document query
   - An aggregation pipeline

5. Click **Find** to execute the generated query and view results.

> ⚠️ Note: Natural language queries may produce incorrect results. Always verify the generated query logic before relying on the outcome.

---

### Sample Questions to Try

- **How many tweets' sentiment is Positive?**
- **The top 10 most popular Twitter users**
- **The top 10 extracted organizations**
- **Tweets with fear or anger emotions**
- **Tweets that mention both OpenAI and GPT-4**

You are encouraged to try your own questions and explore how well the system understands them.

---

## Visualize Twitter Data with MongoDB Charts

**MongoDB Charts** is a powerful web-based tool to visualize your data directly from MongoDB Atlas. You can create dashboards and charts using both manual configuration and natural language input.

---

### Open MongoDB Charts

1. Go to [MongoDB Atlas](https://www.mongodb.com/cloud/atlas).
2. Select your project and cluster.
3. Click the **Charts** tab.
4. It may take a few minutes for MongoDB Charts to initialize for first-time users.

> Once initialized, you will see an empty dashboard.

---

### Manually Create Charts

1. Click your dashboard and select **Add Chart**.
2. Choose the **tweet_collection** from your **demo** database as the data source.

#### Example 1: Count of Tweets

- Select **Number** as the chart type.
- Drag `tweet_id` to the **Number** field.
- Use a **count aggregation function**.

#### Example 2: Sentiment by Tweet

- Add another chart using the same data source.
- Select **Stacked Bar Chart**.
- Assign:
  - **X-axis**: `tweet_id`
  - **Y-axis**: `sentiment`
  - **Series**: `anger` (or any emotion field)

#### Example 3: Choropleth Map of Tweet Locations

- Choose the **Map** chart type.
- Drag `user.location` to the **Location** field.
- Drag `tweet_id` to **Color**, set to **count**.

---

### Create Charts with Natural Language

1. Click **Add Chart**.
2. In the top-left, switch from **Classic Chart** to **Natural Language Chart**.
3. Enter a plain-English question in the prompt box.

Example prompts:

- `"The top 10 most popular Twitter users"`
- `"What are the most common hashtags?"`
- `"Who are the top 10 extracted persons?"`

> ⚠️ Natural language charts may generate incorrect responses. Double-check the generated chart logic.

---

### Enable Interactive Filters

To make your dashboard interactive:

1. After creating charts, click **Add Filter**.
2. Choose a field to filter by (e.g., `sentiment`).
3. Enable filter controls on relevant charts.
4. Now, when you click on a value like "Negative", all charts update to reflect only negative tweets.

> This makes your dashboard dynamic and enables exploratory data analysis through user interaction.

---

## End of the Workshop

Congratulations! You’ve now completed all core parts of the UCGIS 2025 workshop on social media analytics with AI. Before you leave, please review the guidance below regarding your cloud environments and access:

---

### AWS Learner Lab

- You are welcome to explore other notebooks in your Jupyter instance.
- When you finish analyzing your data:
  1. Close the **JupyterLab** tab.
  2. Go to your **SageMaker** instance in the AWS console.
  3. Stop the notebook instance to avoid using more lab time.
  4. Return to the AWS Learner Lab and click **End Lab** to finalize the session.

> ✅ Your AWS Academy Lab will remain accessible until **October 31, 2025**.

---

### MongoDB Atlas

- Your **MongoDB free-tier cluster (M0)** is free forever.
- However, note:
  - If your project is under the same MongoDB organization used during the workshop, the instructor may still be able to access your data.
  - For full privacy, you can delete the current project and create a new one under your own organization.

---

### Twitter API

- You retain **full control** of your Twitter developer account and its credentials.
- Limitations:
  - The **free tier** only allows you to collect **100 tweets per month**.
- If you need more tweets, you will need to upgrade to a paid developer tier.

---

### OpenAI API

- The **OpenAI API key** provided for this workshop will be **revoked immediately** after the workshop ends.
- If you want to continue using OpenAI's services:
  1. Visit [https://platform.openai.com](https://platform.openai.com)
  2. Create your own account.
  3. Purchase API credits and generate a personal API key.

---

Thank you for participating in the UCGIS 2025 Workshop on Advancing Social Media Analytics with AI!

For questions or support after the event, please contact:

**Dr. Xuebin Wei**  
Associate Professor, School of Integrated Science  
James Madison University  
📧 weixx@jmu.edu  
🌐 [www.lbsocial.net](https://www.lbsocial.net)
