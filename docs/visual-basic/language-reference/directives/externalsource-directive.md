---
title: '#Diretiva ExternalSource'
ms.date: 07/20/2015
f1_keywords:
- '#Externalsource'
- '#ExternalSource'
- vb.ExternalSource
- Externalsource
- vb.#ExternalSource
- ExternalSource
helpviewer_keywords:
- ExternalSource directive (#ExternalSource)
- '#ExternalSource directive'
ms.assetid: 243bc6a2-34c3-4eeb-a776-9fd2bf988149
ms.openlocfilehash: 146ab41d74b45acc4063e2463baca26c7caa4652
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="externalsource-directive"></a>Diretiva #ExternalSource
Indica um mapeamento entre linhas específicas do código-fonte e externo para a fonte do texto.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
#ExternalSource( StringLiteral , IntLiteral )  
    [ LogicalLine+ ]  
#End ExternalSource  
```  
  
## <a name="parts"></a>Partes  
 `StringLiteral`  
 O caminho para a fonte externa.  
  
 `IntLiteral`  
 O número de linha da primeira linha da fonte externa.  
  
 `LogicalLine`  
 A linha onde o erro ocorre na origem externa.  
  
 `#End ExternalSource`  
 Encerra o `#ExternalSource` bloco.  
  
## <a name="remarks"></a>Comentários  
 Essa diretiva é usada somente pelo compilador e o depurador.  
  
 Um arquivo de origem pode incluir diretivas de fonte externa, que indicam um mapeamento entre linhas específicas do código no arquivo de origem e o texto externo à fonte, como um arquivo. aspx. Se forem encontrados erros no código-fonte designado durante a compilação, eles são identificados como provenientes da fonte externa.  
  
 Diretivas de fonte externa não têm nenhum efeito na compilação e não podem ser aninhadas. Eles são destinados a uso interno pelo aplicativo somente.  
  
## <a name="see-also"></a>Consulte também  
 [Compilação Condicional](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
