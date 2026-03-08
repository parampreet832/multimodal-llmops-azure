<h1>🎥 Multimodal Video Compliance QA Pipeline(LLMOps)</h1>
<p>An end-to-end, production-grade LLMOps pipeline designed to audit video content against regulatory standards. This project leverages LangGraph for orchestration, Azure Video Indexer for multimodal processing, and GPT-4o for deterministic compliance reasoning.</p>
<h2>🚀 Overview</h2>
<p>This system automates the tedious process of manual video auditing. By transforming unstructured video (visuals, audio, and text) into structured JSON compliance reports, it ensures that content meets legal and regulatory guidelines with high precision and full observability.</p>
<h4>Core Workflow</h4>
<ul>
<li><strong>Ingestion:</strong> Azure Video Indexer extracts transcripts, OCR (on-screen text), and visual labels.</li>
<li><strong>Retrieval:</strong> Azure AI Search uses RAG to pull specific regulatory clauses based on video context.</li>
<li><strong>Orchestration:</strong> LangGraph manages the stateful logic, ensuring the LLM follows a strict "Chain of Compliance" reasoning path.</li>
<li><strong>Analysis:</strong> Azure OpenAI (GPT-4o) evaluates the multimodal data against retrieved rules.</li>
<li><strong>Observability:</strong> Full-stack tracing via LangSmith and telemetry via Azure Application Insights.</li>
</ul>
<h2>🛠️ Tech Stack</h2>
<table>
<thead><tr><td>Component</td><td>Technology</td></tr></thead>
<tbody>
<tr><td><strong>Orchestration</strong></td><td>LangGraph, LangChain</td></tr>
<tr><td><strong>LLM & Embeddings</strong></td><td>Azure OpenAI (GPT-4o, text-embedding-3-large</td></tr>
<tr><td><strong>Multimodal Processing</strong></td><td>Azure Video Indexer</td></tr>
<tr><td><strong>Vector Database</strong></td><td>Azure AI Search</td></tr>
<tr><td><strong>Observability</strong></td><td>LangSmith (Tracing), Azure Application Insights (Telemetry)</td></tr>
<tr><td><strong>Cloud Infrastructure</strong></td><td>Azure Web Apps / Functions, GitHub Actions (CI/CD)</td></tr>
<tbody>
</table>
<h2>🏗️ Architecture</h2>
<p>The system is designed with a Stateful Graph approach to handle the complexities of multimodal data.</p>
<h4>Key Features</h4>
<ul>
<li><strong>Multimodal RAG:</strong> Not just text—the engine reasons over what is seen (OCR/Labels) and what is heard (Transcripts).</li>
<li><strong>Stateful Orchestration:</strong> LangGraph allows for "Human-in-the-loop" checkpoints and iterative refinement of compliance reports.</li>
<li><strong>Full-Stack Observability: * LangSmith:</strong> To debug the prompt chain and monitor token usage/latency per node.
<ul>
<li><strong>App Insights:</strong> For infrastructure health, request rates, and custom business metrics.</li>
</ul></li>
</ul>

<h2>📂 Project Structure</h2>
'''Bash
├── .github/workflows      # CI/CD pipelines (GitHub Actions)
├── src/
│   ├── agents/            # LangGraph node logic & state definitions
│   ├── indexing/          # Azure Video Indexer & AI Search logic
│   ├── prompts/           # Structured system templates for GPT-4o
│   └── utils/             # Telemetry & logging helpers
├── tests/                 # Unit & Integration tests
├── docker-compose.yml     # Local development environment
└── requirements.txt       # Python dependencies
`

<h2>⚙️ Getting Started</h2>
<h4>Prerequisites</h4>
<ul>
<li>An active Azure Subscription.</li>
<li>Azure OpenAI access (with GPT-4o and Embedding models deployed).</li>
<li>LangSmith API Key for tracing.</li>
</ul>
<h4>Installation</h4>
<p><strong>1) Clone the repository:</strong></p>
<p>Bash<br>
git clone https://github.com/your-username/multimodal-video-compliance.git<br>
cd multimodal-video-compliance</p>

<p><strong>2) Configure Environment Variables:</strong><br>
Create a .env file in the root directory:</p>
<p>Code snippet<br>
AZURE_OPENAI_API_KEY=your_key<br>
AZURE_VIDEO_INDEXER_ID=your_id<br>
AZURE_AI_SEARCH_ENDPOINT=your_endpoint<br>
LANGCHAIN_TRACING_V2=true<br>
LANGCHAIN_API_KEY=your_langsmith_key<br>
APPINSIGHTS_INSTRUMENTATION_KEY=your_key</p>

<p><strong>3) Install Dependencies:</strong></p>
<p>Bash<br>
pip install -r requirements.txt</p>

<p><strong>4. Run the Pipeline:</strong></p>
<p>Bash<br>
python main.py --video_url "path_to_your_video.mp4"</p>

<h2>📊 Observability & Monitoring</h2>
<p>This project treats Observability as a first-class citizen.</p>
<ul>
<li>Tracing: Every decision made by the LLM is captured in LangSmith, allowing you to view the exact context retrieved from Azure AI Search.</li>
<li>Logging: Application Insights captures all stderr/stdout and custom dimensions, making it easy to set up alerts for high violation rates or API failures.</li>
</ul>

<h2>📄 License</h2>
<p>This project is licensed under the MIT License - see the LICENSE file for details.</p>
