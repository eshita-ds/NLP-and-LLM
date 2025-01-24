# RAG based chatbot for PDFs using Langchain and OpenAI

## Introduction
Large Language Models (LLMs) are increasingly adopted for diverse applications, and their ability to provide accurate responses is critical. Retrieval-Augmented Generation (RAG) enhances LLM performance by combining retrieval-based and generation-based techniques. RAG retrieves relevant information from an external knowledge base using semantic search and feeds it into the LLM alongside the query, enabling more accurate and informed responses while reducing hallucinations. This project employs Chroma DB for managing embeddings and LangChain for integrating LLMs with external data sources.

This project aims to develop a system where users can upload PDF documents and ask questions based on their content. It integrates OpenAI’s ChatGPT with retrieval mechanisms to deliver accurate, contextually relevant answers.

## Architecture

The system architecture for the RAG LLM part is composed of several key components:
- PDF Ingestion and Parsing: Tools and methods to upload and convert PDF documents into a format suitable for processing by the language model.
- Retrieval Mechanism: A system to search and retrieve relevant passages from the processed documents, using Chroma DB.
- Generative Model (ChatGPT): A pre-trained language model that generates responses based on the retrieved information. Used Gpt 3.5 turbo and later this model is finetuned using JSONL file. For this created an account on Open AI and made an API key to have access to the models.
- Integration with LangChain: Utilizing LangChain to streamline the interaction between retrieval and generation components to ensure smooth and coherent responses.

## Approach

This code implements a Retrieval-Augmented Generation (RAG) pipeline using LangChain for chaining components and OpenAI’s GPT-3.5-turbo for generating context-aware answers. Key steps include:
- Language Model Initialization: The model ChatOpenAI (GPT-3.5-turbo) is configured with a low temperature (0) to produce deterministic and focused responses.
- RAG Chain Setup: A RetrievalQA chain is created to integrate the retriever with the language model. This chain allows the model to generate answers based on retrieved context and trace their origins.
- Retriever Component: The retriever searches relevant documents in response to user queries, using semantic similarity to fetch accurate information.
- Custom Prompt Template: A structured template defines how retrieved context and user queries are formatted during runtime to ensure well-formed answers.
- Answer with Sources: The chain is configured to return both the answer and the source documents, enabling traceability of the generated responses.
- Query Handling: A get_response function processes user questions by invoking the RAG chain, retrieving responses, and extracting answers to present them back to the user.
- Use Case: This setup supports answering user queries based on uploaded PDF documents, providing accurate and contextually relevant answers by integrating retrieval mechanisms with GPT-3.5-turbo.

This approach ensures precise, traceable, and context-rich responses, ideal for document-driven question-answering applications.

## Model Testing & Evaluation

Testing and Prompt Optimization
- The RAG model was tested on various queries to evaluate the accuracy and relevance of responses.
- Different prompt variations were used, and the most effective prompt across all queries was selected.

**Performance Metric: ROUGE Score**
- ROUGE (Recall-Oriented Understudy for Gisting Evaluation) measures text response quality by comparing n-gram overlaps with reference text.
- ROUGE-1: Measures unigram (single-word) overlap.
- ROUGE-2: Measures bigram (two-word sequence) overlap, reflecting coherence.
- ROUGE-L: Captures the longest common subsequences (LCS), focusing on word order.
- ROUGE-Lsum: Evaluates overall sequence similarity and coherence at the summary level.

**Implementation and Results**
- ROUGE scores were calculated using rouge_score and torchmetrics libraries.
- Combined results for 15 questions:
- ROUGE-1 F-measure: 0.7885 (moderate word overlap).
- ROUGE-2 F-measure: 0.6735 (moderate bigram overlap).
- ROUGE-L F-measure: 0.7360 (sequence similarity).
- ROUGE-Lsum F-measure: 0.7738 (summary-level alignment).

**Observations**
- While responses captured key content, there were mismatches in exact word matches and phrase structures.
- Results were organized in a DataFrame format for better understanding, displaying questions, generated answers, and original reference answers.

**Output**

<img width="650" alt="image" src="https://github.com/user-attachments/assets/7267c264-1ed5-4e52-a41d-7350ad1a1fc6" />

## Fine Tuning

The fine-tuning process for OpenAI’s gpt-3.5-turbo begins with preparing a custom dataset in JSONL format (finetune.jsonl). The process involves initializing the OpenAI client with an API key, uploading the dataset, retrieving the file ID, and creating a fine-tuning job for the model. Details of the fine-tuning job are fetched, and the most recent 10 fine-tuning jobs are listed to track progress. Fine-tuning enhances the model’s performance for tasks aligned with the training data, and the job status can be monitored via the OpenAI site or script output.

Once fine-tuned, the model is integrated into a Retrieval-Augmented Generation (RAG) pipeline. A new RetrievalQA chain is set up using the fine-tuned model (ft:gpt-3.5-turbo-0125:personal::AavzugSw). The model is initialized with a temperature value of 0 to ensure deterministic and precise outputs. The chain combines a retriever that searches for relevant documents and the language model to generate responses based on the retrieved context. It is designed to return both the generated answers and their source documents, ensuring transparency and traceability. Custom prompt templates are used to dynamically structure the interaction by inserting the retrieved context and user queries during runtime.

The get_response function manages user interactions by invoking the RAG chain with the query, retrieving the response, and returning the answer. This setup enables accurate, well-formed answers tailored to the uploaded PDF content and the custom fine-tuned model.

<img width="600" alt="image" src="https://github.com/user-attachments/assets/60f8cb41-30b1-4c22-876b-2a794a2a2ad7" />

## Conclusion
From the results of the fine-tuned model, we can conclude that extensive data is needed to tune the exiting LLM. Creating data manually using the currently available knowledge base is a very cumbersome process. As visible from the results above, ROGUE scores were at par or showed a minor improvement for some questions. However, for others, the performance was not as expected, and it was better with the baseline gpt-turbo-3.5 model.
We achieved an overall rougeLsum_precision of 80% with our baseline model and prompts. However, to tune it further, a large corpus of data might be needed. The difference observed in the original vs result answers is mainly because of the sentence formations. Numerical metrics match across the board.

## License
MIT License

Copyright (c) 2024 Eshita Gupta

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
