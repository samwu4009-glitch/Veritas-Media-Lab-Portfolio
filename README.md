# Veritas Media Lab

### AI × Digital Media · An interactive exploration of information, evidence, and trust

**Veritas Media Lab** is an independent portfolio project exploring how artificial intelligence and digital media can help people examine online claims. It brings structured AI analysis, live search references, and an immersive editorial-style interface into one interactive experience.

> **作品集项目｜原型阶段，未公开部署**  
> 完整项目文件与静态资源：[下载完整项目 ZIP](./Veritas_Media_Lab_完整部署包_20261022.zip)。压缩包不包含 API Key、.env 密钥文件或本机历史数据库。

**中文简介**  
Veritas Media Lab 是一个面向数字信息环境的交互式媒体素养原型。它将 AI 辅助分析、跨来源检索与可视化叙事相结合，引导用户从“接受结论”转向“查看依据、比较来源、理解不确定性”。

---

## 项目概述

社交媒体让信息传播更快，也让未经核实的主张、缺少语境的图片与相互冲突的报道更容易进入日常生活。本项目关注一个设计问题：

> **如何把 AI 的分析能力转化为可理解、可追溯的媒介体验，而不是另一个不透明的“真假判定器”？**

因此，项目不只生成结论，也呈现分析结构、相关来源与判断限制，鼓励用户参与核查过程。

## 核心体验

### Truth Lab｜结构化主张分析

用户提交一段文本后，系统识别核心事实主张，结合联网搜索结果生成分层分析。报告以 **SIFT**（Stop、Investigate、Find、Trace）作为核查路径，并以 **PIE**（Point、Illustration、Evidence）组织主张、例证与证据。

结论按证据强度区分为属实、不实或倾向性判断，并附来源链接，方便用户进一步阅读和比较。

### 多源检索｜让证据可见

后端并行查询 Google News、Bing、百度、GDELT 及部分新闻 RSS 源，并在界面中展示可访问的来源信息。新闻内容和分析结论均由实时网络与上游服务可用性影响。

### Ask｜面向探索的 AI 对话

Ask 提供开放式问答入口，帮助用户了解网站、讨论媒体内容或继续追问分析结果。Truth Lab 与 Ask 共享服务端 AI 接口，并支持中英文等多语言交互。

### 编辑式数字体验

页面以杂志式叙事组织内容，结合动效、滚动交互、本地字体与图像资源，尝试让媒体素养主题成为可浏览、可参与的体验，而非单一工具表单。

## 设计原则

- **过程优先**：展示主张、来源与分析步骤，让判断有迹可循。
- **多源比较**：将不同来源并置，帮助用户注意到报道角度与信息差异。
- **诚实表达不确定性**：区分明确证据与模型倾向，不把概率性判断包装成事实。
- **以用户为中心**：用清晰层级和交互反馈降低核查流程的理解门槛。

## 技术实现

| 层级 | 实现 |
| --- | --- |
| 前端 | HTML、Tailwind CSS、原生 JavaScript；GSAP、ScrollTrigger 与 Lenis 提供动效和滚动体验 |
| 后端 | Python、Flask；提供分析、对话、搜索、历史记录与语音转写 API |
| AI | DeepSeek API 用于文本分析与对话；密钥仅由服务端环境变量读取 |
| 检索 | Google News、Bing、百度、GDELT 与公开新闻 RSS；结果经相关性筛选后参与分析 |
| 数据 | Flask-SQLAlchemy；本地可使用 SQLite，服务器配置支持 PostgreSQL |
| 语音 | faster-whisper 多语言模型；模型运行在 Flask 服务端 |
| 部署 | Docker、Gunicorn、Nginx 与 PostgreSQL 部署配置 |

## 方法与能力边界

本项目是**AI 辅助研究原型**，不是自动裁决事实的权威机构。联网搜索可能受部署地区、网络、第三方服务限流或验证机制影响；来源标题与摘要不等于已阅读并核实报道全文。检索不到结果不代表主张为假，模型生成的倾向也不应替代人工判断。

因此，产品将来源链接与不确定性纳入体验设计，鼓励用户打开原文、比较独立报道，并把 AI 输出视为进一步调查的起点。

## 项目反思与下一步

当前原型已打通从用户输入、主张提取、多源检索到结构化报告的基本流程。实践中也观察到，搜索结果的相关性与来源可用性会直接影响用户对系统的信任。

后续迭代方向包括：改进搜索排序和事件匹配、加入来源质量与证据类型的可解释提示、设计可重复的评估集，以及进一步完善隐私告知和用户数据管理。

## 本地体验

完整代码和静态资源请从上方下载 ZIP。运行项目需要 Python 环境及有效的 DeepSeek API Key：

1. 在项目目录安装依赖：**py -m pip install -r requirements.txt**
2. 在本地环境变量中设置 **DEEPSEEK_API_KEY**。
3. 运行 **py app.py**，并访问 **http://127.0.0.1:5000/**。

本仓库用于作品展示与代码存档，**当前没有公开线上演示站点**。不要将 API Key 写入代码、网页或公开仓库。

---

**English summary**  
Veritas Media Lab is an independent AI and digital media portfolio prototype. It combines structured claim analysis, multi-source search references, and an editorial web experience to make evidence and uncertainty more visible. Rather than presenting AI as an authority, the project invites people to inspect sources, compare coverage, and treat model-generated assessments as starting points for further inquiry.
