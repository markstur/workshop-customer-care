---
# REQUIRED: Make sure to update this file's folder name if the item's name or url changes.
draft: false
type: default
title: "インテリジェントにデータを検索するアプリを作成する"
meta_title: "インテリジェントにデータを検索するアプリを作成する"
subtitle: "Node.js と Watson Discovery を利用して、エンリッチされたデータを抽出して視覚化する Web アプリを開発する"
excerpt: "一連の Airbnb に関して一般公開されているレビューを例に、さまざまな UI コンポーネントを使用して洞察を視覚化する方法を説明します。"
meta_description: "一連の Airbnb に関して一般公開されているレビューを例に、さまざまな UI コンポーネントを使用して洞察を視覚化する方法を説明します。"
meta_keywords: "node.js, Watson Discovery"
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
  button_title: "コードを入手する"

# youtube type can be equal to demo or video, the youtube_id is the id part of the youtube url, and the link_title is an optional string that will be displayed in the button (note: always include the link title field).
demo:
- type: "youtube"
  url_or_id: "5EEmQwcjUa4"
  button_title: "デモを見る"

related_links:       # OPTIONAL - Note: zero or more related links
- title: "Overview of the IBM Watson Discovery service"
  url: "https://www.ibm.com/watson/services/discovery/Extract value from unstructured data by converting, normalizing, enriching it."

- title: "Watson Node.js SDK"
  url: "https://github.com/watson-developer-cloud/node-sdk"
  description: "Download the Watson Node SDK."

- title: "Architecture center"
  url: "https://www.ibm.com/cloud/garage/architectures/cognitiveDiscoveryDomain/0_1"
  description: "Learn how this code pattern fits into the Cognitive discovery Reference Architecture."

- title: "Cognitive for intelligence and insights from data"
  url: "https://www.ibm.com/cloud/garage/architectures/cognitiveArchitecture"
  description: "Unlock new intelligence from vast quantities of structured and unstructured data and develop deep, predictive insights."

#- title: "Try the app"
#  url: "https://watson-discovery-ui-demo.mybluemix.net/"
#  description: "Try an app to filter and sort Airbnb Review Data for Ausin, TX"

primary_tag: "artificial-intelligence"

tags:
- "node-js"
- "knowledge-discovery"

# Please select services from the complete set of services below. Do not create new services. Only use services specifically in use by your content.
service-id: "wdui"
services:
- "discovery"
runtimes:
- "sdk-for-node-js"
components:
  - "watson-discovery"
---

<!--
**This code pattern is part of the [Watson Discovery learning path](https://developer.ibm.com/series/learning-path-watson-discovery)**.

| Level | Topic | Type |
| --- | --- | --- |
| 100 | [Introduction to Watson Discovery](https://developer.ibm.com/articles/introduction-watson-discovery) | Article |
| 101 | [Create a cognitive news search app](https://developer.ibm.com/patterns/create-a-cognitive-news-search-app/) | Code pattern |
| **201** | **[Create an app to perform intelligent searches on data](https://developer.ibm.com/patterns/create-an-app-to-perform-intelligent-searches-on-data/)** | Code pattern |
| 301 | [Get customer sentiment insights from product reviews](https://developer.ibm.com/patterns/get-customer-insights-from-product-reviews/) | Code pattern |
| 401 | [Enhance customer helpdesks with Smart Document Understanding](https://developer.ibm.com/patterns/enhance-customer-help-desk-with-smart-document-understanding) | Code pattern |
-->

## 概要

標準的なサイトの検索では、ひと通り目を通すには多すぎるほどの結果が返されることがあります。一方、Watson Discovery Service のインスタンスでは、関連性を基準に絞り込んでから結果を返す検索インターフェースを素早く簡単に構築できます。それは、Watson Discovery Service にはエンリッチされたデータのクエリーを実行し、その結果を処理して関連性の高いものに絞り込んで返す、既製の UI コンポーネントが用意されているためです。このコード・パターンでは、一連の Airbnb に関して一般公開されているレビューを例に、さまざまな UI コンポーネントを使用して洞察を視覚化する方法を説明します。いったんこの方法を把握すれば、データセットを取り換えて、独自の使用ケースに応じて簡単に調整できます。

## 説明

より深い洞察力を持つ検索インターフェースにするには、エンリッチされたデータのクエリーを実行して、その結果を処理するという方法があります。まさにこのように動作するのが、このコード・パターンで紹介する Watson Discovery Service ベースの Node.js アプリです。このパターンでは、すぐに使える個々の UI コンポーネントを使用して、Watson Discovery アナリティクス・エンジンによってエンリッチされたデータを抽出し、視覚化する方法をデモします。

Watson Discovery Service を利用する最大の利点は、コグニティブ・エンリッチを適用してデータから洞察を引き出す、その強力なアナリティクス・エンジンにあります。このコード・パターンのアプリでは、Watson Discovery Service アナリティクス・エンジンのエンリッチ機能を、フィルター、リスト、グラフを使用して提示する例を説明します。データには主に以下のエンリッチが適用されます。

* エンティティー: 人、企業、組織、都市など
* カテゴリー: 深さ最大 5 レベルのカテゴリー階層にデータを分類
* 概念: 必ずしもデータ内で参照されていない一般概念を識別
* キーワード: データのインデックスや検索で通常使用される重要なトピック
* 感情: 各ドキュメントの全体的な感情 (肯定的または否定的)

このアプリは標準的な UI コンポーネント (フィルター、リスト、タグ・クラウド、感情グラフなど) だけでなく、パッセージ機能および強調表示機能といった Discovery の高度な手法も使用します。このアプリはこの 2 つの手法を使用して、クエリーを基に最も関連性の高いスニペットを識別するため、ユーザーが探しているデータと一致した検索結果を返す確率が高くなります。

このコード・パターンをひと通り完了すると、以下の方法がわかるようになります。

* Watson Discovery Service にデータをロードしてエンリッチする
* Watson Discovery Service 内でデータのクエリーを実行し、データを処理する
* Watson Discovery Service によってエンリッチされたデータを示す UI コンポーネントを作成する
* よく使われている JavaScript テクノロジーを使用して、Watson Discovery Service のデータとエンリッチを備えた完全な Web アプリを構築する

## フロー

![フロー](../../images/discovery-ui.png)

1. Airbnb レビューの JSON ファイルを Discovery コレクションに追加します。
1. アプリの UI を使用してバックエンド・サーバーとやり取りします。フロントエンドのアプリ UI が React を使用して検索結果をレンダリングします。この UI は、バックエンドで使用したすべてのビューを再利用してサーバー・サイドのレンダリングを行うことができます。フロントエンドは semantic-ui-react コンポーネントを使用していて、レスポンシブなものとなっています。
1. Discovery が入力を処理してバックエンド・サーバーにルーティングします。バックエンド・サーバーの役目は、ブラウザーに表示するビューをレンダリングすることです。バックエンド・サーバーは Express を使用して作成されており、React で作成されたビューを、express-react-views エンジンを使用してレンダリングします。
1. バックエンド・サーバーがユーザー・リクエストを Watson Discovery Service に送信します。バックエンド・サーバーはプロキシー・サーバーとして機能し、フロントエンドからのクエリーを Watson Discovery Service API に転送する一方で、機密性の高い API キーをユーザーから隠します。

## 手順

このパターンの詳細な手順については、[README](https://github.com/IBM/watson-discovery-ui/blob/master/README.md) を参照してください。手順の概要は以下のとおりです。

1. watson-discovery-ui GitHub リポジトリーを複製します。
1. Watson Discovery サービス・インスタンスを作成します。
1. Discovery ファイルをロードします。
1. 資格情報を構成します。
1. アプリケーションを実行します。


<!--
## まとめ

This code pattern explains how you can use individual out-of-the-box UI components to extract and visualize the enriched data provided by the Discovery analytics engine. The code pattern is part of the [Learning Path: Getting started with Watson Discovery](https://developer.ibm.com/series/learning-path-watson-discovery) series. To continue the series and learn about more Watson Discovery Service features, take a look at the next code pattern, [Get customer sentiment insights from product reviews](https://developer.ibm.com/patterns/get-customer-insights-from-product-reviews).
-->
