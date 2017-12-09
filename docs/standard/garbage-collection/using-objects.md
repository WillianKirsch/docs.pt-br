---
title: Usando objetos que implementam IDisposable
ms.custom: 
ms.date: 04/07/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Dispose method
- try/finally block
- garbage collection, encapsulating resources
ms.assetid: 81b2cdb5-c91a-4a31-9c83-eadc52da5cf0
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: fd78c2f99ca5c8ffe3c753e158ceba3e0c458c5b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="using-objects-that-implement-idisposable"></a><span data-ttu-id="3707a-102">Usando objetos que implementam IDisposable</span><span class="sxs-lookup"><span data-stu-id="3707a-102">Using objects that implement IDisposable</span></span>

<span data-ttu-id="3707a-103">O coletor de lixo do common language runtime recupera a memória usada por objetos gerenciados, mas os tipos que usam recursos não gerenciados implementar o <xref:System.IDisposable> interface para permitir que a memória alocada para esses recursos não gerenciados a ser recuperada.</span><span class="sxs-lookup"><span data-stu-id="3707a-103">The common language runtime's garbage collector reclaims the memory used by managed objects, but types that use unmanaged resources implement the <xref:System.IDisposable> interface to allow the memory allocated to these unmanaged resources to be reclaimed.</span></span> <span data-ttu-id="3707a-104">Após terminar de usar um objeto que implementa <xref:System.IDisposable>, você deverá chamar a implementação de <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> do objeto.</span><span class="sxs-lookup"><span data-stu-id="3707a-104">When you finish using an object that implements <xref:System.IDisposable>, you should call the object's <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="3707a-105">Você pode fazer isso de duas maneiras:</span><span class="sxs-lookup"><span data-stu-id="3707a-105">You can do this in one of two ways:</span></span>  
  
* <span data-ttu-id="3707a-106">Com a instrução `using` do C# ou a instrução `Using` do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="3707a-106">With the C# `using` statement or the Visual Basic `Using` statement.</span></span>  
  
* <span data-ttu-id="3707a-107">Implementando um bloco `try/finally`.</span><span class="sxs-lookup"><span data-stu-id="3707a-107">By implementing a `try/finally` block.</span></span>  

## <a name="the-using-statement"></a><span data-ttu-id="3707a-108">A instrução using</span><span class="sxs-lookup"><span data-stu-id="3707a-108">The using statement</span></span>

<span data-ttu-id="3707a-109">A instrução `using` no C# e a instrução `Using` no Visual Basic simplificam o código que você deve escrever para criar e limpar um objeto.</span><span class="sxs-lookup"><span data-stu-id="3707a-109">The `using` statement in C# and the `Using` statement in Visual Basic simplify the code that you must write to create and clean up an object.</span></span> <span data-ttu-id="3707a-110">A instrução `using` obtém um ou mais recursos, executa as instruções que você especifica e descarta o objeto automaticamente.</span><span class="sxs-lookup"><span data-stu-id="3707a-110">The `using` statement obtains one or more resources, executes the statements that you specify, and automatically disposes of the object.</span></span> <span data-ttu-id="3707a-111">Entretanto, a instrução `using` é útil apenas para os objetos que são usados no escopo do método no qual eles são criados.</span><span class="sxs-lookup"><span data-stu-id="3707a-111">However, the `using` statement is useful only for objects that are used within the scope of the method in which they are constructed.</span></span>  
  
<span data-ttu-id="3707a-112">O exemplo a seguir usa a instrução `using` para criar e liberar um objeto <xref:System.IO.StreamReader?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3707a-112">The following example uses the `using` statement to create and release a <xref:System.IO.StreamReader?displayProperty=nameWithType> object.</span></span>  
  
[!code-csharp[Conceptual.Disposable#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using1.cs#1)]
[!code-vb[Conceptual.Disposable#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using1.vb#1)]  
  
<span data-ttu-id="3707a-113">Observe que, embora a classe <xref:System.IO.StreamReader> implemente a interface <xref:System.IDisposable>, o que indica que ela usa um recurso não gerenciado, o exemplo não chama explicitamente o método <xref:System.IO.StreamReader.Dispose%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3707a-113">Note that although the <xref:System.IO.StreamReader> class implements the <xref:System.IDisposable> interface, which indicates that it uses an unmanaged resource, the example doesn't explicitly call the <xref:System.IO.StreamReader.Dispose%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="3707a-114">Quando o compilador do C# ou do Visual Basic encontra a instrução `using`, ele emite a IL (linguagem intermediária) que equivale ao seguinte código que contém explicitamente um bloco `try/finally`.</span><span class="sxs-lookup"><span data-stu-id="3707a-114">When the C# or Visual Basic compiler encounters the `using` statement, it emits intermediate language (IL) that is equivalent to the following code that explicitly contains a `try/finally` block.</span></span>  
  
[!code-csharp[Conceptual.Disposable#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using3.cs#3)]
[!code-vb[Conceptual.Disposable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using3.vb#3)]  
  
<span data-ttu-id="3707a-115">C# `using` instrução também permite que você adquira vários recursos em uma única instrução, que equivale internamente aninhadas `using` instruções.</span><span class="sxs-lookup"><span data-stu-id="3707a-115">The C# `using` statement also allows you to acquire multiple resources in a single statement, which is internally equivalent to nested `using` statements.</span></span> <span data-ttu-id="3707a-116">O exemplo a seguir cria instancia dois objetos <xref:System.IO.StreamReader> para ler o conteúdo de dois arquivos diferentes.</span><span class="sxs-lookup"><span data-stu-id="3707a-116">The following example instantiates two <xref:System.IO.StreamReader> objects to read the contents of two different files.</span></span>  
  
[!code-csharp[Conceptual.Disposable#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using4.cs#4)]

## <a name="tryfinally-block"></a><span data-ttu-id="3707a-117">Bloco Try/finally</span><span class="sxs-lookup"><span data-stu-id="3707a-117">Try/finally block</span></span>

<span data-ttu-id="3707a-118">Em vez de incluir um bloco `try/finally` em uma instrução `using`, você pode optar por implementar diretamente o bloco `try/finally`.</span><span class="sxs-lookup"><span data-stu-id="3707a-118">Instead of wrapping a `try/finally` block in a `using` statement, you may choose to implement the `try/finally` block directly.</span></span> <span data-ttu-id="3707a-119">Esse pode ser o estilo pessoal de codificação ou talvez você queira fazer isso por um dos seguintes motivos:</span><span class="sxs-lookup"><span data-stu-id="3707a-119">This may be your personal coding style, or you might want to do this for one of the following reasons:</span></span>  
  
* <span data-ttu-id="3707a-120">Para incluir um bloco `catch` para lidar com algumas exceções geradas no bloco `try`.</span><span class="sxs-lookup"><span data-stu-id="3707a-120">To include a `catch` block to handle any exceptions thrown in the `try` block.</span></span> <span data-ttu-id="3707a-121">Caso contrário, todas as exceções geradas pela instrução `using` não são manipuladas, assim como em quaisquer exceções geradas dentro do bloco `using` se um bloco `try/catch` não estiver presente.</span><span class="sxs-lookup"><span data-stu-id="3707a-121">Otherwise, any exceptions thrown by the `using` statement are unhandled, as are any exceptions thrown within the `using` block if a `try/catch` block isn't present.</span></span>  
  
* <span data-ttu-id="3707a-122">Para criar uma instância de um objeto que implementa <xref:System.IDisposable> cujo escopo não é local para o bloco dentro do qual é declarado.</span><span class="sxs-lookup"><span data-stu-id="3707a-122">To instantiate an object that implements <xref:System.IDisposable> whose scope is not local to the block within which it is declared.</span></span>  
  
<span data-ttu-id="3707a-123">O exemplo a seguir é semelhante ao exemplo anterior, exceto que ele usa um `try/catch/finally` blocos para criar uma instância, use e descartar um <xref:System.IO.StreamReader> objeto e para lidar com as exceções geradas pelo <xref:System.IO.StreamReader> construtor e seu <xref:System.IO.StreamReader.ReadToEnd%2A> método.</span><span class="sxs-lookup"><span data-stu-id="3707a-123">The following example is similar to the previous example, except that it uses a `try/catch/finally` block to instantiate, use, and dispose of a <xref:System.IO.StreamReader> object, and to handle any exceptions thrown by the <xref:System.IO.StreamReader> constructor and its <xref:System.IO.StreamReader.ReadToEnd%2A> method.</span></span> <span data-ttu-id="3707a-124">Observe que o código no bloco `finally` verifica se o objeto que implementa <xref:System.IDisposable> não é `null` antes de chamar o método <xref:System.IDisposable.Dispose%2A>.</span><span class="sxs-lookup"><span data-stu-id="3707a-124">Note that the code in the `finally` block checks that the object that implements <xref:System.IDisposable> isn't `null` before it calls the <xref:System.IDisposable.Dispose%2A> method.</span></span> <span data-ttu-id="3707a-125">Não fazer isso poderá levar a uma exceção de <xref:System.NullReferenceException> em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="3707a-125">Failure to do this can result in a <xref:System.NullReferenceException> exception at run time.</span></span>  
  
[!code-csharp[Conceptual.Disposable#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using5.cs#6)]
[!code-vb[Conceptual.Disposable#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using5.vb#6)]  
  
<span data-ttu-id="3707a-126">Você pode seguir este padrão básico se você optar por implementar ou deve implementar um `try/finally` bloquear, como a linguagem de programação não dá suporte uma `using` instrução, mas permite chamadas diretas para o <xref:System.IDisposable.Dispose%2A> método.</span><span class="sxs-lookup"><span data-stu-id="3707a-126">You can follow this basic pattern if you choose to implement or must implement a `try/finally` block, because your programming language doesn't support a `using` statement but does allow direct calls to the <xref:System.IDisposable.Dispose%2A> method.</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="3707a-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3707a-127">See also</span></span>

<span data-ttu-id="3707a-128">[Limpando recursos não gerenciados](../../../docs/standard/garbage-collection/unmanaged.md) </span><span class="sxs-lookup"><span data-stu-id="3707a-128">[Cleaning Up Unmanaged Resources](../../../docs/standard/garbage-collection/unmanaged.md) </span></span>  
<span data-ttu-id="3707a-129">[usando a instrução (referência de c#)](~/docs/csharp/language-reference/keywords/using-statement.md) </span><span class="sxs-lookup"><span data-stu-id="3707a-129">[using Statement (C# Reference)](~/docs/csharp/language-reference/keywords/using-statement.md) </span></span>  
[<span data-ttu-id="3707a-130">Usando a instrução (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3707a-130">Using Statement (Visual Basic)</span></span>](~/docs/visual-basic/language-reference/statements/using-statement.md)