<h1 aling=center>Training a Question and Answer model using BERT on SQUAD dataset</h1>

<img width="839" align=center alt="image" src="https://github.com/user-attachments/assets/b6d70952-fada-42cd-afe3-782a2e33edea" />


## Overview
This project implements a Question Answering (QnA) model using BERT (Bidirectional Encoder Representations from Transformers) on the Stanford Question Answering Dataset (SQuAD) 2.0. The model is trained to extract precise answer spans from given contexts based on input questions.

## Features

- Fine-tuned BERT model for question answering
- Uses SQuAD 2.0 dataset for training and validation
- Custom preprocessing and tokenization
- Evaluation metrics including Exact Match and F1 Score
- Supports inference on custom contexts and questions

## Requirements

- Python 3.7+
- PyTorch
- Transformers
- torchtext
- matplotlib

`pip install torch==2.3.0 torchtext==0.18.0 transformers==4.37.2 matplotlib`

## Approach
**Data Preprocessing**
- Load SQuAD 2.0 dataset
- Tokenize contexts and questions using pre-trained bert tokenizer
- Convert character-level answer positions to token-level positions

**Model**
- Used Pre-trained BERT base uncased model
- Fine-tuned for question answering task using the preprocessed SQUAD2 Datatset
- Uses AdamW optimizer

**Training**
- 5 epochs of training, Batch size of 8
- Learning rate of 5e-5

<img width="550" alt="image" src="https://github.com/user-attachments/assets/33287fe6-4359-47fb-a12c-12d13d15cb12" />


**Inference**
- Perform inference against the ground truth answers and calculate the Exact Match and F1 Score for final evaluation.

## Setup Instructions
1. Clone the repository or download the notebook file.
2. Open the notebook in Jupyter Notebook or JupyterLab.
3. Run the initial setup cells to install the required libraries:
   ```python
   #!pip uninstall -q -y torch torchtext
   #!pip install -q torch==2.3.0 torchtext==0.18.0 torchdata portalocker==2.10.0
   #!pip install -q transformers==4.37.2
   ```

## Conclusion
This project aims at demonstrating the foundational steps for implementing transformer-based models. By following the instructions, you can replicate the results and further enhance the model's capabilities for NLP tasks.

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
