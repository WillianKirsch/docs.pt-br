---
title: Materialização intermediária (C#)
ms.date: 07/20/2015
ms.assetid: 7922d38f-5044-41cf-8e17-7173d6553a5e
ms.openlocfilehash: b98f9765f5c54a49f26a9d1a3ac351f3eebcf9c2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="intermediate-materialization-c"></a>Materialização intermediária (C#)
Se você não for cauteloso, em algumas situações dràstica você pode alterar a memória e o perfil de desempenho do seu aplicativo causando o materialization prematuro das coleções nas suas consultas. Alguns operadores de consulta padrão faz com que o materialization de sua coleção de origem antes de produzir um único elemento. Por exemplo, <xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType> primeiro itera através da coleção inteira de origem, então classe todos os itens, e então produz basicamente o primeiro item. Isso significa que é grande obter o primeiro item de uma coleção ordenada; cada item não for depois disso caro. Isso faz sentido: Seria impossível para esse operador de consulta de fazer outra maneira.  
  
## <a name="example"></a>Exemplo  
 Este exemplo altera o exemplo anterior. O método de `AppendString` chama <xref:System.Linq.Enumerable.ToList%2A> antes de fazer iterações pela origem. Isso faz com que o materialization.  
  
```csharp  
public static class LocalExtensions  
{  
    public static IEnumerable<string>  
      ConvertCollectionToUpperCase(this IEnumerable<string> source)  
    {  
        foreach (string str in source)  
        {  
            Console.WriteLine("ToUpper: source >{0}<", str);  
            yield return str.ToUpper();  
        }  
    }  
  
    public static IEnumerable<string>  
      AppendString(this IEnumerable<string> source, string stringToAppend)  
    {  
        // the following statement materializes the source collection in a List<T>  
        // before iterating through it  
        foreach (string str in source.ToList())  
        {  
            Console.WriteLine("AppendString: source >{0}<", str);  
            yield return str + stringToAppend;  
        }  
    }  
}  
  
class Program  
{  
    static void Main(string[] args)  
    {  
        string[] stringArray = { "abc", "def", "ghi" };  
  
        IEnumerable<string> q1 =  
            from s in stringArray.ConvertCollectionToUpperCase()  
            select s;  
  
        IEnumerable<string> q2 =  
            from s in q1.AppendString("!!!")  
            select s;  
  
        foreach (string str in q2)  
        {  
            Console.WriteLine("Main: str >{0}<", str);  
            Console.WriteLine();  
        }  
    }  
}  
```  
  
 Este exemplo gera a seguinte saída:  
  
```  
ToUpper: source >abc<  
ToUpper: source >def<  
ToUpper: source >ghi<  
AppendString: source >ABC<  
Main: str >ABC!!!<  
  
AppendString: source >DEF<  
Main: str >DEF!!!<  
  
AppendString: source >GHI<  
Main: str >GHI!!!<  
```  
  
 Nesse exemplo, você pode ver que a chamada a <xref:System.Linq.Enumerable.ToList%2A> faz com que `AppendString` enumerar sua fonte inteiro antes de como o primeiro item. Se a origem foi uma matriz grande, essa alteraria significativamente o perfil de memória do aplicativo.  
  
 Os operadores de consulta padrão podem também ser encadeados juntos. O final deste tópico ilustra este tutorial.  
  
-   [Encadeando operadores de consulta padrão juntos (C#)](../../../../csharp/programming-guide/concepts/linq/chaining-standard-query-operators-together.md)  
  
## <a name="see-also"></a>Consulte também  
 [Tutorial: encadear consultas juntas (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md)
