---
title: 18.How to Run Ai locally on Your Pc
date: 2025-01-25
draft: 
tags:
  - AIML
  - basic
  - setup
Toc: true
---
---
### **Why Run AI Locally?**  
1. **Privacy**: Your data stays on your machine.  
2. **Cost**: No API fees or subscriptions.  
3. **Customization**: Tweak models to solve your unique problems.  
4. **Offline Access**: Use AI even without an internet connection.  

---

### **Step 1: Installing Ollama**  
Ollama works on Windows, macOS, and Linux. Here’s how to set it up:  

#### **For Windows (Preview)**:  
1. Download the [Ollama Windows installer](https://ollama.com/download).  
2. Run the `.exe` file and follow the prompts.  
3. Open PowerShell or Command Prompt and test with `ollama --version`.  

#### **For macOS/Linux**:  
1. Open Terminal and run this command:  
   ```bash  
   curl -fsSL https://ollama.ai/install.sh | sh  
   ```  
2. Verify the install: `ollama --version`.  

---

### **Step 2: Running Your First AI Model**  
Ollama has a library of pre-trained models. Let’s start with **Llama 2** (a popular open-source model by Meta):  

1. In your terminal, run:  
   ```bash  
   ollama run llama2  
   ```  
   *(This downloads the model—it’s ~4GB, so grab a coffee.)*  

2. **Chat with the model**:  
   ```  
   >>> Write a haiku about pizza  
   Crispy crust whispers,  
   Melting cheese hugs savory dreams—  
   Slice of heaven’s warmth.  
   ```  

**Other models to try**:  
- `mistral`: Fast and lightweight.  
- `codellama`: Specializes in code generation.  
- `phi3`: Microsoft’s small but powerful model.  

---

### **Step 3: Fine-Tuning Your Model**  
Fine-tuning lets you adapt a model to your specific tasks. For example, you could train it to:  
- Write in your brand’s voice.  
- Summarize medical reports.  
- Generate Python code for data analysis.  

#### **How to Fine-Tune with Ollama**:  
1. **Prepare Your Data**:  
   Create a `.txt` file with examples. For instance, if training a story-writing AI:  
   ```  
   [Prompt]: Write a fantasy story about a robot knight  
   [Response]: Sir Clank-a-Lot, a rusted but valiant robot, embarked on a quest to…  
   ```  

2. **Create a Modelfile**:  
   This configures the base model and your training data. Save this as `modelfile.txt`:  
   ```  
   FROM llama2  
   SYSTEM """You are a creative fantasy writer."""  
   MESSAGE user "Write a story"  
   MESSAGE assistant "Sir Clank-a-Lot..."  
   # Add more examples here  
   ```  

3. **Train the Model**:  
   Run:  
   ```bash  
   ollama create my-custom-model -f modelfile.txt  
   ```  

4. **Use Your Custom Model**:  
   ```bash  
   ollama run my-custom-model  
   ```  

---

### **Tips for Effective Fine-Tuning**  
- **Start Small**: Fine-tune with 10-20 examples first.  
- **Quality Over Quantity**: Use clear, diverse prompts/responses.  
- **Iterate**: Test the model, find weaknesses, and add more data.  

---

### **Advanced: Integrate Ollama with Other Tools**  
- **LangChain**: Build AI workflows (e.g., connect Ollama to a PDF parser).  
- **Docker**: Containerize your models for deployment.  
- **Ollama API**: Use `http://localhost:11434` to integrate with apps like Obsidian or VS Code.  

---

### **Running DeepSeek-R1 Locally with Ollama**  
DeepSeek-R1 is a standout model for technical tasks like code generation, debugging, and mathematical problem-solving. Here’s how to run and fine-tune it using Ollama:

---

### **Step 2 (Updated): Running Models like DeepSeek-R1**  
After installing Ollama, you can pull and run DeepSeek-R1 with ease:  

1. **Download DeepSeek-R1**:  
   Open your terminal and run:  
   ```bash  
   ollama run deepseek-r1  
   ```  
   *Note:* If the model isn’t listed publicly yet, you might need to pull it directly using its full name (e.g., `ollama run deepseek-ai/deepseek-r1`). Check the [Ollama model library](https://ollama.ai/library) for exact syntax.  

2. **Test Its Coding Skills**:  
   ```  
   >>> Write a Python function to calculate Fibonacci numbers recursively  
   ```  
   The model should generate:  
   ```python  
   def fibonacci(n):  
       if n <= 1:  
           return n  
       else:  
           return fibonacci(n-1) + fibonacci(n-2)  
   ```  

**Why DeepSeek-R1?**  
- Excels at **code generation** (Python, JavaScript, etc.).  
- Strong at **math/logic problems** (e.g., SAT questions, algebra).  
- Compact size compared to giants like GPT-4, making it ideal for local use.  

---

### **Step 3 (Updated): Fine-Tuning DeepSeek-R1**  
Let’s say you want to specialize DeepSeek-R1 for your company’s internal APIs or a niche programming language. Here’s how:  

#### **Example: Training It for Internal Code Conventions**  
1. **Prepare a Dataset**:  
   Create a `deepseek-data.txt` file with examples of code snippets paired with prompts:  
   ```  
   [Prompt]: Write a Python function to connect to our internal database API  
   [Response]: def connect_db(api_key):  
                   from internal_db import Client  
                   return Client(api_key, timeout=30)  
   ```  

2. **Create a Modelfile**:  
   Save this as `deepseek-modelfile.txt`:  
   ```  
   FROM deepseek-r1  
   SYSTEM """You are a senior Python developer for Acme Corp. Follow PEP8 and use internal libraries."""  
   MESSAGE user "Write a Python function to connect to our internal database API"  
   MESSAGE assistant "def connect_db(api_key):..."  
   # Add more coding examples  
   ```  

3. **Train Your Custom Model**:  
   ```bash  
   ollama create acme-coder -f deepseek-modelfile.txt  
   ```  

4. **Run and Test**:  
   ```bash  
   ollama run acme-coder  
   >>> How do I fetch user data from the database?  
   ```  
   The model should now generate code using your company’s conventions.  

---

### **Tips for Fine-Tuning DeepSeek-R1**  
- **Focus on Code Structure**: Provide examples with clear input/output patterns.  
- **Include Error Handling**: Train it to handle edge cases (e.g., `try/except` blocks).  
- **Use Small Batches**: Start with 10-15 high-quality code examples to avoid overload.  

---

### **Advanced Use Cases for DeepSeek-R1**  
1. **Documentation Generation**:  
   Fine-tune it to turn code comments into Markdown docs.  
2. **Math Tutoring**:  
   Train it to solve and explain calculus problems step-by-step.  
3. **CI/CD Automation**:  
   Integrate with GitHub Actions to review pull requests locally.  

---

### **Performance Notes**  
- **Hardware Requirements**: DeepSeek-R1 runs well on 16GB RAM, but GPU acceleration (e.g., NVIDIA) speeds up inference.  
- **Quantized Versions**: Look for `deepseek-r1:4b-q4` for lighter-weight usage on low-end machines.  

---

### **Final Thoughts**  
DeepSeek-R1 turns your local machine into a coding powerhouse. Whether you’re automating workflows, tutoring yourself in math, or enforcing code standards, Ollama’s simplicity lets you experiment without cloud costs.  

**Pro Tip**: Combine DeepSeek-R1 with Ollama’s API (`http://localhost:11434`) and tools like **VS Code** or **PyCharm** for a seamless coding assistant.  

---
[Crusveder]