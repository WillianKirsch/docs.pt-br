---
title: Operador &amp; (Referência de C#)
ms.date: 04/04/2018
f1_keywords:
- '&_CSharpKeyword'
helpviewer_keywords:
- bitwise AND operator [C#]
- ampersand operator (&) [C#]
- '& operator [C#]'
- AND operator (&) [C#]
ms.assetid: afa346d5-90ec-4b1f-a2c8-3881f018741d
ms.openlocfilehash: 59813b4bc5781776c9f9741c3e49e660c684bff9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="amp-operator-c-reference"></a>Operador &amp; (Referência de C#)
O operador `&` pode funcionar como um operador unário ou binário.  
  
## <a name="remarks"></a>Comentários  
 O operador unário `&` retorna o endereço de seu operando (requer um contexto [desprotegido](../../../csharp/language-reference/keywords/unsafe.md)).  
  
 Os operadores binários `&` são predefinidos para os tipos integrais e `bool`. Para os tipos integrais, o & computa o AND lógico bit a bit de seus operandos. Para operandos `bool`, o & computa o AND lógico de seus operandos; ou seja, o resultado será `true` se e somente se ambos seus operandos forem `true`.  
  
 O operador binário `&` avalia os dois operadores, independentemente do valor do primeiro, ao contrário do [operador E condicional](../../../csharp/language-reference/operators/conditional-and-operator.md) `&&`. Por exemplo:  
  
 [!code-csharp[csRefOperators#37](../../../csharp/language-reference/operators/codesnippet/CSharp/and-operator_1.cs)]  
  
 Tipos definidos pelo usuário podem sobrecarregar o operador binário `&` (consulte [operador](../../../csharp/language-reference/keywords/operator.md)). As operações em tipos integrais geralmente são permitidas na enumeração. Quando um operador binário está sobrecarregado, o operador de atribuição correspondente, se houver, também estará implicitamente sobrecarregado.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[csRefOperators#38](../../../csharp/language-reference/operators/codesnippet/CSharp/and-operator_2.cs)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Operadores do C#](../../../csharp/language-reference/operators/index.md)
