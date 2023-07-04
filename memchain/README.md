# Integration of OpenAI in-memory ConversationChain using LangChain 

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
from langchain import OpenAI, ConversationChain
from langchain.llms import OpenAI
```

#### Step 2: Loading the environment variables
```python
import os
my_ai_key = os.getenv('OPENAI_API_KEY')
```

#### Step 3: Setting up OpenAI integration
```python
llm_ai = OpenAI(model_name='text-davinci-003')
```

#### Step 4: Instantiating in-memory ConversationChain 
```python
mem_chain = ConversationChain(
    llm=llm_ai,
    verbose=True
)
```

#### Step 5: Adding a conversation to the chain
```python
mem_chain.predict(input="Hi, I'm Ganesan Senthilvel from Princeton, NJ")
mem_chain.predict(input="Howlong will it take to finish PhD in Computer Science?")
mem_chain.predict(input="What is the longest beach in the world?")
mem_chain.predict(input="What is my name?")
```

### Final Output
```python
> Entering new ConversationChain chain...
Prompt after formatting:
The following is a friendly conversation between a human and an AI. The AI is talkative and provides lots of specific details from its context. If the AI does not know the answer to a question, it truthfully says it does not know.

Current conversation:
Human: Hi, I'm Ganesan Senthilvel from Princeton, NJ
AI:  Hi Ganesan! It's nice to meet you. I understand that you are from Princeton, NJ. Can you tell me a bit about the city?
Human: Howlong will it take to finish PhD in Computer Science?
AI:  That's a great question! The answer depends on a number of factors, such as the university you attend, the specific program requirements, and the amount of time you can dedicate to your studies. Generally, a PhD in Computer Science can take anywhere from 3-7 years to complete.
Human: What is the longest beach in the world?
AI:  The longest beach in the world is Praia do Cassino Beach in Brazil, which stretches for over 200 miles.
Human: What is my name?
AI: Your name is Ganesan Senthilvel

> Finished chain.
```

## Author

- [Ganesan Senthilvel](https://github.com/gsenthilvel/)


## License

[MIT](https://choosealicense.com/licenses/mit/)


## Acknowledgements

 - [Official Documentation](https://langchain-langchain.vercel.app/docs/get_started)
 - [Offiial GitHub Repo](https://github.com/hwchase17/langchain)
 - [Official Tweets](https://twitter.com/hwchase17)
