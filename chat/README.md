# LangChain Open AI Chat Integration

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
from langchain.chat_models import ChatOpenAI
from langchain.schema import HumanMessage, SystemMessage
```

#### Step 2: Loading the environment variables

```python
import os
my_ai_key = os.getenv('OPENAI_API_KEY')
```

#### Step 3: Instantiating ChatOpenAI class with temperature

```python
chat = ChatOpenAI(temperature=0.7, openai_api_key=my_ai_key)
```

#### Step 4: Setting up chat API with system and human message

```python
chat (
    [
        SystemMessage(content="You are a nice AI bot that helps a user figure out where to travel in one short sentence"),
        HumanMessage(content="I like the long beaches where should I go in Tamilnadu India?")
    ]
)
```

### Final Output
```python
AIMessage(content='You should visit Marina Beach in Chennai, Tamil Nadu, which is one of the longest urban beaches in the world.', additional_kwargs={}, example=False)
```

## Author

- [Ganesan Senthilvel](https://github.com/gsenthilvel/)


## License

[MIT](https://choosealicense.com/licenses/mit/)


## Acknowledgements

 - [Official Documentation](https://langchain-langchain.vercel.app/docs/get_started)
 - [Offiial GitHub Repo](https://github.com/hwchase17/langchain)
 - [Official Tweets](https://twitter.com/hwchase17)
