# Display the list of supported Large Lang Model using LangChain 

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
import langchain.llms as list_llm_support
```

#### Step 2: To list all supported LLM models by LangChain
```python
dir (list_llm_support)
```

### Final Output
```python
['AI21',
 'AlephAlpha',
 'Anthropic',
 'Anyscale',
 'Aviary',
 'AzureOpenAI',
 'Banana',
 'BaseLLM',
 'Beam',
 'Bedrock',
 'CTransformers',
 'CerebriumAI',
 'Cohere',
 'Databricks',
 'DeepInfra',
 'Dict',
 'FakeListLLM',
 'ForefrontAI',
 'GPT4All',
 'GooglePalm',
 'GooseAI',
 'HuggingFaceEndpoint',
 'HuggingFaceHub',
 'HuggingFacePipeline',
 'HuggingFaceTextGenInference',
 'HumanInputLLM',
 'LlamaCpp',
 'Modal',
 'MosaicML',
 'NLPCloud',
 'OpenAI',
 'OpenAIChat',
 'OpenLM',
 'Petals',
 'PipelineAI',
 'PredictionGuard',
 'PromptLayerOpenAI',
 'PromptLayerOpenAIChat',
 'RWKV',
 'Replicate',
 'SagemakerEndpoint',
 'SelfHostedHuggingFaceLLM',
 'SelfHostedPipeline',
 'StochasticAI',
 'Type',
 'VertexAI',
 'Writer',
 '__all__',
 '__annotations__',
 '__builtins__',
 '__cached__',
 '__doc__',
 '__file__',
 '__loader__',
 '__name__',
 '__package__',
 '__path__',
 '__spec__',
 'ai21',
 'aleph_alpha',
 'anthropic',
 'anyscale',
 'aviary',
 'bananadev',
 'base',
 'beam',
 'bedrock',
 'cerebriumai',
 'cohere',
 'ctransformers',
 'databricks',
 'deepinfra',
 'fake',
 'forefrontai',
 'google_palm',
 'gooseai',
 'gpt4all',
 'huggingface_endpoint',
 'huggingface_hub',
 'huggingface_pipeline',
 'huggingface_text_gen_inference',
 'human',
 'llamacpp',
 'loading',
 'modal',
 'mosaicml',
 'nlpcloud',
 'openai',
 'openlm',
 'petals',
 'pipelineai',
 'predictionguard',
 'promptlayer_openai',
 'replicate',
 'rwkv',
 'sagemaker_endpoint',
 'self_hosted',
 'self_hosted_hugging_face',
 'stochasticai',
 'type_to_cls_dict',
 'utils',
 'vertexai',
 'writer']
```

## Author

- [Ganesan Senthilvel](https://github.com/gsenthilvel/)


## License

[MIT](https://choosealicense.com/licenses/mit/)


## Acknowledgements

 - [Official Documentation](https://langchain-langchain.vercel.app/docs/get_started)
 - [Offiial GitHub Repo](https://github.com/hwchase17/langchain)
 - [Official Tweets](https://twitter.com/hwchase17)
