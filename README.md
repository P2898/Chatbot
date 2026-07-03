This project demonstrates how to build and host your own AI-powered chatbot web applications using two different approaches:

Cloud-Based API: Using OpenAI's API.
Local Open-Source LLM: Using Hugging Face's Transformers and a local model (Microsoft's Phi-4-mini-instruct).
Both versions use Streamlit to provide a clean, ChatGPT-like web interface, and utilize localtunnel to expose the application to the internet, making it easy to run on platforms like Google Colab.

Features
1. Two different AI backends (OpenAI API and Local Hugging Face model).
2. Interactive chat UI powered by Streamlit.
3. Easy public access using Localtunnel.
   
Prerequisites
To run this project locally or in a cloud environment (like Google Colab), you will need:

Python 3.8+
Node.js (for localtunnel)
Required Python Packages
Depending on which version of the app you run, you will need to install specific dependencies.

For the OpenAI version:
bash
pip install openai python-dotenv streamlit

For the Hugging Face version:
bash
pip install transformers torch streamlit

Required Node Packages
For exposing the app to the internet:

bash
npm install -g localtunnel

1. OpenAI Chatbot (app_openai.py)
This version connects to the OpenAI API (using gpt-4o-mini) to generate responses.

Setup
Create a .env file in the root directory.
Add your OpenAI API key to the .env file:
env

OPENAI_API_KEY=your_actual_api_key_here
(If using Jupyter Notebook) The code is available to automatically generate app_openai.py.

Run the Streamlit application:
bash
streamlit run app_openai.py

2. Local Open-Source Chatbot (app_huggingface.py)
This version runs a local LLM (microsoft/Phi-4-mini-instruct) using the Hugging Face Transformers library. Note: A GPU is highly recommended for running this model efficiently.

Setup
(If using Jupyter Notebook) The code is available to automatically generate app_huggingface.py.

Run the Streamlit application:
bash
streamlit run app_huggingface.py
(Note: If you run into Hugging Face token warnings, you can optionally authenticate your environment using a Hugging Face token).

Accessing the Apps via Localtunnel
If you are running these scripts on a remote server or Google Colab and want to access them via a public URL, you can tunnel the Streamlit port (default 8501) using Localtunnel.

Find your public IP address (required by localtunnel for security purposes):
bash

curl ipv4.icanhazip.com
Start the tunnel on the Streamlit port:

bash
npx localtunnel --port 8501

Visit the URL provided by localtunnel, and enter the IP address you found in step 1.
