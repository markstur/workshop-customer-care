---
# REQUIRED: Make sure to update this file's folder name if the item's name or url changes.
draft: false
type: default
title: "Cree una aplicación para realizar búsquedas inteligentes en los datos"
meta_title: "Cree una aplicación para realizar búsquedas inteligentes en los datos"
subtitle: "Utilice Node.js y Watson Discovery  para desarrollar una aplicación web para extraer y visualizar datos entristecidos"
excerpt: "Enseña un ejemplo práctico de una aplicación web que consulta y manipula datos del Servicio Watson Discovery. Esta aplicación web contiene múltiples componentes de UI que puede utilizar como punto de partida para desarrollar sus propias aplicaciones de Watson Discovery Service."
meta_description: "Vea un ejemplo práctico de una aplicación web que consulta y manipula datos del Servicio Watson Discovery. Esta aplicación web contiene múltiples componentes de UI que puede utilizar como punto de partida para desarrollar sus propias aplicaciones de Watson Discovery Service."
meta_keywords: "node.js, Watson Discovery"
authors:
- name: "Rich Hagarty"
  email: "Rich.Hagarty@ibm.com"
completed_date: "2018-02-21"
last_updated: "2020-03-05"
pwg:
- "watson discovery"
pta:
- "cognitive, data, and analytics"
github:
- url: "https://github.com/IBM/watson-discovery-ui"
  button_title: "Obtener el código (En Inglés)"

# el tipo de youtube puede ser igual a demo o video, youtube_id es la parte de identificación de la url de youtube y link_title es una cadena opcional que se mostrará en el botón (nota: siempre incluya el campo de título del enlace).
demo:
- type: "youtube"
  url_or_id: "5EEmQwcjUa4"
  button_title: "Ver la demo"

related_links:           # OPCIONAL - Nota: Cero o más enlaces relacionados
- title: "Visión general del servicio IBM Watson Discovery"
  url: "https://www.ibm.com/watson/services/discovery/Extract%20value%20from%20unstructured%20data%20by%20converting,%20normalizing,%20enriching%20it."

- title: "SDK de Watson Node.js"
  url: "https://github.com/watson-developer-cloud/node-sdk"
  description: "Descargue el SDK de Watson Node. (En Inglés)"

- title: "Centro de arquitectura"
  url: "https://www.ibm.com/cloud/garage/architectures/cognitiveDiscoveryDomain/0_1"
  description: "Descubra cómo este code pattern encaja en la Arquitectura de Referencia de Descubrimiento Cognitivo."

- title: "Capacidades cognitivas para extraer inteligencia e insights de los datos"
  url: "https://www.ibm.com/cloud/garage/architectures/cognitiveArchitecture"
  description: "Desbloquee nueva inteligencia de enormes cantidades de datos estructurados y no estructurados y desarrolle insights profundos y predictivos."

- title: "Pruebe la aplicación"
  url: "https://watson-discovery-ui-demo.mybluemix.net/"
  description: "Pruebe una aplicación para filtrar y ordenar los datos de los comentarios de Airbnb para Ausin, TX"

primary_tag: "knowledge-discovery"

tags:
- "javascript"

# Seleccione los servicios del conjunto completo de servicios abajo. No cree nuevos servicios. Utilice solo servicios usados específicamente por su contenido.
service-id: "wdui"
services:
- "discovery"
runtimes:
- "sdk-for-node-js"
components:
- "watson-discovery"

---

**This code pattern is part of the [Watson Discovery learning path](https://developer.ibm.com/series/learning-path-watson-discovery)**.

| Level | Topic | Type |
| --- | --- | --- |
| 100 | [Introducción a Watson Discovery](https://developer.ibm.com/articles/introduction-watson-discovery) | Artículo |
| 101 | [Cree una aplicación cognitiva de búsqueda de noticias](https://developer.ibm.com/patterns/create-a-cognitive-news-search-app/) | Code pattern |
| **201** | **[Cree una aplicación para realizar búsquedas inteligentes en los datos](https://developer.ibm.com/patterns/create-an-app-to-perform-intelligent-searches-on-data/)** | Code pattern |
| 301 | [Obtenga insights sobre el parecer de los clientes de las revisiones de los productos](https://developer.ibm.com/patterns/get-customer-insights-from-product-reviews/) | Code pattern |
| 401a | Mejore el centro de ayuda clientes con Smart Document Understanding usando [webhooks en Watson Assistant](https://developer.ibm.com/patterns/enhance-customer-help-desk-with-smart-document-understanding) | Code pattern |
| 401b | Mejore el centro de ayuda clientes utilizando la [habilidad de búsqueda de Watson Assistant](https://developer.ibm.com/patterns/enhance-customer-helpdesk-with-smart-document-understanding-using-search-skill) | Code pattern |

## Resumen

Una búsqueda estándar de un sitio puede de devolver demasiados resultados para alguien que quiere buscar entre ellos. Sin embargo, existe la posibilidad de desarrollar rápidamente una interfaz de búsqueda para una instancia de IBM Watson Discovery utilizando componentes preparados de una IU que consulten y manipulen los datos enriquecidos para devolver los resultados más relevantes de la búsqueda. Este code pattern utiliza comentarios que están disponibles públicamente en listados de Airbnb para demostrar cómo se utilizan los componentes individuales de la IU para visualizar conocimientos. A continuación, es posible alterar fácilmente el conjunto de datos, para adaptarlo a sus propios casos de uso.

## Descripción

Es posible consultar y manipular datos enriquecidos para desarrollar una interfaz de búsqueda más esclarecedora. Este code pattern proporciona una aplicación de Node.js que ha sido construida sobre el servicio Watson Discovery Service que hace exactamente eso. El patrón demuestra cómo utilizar componentes individuales preparados de la IU para extraer y visualizar los datos enriquecidos que brinda el motor analítico de Discovery.

La ventaja principal de usar Watson Discovery Services es su potente motor de analítica que proporciona un enriquecimiento cognitivo e insights sobre sus datos. La aplicación de este code pattern brinda ejemplos de cómo demostrar esos enriquecimientos a través del uso de filtros, listas y gráficos. Los principales enriquecimientos son:

* Entidades: personas, compañías, organizaciones, ciudades, etc.
* Categorías: clasificación de los datos en una jerarquía de categorías hasta 5 niveles de profundidad
* Conceptos: conceptos generales identificados que no están necesariamente referenciados en los datos
* Palabras clave: temas importantes que normalmente se utilizan para indexar o buscar en los datos
* Parecer: el parecer general, positivo o negativo, de cada documento

La aplicación utiliza componentes de búsqueda estándar de la IU, como listas de filtros, nubes de etiquetas y gráficos de sentimientos, aunque también utiliza opciones más complejas de Discovery, como los pasajes y las funciones de destaque. La aplicación utiliza esas dos funciones para identificar fragmentos más relevantes de los datos basándose en la consulta, y es más probable que devuelva los datos que se buscan.

Cuando haya completado este code pattern, usted debería saber:

* Cargar y enriquecer datos en Watson Discovery Service
* Consultar y manipular los datos en Watson Discovery Service
* Crear componentes de la IU para representar datos enriquecidos que han sido creados por Watson Discovery Service
* Desarrollar una aplicación web completa que utilice tecnologías populares de JavaScript para presentar enriquecimientos y datos de Watson Discovery Service

## Flujo

![flujo](../../images/discovery-ui.png)

1. Añadir los archivos JSON de comentarios de Airbnb a la colección de Discovery.
1. Utilizar la IU de la aplicación para interactuar con el servidor backend. La IU de la aplicación frontend utiliza React para representar los resultados de la búsqueda y puede reutilizar todas las listas que el backend utiliza para representar por el lado del servidor. El frontend utiliza componentes de semantic-ui-react y tiene diseño adaptativo.
1. Discovery procesa los datos y los redirige al servidor backend, que es responsable de la representación por el lado del servidor de las vistas que se muestran en el navegador. El servidor backend se escribe con Express y utiliza un motor express-react-views para representar las vistas que se escriben con React.
1. El servidor backend envía las solicitudes de los usuarios a Watson Discovery Service. Actúa como servidor proxy, redirigiendo las consultas desde el frontend hasta la API de Watson Discovery Service mientras mantiene las claves confidenciales de la API ocultas para el usuario.

## Instrucciones

¿Listo para poner este code pattern en uso? Los detalles completos sobre cómo comenzar a ejecutar y a utilizar esta aplicación se encuentran en [README (En Inglés)](https://github.com/IBM/watson-discovery-ui/blob/master/README.md).

## Conclusión

Este code pattern explica cómo utilizar componentes individuales preparados de la IU para extraer y visualizar los datos enriquecidos que brinda el motor analítico de Discovery. Este code pattern forma parte de la serie [Ruta de Aprendizaje: Introducción a Watson Discovery](https://developer.ibm.com/series/learning-path-watson-discovery). Para continuar con la serie y conocer más funciones de Watson Discovery Service, vea el siguiente code pattern, [Obtener insights de sentimiento de los clientes de los comentarios de los productos](https://developer.ibm.com/patterns/get-customer-insights-from-product-reviews).

## Aviso

El contenido aquí presentado fue traducido de la página IBM Developer US. Puede revisar el contenido original en [este link](https://developer.ibm.com/patterns/create-an-app-to-perform-intelligent-searches-on-data/).
