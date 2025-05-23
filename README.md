<<<<<<< HEAD
# LangChat

> 快速构建企业级AIGC项目

LangChat是Java生态下企业级AIGC项目解决方案，集成RBAC和AIGC大模型能力，帮助企业快速定制AI知识库、企业AI机器人。
 
**支持的AI大模型：** DeepSeek / Gitee AI / 阿里通义 / 百度千帆 / 抖音豆包 / 智谱清言 / 零一万物 / 讯飞星火 / OpenAI / Gemini / Ollama / Azure / Claude 等大模型。

- 产品官网：[http://langchat.cn/](http://langchat.cn/)
- 文档地址：[http://docs.langchat.cn/](http://docs.langchat.cn/)
- 预览地址：[http://backend.langchat.cn/](http://backend.langchat.cn/)

**开源地址：**

- Gitee：https://gitee.com/langchat/langchat
- Github：https://github.com/tycoding/langchat
- GitCode: https://gitcode.com/LangChat/LangChat

**注意：** 如果想和作者深入交流LangChat开发规划、AIGC产品研发、变现等方式，**可以请作者喝一杯咖啡加入LangChat交流群**

**开源不易，欢迎Star、fork 持续关注**

## V2版本说明

> **LangChat正在全力开发v2版本，增加更多新特性**

注意：如果文档中已经 `application-dev.yml` 中配置项和本地不同，是因为有部分配置已经迁移到Web端动态配置了，例如向量数据库

**我们投入了大量的精力打磨LangChat产品（包括UI、架构和代码等），但是仅仅依靠开源是无法存活下去的，更希望大家能够支持一下LangChat（赞助），让LangChat更好的发展下去**

LangChat V2版本产品形态如下：

![](imgs/MIK-lsqJpo.png)

![](imgs/MIK-fFMz5U.png)

![](imgs/MIK-FLutGm.png)

![](imgs/MIK-lSq51v.png)

![](imgs/MIK-D1hnnY.png)

## 商业化支持

> 提供一些列商业化服务&技术支持

1. 提供项目部署服务，远程部署到服务器
2. 提供Docker一键部署脚本、提供前后端nginx配置脚本
3. 提供项目架构讲解和AIGC产品设计&技术支持
4. 提供项目二开合作，本项目不可商用，商用请联系作者授权
5. 更多支持...

以上，希望有需要的朋友都可以加我微信 **LangchainChat** 跟我沟通。

## 特性

1. 多模态：支持集成国内外数十家AI大模型
2. 动态配置：支持再页面上可视化动态配置大模型参数、Key等信息，无感刷新、无需每次重启服务
3. 知识库：支持向量化知识库文档，定制化Prompt对话场景
4. 高级RAG：支持Embedding模型，从知识库中精确搜索；集成Web Search等RAG插件
5. Function Call：支持定制化Tool工具类，实现本地函数调用，从第三方加载数据并提供给LLM
6. 多渠道发布：计划封装Web SDK，将AI智能客服快速嵌入任意第三方Web应用中；计划支持微信、飞书、钉钉等消息通信渠道（待完善）
7. Workflows：计划开发可视化LLM流程设计器，高自定义机器人执行流程（待完善）
8. 提供AIGC客户端应用，快速管理客户端数据
9. 支持动态配置Embedding模型和向量数据库
10. 支持不同的知识库关联不同的模型和向量数据库
11. 更多特性...

## 赞助

由于作者精力有限，开发文档会有所欠缺，**可以加入我的Java微信交流群：LangChainChat（备注：闲聊）**。如果有Java全栈、NextJS全栈、二开、接单、项目合作也欢迎联系我。

如果你有关于LangChat的开发问题或者二开定制等需求，或者想要深入交流Java生态AIGC产品开发、产品变现等，也可以请作者喝一杯咖啡加入我的LangChat交流群（可以一起交流LangChat后续开发规划）：

添加微信：LangChainChat（备注：赞助）

![](docs/imgs/MIK-3F1Xlb.png)

## 版权和协议

Licensed under the GNU License (GPL) v3. 

Copyright (c) 2024-present, TyCoding.

采用GUN GPL-v3开源协议，可以免费学习使用，个人可以免费是接入使用，商业应用请联系作者授权。

## 版本更新

- 2024.11.27 支持Gitee AI模型接入
- 2024.11.16 重新调整项目结构设计、分包设计
- 2024.7.30 LangChat开发Web SDK，接入API、WEB消息渠道，支持Iframe嵌入
- 2024.7.21 LangChat完成多存储方案，支持本地、七牛云、阿里云、腾讯云OSS服务
- 2024.7.19 LangChat完成分离Server、Client端业务架构，保持业务分离
- 2024.7.15 LangChat正式发布、公开仓库

## Star History

[![Star History Chart](https://api.star-history.com/svg?repos=TyCoding/langchat&type=Date)](https://star-history.com/#TyCoding/langchat&Date)

## 预览

![](docs/imgs/MIK-jJfiee.png)

![](docs/imgs/MIK-qQTgUW.png)

![](docs/imgs/MIK-hkimZf.png)


![](docs/imgs/MIK-Axv453.png)

![](docs/imgs/MIK-B0EgMc.png)

![](docs/imgs/MIK-aumvM8.png)

![](docs/imgs/MIK-D8rxTi.png)

![](docs/imgs/MIK-nXe2mr.png)

![](docs/imgs/MIK-dwX7mz.png)

![](docs/imgs/MIK-KGG50l.png)


![](docs/imgs/MIK-qmfti3.png)


## 感谢

- [LangChain4j](https://github.com/langchain4j/langchain4j)


## 联系

- 博客: https://tycoding.cn
- Github: https://github.com/tycoding
- 邮箱: langchat@outlook.com
=======
# Taihang-RAGAI
>>>>>>> 57cfd18ce611c963b2ba394fd3260933605913cc
