# UCGIS 2025 Workshop: Advancing Social Media Analytics with AI

**Instructor:** Xuebin Wei  
**Associate Professor, School of Integrated Science, James Madison University**  
**Email:** weixx@jmu.edu  
**Website:** [www.lbsocial.net](https://www.lbsocial.net)  
**Textbook:** [Social Data Analytics in the Cloud with AI](https://www.taylorfrancis.com/books/mono/10.1201/9781003437611/social-data-analytics-cloud-ai-xuebin-wei-xinyue-ye)  
**Demo Code:** [https://github.com/xbwei/data-analysis-with-generative-ai](https://github.com/xbwei/data-analysis-with-generative-ai)  

---

## Introduction

This hands-on workshop explores AI-powered social media analytics, focusing on Twitter (X) data collection, analysis, and visualization. Participants will learn to use MongoDB for scalable storage, generative AI for text and image processing, and retrieval-augmented generation (RAG) for enhanced data insights. These techniques are critical for researchers and professionals working in fields such as public sentiment analysis, misinformation detection, disaster response, and urban studies.

---

## Set Up Cloud Resources

### Twitter Free API

Twitter recently updated its policy to allow the free Twitter API to collect 100 Tweets per month.

1. Register for a Twitter account at [https://x.com](https://x.com) if you don’t already have one.
2. Apply for a free Twitter developer account at [https://developer.x.com/en](https://developer.x.com/en) using your Twitter account.
3. A short video demo is available here: [https://www.youtube.com/shorts/GBmR_bnqrOs](https://www.youtube.com/shorts/GBmR_bnqrOs).
4. Log in to your Twitter developer account. Under **Projects & Apps**, you will find your default app.
5. Click **Keys and Tokens**, and generate a **Bearer Token**.
6. Copy the Bearer Token and save it to your local computer (e.g., in a `.txt` file).

> If you can’t create a Twitter API, use the provided demo tweet data.

---

### MongoDB Cluster

MongoDB is the most popular NoSQL database and offers a free M0 cluster through its Atlas service.

1. Accept the invitation from MongoDB and register at [https://www.mongodb.com](https://www.mongodb.com).
2. Once logged in, create a new project (you can name it after yourself).
3. In your project, create a cluster. You can only have one free cluster per project.
4. On the next screen, create a database user (different from your MongoDB login). Use the following credentials for simplicity:
   - **Username:** `demo`
   - **Password:** `UCGIS2025`
5. While the cluster is being created, update **Network Access**:
   - Under **Security**, click **Network Access**, then **Edit**.
   - Allow access from anywhere.

6. To get the connection string:
   - Go to **Clusters** > **Connect** > **Drivers/Python**.
   - Copy the connection string and save it locally.

7. Download and install [MongoDB Compass](https://www.mongodb.com/try/download/compass).
8. Start Compass, create a new connection using the saved connection string. Replace the password with `UCGIS2025`.
9. You should now see your cluster listed in the sidebar.

---

### AWS Academy Lab

AWS Academy provides free credits to students for cloud services.

1. Accept the AWS Academy Learner Lab invitation.
2. Set your password and complete account setup.
3. Log in to [https://awsacademy.instructure.com/login/canvas](https://awsacademy.instructure.com/login/canvas).
4. Go to **Modules** and click **Launch AWS Academy Learner Lab**.
5. Accept terms and click **Start Lab**.
6. When the green dot appears, click the AWS link to open the console.

#### Store Secrets in AWS Secrets Manager

1. Search for **Secrets Manager** in AWS Console and open it.
2. Click **Store a new secret**.
3. Select **Other type of secret**, and add the following:

**Twitter API:**
- Key: `bearer_token`
- Value: *your bearer token*
- Secret name: `twitter_api`

**MongoDB:**
- Key: `connection_string`
- Value: *your connection string with password*
- Secret name: `mongodb`

**OpenAI:**
- Key: `api_key`
- Value: *your OpenAI API key from email*
- Secret name: `openai`

---

### Set Up SageMaker Notebook

1. Search for **Amazon SageMaker** and go to **Notebook Instances**.
2. Click **Create notebook instance**.
3. Provide an instance name.
4. Under Git repositories, select **Clone a public Git repository**.
5. Repository URL: `https://github.com/xbwei/data-analysis-with-generative-ai.git`
6. Leave all other settings default and create the instance.

> It may take 1–2 minutes to be ready. Feel free to ask questions during the wait.

---

## Collect Twitter Data

1. Once the notebook is in service, open **JupyterLab**.
2. Open `Collect_Twitter_Data` notebook.
3. Run each cell top to bottom.
4. Modify the keyword in the query if desired (default: “generative AI”).
5. After collection, refresh MongoDB Compass to see the data.

### Optional: Import Demo Tweets

If API access fails:

1. In Compass, create a **database** named `demo`.
2. Create a **collection** named `tweet_collection`.
3. Click **Import Data**, and upload the demo file sent via email.

---

## Analyze Tweet Text with OpenAI

1. Open the `Analyze_Twitter_Data` notebook.
2. Run all cells in order.
3. The notebook performs:
   - Sentiment analysis
   - Language translation
   - Emotion detection
   - Entity extraction
   - Summarization
4. Results are written back to MongoDB for each tweet.

---

## Analyze Tweet Images with OpenAI

1. Open the `Twitter-Image-Classification-Recreation-Editing` notebook.
2. Select the `conda_pytorch` kernel.
3. Run all cells in sequence.

Tasks include:
- Extracting tweets with images.
- Analyzing and describing images.
- Randomly selecting one image to recreate using your prompt.
- Generating new images based on AI interpretations.
- Optionally applying a PyTorch mask.

> To change the image, re-run the image selection cell. Customize prompts to create different images.

---

## Vector Database and RAG System

1. Open the `Exploring-Twitter-Data-with-Vector-Databases-and-RAG-Systems` notebook.
2. Run all cells.

Steps:
- Create vector embeddings for tweet text.
- Store vectors in MongoDB.
- View embeddings in Compass.
- Implement a chatbot using RAG.
- Ask it questions like:
  - “What are people saying about AI education?”
  - “Summarize public opinions on ChatGPT.”

---

## Query Twitter Data in Compass

1. Open MongoDB Compass and go to `tweet_collection`.
2. Click **Generate Query**.
3. Log in with your Atlas credentials if prompted.
4. Ask questions in natural language like:
   - “Which tweets have the most likes?”
   - “How many tweets’ sentiment is Positive?”
   - “Top 10 extracted organizations”

> MongoDB will convert the question into a query or aggregation pipeline. Verify correctness manually.

---

## Visualize Twitter Data with MongoDB Charts

1. In MongoDB Atlas, click **Charts**.
2. Wait for initialization. Then open your dashboard.

### Create Charts Manually

- Select the `tweet_collection` from `demo`.
- Examples:
  - **Number chart**: count of tweet IDs.
  - **Stacked bar**: tweet ID (X), sentiment (Y), series = anger.
  - **Map**: user location and count of tweets.

### Create Charts Using Natural Language

- Add chart > switch to **Natural Language Chart**.
- Example questions:
  - “Top 10 most popular Twitter users”
  - “Most common hashtags”
  - “Top 10 extracted persons”

### Enable Filters

- Add filters (e.g., by sentiment).
- Clicking a filter like “Negative” updates all charts dynamically.

---

## End of the Workshop

### AWS Learner Lab

- Feel free to try other notebooks.
- When done:
  - Close JupyterLab.
  - Stop notebook instance.
  - Click **End Lab** in AWS Learner Lab.

### MongoDB

- Your cluster is free forever.
- Instructor can access data in this organization.
- Delete and recreate your project under a new org if you want privacy.

### Twitter API

- You have full control.
- Free tier: 100 tweets/month.

### OpenAI API

- This key will be revoked after the workshop.
- To continue using OpenAI, get a new key at [https://platform.openai.com](https://platform.openai.com).

---
