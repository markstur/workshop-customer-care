---
# REQUIRED: Make sure to update this file's folder name if the item's name or url changes.
draft: false
type: default
title: "Crie um aplicativo para executar procuras inteligentes sobre dados"
meta_title: "Crie um aplicativo para executar procuras inteligentes sobre dados"
subtitle: "Desenvolva um aplicativo web para extrair e visualizar dados enriquecidos usando Node.js e Watson Discovery"
excerpt: "Desenvolva um aplicativo web para extrair e visualizar dados enriquecidos usando Node.js e Watson Discovery"
meta_description: "Desenvolva um aplicativo web para extrair e visualizar dados enriquecidos usando Node.js e Watson Discovery"
meta_keywords: "node.js, Watson Discovery, busca inteligente, dados"
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
  button_title: "Obtenha o código"

# youtube type can be equal to demo or video, the youtube_id is the id part of the youtube url, and the link_title is an optional string that will be displayed in the button (note: always include the link title field).
demo:
- type: "youtube"
  url_or_id: "5EEmQwcjUa4"
  button_title: "Assista à demo"

related_links:       # OPTIONAL - Note: zero or more related links
- title: "Visão geral do serviço IBM Watson Discovery"
  url: "https://www.ibm.com/watson/services/discovery/Extract"
  description: "Valor de dados não estruturados convertendo, normalizando e enriquecendo."

- title: "Watson Node.js SDK"
  url: "https://github.com/watson-developer-cloud/node-sdk"
  description: "Faça o download do Watson Node SDK."

- title: "Centro de arquitetura"
  url: "https://www.ibm.com/cloud/garage/architectures/cognitiveDiscoveryDomain/0_1"
  description: "Aprenda como esse padrão de código se encaixa na Arquitetura de referência de descoberta cognitiva."

- title: "Cognitivo para inteligência e insights de dados"
  url: "https://www.ibm.com/cloud/garage/architectures/cognitiveArchitecture"
  description: "Desbloqueie novas informações a partir de grandes quantidades de dados estruturados e não estruturados e desenvolva insights profundos e preditivos."

- title: "Experimente o aplicativo"
  url: "https://watson-discovery-ui-demo.mybluemix.net/"
  description: "Experimente um aplicativo para filtrar e classificar os Dados de Revisão do Airbnb em Austin, TX"

# social-media-meta:
#   - type: twitter
#     title:
#     abstract:
#     img:
#     - height:
#      width:
#      src:

primary_tag: "machine-learning"

# Please select tags from the complete set of tags below. Do not create new tags. Only use tags specifically targeted for your content. If your content could match all tags (for example cloud, hybrid, and on-prem) then do not tag it with those tags. Less is more.
tags:
- "data-science"
- "node-js"
- "knowledge-discovery"
- "analytics"

# Please select services from the complete set of services below. Do not create new services. Only use services specifically in use by your content.
services:
- "discovery"
runtimes:
- "sdk-for-node-js"
---

## Apresentação

Uma procura padrão por um site pode retornar vários resultados para alguém que deseja seguir adiante. No entanto, é possível desenvolver rapidamente uma interface de procura para sua instância do Watson Discovery utilizando componentes de UI simples de instalar que consultem e manipulem os dados enriquecidos para retornar resultados de procura mais relevantes. Este padrão de código utiliza revisões publicamente disponíveis sobre listagens da Airbnb para demonstrar como usar componentes individuais da UI na visualização de insights. É possível trocar facilmente o conjunto de dados para adaptá-lo aos seus próprios casos de uso.

## Descrição

Com a consulta e a manipulação de dados enriquecidos, é possível desenvolver uma interface de procura com mais insights. Este padrão de código fornece um aplicativo Node.js baseado no Watson Discovery Service que faz exatamente isso. O padrão demonstra como é possível usar componentes de UI simples de instalar para extrair e visualizar os dados enriquecidos fornecidos pelo mecanismo de análise Watson Discovery.

O principal benefício do uso do Watson Discovery Service é seu eficiente mecanismo de análise, que fornece enriquecimentos cognitivos e insights para seus dados. O aplicativo neste padrão de código fornece exemplos de como mostrar esses enriquecimentos utilizando filtros, listas e gráficos. Os principais enriquecimentos são:

* Entidades: pessoas, empresas, organizações, cidades e mais.
* Categorias: classificação dos dados em uma hierarquia de categorias de até cinco níveis de profundidade.
* Conceitos: conceitos gerais identificados que não são necessariamente referenciados nos dados.
* Palavras-chave: tópicos importantes normalmente usados para indexar ou procurar os dados.
* Impressão: a impressão geral positiva ou negativa de cada documento.

O aplicativo usa os componentes de UI de procura, como listas de filtro, nuvens de tag e gráficos de impressão, mas também opções mais complexas do Discovery, como recursos de trechos e destaques. Com esses dois recursos, o aplicativo identifica os fragmentos mais relevantes em seus dados com base em sua consulta e tem mais chance de retornar os dados que você está procurando.

Após concluir esse padrão de código, você deverá saber:

* Carregar e enriquecer dados no Watson Discovery Service.
* Consultar e manipular dados no Watson Discovery Service.
* Criar componentes de UI para representar dados enriquecidos criados pelo Watson Discovery Service.
* Desenvolver um aplicativo web completo que utilize tecnologias JavaScript populares para apresentar dados e enriquecimentos do Watson Discovery Service.

## Fluxo

![Fluxograma das etapas para criação do app](../../images/discovery-ui-br.png)

1. Inclua os arquivos JSON de revisão da Airbnb na coleção do Discovery.
1. Use a UI do aplicativo para interagir com o servidor de backend. A UI do aplicativo frontend usa React para renderizar resultados da procura e pode reutilizar todas as visualizações usadas pelo backend para renderização do lado do servidor. O frontend está usando componentes semantic-ui-react e é responsivo.
1. O Discovery processa a entrada e a roteia para o servidor de backend, que é responsável pela renderização do lado do servidor das visualizações exibidas no navegador. O servidor de backend é gravado usando Express e utiliza um mecanismo express-react-views para renderizar visualizações gravadas usando React.
1. O servidor de backend envia solicitações do usuário para o Watson Discovery Service. Ele age como um servidor proxy, encaminhando consultas do frontend para a API do Watson Discovery Service, enquanto mantém chaves API sensíveis escondidas do usuário.

## Aviso

O conteúdo aqui presente foi traduzido da página IBM Developer US. Caso haja qualquer divergência de texto e/ou versões, consulte [o conteúdo original](https://developer.ibm.com/patterns/create-an-app-to-perform-intelligent-searches-on-data/).
