# Calculating token usage in OpenAI and Azure OpenAI endpoints API calls with and without Streaming
By default, when you call an OpenAI or Azure OpenAI API endpoint, it's necessary to wait for the the entire completion to get generated before it's returned to the calling application. The longer is the completion, the longer it takes to get the response.

If you want to change this user experience and get completion in chunks as it's being generated, then you can set Chat Completion's API paramemer stream to True (by default it's set to False). This would allow your Generative AI solution to start processing those chunks in parts in almost real-time and not to wait till the full completion.
```
stream=True
```

## Table of contents:
- [1. Prerequisites](https://github.com/LazaUK/AOAI-Streaming-TokenUsage/blob/main/README.md#1-prerequisites)
- [2. Shared helper functions](https://github.com/LazaUK/AOAI-Whisper-Gradio/tree/main#option-1---access-to-whisper-models-via-azure-openai-endpoint)
- [3. System- and Tiktoken-calculated token usage in non-streaming API calls](https://github.com/LazaUK/AOAI-Whisper-Gradio/blob/main#option-2---access-to-whisper-models-via-azure-ai-speech-endpoint)
- [4. Tiktoken-calculated token usage in streaming API calls](https://github.com/LazaUK/AOAI-Whisper-Gradio/blob/main#option-2---access-to-whisper-models-via-azure-ai-speech-endpoint)

## 1. Prerequisites
These notebooks would require installation of 2 Python packages:
1. Interactions with API endpoint are enabled through openai package. You can install it with the following pip command.
```
pip install --upgrade openai
```
2. Conversion of texts into tokens and calcualtion of their numbers can be achieved through tiktoken package. You can install it with the following pip command.
```
pip install --upgrade tiktoken
```
3. Deploy relevant GPT model in your Azure OpenAI resource.
![screenshot_1_deploy](images/demo_app_1_deploy.png)





2. Copy API endpoint and key details.
![screenshot_1_access](images/demo_app_1_access.png)
3. Create environment variables and assign to them copied API endpoint and key details from the previous step.
![screenshot_1_environ](images/demo_app_1_environ.png)
4. Set AOAI_DEPLOYMENT_ID variable to the name of your Azure OpenAI Whisper deployment.
![screenshot_1_variable](images/demo_app_1_variable.png)
5. Install gradio Python package. This will allow you to define and instantiate a Web app, that will run locally as a Web service.
```
pip install --upgrade gradio
```
6. Install openai Python package. This is the client SDK that your Web app will use to interact with Azure OpenAI endpoint.
```
pip install --upgrade openai
```
7. Launch provided Python script for a Web app, integrated with Azure OpenAI endpoint.
```
python 1_Whisper_AOAI_endpoint.py
```
If successful, you should be able to access new Web app's interface at http://127.0.0.1:7860/ as shown below. You can now record your speech through the computer's microphone and transcribe it using Whisper model enabled in Azure OpenAI.
![screenshot_1_AOAI](images/demo_app_1.png)

## Option 2 - Access to Whisper models via Azure AI Speech endpoint
Whisper models are also available through Azure AI Speech. Using batch API (similar to what is described [here](https://github.com/Azure-Samples/cognitive-services-speech-sdk/tree/master/samples/batch/python/python-client)), can increase audio file size limit up to 1 Gb.

> **Note:** This option is still "Work in Progress". Please, check the latest version of 2_Whisper_AzureAISpeech_endpoint.py file provided for updates.
![screenshot_1_AISpeech](images/demo_app_2.png)

