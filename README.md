# Calculating token usage in Azure OpenAI endpoints API calls with and without Streaming
By default, when you call Azure OpenAI API endpoints, it's necessary to wait for the the entire completion to get generated and returned to the calling application. The longer is the completion, the longer it takes to get the response.

If you want to change the user experience and receive completion in chunks as it's being generated, then you can set Chat Completion's API paramemer strem to True (by default it's set to False). This would allow your Generative AI solution to start processing those chunks in parts and not to wait till the full completion.
```
stream=True
```

## Table of contents:
- [1. Prerequisites](https://github.com/LazaUK/AOAI-Whisper-Gradio/blob/main#option-0---access-to-whisper-models-in-offline-mode)
- [2. Shared helper functions](https://github.com/LazaUK/AOAI-Whisper-Gradio/tree/main#option-1---access-to-whisper-models-via-azure-openai-endpoint)
- [3. System- and Tiktoken-calculated token usage in non-streaming API calls](https://github.com/LazaUK/AOAI-Whisper-Gradio/blob/main#option-2---access-to-whisper-models-via-azure-ai-speech-endpoint)
- [4. Tiktoken-calculated token usage in streaming API calls](https://github.com/LazaUK/AOAI-Whisper-Gradio/blob/main#option-2---access-to-whisper-models-via-azure-ai-speech-endpoint)

## Option 0 - Access to Whisper models in offline mode
Whisper model can be consumed offline. You may notice differences in its performance on the weaker local computers in comparison to an Azure based deployment. At the same time, this may serve certain scenarios where access to external resources is prohibited or not possible.

To instantiate Web app with offline Whisper functionality, please follow these steps:
1. Install gradio Python package. This will allow you to define and instantiate a Web app, that will run locally as a Web service.
```
pip install --upgrade gradio
```
2. Install openai-whisper Python package. It comes with a few pre-trained Whisper models of various sizes. E.g. "base" model may require ~1 Gb of RAM, while "large" one would expect ~10 Gb of RAM.
```
pip install --upgrade openai-whisper
```
3. Launch provided Python script for offline Web app.
```
python 0_Whisper_Offline.py
```
If successful, you should be able to access new Web app's interface at http://127.0.0.1:7860/ as shown below. You can now record your speech through the computer's microphone and transcribe it using one of selected Whisper models.
![screenshot_0_offline](images/demo_app_0.png)
> **Note:** You may also require installation of [FFMpeg package](https://ffmpeg.org/) to make this solution work on your local computer.

## Option 1 - Access to Whisper models via Azure OpenAI endpoint
Whisper models are now available as a part of Azure OpenAI resource. To consume its API endpoint in your Gradio app, please follow these steps:
1. Deploy Whisper in available Azure OpenAI region.
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

