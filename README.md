## What is MFCS?  
MFCS (Model Function Calling Standard) is an open-source standard protocol designed to facilitate interaction between LLMs (Large Language Models) and external tools. It defines how to invoke external tools and process their returned results. The protocol primarily addresses the following issues:  

- **Compatibility Issues**: Different LLMs have inconsistent Function Calling interfaces, requiring repeated adaptation when switching models.  
- **Feature Deficiency**: Some LLMs (e.g., DeepSeek R1, ChatGPT O3) do not support Function Calling.  
- **Development Efficiency**: Business development requires adjusting Function Calling logic for different models, increasing maintenance costs.  
- **Scalability Limitations**: Existing Function Calling solutions have constraints in tool quantity, invocation flexibility, monitoring capabilities, etc.  

## Overall Architecture  
![Local Image](./images/architecture.png)  

MFCS ("Model Function Calling Standard")—here’s a more precise understanding of the architecture diagram:  

### Architecture Overview  

This diagram illustrates a system architecture centered around a Large Language Model (LLM), highlighting its interactions with the memory module, Model Function Calling Standard (MFCS), and various tools.  

### Detailed Component Explanations  

#### 1. **LLM (Large Language Model)**  
The LLM serves as the intelligent core of the system, such as GPT-4, ERNIE Bot, etc. Trained on vast text data, it can generate natural language text, understand user intent, and more.  

#### 2. **Memory (Memory Module)**  
The memory module is critical for the LLM. It stores contextual information from conversations, such as previous user queries and model responses. This allows the LLM to reference past interactions when processing new inputs, ensuring more coherent and context-aware replies.  

#### 3. **MFCS (Model Function Calling Standard)**  
The Model Function Calling Standard is a protocol that coordinates interactions between the LLM and external tools. It defines how the LLM invokes tool functions and processes their results. Through MFCS, the LLM can leverage external tools to enhance its capabilities.  

#### 4. **Tools**  
- **MCP**: A Model Context Protocol introduced by Claude for third-party tool integration.  
- **OpenAPI**: Typically refers to open Application Programming Interfaces that enable interaction and data sharing between software systems. In this architecture, the LLM can use MFCS to call OpenAPIs for external services, such as fetching weather data or stock information.  
- **Python**: As a powerful programming language, Python offers extensive libraries and frameworks. Here, the LLM can use MFCS to execute Python scripts for complex tasks like data analysis or machine learning model training.  

### Interaction Flow  

The LLM interacts bidirectionally with memory—reading stored information and writing new data. The combined data from the LLM and memory is processed via MFCS, which then invokes the appropriate tools (e.g., MCP, OpenAPI, Python) to fulfill specific tasks.  

This architectural design enables the LLM to harness external tools effectively, expanding its application scope and improving its ability to handle complex tasks.  
