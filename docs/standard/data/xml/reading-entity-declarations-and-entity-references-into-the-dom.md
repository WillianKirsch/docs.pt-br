---
title: Declarações de entidade de leitura e referências a entidades em DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 86dba977-5cc4-4567-964f-027ffabc47b2
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 986f0f1d6ce20722b85ac0cfa9e3fe3fa351b75e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="reading-entity-declarations-and-entity-references-into-the-dom"></a>Declarações de entidade de leitura e referências a entidades em DOM
Uma entidade é uma declaração que indica um nome ser usado em XML no lugar do conteúdo ou marcação. Há duas partes a entidades. Primeiro, você deve a um nome ao conteúdo de substituição utilizando uma declaração de entidade. Uma declaração de entidade é criada usando a sintaxe de `<!ENTITY name "value">` em um Document type definition (DTD) ou no esquema XML. Em segundo lugar, o nome definido na declaração de entidade é usado posteriormente em XML. Quando usado em XML, é chamado uma referência de entidade. Por exemplo, a seguinte declaração de entidade declara uma entidade de nome `publisher` que está sendo associado com o conteúdo de “de pressionamento Microsoft”.  
  
```xml  
<!ENTITY publisher "Microsoft Press">  
```  
  
 O exemplo a seguir mostra o uso dessa declaração de entidade em XML como uma referência de entidade.  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 Alguns analisadores expandem automaticamente entidades quando um documento é carregado na memória. Portanto, quando XML está sendo lido na memória, as declarações de entidade são recordadas e salvas. Quando o analisador encontra posteriormente os caracteres de `&;` , que identifica uma referência de entidade geral, o analisador pesquisa que nome em uma tabela da declaração de entidade. A referência, `&publisher;` é substituído pelo conteúdo que representa. Usando o seguinte XML,  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 expanda a referência de entidade e substituir `&publisher;` com o conteúdo da Microsoft oferece seguinte XML expandido.  
  
 **Saída**  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by Microsoft Press</pubinfo>  
```  
  
 Há muitos tipos das entidades. O diagrama a seguir mostra a divisão dos tipos de entidade e da terminologia.  
  
 ![fluxograma da hierarquia de tipos de entidade](../../../../docs/standard/data/xml/media/entity-hierarchy.gif "Entity_hierarchy")  
  
 O padrão para a implementação do Microsoft .NET Framework o modelo de objeto (DOM) de documento XML é preservar as referências de entidades e não expandir quando as entidades XML é carregado. A implicação disso é como um documento é carregado em DOM, um nó de **XmlEntityReference** que contém a referência `&publisher;` variável é criado, com os nós filhos que representam o conteúdo no entidade declarada no DTD.  
  
 Usando a declaração de entidade de `<!ENTITY publisher "Microsoft Press">`, o diagrama a seguir mostra os nós **XmlEntity** e **XmlText** criados dessa declaração.  
  
 ![nós criados da declaração de entidade](../../../../docs/standard/data/xml/media/xml-entitydeclaration-node2.png "xml_entitydeclaration_node2")  
  
 As diferenças quando as referências a entidades são expandidos e quando não são faz uma diferença no qual nós são gerados na árvore DOM, na memória. A diferença em nós que são gerados é explicado nos tópicos [Referências a entidades são preservadas](../../../../docs/standard/data/xml/entity-references-are-preserved.md) e [Referências a entidades são expandidos e não preservadas](../../../../docs/standard/data/xml/entity-references-are-expanded-and-not-preserved.md).  
  
## <a name="see-also"></a>Consulte também  
 [DOM (Modelo de Objeto do Documento) de XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
