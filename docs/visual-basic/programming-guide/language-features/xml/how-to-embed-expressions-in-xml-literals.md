---
title: Como inserir expressões em literais XML (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- embedded expressions [Visual Basic]
- XML literals [Visual Basic], embedded expressions
ms.assetid: 75016fad-0141-42de-8564-5051be29487e
ms.openlocfilehash: 41dc6ef8d2ec2ffd6cd1cf793911f2e09f1a1e77
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-embed-expressions-in-xml-literals-visual-basic"></a>Como inserir expressões em literais XML (Visual Basic)
Você pode combinar literais XML com expressões incorporadas para criar um documento XML, fragmento ou elemento que contém o conteúdo criado no tempo de execução. Os exemplos a seguir demonstram como usar expressões inseridas para preencher os nomes de elementos, atributos e conteúdo de elemento em tempo de execução.  
  
 A sintaxe para uma expressão inserida é `<%=` `exp` `%>`, que é a mesma sintaxe que [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] usa. Para obter mais informações, consulte [expressões inseridas no XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).  
  
 Você também pode usar o [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] APIs para criar [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objetos. Para obter mais informações, consulte <xref:System.Xml.Linq.XElement>.  
  
## <a name="procedures"></a>Procedimentos  
  
#### <a name="to-insert-text-as-element-content"></a>Para inserir texto como conteúdo de elemento  
  
-   O exemplo a seguir mostra como inserir o texto que está contido no `contactName` variável entre os nomes de elementos de abertura e fechamento.  
  
     [!code-vb[VbXMLSamples#39](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-embed-expressions-in-xml-literals_1.vb)]  
  
     Este exemplo gera a seguinte saída:  
  
    ```xml  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
#### <a name="to-insert-text-as-an-attribute-value"></a>Para inserir texto como um valor de atributo  
  
-   O exemplo a seguir mostra como inserir o texto que está contido no `phoneType` variável como o valor da `type` atributo.  
  
     [!code-vb[VbXMLSamples#40](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-embed-expressions-in-xml-literals_2.vb)]  
  
     Este exemplo gera a seguinte saída:  
  
    ```xml  
    <contact>  
      <phone type="home">206-555-0144</phone>  
    </contact>  
    ```  
  
#### <a name="to-insert-text-for-an-element-name"></a>Para inserir texto para um nome de elemento  
  
-   O exemplo a seguir mostra como inserir o texto que está contido no `elementName` variável como o nome de um elemento.  
  
     Ao criar elementos usando essa técnica, você deve fechá-los com o \</ > marca.  
  
     [!code-vb[VbXMLSamples#41](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-embed-expressions-in-xml-literals_3.vb)]  
  
     Este exemplo gera a seguinte saída:  
  
    ```xml  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
## <a name="see-also"></a>Consulte também  
 [Como criar literais XML](../../../../visual-basic/programming-guide/language-features/xml/how-to-create-xml-literals.md)  
 [Expressões Inseridas no XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)  
 [Criando XML no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
