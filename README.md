# Document-Based Search Engine

## Overview
This project implements a simple search engine that indexes and retrieves information from a document or a set of documents. It allows users to input queries and returns the most relevant sections based on semantic similarity or keyword matching.

## Installation

```bash
pip install requests pandas scikit-learn jupyter
```

Start jupyter:

```bash
jupyter notebook
```

Download the data:

```python
import requests 

docs_url = 'https://github.com/alexeygrigorev/llm-rag-workshop/raw/main/notebooks/documents.json'
docs_response = requests.get(docs_url)
documents_raw = docs_response.json()

documents = []

for course in documents_raw:
    course_name = course['course']

    for doc in course['documents']:
        doc['course'] = course_name
        documents.append(doc)
```

Creating the dataframe:

```python
import pandas as pd

df = pd.DataFrame(documents, columns=['course', 'section', 'question', 'text'])
df.head()
```
