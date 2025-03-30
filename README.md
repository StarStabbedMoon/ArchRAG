<div align="center">

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](./LICENSE)    [![support: Ollama](https://img.shields.io/badge/Support-Ollama-green.svg)](https://ollama.com/)    [![support: LlamaIndex](https://img.shields.io/badge/Support-LlamaIndex-purple.svg)](https://www.llamaindex.ai/)   

</div>

### Table of Contents

- [Overview](#What-is-ArchRAG)
- [Model Support](#Support-Models)
- [Quick Start](#quick-start)
- [License](#License)

<div id='What-is-ArchRAG'></a>

# ArchRAG

ArchRAG is a deployment of ThinkRAG with architectural codes preloaded into the system.

https://github.com/wzdavid/ThinkRAG

<div id='Support-Models'></a>

# Model Support

ThinkRAG and ArchRAG can use all models supported by the LlamaIndex data framework. For model list information, please refer to [relevant documentation](https://docs.llamaindex.ai/en/stable/module_guides/models/llms/modules/). 

This application supports OpenAI API and all compatible LLM APIs. If you want to deploy LLMs locally you may use Ollama. We can download models to run locally through Ollama. ArchRAG was tested using Ollama with Gemmma.

## Known Issues

Currently, there are issues from Windows users that have not been resolved.

Due to incompatibility between llama_index and the latest ollama 0.4, please install ollama 0.3.3, which is reflected in the requirements.txt file.

<div id='quick-start'></a>

# Quick Start

## Step 1 Download and Installation

After downloading the code from Github, use pip to install the required components.
```zsh
pip install -r requirements.txt
```
If you want to run the system offline, please first download Ollama from the official website. Then, use the Ollama command to download LLMs such as DeepSeek, Qwen, and Gemma.

Then, download the embedding model (BAAI/bge-large-en-v1.5) and reranking model (BAAI/bge-reranker-base) from Hugging Face to the `localmodels` directory.

For specific steps, please refer to the document in the `docs` directory: HowToDownloadModels.md

## Step 2 System Configuration

For better performance, it is recommended to use commercial LLM APIs.

First, obtain the API key from the LLM service provider and configure the following environment variables.

```zsh
OPENAI_API_KEY = ""
DEEPSEEK_API_KEY = ""
MOONSHOT_API_KEY = ""
ZHIPU_API_KEY = ""
```

You can skip this step and configure the API keys through the application interface after the system is running.

If you choose to use one or more LLM APIs, please delete the unused service providers in the config.py configuration file.

ThinkRAG runs in development mode by default. In this mode, the system uses local file storage, and you do not need to install any databases.

If you want to switch to production mode, you can configure the environment variables as follows.

```zsh
THINKRAG_ENV = production
```

In production mode, the system uses vector databases Chroma or LanceDB, and key-value databases Redis.

If you do not have Redis installed, it is recommended to install it through Docker or use an existing Redis instance. Please configure the parameters of the Redis instance in the config.py file.

## Step 3 Running the System

Please run the following command in the directory containing the app.py file.

```zsh
streamlit run app.py
```

The system will run and automatically open the following URL in the browser to display the application interface.

http://localhost:8501/

The first run may take a moment. If you have not downloaded the embedding model from Hugging Face in advance, the system will automatically download the model, which will take a longer time.

<div id='License'></a>

# License

ThinkRAG uses the [MIT License](LICENSE).
