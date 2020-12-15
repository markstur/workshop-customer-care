---
# REQUIRED: Make sure to update this file's folder name if the item's name or url changes.
draft: false
type: default
title: "创建应用程序来对数据执行智能搜索"
meta_title: "创建应用程序来对数据执行智能搜索"
subtitle: "使用 Node.js 和 Watson Discovery 开发一个 Web 应用程序来提取和可视化增强数据"
excerpt: "学习如何创建一个使用标准搜索 UI 组件的 Web 应用，它可以对 Watson Discovery 分析引擎提供的增强数据进行提取和可视化，并返回相关度更高的搜索结果。"
meta_description: "学习如何创建一个使用标准搜索 UI 组件的 Web 应用，它可以对 Watson Discovery 分析引擎提供的增强数据进行提取和可视化，并返回相关度更高的搜索结果。"
meta_keywords: "node.js, Watson Discovery,智能搜索"
authors:
- name: "Rich Hagarty"
  email: "Rich.Hagarty@ibm.com"
completed_date: "2018-02-21"
last_updated: "2018-07-03"
pwg:
- "watson discovery"
pta:
- "cognitive, data, and analytics"
github:
- url: "https://github.com/IBM/watson-discovery-ui"
  button_title: "获得代码"

# youtube type can be equal to demo or video, the youtube_id is the id part of the youtube url, and the link_title is an optional string that will be displayed in the button (note: always include the link title field).
demo:
- type: "demo"
  url_or_id: "https://mediacenter.ibm.com/media/1_xaikloyb"
  button_title: "观看视频"

related_links:       # OPTIONAL - Note: zero or more related links
- title: "关于 AI 的 Code Pattern"
  url: "https://developer.ibm.com/cn/technologies/artificial-intelligence/"
  description: "学习更多关于人工智能的 Code Pattern。"
  
- title: "Watson Node.js SDK"
  url: "https://github.com/watson-developer-cloud/node-sdk"
  description: "下载 Watson Node SDK"

- title: "框架中心"
  url: "https://www.ibm.com/devops/method/content/architecture/cognitiveDiscoveryDomain2/0_1"
  
  description: "了解本 Code Pattern 如何融入到认知发现参考体系结构中。"
related_content:
  - type: "articles"
    slug: "cc-port-business-chatbot-watson-conversation"
  - type: "tutorials"
    slug: "cc-build-chatbot-ibm-cloud"
# social-media-meta:
#   - type: twitter
#     title:
#     abstract:
#     img:
#     - height:
#      width:
#      src:

primary_tag: "artificial-intelligence"

# Please select tags from the complete set of tags below. Do not create new tags. Only use tags specifically targeted for your content. If your content could match all tags (for example cloud, hybrid, and on-prem) then do not tag it with those tags. Less is more.
tags:
- "node-js"
- "knowledge-discovery"
- "retail"

# Please select services from the complete set of services below. Do not create new services. Only use services specifically in use by your content.
services:
- "discovery"
runtimes:
- "sdk-for-node-js"
components:
- "watson-discovery"
---

**本 Code Pattern 纳入 [Watson Discovery 学习路径](https://developer.ibm.com/cn/blog/2019/learning-path-watson-discovery/)**。

| 等级 | 课题 | 分类 |
| --- | --- | --- |
| 100 | [Watson Discovery 简介](https://www.ibm.com/developerworks/cn/analytics/library/introduction-watson-discovery/index.html) | 文章 |
| 101 | [创建认知新闻搜索应用](https://developer.ibm.com/cn/patterns/create-a-cognitive-news-search-app/) | Code Pattern |
| **201** | **[创建应用程序来对数据执行智能搜索](https://developer.ibm.com/cn/patterns/create-an-app-to-perform-intelligent-searches-on-data/)** | Code Pattern |
| 301 | [通过产品评价获取客户情绪洞察](https://developer.ibm.com/cn/patterns/get-customer-insights-from-product-reviews/) | Code Pattern |
| 401 | [利用智能文档理解改善客服系统](https://developer.ibm.com/cn/patterns/enhance-customer-help-desk-with-smart-document-understanding) | Code Pattern |

## 摘要

对站点的标准搜索可能返回太多结果，用户不想浏览这么多的结果。但是，可以使用开箱即用的 UI 组件为您的 Watson Discovery 实例快速构建一个搜索接口，这些组件可以查询和处理那些增强数据(enriched data)并返回相关度更高的搜索结果。本 Code Pattern 使用 Airbnb 上列出的公开评论来演示如何使用单个 UI 组件来可视化洞察。 然后，您可以轻松切换数据集以使其适应您自己的用例。

## 概览

通过查询和处理增强数据，可以构建更富有洞察的搜索接口。本 Code Pattern 提供了一个构建于 Watson Discovery Service 之上的 Node.js 应用程序来实现此目的。该模式演示了如何使用各个开箱即用的 UI 组件，对 Watson Discovery 分析引擎提供的增强数据进行提取和可视化。

使用 Watson Discovery Service 的主要优势是它的强大分析引擎对您的数据进行了认知数据充实并提供了洞察。本 Code Pattern 中的应用程序提供了如何通过使用过滤器、列表和图表来展示这些增强数据示例。主要增强数据包括：

* 实体：人员、公司、组织、城市等
* 类别：将数据分类到一个最高可达 5 级的分层结构中
* 概念：已识别的一般概念，不一定会在数据中引用
* 关键词：通常用于建立索引或搜索数据的重要主题
* 情感：每个文档的整体正面或负面情感

该应用程序使用了一些标准搜索 UI 组件，比如过滤器、列表、标记云和情感图，还使用了更复杂的 Discovery 选项，比如段落和突出显示特性。通过这两个特性，应用程序能够根据您的查询来识别数据中的最相关数据段，而且更有可能返回您搜索的数据。

学完本 Code Pattern 后，您应该掌握如何：

* 在 Watson Discovery Service 中加载并充实数据。
* 在 Watson Discovery Service 中查询并处理数据。
* 创建 UI 组件来展示 Watson Discovery Service 创建的增强数据。
* 构建一个完整的 Web 应用程序，该应用程序利用流行的 JavaScript 技术来描绘 Watson Discovery Service 数据和数据充实。

## 流程

![流程](../../images/discovery-ui.png)

1. 将 Airbnb 评价 JSON 文件添加到 Discovery 集合中。
1. 使用应用程序 UI 与后端服务器进行交互。前端应用程序 UI 使用 React 呈现搜索结果，可以重用后端用于服务器端呈现的所有视图。前端使用了 semantic-ui-react 组件，而且是响应式的。
1. Discovery 处理输入并将其路由到后端服务器，后者负责在服务器端呈现在浏览器上显示的视图。后端服务器是使用 Express 编写的，还使用了一个 express-react-views 引擎来呈现使用 React 编写的视图。
1. 后端服务器将用户请求发送到 Watson Discovery Service。它充当代理服务器，将查询从前端转发到 Watson Discovery Service API，同时保持对用户隐藏敏感 API 密钥。

本文翻译自：[Create an app to perform intelligent searches on data](https://developer.ibm.com/patterns/create-an-app-to-perform-intelligent-searches-on-data/)（2018-02-21）
