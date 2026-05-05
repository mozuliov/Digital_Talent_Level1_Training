### Phase 1: Get your Gemini API Key

This part happens in **Google AI Studio**, the place where Google manages its AI tools for developers.

1. **Go to Google AI Studio:** Visit [![Google AI Studio](https://img.shields.io/badge/Google%20AI%20Studio-Platform-4285F4?logo=google&logoColor=white)](https://aistudio.google.com). Sign in with your standard Google/Gmail account.
    
2. **Agree to Terms:** If it’s your first time, a window will pop up asking you to agree to the Terms of Service. Check the boxes and click **Continue**.
    
3. **Find the API Key Menu:** On the left-hand sidebar, click the button that says **"Get API key"** (it usually has a key icon 🔑).
    
4. **Create the Key:**
    
    - Click the blue button: **"Create API key in new project"**.
        
    - Google will take a moment to set things up in the background.
        
5. **Copy the Key:**
    
    - A long string of random letters and numbers will appear (e.g., `AIzaSy...`).
        
    - Click **Copy**.
        
    - **⚠️ Important:** Keep this private! Anyone with this key can use your Gemini account. Paste it into a temporary Note or Word doc so you don't lose it while switching tabs.
        

### Phase 2: Set up the Key in n8n

Now, we need to tell n8n to use that key.

1. **Open n8n:** Log in to your [![n8n](https://img.shields.io/badge/n8n-Automation-orange?logo=n8n&logoColor=white)](https://n8n.io/) instance.
    
2. **Go to Credentials:** On the left sidebar, click on **Credentials**.
    
3. **Add New Credential:**
    
    - Click the **"Add Credential"** button (top right).
        
    - In the search bar, type **"Google Gemini"**.
        
    - Select **"Google Gemini(PaLM) API"** from the list.
        
4. **Paste your Key:**
    
    - Find the field labeled **API Key**.
        
    - Paste the code you copied from Google AI Studio earlier.
        
5. **Save:** Click **Save** at the top right. You should see a green badge that says "Connected" or "Saved."
    

### Phase 3: Using Gemini in a Workflow

1. **Create a New Workflow:** Click the "+" icon on your n8n dashboard.
    
2. **Add the Gemini Node:**
    
    - Click the **"+"** button in the workflow editor.
        
    - Search for **"Google Gemini"**.
        
    - Choose the node (e.g., "Google Gemini Chat Model" if you are building an AI Agent).
        
3. **Select your Credential:** Inside the node settings, look for the **Credential** dropdown and select the one you just created.
    
4. **Test it:** Enter a simple prompt like "Hello, who are you?" and click **Execute Node**.
    

### Troubleshooting for Beginners

- **"API Key not found":** Make sure you didn't accidentally copy a space at the beginning or end of the key.
    
- **"Quota Exceeded":** The free version of Gemini has limits. If you use it too fast, Google might tell you to slow down for a few minutes.
    
- **Billing:** The "Free" tier is usually sufficient for beginners and doesn't require a credit card in AI Studio, but some regions may require a Google Cloud Billing account linked if you want higher limits.