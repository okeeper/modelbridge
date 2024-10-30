# modelbridge
一个国内可访问的免费的OpenAI API,无缝兼容任何以openai api为接口的应用

## 前言：OpenAI API有什么用

OpenAI API的应用场景非常广泛，涵盖了从自然语言处理到图像生成等多个领域。以下是一些具体的应用场景示例：

- **自然语言处理和生成**：用于自动撰写文章、生成创意文案、构建聊天机器人、客户服务自动化等。
- **内容创建和编辑**：自动生成新闻报道、博客文章、小说等。
- **代码辅助和开发**：理解自然语言并生成相应的代码。
- **数据分析和理解**：用于会议记录、播客制作等。
- **自动化办公任务**：自动写作、自动翻译等。
- **教育和培训**：改进教育软件和服务，提供个性化的学习体验。
- **娱乐和游戏开发**：开发各种类型的游戏，包括文字游戏、图形游戏等。
- **机器人技术**：开发各种类型的机器人，包括家庭机器人、工业机器人等。
- **实时语音交互**：用于语音助手、在线教育、游戏等场景。

市面上可直接使用OpenAI API_KEY应用软件。

- **ChatBox:** 一款开源免费的跨平台OpenAI API桌面客户端，支持Windows、macOS和Linux。它允许用户自定义API Key和API Host地址，并在本地保存所有聊天记录，同时管理多个会话和设置不同的Prompt
- **OpenCat**:  专为macOS和iOS设计的原生客户端，支持自定义API地址，提供即开即用的体验，无需等待网页加载
- **PingPongChat**：一款智能AI客户端，支持iPhone、iPad、Mac等设备，无需注册账号或折腾API即可使用，基于GPT-3.5模型
- **ChatGPT-Next-Web**: 一键免费部署你的私人 ChatGPT 网页应用，支持 GPT3, GPT4 & Gemini Pro 模型。可配置自定义的base_url和api key.

## 那么如何获取一个OpenAI API_KEY呢？

众所周知，openai 在2024年7月已经全面禁止了对国内的访问服务。即使不封禁，想要获取官方的openai api账号，你需要境外银行卡进行订阅，同时还需要梯子才能访问。不过，今天我要介绍一个不需要任何魔法，免费可用的OpenAI api——ModelBridge。

## ModelBridge是什么？

想象一下，有一个平台，它能够让你轻松访问国内外的主流大语言模型，而且免费体验。这就是ModelBridge——一个国内免费的OpenAI API代理，它让人工智能的魔法触手可及。

ModelBridge官网：https://model-bridge.okeeper.com

### 1. 标准的OpenAI接口格式

ModelBridge遵循OpenAI的接口格式，这意味着如果你已经熟悉OpenAI的API，那么ModelBridge对你来说就像是老朋友一样亲切。你可以直接参照OpenAI的接口文档，轻松上手。

### 2. 一次对接，模型任意切换

ModelBridge的另一个神奇之处在于它的灵活性。你只需要进行一次API对接，就可以在不同的大模型之间自由切换，就像在魔法世界中随意变换魔杖一样简单。

### 3. 无需魔法，免费使用

对于国内用户来说，访问某些国外的API可能需要一些“魔法”。但ModelBridge打破了这一限制，让你无需任何特殊配置，就能免费使用这个平台。

### 4. 支持国内外主流大模型

无论你需要的是百度文心一言、阿里、讯飞、智谱ChatGLM，还是GPT系列等，ModelBridge都能满足你的需求。它就像一个魔法宝库，里面装满了各种强大的模型。

## 如何开始使用ModelBridge？只需两步

首先，访问ModelBridge的官网进行注册和登录。然后，参照官方文档进行API对接。由于接口请求规范完全和OpenAI一样，你可以直接以OpenAI的接口文档为参考。如果是国内模型，只需要将模型参数`model`修改为国内的模型名字即可。

### 第一步：用邮箱注册并登录ModelBridge，获取复制出API_SECRET_KEY，地址：https://model-bridge.okeeper.com/home/login

![image-20240926155117726](https://okeeper-blog-images.oss-cn-hangzhou.aliyuncs.com/images/image-20240926155117726.png)

### 第2步：编写代码。配置的base_url是：https://model-bridge.okeeper.com/v1

#### 使用Openai SDK对接任意模型：

```
import os
from openai import OpenAI
import openai
import requests
import time
import json
import time

API_SECRET_KEY = "your_api_secret";
BASE_URL = "https://model-bridge.okeeper.com/v1/"

# chat
def chat_completions3(query):
    client = OpenAI(api_key=API_SECRET_KEY, base_url=BASE_URL)
    resp = client.chat.completions.create(
        model="gpt-3.5-turbo",
        messages=[
            {"role": "system", "content": "You are a helpful assistant."},
            {"role": "user", "content": query}
        ]
    )
    print(resp)
    #print(resp.choices[0].message.content)

# chat with other model
def chat_completions4(query):
    client = OpenAI(api_key=API_SECRET_KEY, base_url=BASE_URL)
    resp = client.chat.completions.create(
        model="ERNIE-4.0-8K", #百度的千帆模型
        messages=[
            {"role": "system", "content": "You are a helpful assistant."},
            {"role": "user", "content": query}
        ]
    )
    print(resp)
    #print(resp.choices[0].message.content)
```



想要了解更多关于ModelBridge的魔法秘籍，可以访问他们的[官方文档](https://model-bridge.okeeper.com)
