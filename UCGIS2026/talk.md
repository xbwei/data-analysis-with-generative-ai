<div class="title-grid">
  <div>
    <p class="eyebrow">UCGIS 2026 Lightning Talk</p>
    <h1 class="deck-title">Humans, AI Agents, and Teaching Stacks in GeoAI Education</h1>
    <p class="subtitle">AI is becoming a stronger tool. Humans still give it purpose.</p>
  </div>
  <div class="contact-panel">
    <p class="name">Xuebin Wei</p>
    <p>James Madison University</p>
    <p><a href="mailto:weixx@jmu.edu">weixx@jmu.edu</a></p>
    <p><a href="https://www.lbsocial.net">lbsocial.net</a></p>
  </div>
</div>

Note:
My idea is simple. AI is changing very fast. It is becoming a stronger tool for teaching and research. But I do not think AI replaces the human role. Humans still define the goal, the value, and the reason why we use these tools.

---

## My Idea: Three Stages

<div class="stage-overview">
  <div class="stage-card prompt">
    <span class="stage-number">1</span>
    <h3>Prompt engineering</h3>
    <p>Human and model talk directly.</p>
  </div>
  <div class="stage-arrow">-&gt;</div>
  <div class="stage-card context">
    <span class="stage-number">2</span>
    <h3>Context engineering</h3>
    <p>The model receives trusted materials.</p>
  </div>
  <div class="stage-arrow">-&gt;</div>
  <div class="stage-card harness">
    <span class="stage-number">3</span>
    <h3>Harness engineering</h3>
    <p>Agents use tools, skills, MCP, and scale.</p>
  </div>
</div>

<div class="experiment-strip">
  <div class="mini-node">tutorial videos</div>
  <div class="mini-line"></div>
  <div class="mini-node strong">KG/MCP search</div>
  <div class="mini-line"></div>
  <div class="mini-node">clips for this deck</div>
</div>

Note:
I want to make clear that this is my own idea from my own recent work. I see the change in three stages. First, prompt engineering: we learned how to ask better. Second, context engineering: we learned how to give AI the right materials. Third, harness engineering: we give AI tools, MCP services, cloud systems, and scale. For this talk, I also used an AI agent to call my KG/MCP service, search my tutorial knowledge graph, and find the video segments that match this story. So this presentation is also a small example of what I am talking about.

---

## From Prompt Engineering

<div class="slide-grid">
  <div>
    <p class="stage-label">Stage 1</p>
    <ul>
      <li>At the beginning, we learned to control LLMs with better prompts.</li>
      <li>We used examples, formats, and clear instructions.</li>
      <li>The model mostly worked inside the conversation.</li>
    </ul>
    <div class="prompt-diagram">
      <div class="person-dot">Human</div>
      <div class="chat-stack">
        <span>instruction</span>
        <span>example</span>
        <span>format</span>
      </div>
      <div class="model-dot">LLM</div>
    </div>
  </div>
  <div class="video-card compact">
    <iframe src="https://www.youtube.com/embed/fdg0Zo7Wj5M?start=745" title="Prompt engineering tutorial" allowfullscreen></iframe>
    <p><a href="https://www.youtube.com/watch?v=fdg0Zo7Wj5M&t=745s">Prompt engineering example</a></p>
  </div>
</div>

Note:
The first stage I taught was prompt engineering. We learned that if we give examples and clear output formats, the model can follow patterns. This was a very important step. But it was still mostly about asking the model in a better way.

---

## To Reasoning Models

<div class="slide-grid">
  <div>
    <p class="stage-label">A stronger model core</p>
    <ul>
      <li>Models became better at multi-step thinking.</li>
      <li>They can compare different paths before giving an answer.</li>
      <li>This makes them more useful for data analysis and research tasks.</li>
    </ul>
    <div class="reasoning-diagram">
      <div>question</div>
      <div class="path-grid">
        <span>path A</span>
        <span>path B</span>
        <span>path C</span>
      </div>
      <div class="answer-chip">answer</div>
    </div>
  </div>
  <div class="video-card compact">
    <iframe src="https://www.youtube.com/embed/DAyfcycvM4E?start=37" title="Reasoning model tutorial" allowfullscreen></iframe>
    <p><a href="https://www.youtube.com/watch?v=DAyfcycvM4E&t=37s">Reasoning model example</a></p>
  </div>
</div>

Note:
The next stage is reasoning models. In my tutorial, I explained that reasoning models may take multiple steps before they answer. They can compare possible solutions. They are not perfect, but they are stronger for harder tasks. This changed how I think about AI for research and teaching.

---

## To Context Engineering

<div class="slide-grid">
  <div>
    <p class="stage-label">Stage 2</p>
    <ul>
      <li>Prompting is not enough when the task needs trusted knowledge.</li>
      <li>Context engineering gives AI the right documents, data, memory, and evidence.</li>
      <li>RAG, embeddings, and knowledge graphs help AI use the right material.</li>
    </ul>
    <div class="context-diagram">
      <div class="source-stack">
        <span>docs</span>
        <span>data</span>
        <span>memory</span>
        <span>graph</span>
      </div>
      <div class="retriever">retrieve</div>
      <div class="grounded-model">grounded LLM</div>
    </div>
  </div>
  <div class="video-card compact">
    <iframe src="https://www.youtube.com/embed/nmdQcFbVXug?start=41" title="RAG and embeddings tutorial" allowfullscreen></iframe>
    <p><a href="https://www.youtube.com/watch?v=nmdQcFbVXug&t=41s">RAG and embeddings example</a></p>
  </div>
</div>

Note:
After prompt engineering, I think the next important idea is context engineering. We cannot put everything in one prompt. We need to select the right information. That is why RAG, embeddings, vector search, and knowledge graphs are useful. They help AI find trusted materials before it answers.

---

## GeoAI Needs Grounding

<div class="slide-grid">
  <div>
    <p class="stage-label">Geographic context</p>
    <ul>
      <li>In GeoAI, evidence is not only text.</li>
      <li>We also need places, relations, scale, and spatial context.</li>
      <li>GraphRAG can connect language, graph structure, and geographic evidence.</li>
    </ul>
    <div class="geo-diagram">
      <span class="map-tile">place</span>
      <span class="map-tile">relation</span>
      <span class="map-tile">scale</span>
      <span class="map-tile">evidence</span>
    </div>
  </div>
  <div class="video-card compact">
    <iframe src="https://www.youtube.com/embed/JX5BOb-nQrY?start=708" title="Geo GraphRAG tutorial" allowfullscreen></iframe>
    <p><a href="https://www.youtube.com/watch?v=JX5BOb-nQrY&t=708s">Geo GraphRAG example</a></p>
  </div>
</div>

Note:
For GIScience and GeoAI, context is even more important. Spatial questions include location, distance, scale, and relationships. In my Geo GraphRAG tutorial, I combined spatial filtering, vector search, graph retrieval, and a language model. This is a good example of AI using more than text.

---

## To Harness Engineering

<div class="harness-layout">
  <div>
    <p class="stage-label">Stage 3</p>
    <ul>
      <li>Now we are moving toward agents with tools.</li>
      <li>Agents can use MCP services, data, skills, and cloud systems.</li>
      <li>The key question becomes: what should we let the agent do?</li>
    </ul>
    <div class="harness-diagram">
      <div class="agent-core">AI agent</div>
      <span>MCP</span>
      <span>tools</span>
      <span>skills</span>
      <span>scale</span>
    </div>
  </div>
  <div class="video-row two">
    <div class="video-card small">
      <iframe src="https://www.youtube.com/embed/Dna_DZLC8d0?start=70" title="MCP and KG agent tutorial" allowfullscreen></iframe>
      <p><a href="https://www.youtube.com/watch?v=Dna_DZLC8d0&t=70s">MCP + KG agent</a></p>
    </div>
    <div class="video-card small">
      <iframe src="https://www.youtube.com/embed/_ssB1YXRRtk?start=935" title="Classroom agent workflow tutorial" allowfullscreen></iframe>
      <p><a href="https://www.youtube.com/watch?v=_ssB1YXRRtk&t=935s">Classroom workflow agent</a></p>
    </div>
  </div>
</div>

Note:
I call the current stage harness engineering. The model itself is important, but the harness around it is also important. The agent needs tools, skills, MCP services, databases, and cloud execution. If we build the harness well, the agent can do much more than answer questions. It can use tools and finish workflows. But this also means we need to decide what actions are safe and what actions need human approval.

---

## A Personal Teaching Stack

<div class="mode-stack">
  <div class="mode-card">
    <h3>Study Mode</h3>
    <p>AI helps students learn from trusted course materials.</p>
  </div>
  <div class="mode-card">
    <h3>Teaching Mode</h3>
    <p>AI helps instructors draft lessons, labs, quizzes, and videos.</p>
  </div>
  <div class="mode-card">
    <h3>Analysis Mode</h3>
    <p>AI helps with data analysis, dashboards, and GeoAI workflows.</p>
  </div>
</div>

<p class="closing-line">This is a teaching stack, not one chatbot.</p>

Note:
This is how I connect these ideas to education. In my personal project, I use three modes. Study Mode helps students learn from trusted course material. Teaching Mode helps instructors draft lessons, labs, quizzes, and videos, but the teacher still reviews everything. Analysis Mode helps with data analysis, dashboards, and GeoAI workflows. I see this as a teaching stack, not as one chatbot.

---

## Study Mode

<div class="mode-slide">
  <div class="screenshot-slot">
    <span>Study Mode screenshot slot</span>
    <p>Trusted course material, KG retrieval, guided learning</p>
  </div>
  <div class="video-card compact">
    <iframe src="https://www.youtube.com/embed/p0N20TW0dN0?start=0" title="AI teaching assistant tutorial" allowfullscreen></iframe>
    <p><a href="https://www.youtube.com/watch?v=p0N20TW0dN0&t=0s">Study support</a></p>
  </div>
</div>

Note:
Study Mode is for students. The goal is not just to answer questions, but to help students learn from trusted course materials. This is where context engineering matters.

---

## Teaching Mode

<div class="mode-slide">
  <div class="screenshot-slot">
    <span>Teaching Mode screenshot slot</span>
    <p>Drafting materials with instructor review</p>
  </div>
  <div class="video-card compact">
    <iframe src="https://www.youtube.com/embed/RDKVcaE52hg?start=31" title="AI teaching video workflow" allowfullscreen></iframe>
    <p><a href="https://www.youtube.com/watch?v=RDKVcaE52hg&t=31s">Teaching workflow</a></p>
  </div>
</div>

Note:
Teaching Mode is for instructors. AI can help draft lesson materials, labs, quizzes, and videos. But the teacher still reviews, edits, and decides what is appropriate.

---

## Analysis Mode

<div class="mode-slide">
  <div class="screenshot-slot">
    <span>Analysis Mode screenshot slot</span>
    <p>Data analysis, dashboards, and GeoAI workflows</p>
  </div>
  <div class="video-card compact">
    <iframe src="https://www.youtube.com/embed/AJLRsjjWWKo?start=42" title="AI analysis dashboard tutorial" allowfullscreen></iframe>
    <p><a href="https://www.youtube.com/watch?v=AJLRsjjWWKo&t=42s">Analysis workflow</a></p>
  </div>
</div>

Note:
Analysis Mode connects the same idea to research. AI can help with data, dashboards, and GeoAI workflows. This is where agents can become useful, as long as we keep human goals and review in the loop.

---

## What AI Still Does Not Have

<div class="human-ai-layout">
  <div>
    <ul>
      <li>AI can help us think, but it does not have human life.</li>
      <li>AI can sound friendly, but it does not naturally care.</li>
      <li>Humans care about children, communities, fairness, and the future.</li>
      <li>That is why human judgment must stay in the loop.</li>
    </ul>
  </div>
  <div class="human-ai-diagram">
    <div class="ai-side">
      <h3>AI</h3>
      <p>speed</p>
      <p>scale</p>
      <p>memory</p>
    </div>
    <div class="bridge">supports</div>
    <div class="human-side">
      <h3>Human</h3>
      <p>purpose</p>
      <p>care</p>
      <p>judgment</p>
    </div>
  </div>
</div>

Note:
This is the most important part for me. AI may become very powerful, but it is still different from humans. Humans have life. Humans have emotion. Humans have self-awareness. We care about the future. We want our children and our communities to live better lives. AI does not naturally care about that. AI can help us, but it should not replace the human role in deciding purpose and value.

---

## What This Means for GIScience and GeoAI

<div class="final-grid">
  <div class="mode-mini">
    <span>Study Mode</span>
    <p>learn</p>
  </div>
  <div class="mode-mini">
    <span>Teaching Mode</span>
    <p>teach</p>
  </div>
  <div class="mode-mini">
    <span>Analysis Mode</span>
    <p>research</p>
  </div>
</div>

<ol class="final-points">
  <li>Use AI so people can do more meaningful work in less time.</li>
  <li>Teach students to build critical thinking and exercise their brain muscle.</li>
  <li>Keep humans as the question askers, because humans care about the world.</li>
</ol>

<p class="closing-line">AI can help us do more. Humans must decide what matters.</p>

Note:
My suggestion is practical. I am building Study Mode, Teaching Mode, and Analysis Mode because I think AI can help us learn, teach, and do research. AI can help fewer people do more work in less time. But this does not mean students should think less. They need to build critical thinking. They need to exercise their brain muscle. And humans are still the question askers, because humans have life and humans care about the world.
