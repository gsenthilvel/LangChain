# Integration of 2 AI frameworks OpenAI+HuggingFace using LangChain 

A brief description of initial hands-on experience in AI LangChain technologies.


## Technial definition of LangChain

Based on my learning, the logical architecture of LangChain is represented at https://drive.google.com/file/d/1XG_AE7iqHZjgg8rM-Fxr_2Rm1VHL_R3I/view

In a nutshell, LangChain connects the industry popular Large Language Models such as OpenAI and HuggingFace Hub, to few external sources like external files, Database, Google, Wikipedia and Wolfram.

## Implementation Steps

#### Step 0: Pre-requiste
* Install python libraries using pip command
* Store your OpenAI API keys in environment variables

#### Step 1: Importing the libraries
```python
from langchain.llms import OpenAI, HuggingFaceHub
```

#### Step 2: Loading the environment variables
```python
import os
my_ai_key = os.getenv('OPENAI_API_KEY')
my_hugg_key = os.getenv('HUGGINGFACEHUB_API_TOKEN')
```

#### Step 3: Creating the common query to be used
```python
input_text = "Who is Indira Gandhi?"
```

#### Step 4: First LLM - OpenAI integration
```python
llm_1 = OpenAI(model_name='text-davinci-003')

llm_1_output = llm_1(input_text)
print(llm_1_output)
```

### First LLM Output
```python
Indira Gandhi (1917-1984) was an Indian stateswoman and the first and only female Prime Minister of India. She served as Prime Minister from 1966 to 1977 and again from 1980 until her assassination in 1984. She was a central figure of the Indian National Congress party, and was known for her political ruthlessness and unprecedented centralisation of power. She is considered one of the most powerful female leaders of the 20th century.
```

#### Step 5: Second LLM - HuggingFace integration
```python
llm_2 = HuggingFaceHub(
    repo_id="google/flan-t5-base",
    model_kwargs={"temperature":0.7, "max_length":64},
    verbose=True
)

llm_2_output = llm_2(input_text)
print(llm_2_output)
```

### Second LLM Output
```python
c:\Python311\Lib\site-packages\tqdm\auto.py:21: TqdmWarning: IProgress not found. Please update jupyter and ipywidgets. See https://ipywidgets.readthedocs.io/en/stable/user_install.html
  from .autonotebook import tqdm as notebook_tqdm
nanda gandhi
```

## Author

- [Ganesan Senthilvel](https://github.com/gsenthilvel/)


## License

[MIT](https://choosealicense.com/licenses/mit/)


## Acknowledgements

 - [Official Documentation](https://langchain-langchain.vercel.app/docs/get_started)
 - [Offiial GitHub Repo](https://github.com/hwchase17/langchain)
 - [Official Tweets](https://twitter.com/hwchase17)
