---
title: Preservar espaço em branco ao Serializing2
ms.date: 07/20/2015
ms.assetid: 2d7abbd4-37f4-422b-89dd-0a694b5edc17
ms.openlocfilehash: a08d69a817c3e493e571d1b3b98f6f2a144ad995
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="preserving-white-space-while-serializing"></a>Preservar espaço em branco para serializar
Este tópico descreve como controlar o espaço em branco para serializar uma árvore XML.  
  
 Um cenário comum é ler o XML recuado, criar uma árvore XML na memória sem nenhum nó de texto de espaço em branco (isto é, não preservar espaço em branco), executar algumas operações no XML e, em seguida, salvar o XML com recuo. Quando você serializa o XML com formatação, somente os espaços em branco significativos na árvore XML são preservados. Este é o comportamento padrão para [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].  
  
 Outro cenário comum é ler e modificar XML que já foi recuado intencionalmente. Você pode não querer modificar este recuo de nenhuma forma. Para fazer isso em [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], você preserva o espaço em branco quando você carregar ou analisar XML e desativa o formatação quando você serializa XML.  
  
## <a name="white-space-behavior-of-methods-that-serialize-xml-trees"></a>Comportamento de espaço em branco de métodos que serialize árvores XML  
 Os seguintes métodos nas classes de <xref:System.Xml.Linq.XElement> e de <xref:System.Xml.Linq.XDocument> serialize uma árvore XML. Você pode serializar uma árvore XML para um arquivo, um <xref:System.IO.TextReader>, ou um <xref:System.Xml.XmlReader>. O método de `ToString` serializa a uma cadeia de caracteres.  
  
-   <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XElement.ToString%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XDocument.ToString%2A?displayProperty=nameWithType>  
  
 Se o método não utiliza <xref:System.Xml.Linq.SaveOptions> como um argumento, o método irá formatar (corte XML serializável.) Nesse caso, qualquer espaço em branco irrisória na árvore XML é descartado.  
  
 Se o método utiliza <xref:System.Xml.Linq.SaveOptions> como um argumento, então você pode especificar que o formato de método não (corte XML serializável.) Nesse caso, qualquer espaço em branco na árvore XML é preservada.  
  
## <a name="see-also"></a>Consulte também  
 [Serializando árvores XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md)
