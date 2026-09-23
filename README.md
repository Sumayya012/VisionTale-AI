# 🖼️ Image-to-Speech GenAI Tool

An AI-powered Streamlit application that transforms an image into a short creative story and converts that story into speech.

The application combines **image understanding, generative AI, and text-to-speech** into a single workflow.

---

## ✨ How It Works

The application follows a simple AI pipeline:

**Image → Image Caption → Story Generation → Speech Generation**

1. **Upload an Image**
   - The user uploads a JPG image through the Streamlit interface.

2. **Image Understanding**
   - Salesforce BLIP analyzes the image and generates a textual description.

3. **Story Generation**
   - Google Gemini uses the generated description as context and creates a short creative story.

4. **Text-to-Speech**
   - The generated story is converted into natural-sounding speech using the Kokoro text-to-speech model.

5. **Output**
   - The application displays:
     - Generated image description
     - Generated short story
     - Audio narration

---

## 🤖 AI Models Used

### 1. Image Captioning — BLIP

**Model:** `Salesforce/blip-image-captioning-base`

BLIP is used to understand the uploaded image and generate a textual description.

### 2. Story Generation — Google Gemini

**Model:** `gemini-3.5-flash-lite`

Gemini takes the image description and generates a short creative story based on the detected scene.

### 3. Text-to-Speech — Kokoro

**Model:** `hexgrad/Kokoro-82M`

Kokoro converts the generated story into speech.

The application accesses the model through the Hugging Face Inference Client using the `deepinfra` provider.

---

## 🏗️ System Architecture

```text
                 ┌─────────────────┐
                 │   User Uploads  │
                 │      Image      │
                 └────────┬────────┘
                          │
                          ▼
              ┌───────────────────────┐
              │      BLIP Model       │
              │  Image Captioning     │
              └───────────┬───────────┘
                          │
                          ▼
                 Image Description
                          │
                          ▼
              ┌───────────────────────┐
              │    Google Gemini      │
              │   Story Generation    │
              └───────────┬───────────┘
                          │
                          ▼
                    Short Story
                          │
                          ▼
              ┌───────────────────────┐
              │     Kokoro-82M        │
              │    Text-to-Speech     │
              └───────────┬───────────┘
                          │
                          ▼
                  🔊 Audio Output
🛠️ Technologies Used
Python
Streamlit
PyTorch
Hugging Face Transformers
Hugging Face Inference Client
Google Gemini API
BLIP
Kokoro TTS
python-dotenv
📁 Project Structure
Image-to-Speech-GenAI-Tool-Using-LLM/
│
├── app.py
├── requirements.txt
├── README.md
├── LICENSE
├── .gitignore
│
├── img/
│   ├── sumayya_logo.png
│   └── ...
│
├── audio-img/
│   ├── app-snapshot.jpg
│   └── happy couple.jpg
│
├── utils/
│   └── custom.py
│
├── nature.jpg
└── storytelling.jpg
⚙️ Local Setup
1. Clone the repository
git clone <YOUR-GITHUB-REPOSITORY-URL>
cd Image-to-Speech-GenAI-Tool-Using-LLM
2. Create a virtual environment
python -m venv .venv
3. Activate the virtual environment

Windows PowerShell:

.\.venv\Scripts\Activate.ps1
4. Install dependencies
pip install -r requirements.txt
5. Configure API keys

Create a .env file in the project root:

GEMINI_API_KEY=your_gemini_api_key
HUGGINGFACE_API_TOKEN=your_huggingface_token

Important: Never upload your .env file or expose API keys publicly.

6. Run the application
python -m streamlit run app.py

The application will open in your browser.

🔐 Environment Variables
Variable	Purpose
GEMINI_API_KEY	Used for Gemini story generation
HUGGINGFACE_API_TOKEN	Used for Hugging Face model inference

For cloud deployment, these keys should be configured using the platform's secrets management rather than committed to GitHub. Streamlit Community Cloud supports adding secrets through the deployment settings.

🎯 Key Features
🖼️ Image upload through Streamlit
👁️ AI-based image understanding
✍️ Automatic short-story generation
🔊 AI-powered text-to-speech
⚡ Simple interactive web interface
🔐 API keys kept outside the source code
🤖 Multiple AI models working together in a single pipeline
📸 Application

The application provides three main outputs:

1. Image Scenario

The BLIP model generates a description of the uploaded image.

2. Generated Story

Gemini transforms the description into a short creative story.

3. Audio Narration

The generated story is converted into speech and played directly in the application.

🚀 Deployment

This project can be deployed using Streamlit Community Cloud.

The repository should contain the application's requirements.txt and the required project files. Streamlit Community Cloud installs the Python dependencies from the dependency file and allows API keys to be configured through its Secrets settings.

Typical deployment flow:

GitHub Repository
        │
        ▼
Streamlit Community Cloud
        │
        ├── Install dependencies
        ├── Configure secrets
        └── Run app.py
        │
        ▼
   Live Streamlit App

After deployment, Streamlit provides a shareable streamlit.app URL.

📚 What I Learned

Through this project, I explored:

Image captioning using BLIP
Working with pretrained Hugging Face models
Generative AI APIs
Prompt-based story generation
Text-to-speech models
Integrating multiple AI models into one application
Streamlit application development
Environment variables and API-key security
Deploying AI applications
🔄 AI Pipeline
              INPUT
                │
                ▼
          📷 Uploaded Image
                │
                ▼
        🤖 BLIP Image Model
                │
                ▼
       📝 Image Description
                │
                ▼
       ✨ Google Gemini
                │
                ▼
          📖 Short Story
                │
                ▼
          🔊 Kokoro TTS
                │
                ▼
          🎧 Audio Output
📌 Project Status

Working locally: ✅

The complete pipeline has been tested locally:

Image → BLIP → Gemini → Kokoro → Audio

Cloud deployment can be configured after pushing the project to GitHub.

🙏 Credits

This project is based on the original open-source project:

Image-to-Speech GenAI Tool Using LLM
Original repository by Gurpreet Kaur Jethra

Original repository:

https://github.com/GURPREETKAURJETHRA/Image-to-Speech-GenAI-Tool-Using-LLM

This version has been adapted for current AI services, updated API integrations, and personalized UI/branding for learning and portfolio purposes.

The original project's license is retained in the repository.

👩‍💻 Author

Mohammed Sumayya