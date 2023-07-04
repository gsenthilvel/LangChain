# Integration of Wikipedia using LangChain 

A brief description of initial hands-on experience in AI LangChain technologies.


## Technial definition of LangChain

Based on my learning, the logical architecture of LangChain is represented at https://drive.google.com/file/d/1XG_AE7iqHZjgg8rM-Fxr_2Rm1VHL_R3I/view

In a nutshell, LangChain connects the industry popular Large Language Models such as OpenAI and HuggingFace Hub, to few external sources like external files, Database, Google, Wikipedia and Wolfram.

## Implementation Steps

#### Step 0: Pre-requiste
* Install python libraries using pip command
* Store your OpenAI API keys in environment variables

#### Step 1: Importing the libraries
from langchain.retrievers import WikipediaRetriever
from langchain.chains import ConversationalRetrievalChain
from langchain.chat_models import ChatOpenAI

#### Step 2: Instantiating Wikipedia Retriever
my_retriever = WikipediaRetriever()

#### Step 3: Getting relevant info from Wikipedia
docs = my_retriever.get_relevant_documents(query="K.Kamaraj")

#### Step 4: Printing the meta-information of the response
docs[0].metadata  

### Outputof Wiki Metadata
```python
{'title': 'K. Kamaraj',
 'summary': 'Kumaraswami Kamaraj (15 July 1903 – 2 October 1975), popularly known as Kamarajar was an Indian independence activist and politician who served as the Chief Minister of Madras State (Tamil Nadu) from 13 April 1954 to 2 October 1963. He was the founder and the president of the Indian National Congress (Organisation), widely acknowledged as the "Kingmaker" in Indian politics during the 1960s. He also served as the president of the Indian National Congress for two terms i.e. four years between 1964–1967 and was responsible for the elevation of Lal Bahadur Shastri to the position of Prime Minister of India after Nehru\'s death and Indira Gandhi after Shastri\'s death. He was the Member of Parliament, Lok Sabha during 1952–1954 and 1969–1975. He was known for his simplicity and integrity. He played a major role in developing the infrastructure of the Madras state and worked to improve the quality of life of the needy and the disadvantaged.As the president of the INC, he was instrumental in steering the party after the death of Jawaharlal Nehru. As the chief minister of Madras, he was responsible for bringing free education to the disadvantaged and introduced the free Midday Meal Scheme while he himself did not complete schooling. He was awarded with India\'s highest civilian honour, the Bharat Ratna, posthumously in 1976. US Vice-president Hubert Humphrey, referred to Kamaraj as "one of the greatest political leaders in all the countries of the free world"  in January 1966.',
 'source': 'https://en.wikipedia.org/wiki/K._Kamaraj'}
```

#### Step 5: Printing the actual content of the response
docs[0].page_content  

### Wiki Page Content Output
```python
'Kumaraswami Kamaraj (15 July 1903 – 2 October 1975), popularly known as Kamarajar was an Indian independence activist and politician who served as the Chief Minister of Madras State (Tamil Nadu) from 13 April 1954 to 2 October 1963. He was the founder and the president of the Indian National Congress (Organisation), widely acknowledged as the "Kingmaker" in Indian politics during the 1960s. He also served as the president of the Indian National Congress for two terms i.e. four years between 1964–1967 and was responsible for the elevation of Lal Bahadur Shastri to the position of Prime Minister of India after Nehru\'s death and Indira Gandhi after Shastri\'s death. He was the Member of Parliament, Lok Sabha during 1952–1954 and 1969–1975. He was known for his simplicity and integrity. He played a major role in developing the infrastructure of the Madras state and worked to improve the quality of life of the needy and the disadvantaged.As the president of the INC, he was instrumental in steering the party after the death of Jawaharlal Nehru. As the chief minister of Madras, he was responsible for bringing free education to the disadvantaged and introduced the free Midday Meal Scheme while he himself did not complete schooling. He was awarded with India\'s highest civilian honour, the Bharat Ratna, posthumously in 1976. US Vice-president Hubert Humphrey, referred to Kamaraj as "one of the greatest political leaders in all the countries of the free world"  in January 1966.\n\n\n== Early life ==\nKamaraj was born on 15 July 1903 in Virudhunagar, Tamil Nadu, to Kumaraswami Nadar  and Sivakami Ammal. His name was originally Kamatchi, later changed to Kamarajar. His father Kumaraswami Nadar was a merchant. Kamaraj had a younger sister named  Nagammal. Kamaraj was first enrolled in a traditional school in 1907 and in 1908 he was admitted to Yenadhi Narayana Vidhya Salai. In 1909 Kamaraj was admitted in Virudupatti High School. Kamaraj\'s father died when he was six years old, his mother was forced to support the family. In 1914 Kamaraj dropped out of school to support his mother.\n\n\n== Politics ==\nAs a young boy, Kamaraj worked in his uncle\'s provision shop and during that time he began to attend public meetings and processions about the Indian Home Rule movement. Kamaraj developed an interest in prevailing political conditions by reading newspapers daily. The Jallianwala Bagh massacre was the decisive turning point in his life - he decided to fight for national freedom and to bring an end to foreign rule. In 1920, when he was 18, he became active in politics. He joined Congress as a full-time political worker. In 1921 Kamaraj organised public meetings at Virudhunagar for Congress leaders. He was eager to meet Gandhi, and when Gandhi visited Madurai on 21 September 1921, Kamaraj attended the public meeting and met Gandhi for the first time. He visited villages carrying Congress propaganda.In 1922 Congress boycotted the visit of the Prince of Wales as part of the Non-Cooperation Movement. He came to Madras and took part in the event. In 1923–25 Kamaraj participated in the Nagpur Flag Satyagraha. In 1927, Kamaraj started the Sword Satyagraha in Madras and was chosen to lead the Neil Statue Satyagraha, but this was given up later in view of the Simon Commission boycott.Kamaraj went to jail for two years in June 1930 for participating in the "Salt Satyagraha". led by Rajagopalachari at Vedaranyam; he was released before he served the two-year sentence as a result of 1931 Gandhi–Irwin Pact. In 1932, Section 144 was imposed in Madras prohibiting the holding of meetings and organisation of processions against the arrest of Gandhi in Bombay. In Virdhunagar, under Kamaraj\'s leadership, processions and demonstrations happened every day. Kamaraj was arrested again in January 1932 and sentenced to one year\'s imprisonment. In 1933 Kamaraj was falsely charged in the Virudhunagar bomb case. Varadarajulu Naidu and George Joseph argued on Kamaraj\'s behalf and p'
```

#### Step 6: Instantiating Wiki contraversial chain
ai_model = ChatOpenAI(model_name="gpt-3.5-turbo")
wikichain = ConversationalRetrievalChain.from_llm(
    ai_model, 
    retriever=my_retriever)
	
#### Step 7: Adding the list of queries to the chain
my_queries = [
    "What is salt march?",
    "What is the contribution by Mahatma Gandhi?",
]
my_chat_list = []

#### Step 8: Printing the request and response list
for question in my_queries:
    result = wikichain(
        {"question": question, 
         "chat_history": my_chat_list}
         )
    my_chat_list.append(
        (question, result["answer"])
        )
    print(f"-> Asked Question?? : {question} \n")
    print(f"## Answer ##: {result['answer']} \n")
	
### Wiki Chain Output
```python
-> Asked Question?? : What is salt march? 

## Answer ##: The Salt March, also known as the Salt Satyagraha or Dandi March, was a nonviolent civil disobedience movement led by Mahatma Gandhi in colonial India. It took place from 12 March to 5 April 1930 and was a protest against the British salt monopoly. Gandhi and his followers marched 387 kilometers from Sabarmati Ashram to Dandi, where they broke the British salt laws by making salt from seawater. The march inspired millions of Indians to join the movement and sparked large-scale acts of civil disobedience against the salt laws. 

-> Asked Question?? : What is the contribution by Mahatma Gandhi? 

## Answer ##: Mahatma Gandhi played a significant role in organizing and leading the Salt March, also known as the Dandi Salt March, in 1930. The Salt March was a nonviolent protest against the British salt monopoly, which imposed a heavy tax on salt and prohibited Indians from making their own salt. Gandhi and a group of followers walked about 400 kilometers (250 miles) from Sabarmati Ashram to the coastal village of Dandi, where they symbolically made their own salt from seawater. This act of civil disobedience was a powerful demonstration of resistance against British colonial rule. The Salt March gained widespread attention and ignited a wave of protests and civil disobedience throughout India, significantly contributing to the Indian independence movement. 
```

## Author

- [Ganesan Senthilvel](https://github.com/gsenthilvel/)


## License

[MIT](https://choosealicense.com/licenses/mit/)


## Acknowledgements

 - [Official Documentation](https://langchain-langchain.vercel.app/docs/get_started)
 - [Offiial GitHub Repo](https://github.com/hwchase17/langchain)
 - [Official Tweets](https://twitter.com/hwchase17)
