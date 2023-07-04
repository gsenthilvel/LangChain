
# LangChain PDF Integration

A brief description of initial hands-on experience in AI LangChain technologies.


## Technial definition of LangChain

Based on my learning, the logical architecture of LangChain is represented at https://drive.google.com/file/d/1XG_AE7iqHZjgg8rM-Fxr_2Rm1VHL_R3I/view

In a nutshell, LangChain connects the industry popular Large Language Models such as OpenAI and HuggingFace Hub, to few external sources like external files, Database, Google, Wikipedia and Wolfram.

## Implementation Steps

#### Step 0: Pre-requiste
* Install python libraries using pip command
* Store your OpenAI API keys in environment variables

#### Step 1: Importing Libraries

```python
from langchain.document_loaders import UnstructuredPDFLoader
from langchain.text_splitter import RecursiveCharacterTextSplitter
```

#### Step 2: Loading PDF data

```python
loader = UnstructuredPDFLoader ("TopK_Ganesan.pdf")
data = loader.load()
```

#### Step 3: Split text similar to MapReduce

```python
text_splitter = RecursiveCharacterText Splitter (chunk_size=1000, chunk_overlap)
text = text_splitter.split_documents(data)
```

#### Step 4: Vectorizing using Pinecone

```python
docsearch = Pinecone.from_texts(
    [data_source.page_content for data_source in split_text], 
    ai_embeddings, index_name=myindex)
```

#### Step 5: Prompt query using OpenAI

```python
llm = OpenAI(temperature=0, openai_api_key)
chain = load_qa_chain(llm, chain_type="stuff")
```

#### Step 6: Intellectual query in PDF

```python
query = "What is the recommended next steps in this research?"
d=docsearch.similarity_search(query)
chain.run (input_documents=d, question=query)
```
### Final Output
```python
' The recommended next step is to extend the existing analysis pattern to the rest of commonly available financial stock exchange data.'
```

## Demo

Detailed walk through video demo is available at

## Author

- [Ganesan Senthilvel](https://github.com/gsenthilvel/)


## License

[MIT](https://choosealicense.com/licenses/mit/)


## Acknowledgements

 - [Official Documentation](https://langchain-langchain.vercel.app/docs/get_started)
 - [Offiial GitHub Repo](https://github.com/hwchase17/langchain)
 - [Official Tweets](https://twitter.com/hwchase17)
