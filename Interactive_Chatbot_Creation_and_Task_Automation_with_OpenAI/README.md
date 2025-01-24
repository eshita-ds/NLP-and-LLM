# Interactive Chatbot creation and Task automation with OpenAI

## Introduction
The project involved using OpenAI API and Langchain to create a chatbot that is capable of handling a sequence of chats and ability summarize the entire chat at the end of the session. The tasks involved solving a complex Maths problem, parse a PDF or Website and answer questions about the content or combine information from multiple sources and provide intelligent responses.

The code is a demonstration of interacting with the OpenAI ChatGPT API, showcasing a sophisticated, multi-step conversational approach that combines several key functionalities:

- Complex mathematical problem solving
- Document extraction and analysis
- Content rewriting for specific audiences
- Interactive Q&A generation
- Conversation summarization

## Approach
- Problem Solving - Uses RAG Database to pass context to LLM to allow solving complex mathematic problems.
- Multi-Source Document Analysis
  - PDF text extraction using pdfplumber or Website content scraping with BeautifulSoup
  - Combines and processes content from different sources & Rewrites content based on context specification
- Interactive Question-Answering
  - Generates targeted questions about the extracted content by passing context using a RAG database and using a Langchain pipeline
  - Demonstrates ability to interpret and explain complex topics
- Conversation Management
  - Maintains a full conversation history
  - Generates a comprehensive summary of the entire interaction
 
**Key Python Libraries Used**

- openai: For API interactions
- pdfplumber: PDF text extraction
- requests: Web content retrieval
- BeautifulSoup: HTML parsing
- pandas: Data manipulation and visualization

## Prerequisites
- Python 3.9+
- **Required libraries:**
  - openai
  - pdfplumber
  - requests
  - beautifulsoup4
  - pandas
 
`pip install openai pdfplumber requests beautifulsoup4 pandas`

## Sample Outputs

|QnA Based on multiple sources|Problem Solving|
|---|---|
|<img width="806" alt="image" src="https://github.com/user-attachments/assets/f75f4728-309b-456c-8912-e2487d853148" />|<img width="1131" alt="image" src="https://github.com/user-attachments/assets/55ee609c-bbda-41dc-9091-4f2aca7f5f15" />|



## How to Run ?
- Set up your OpenAI API key
- Ensure 'Integers.pdf' is in the same directory
- Run the Jupyter Notebook cells sequentially

**Note:** Requires a valid OpenAI API key, You can customize content and questions as needed.

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
