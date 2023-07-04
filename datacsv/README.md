# Integration of CSV file for OpenAI queries using LangChain 

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
import numpy as np
import pandas as pd

from langchain.llms import OpenAI
from langchain.agents import create_pandas_dataframe_agent
```

#### Step 2: Loading CSV file content using numpy framework
```python
df = pd.read_csv("../datacsv/datafile/stockdata.csv")

df.head(3)
```

#### Step 3: Instantiating pandas dataframe agent 
```python
agent = create_pandas_dataframe_agent(OpenAI(temperature=0), df,verbose=True)
```

#### Step 4: Executing few AI queries against CSV file 
```python
agent.run("howmany rows are there?")
agent.run("Howmany entries of May are present?")
```

### Final Output
```python

> Entering new AgentExecutor chain...
Thought: I need to count the rows
Action: python_repl_ast
Action Input: df.shape[0]
Observation: 62
Thought: I now know the final answer
Final Answer: There are 62 rows.

> Finished chain.


> Entering new AgentExecutor chain...
Thought: I need to filter the dataframe to only include entries from May
Action: python_repl_ast
Action Input: df[df['Date'].str.contains('05/')]
Observation:         Date      Open      High       Low     Close
13  06/05/23  15345.19  15353.09  15258.92  15275.21
16  05/31/23  14994.64  14994.64  14810.57  14887.14
17  05/30/23  15078.69  15087.97  14951.16  14994.64
18  05/26/23  14975.97  15119.16  14975.97  15078.69
19  05/25/23  15022.89  15022.89  14898.70  14975.97
20  05/24/23  15172.27  15172.27  15006.28  15022.89
21  05/23/23  15318.85  15319.11  15161.47  15172.27
22  05/22/23  15324.32  15387.76  15271.22  15318.85
23  05/19/23  15345.43  15421.80  15283.70  15324.32
24  05/18/23  15313.92  15361.74  15214.00  15345.43
25  05/17/23  15129.25  15338.47  15129.25  15313.92
26  05/16/23  15322.56  15322.56  15128.62  15129.25
27  05/15/23  15246.36  15343.64  15228.80  15322.56
28  05/12/23  15263.07  15319.64  15167.78  15246.36
29  05/11/23  15349.17  15349.17  15176.64  15263.07
30  05/10/23  15352.81  15441.99  15228.42  15349.17
31  05/09/23  15391.27  15393.16  15297.09  15352.81
32  05/08/23  15380.87  15448.71  15353.68  15391.27
33  05/05/23  15117.67  15419.57  15117.67  15380.87
34  05/04/23  15233.85  15233.85  15055.43  15117.67
35  05/03/23  15314.57  15421.47  15227.66  15233.85
36  05/02/23  15535.89  15535.89  15189.25  15314.57
37  05/01/23  15545.88  15622.56  15525.90  15535.89
54  04/05/23  15374.11  15419.65  15304.06  15368.26
Thought: I now know the final answer
Final Answer: 22 entries of May are present.

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
