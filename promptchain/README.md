# Integration of Prompt Template of LLM Chain using LangChain 

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
from langchain import PromptTemplate, LLMChain
from langchain.llms import OpenAI
from langchain.chains import SimpleSequentialChain
```

#### Step 2: Loading the environment variables
```python
import os
my_ai_key = os.getenv('OPENAI_API_KEY')
```

#### Step 3: OpenAI LLM using text-davinci-003 model
```python
llm_ai = OpenAI(model_name='text-davinci-003')
```

#### Step 4: Setting up the prompt template with 4 chains 
```python
prompt_1 = PromptTemplate(
    template="What is the {type} democracy country in the world?",
    input_variables=["type"],
)
chain_1 = LLMChain(llm=llm_ai, prompt=prompt_1)

prompt_2 = PromptTemplate(
    template="Who is the first president of {country}?",
    input_variables=["country"],
)
chain_2 = LLMChain(llm=llm_ai, prompt=prompt_2)

prompt_3 = PromptTemplate(
    template="When was {input_president} born?",
    input_variables=["input_president"],
)
chain_3 = LLMChain(llm=llm_ai, prompt=prompt_3)

prompt_4 = PromptTemplate(
    template="Where was {input_president} born?",
    input_variables=["input_president"],
)
chain_4 = LLMChain(llm=llm_ai, prompt=prompt_4)
```

#### Step 5: Configuring in a sequential chain
```python
full_chain = SimpleSequentialChain(
    chains=[chain_1, chain_2, chain_3, chain_4],
    verbose=True
)
```

#### Step 6: Displaying the executed chains results
```python
print(full_chain.run("largest"))
```

### Final Output
```python

> Entering new SimpleSequentialChain chain...


India is the largest democracy country in the world. It is a federal republic comprising of 29 states and seven union territories. It has the second largest population in the world, and is the world's most populous democracy.


The first President of India was Dr. Rajendra Prasad, who served from 1950 to 1962. He was the only President to be elected twice to the highest office in the country.


Dr. Rajendra Prasad was born on 3 December 1884 in Siwan district of Bihar, India.


Siwan district of Bihar, India

> Finished chain.


Siwan district of Bihar, India
```

## Author

- [Ganesan Senthilvel](https://github.com/gsenthilvel/)


## License

[MIT](https://choosealicense.com/licenses/mit/)


## Acknowledgements

 - [Official Documentation](https://langchain-langchain.vercel.app/docs/get_started)
 - [Offiial GitHub Repo](https://github.com/hwchase17/langchain)
 - [Official Tweets](https://twitter.com/hwchase17)
