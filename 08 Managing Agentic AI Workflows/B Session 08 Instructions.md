#### This Session
>Introduces agentic AI concepts and orchestration frameworks, showing how to design and oversee multi-step automated workflows that can handle judgment-based finance tasks.

[![GitHub](https://img.shields.io/badge/GitHub-08_Managing_Agentic_AI_Workflows-black?logo=github)](https://github.com/mozuliov/Digital_Talent_Level1_Training/tree/main/08%20Managing%20Agentic%20AI%20Workflows)

**Working Environment:** [![n8n](https://img.shields.io/badge/n8n-Automation-orange?logo=n8n&logoColor=white)](https://n8n.io/)

# Building Your Autonomous Data Analyst

In this session, you will build an AI Agent that translates human questions into SQL, queries a live BigQuery database, and (optionally) generates visual charts.

**Prerequisites:** Google Gemini API Key - [[B Step-by-Step Connecting Gemini to n8n|Instructions]]

## Part 1: Setting up the AI Brain (Agent Core)

1. **Create Workflow:** Click **"Create New Workflow"** in  [![n8n](https://img.shields.io/badge/n8n-Automation-orange?logo=n8n&logoColor=white)](https://n8n.io/).    
2. **Add Chat Trigger:** Press `+`, search for **"Chat Trigger"**, and place it.    
3. **Add AI Agent:** Connect the Chat Trigger to an **"AI Agent"** node.    
    - **Agent Type:** Set to `AI Agent`.        
    - **Prompt Type:** `Define below`.        
4. **Connect the Essentials:**    
    - **Model:** Attach a `Google Gemini Chat Model`. Select `gemini-1.5-flash-preview-09-2025`. Set **Temperature** to `0.1` for precision.        
    - **Memory:** Attach a `Window Buffer Memory`. Set **Context Window** to `10`.        

## Part 2: Connecting the Database (BigQuery Tool)

1. **Add Tool:** Under the **Tools** input of the AI Agent, add the **"Google BigQuery"** tool.    
2. **Authentication:** * Create a new credential using **Service Account JSON** or **OAuth2**.    
    - Ensure your service account has `BigQuery Data Viewer` and `BigQuery Job User` roles.   
3. **Configure Tool Settings:**    
    - **Description (VERY IMPORTANT):** Paste this exact string:        
        > "Use this tool to interact with the 'austin_bikeshare' dataset in Google BigQuery. You must write standard SQL queries to answer user questions about trips, stations, and bike types. Tables available: 'bikeshare_trips', 'bikeshare_stations'."        

## Part 3: The System Message (Instruction Layer)

Open the **AI Agent** node and paste this into the **System Message** field:

> "You are a Senior Data Analyst. Your goal is to provide accurate insights from the Austin Bikeshare dataset.
> 
> 1. Use the BigQuery tool to fetch data.>     
> 2. If a query fails, check your column names and try again.>     
> 3. Always format numbers clearly (e.g., use commas for thousands).>     
> 4. Summarize findings professionally.">     

## Part 4: Testing Part 1

Click **"Execute Workflow"** and type this in the chat:

> _"What are the names of the top 3 busiest start stations this month?"_

## 🏆 Advanced Challenge: Automated Visualization

To make your bot draw charts, you must connect it to the **Visualization Microservice**.

### 1. The Tool Setup

Add an **HTTP Request** node as a **second tool** for the AI Agent.

- **Name:** `generate_visual`    
- **Description:** > "Use this tool to create a chart after fetching data. You must provide: data (array), x_axis (string), y_axis (string), chart_type ('bar', 'line', 'pie', or 'scatter'), and chart_title (string)."    

### 2. The API Handshake (Parameters)

- **Method:** `POST`    
- **URL:** `https://ais-dev-z5h6y3-uc.a.run.app` (Use the provided microservice link).    
- **Body Parameters:** Click **Add Parameter** for each:    
    - `data` → Expression: `{{ $fromAI('data') }}`        
    - `x_axis` → Expression: `{{ $fromAI('x_axis') }}`        
    - `y_axis` → Expression: `{{ $fromAI('y_axis') }}`        
    - `chart_type` → Expression: `{{ $fromAI('chart_type') }}`        
    - `chart_title` → Expression: `{{ $fromAI('chart_title') }}`        

### 3. Authentication (Clearing the Wall)

If you hit a "Cookie Check" or security error:

1. Open **Google Cloud Shell** (`>_` icon in GCP).    
2. Run: `gcloud auth print-identity-token`    
3. In n8n HTTP Request node, add a **Header**:    
    - **Name:** `Authorization`        
    - **Value:** `Bearer [PASTE_TOKEN_HERE]`        

### 4. The Final Instruction

Update your **AI Agent System Message** to include:

> "Whenever you retrieve numerical data, automatically call the 'generate_visual' tool. When it returns a 'chart_base64' string, display it exactly as: `![Chart](data:image/png;base64,PASTE_STRING_HERE)`."

![[C Chatbot Illustration.png|697]]
## Troubleshooting List

- **Error: 404/403:** Check your Project ID in the BigQuery node.    
- **Error: "Cookie Check":** Your Authorization token has expired or is missing.    
- **No Chart:** Ensure the Agent is passing `x_axis` and `y_axis` without spaces.