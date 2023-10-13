# Calculating token usage in OpenAI and Azure OpenAI endpoints API calls with and without Streaming
By default, when you call an OpenAI or Azure OpenAI API endpoint, it's necessary to wait for the the entire completion to get generated before it's returned to the calling application. The longer is the completion, the longer it takes to get the response.

If you want to change this user experience and get completion in chunks as it's being generated, then you can set Chat Completion's API paramemer stream to True (by default it's set to False). This would allow your Generative AI solution to start processing those chunks in parts in almost real-time and not to wait till the full completion.
```
stream=True
```

## Table of contents:
- [1. Prerequisites](https://github.com/LazaUK/AOAI-Streaming-TokenUsage/blob/main/README.md#1-prerequisites)
- [2. Shared helper functions](https://github.com/LazaUK/AOAI-Streaming-TokenUsage/blob/main/README.md#2-shared-helper-functions)
- [3. System- and Tiktoken-calculated token usage in non-streaming API calls]()
- [4. Tiktoken-calculated token usage in streaming API calls]()

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
3. Next, deploy relevant GPT model in your Azure OpenAI resource and copy its name.
![screenshot_1_deploy](images/tiktoken_1_deploy.png)
4. Then copy API endpoint and key details.
![screenshot_1_access](images/tiktoken_1_access.png)
5. Finally, create environment variables OPENAI_API_DEPLOY, OPENAI_API_BASE and OPENAI_API_KEY, and assign to them copied deployment name, API endpoint and key details from the previous steps.
![screenshot_1_environ](images/tiktoken_1_environ.png)


## 2. Shared helper functions

## 3. System- and Tiktoken-calculated token usage in non-streaming API calls

## 4. Tiktoken-calculated token usage in streaming API calls
