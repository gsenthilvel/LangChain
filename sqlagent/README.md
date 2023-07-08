# Integration of AWS RDS Postgres database with OpenAI using LangChain 

A brief description of initial hands-on experience in AI LangChain technologies.


## Technial definition of LangChain

Based on my learning, the logical architecture of LangChain is represented at https://drive.google.com/file/d/1XG_AE7iqHZjgg8rM-Fxr_2Rm1VHL_R3I/view

In a nutshell, LangChain connects the industry popular Large Language Models such as OpenAI and HuggingFace Hub, to few external sources like external files, Database, Google, Wikipedia and Wolfram.

## Implementation Steps

#### Step 0: Pre-requiste
* Install python libraries using pip command
* Store your OpenAI API keys in environment variables
* Loaded CSV data into AWS RDS Postgres database using pgAdmin

#### Step 1: Importing the libraries
```python
from langchain.agents import create_sql_agent 
from langchain.agents.agent_toolkits import SQLDatabaseToolkit 
from langchain.sql_database import SQLDatabase 
from langchain.llms.openai import OpenAI 
from langchain.agents import AgentExecutor 
from langchain.agents.agent_types import AgentType
from langchain.chat_models import ChatOpenAI
```

#### Step 2: Loading the environment variables
```python
import os
my_ai_key = os.getenv('OPENAI_API_KEY')
```

#### Step 3: Setting up OpenAI integration
```python
my_llm = OpenAI(temperature=0, openai_api_key=my_ai_key)
```

#### Step 4: AWS RDS PostgreSQL connection setup 
```python
my_db = SQLDatabase.from_uri(
    "postgresql://userid:password@servername.us-east-1.rds.amazonaws.com:5432/postgres")
```
	
#### Step 5: Instantiating SQL DB Tool kit agent
```python
my_toolkit = SQLDatabaseToolkit(db=my_db, llm=my_llm)
```


#### Step 6: Creating SQL Agent with LLM and Toolkit
```python
my_agent_exec = create_sql_agent(
    llm=my_llm,
    toolkit=my_toolkit,
    verbose=True,
    agent_type=AgentType.ZERO_SHOT_REACT_DESCRIPTION,
)
```

#### Step 7: Executing few sample queries using SQL Agent
```python
question1 = "How many records are in stockprice with Open price greater than 15000?"
question2 = "What is the minimum value of close price ?"
question3 = "Average price of high marking?"

my_agent_exec.run(question1)
my_agent_exec.run(question2)
my_agent_exec.run(question3)

```

### Final Output
```python
> Entering new SQLDatabaseChain chain...
Howmany records are in stockprice with Open price greater than 15000?
SQLQuery:SELECT COUNT(*) FROM stock WHERE openday > 15000;
SQLResult: [(56,)]
Answer:There are 56 records in stockprice with Open price greater than 15000.
> Finished chain.


> Entering new SQLDatabaseChain chain...
What is the minimum value of close price ?
SQLQuery:SELECT MIN(closeday) FROM stock;
SQLResult: [(Decimal('14887.14'),)]
Answer:The minimum value of close price is 14887.14.
> Finished chain.


> Entering new SQLDatabaseChain chain...
Average price of high marking?
SQLQuery:SELECT AVG("high") FROM stock;
SQLResult: [(Decimal('15449.034032258065'),)]
Answer:The average price of high marking is 15449.03.
> Finished chain.
'The average price of high marking is 15449.03.'
```

## Author

- [Ganesan Senthilvel](https://github.com/gsenthilvel/)


## License

[MIT](https://choosealicense.com/licenses/mit/)


## Acknowledgements

 - [Official Documentation](https://langchain-langchain.vercel.app/docs/get_started)
 - [Offiial GitHub Repo](https://github.com/hwchase17/langchain)
 - [Official Tweets](https://twitter.com/hwchase17)
