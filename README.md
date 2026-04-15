# End_To_End_Chatbot-Q_A-
# 🤖 LangChain Demo with TinyLlama (Streamlit App)

A modern Streamlit-based chatbot application that integrates LangChain with the TinyLlama model running locally through Ollama.

This project demonstrates how to build a lightweight local AI assistant with prompt templates, output parsing, and an interactive UI.

---

# 🚀 Features

* 🔗 Built using LangChain Expression Language (LCEL)
* 🧠 Uses TinyLlama locally via Ollama
* 💬 Interactive Streamlit web interface
* ⚡ Real-time question answering
* 🧩 Prompt templates with system + user roles
* 🛡️ Local inference (no internet required after setup)
* 🎨 Clean and beginner-friendly UI

---

# 📸 Demo Preview

## Home Screen

```text
+------------------------------------------------+
| LangChain + TinyLlama Chatbot                  |
|------------------------------------------------|
| Ask me anything:                               |
| [ What is Artificial Intelligence?         ]   |
|                                                |
|                [ Submit ]                      |
|                                                |
| Response:                                      |
| AI is the simulation of human intelligence...  |
+------------------------------------------------+
```

## Example Output

### Input

```text
What is Artificial Intelligence?
```

### Output

```text
Artificial Intelligence (AI) is the simulation of human intelligence in machines. These systems can learn, reason, solve problems, and make decisions similar to humans.
```

---

# 🖼️ Suggested Demo GIF / Screenshot Section

Add screenshots inside a `screenshots/` folder:

```text
project/
│── screenshots/
│   ├── home.png
│   ├── output.png
│   └── demo.gif
```

Then include them in your README:

```markdown
## Demo

![Home Screen](screenshots/home.png)

![Model Response](screenshots/output.png)

![Demo GIF](screenshots/demo.gif)
```

---

# 📁 Project Structure

```text
LangChain-TinyLlama-App/
│
├── app.py
├── .env
├── requirements.txt
├── README.md
└── screenshots/
    ├── home.png
    ├── output.png
    └── demo.gif
```

---

# ⚙️ Installation

## 1️⃣ Clone the Repository
git clone https://github.com/amisha8o/End_To_End_Chatbot-Q_A-.git
cd End_To_End_Chatbot-Q_A-
LIVE DEMO: https://your-live-demo-link.com


## 2️⃣ Create Virtual Environment

### Windows

```bash
python -m venv venv
venv\Scripts\activate
```

### Mac/Linux

```bash
python -m venv venv
source venv/bin/activate
```

---

## 3️⃣ Install Dependencies

```bash
pip install -r requirements.txt
```

Or manually:

```bash
pip install langchain langchain-core langchain-community streamlit python-dotenv ollama
```

---

# 🧠 Install Ollama and TinyLlama

## Install Ollama

Download and install Ollama from:

```text
https://ollama.com
```

## Pull the TinyLlama Model

```bash
ollama pull tinyllama
```

Verify the model:

```bash
ollama list
```

Expected output:

```text
NAME         ID              SIZE
 tinyllama    xxxxxxxx        637 MB
```

---

# 🔑 Environment Variables

Create a `.env` file:

```env
LANGCHAIN_API_KEY=your_api_key_here
LANGCHAIN_TRACING_V2=true
LANGCHAIN_PROJECT=TinyLlamaDemo
```

---

# ▶️ Run the Application

```bash
streamlit run app.py
```

After running, Streamlit will open automatically in your browser.

Usually at:

```text
http://localhost:8501
```

---

# 🖥️ How the Output Looks

When you enter a query:

```text
Explain Machine Learning in simple words
```

The app displays:

```text
Machine Learning is a branch of AI where computers learn from data instead of being directly programmed. For example, a spam filter learns which emails are spam by analyzing many examples.
```

---

# 🧩 Code Workflow

```text
User Input
    ↓
Prompt Template
    ↓
TinyLlama via Ollama
    ↓
Output Parser
    ↓
Streamlit UI Response
```

---

# 💻 Example app.py

```python
import streamlit as st
from langchain.prompts import ChatPromptTemplate
from langchain_community.llms import Ollama
from langchain_core.output_parsers import StrOutputParser

st.title("🤖 LangChain + TinyLlama Chatbot")

query = st.text_input("Ask me anything:")

prompt = ChatPromptTemplate.from_messages([
    ("system", "You are a helpful AI assistant."),
    ("user", "Question: {question}")
])

llm = Ollama(model="tinyllama")
output_parser = StrOutputParser()

chain = prompt | llm | output_parser

if query:
    response = chain.invoke({"question": query})
    st.write("### Response")
    st.success(response)
```

---

# 📦 requirements.txt

```text
langchain
langchain-core
langchain-community
streamlit
python-dotenv
ollama
```

---

# 🛠️ Tech Stack

* Python
* LangChain
* Streamlit
* Ollama
* TinyLlama

---

# 🔥 Future Improvements

* Add chat history
* Add memory using ConversationBufferMemory
* Support multiple models (Llama3, Mistral, Gemma)
* Add dark/light theme toggle
* Add speech-to-text input
* Deploy using Streamlit Cloud or Docker

---

# 🧪 Future Version Output Example

```text
You: What is Python?

Bot: Python is a high-level programming language known for its simple syntax and wide use in web development, AI, automation, and data science.
```

---

# ⚠️ Important Notes

* Ollama must be running locally before starting Streamlit
* TinyLlama model must already be downloaded
* Internet is not required after installation
* If the app shows "Connection Error", restart Ollama:

```bash
ollama serve
```

---

# 📄 License

This project is open-source and available under the MIT License.

---

# 🙌 Acknowledgements

* LangChain
* Ollama
* Streamlit
* TinyLlama
