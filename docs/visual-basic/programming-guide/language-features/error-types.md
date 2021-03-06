---
title: Tipos de erro (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions, types
- errors [Visual Basic], types
- errors [Visual Basic], logic
- errors [Visual Basic], syntax
- logic errors [Visual Basic], Visual Basic
- run-time errors [Visual Basic], types of errors
- syntax errors [Visual Basic], Visual Basic
ms.assetid: 3048aabf-8c97-4e13-9150-853769cb5f6f
ms.openlocfilehash: c11b7f41dee57fc52ca1dff75734ad0b27b6a43a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="error-types-visual-basic"></a>Tipos de erro (Visual Basic)
No Visual Basic, erros (também chamado de *exceções*) se enquadram em três categorias: erros de sintaxe, erros de tempo de execução e erros lógicos.  
  
## <a name="syntax-errors"></a>Erros de sintaxe  
 *Erros de sintaxe* são aqueles que aparecem enquanto você escreve código. Visual Basic verifica seu código conforme você digita o **Editor de códigos** janela e o alerta se você cometer um erro, como digitar incorretamente uma palavra ou usar um elemento de linguagem incorretamente. Erros de sintaxe são o tipo mais comum de erros. Você pode corrigi-los facilmente no ambiente de codificação assim que eles ocorrem.  
  
> [!NOTE]
>  O `Option Explicit` instrução é um meio de evitar erros de sintaxe. Força a declare, com antecedência, todas as variáveis a ser usado no aplicativo. Portanto, quando essas variáveis são usadas no código, qualquer erro tipográfico é detectado imediatamente e pode ser corrigido.  
  
## <a name="run-time-errors"></a>Erros de tempo de execução  
 *Erros de tempo de execução* são aqueles que aparecem somente após você compilar e executar seu código. Esses envolvem código que pode parecer estar correto em que ele não tem nenhum erro de sintaxe, mas que não serão executadas. Por exemplo, você pode escrever corretamente uma linha de código para abrir um arquivo. Mas se o arquivo estiver corrompido, o aplicativo não pode executar o `Open` função e ele deixará de ser executado. Você pode corrigir a maioria dos erros de tempo de execução por reescrever o código com falha e, em seguida, recompilar e executá-lo novamente.  
  
## <a name="logic-errors"></a>Erros de lógica  
 *Erros de lógica* são aqueles que aparecem depois que o aplicativo está em uso. Eles são mais resultados geralmente indesejados ou inesperados em resposta a ações do usuário. Por exemplo, uma chave digitada incorretamente ou outra fora da influência pode fazer o seu aplicativo pare de funcionar dentro dos parâmetros esperados, ou completamente. Erros de lógica geralmente são o tipo mais difícil para corrigir, pois não é sempre claro onde eles se originam.  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [Noções básicas do depurador](/visualstudio/debugger/debugger-basics)
