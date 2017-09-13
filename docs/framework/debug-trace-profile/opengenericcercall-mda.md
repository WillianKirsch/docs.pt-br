---
title: MDA openGenericCERCall
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MDAs (managed debugging assistants), CER calls
- open generic CER calls
- constrained execution regions
- openGenericCERCall MDA
- CER calls
- managed debugging assistants (MDAs), CER calls
- generics [.NET Framework], open generic CER calls
ms.assetid: da3e4ff3-2e67-4668-9720-fa776c97407e
caps.latest.revision: 13
author: mairaw
ms.author: mairaw
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 347f9efcf1b0cdaf9cd37bcf6045a42341e4f643
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="opengenericcercall-mda"></a><span data-ttu-id="befe8-102">MDA openGenericCERCall</span><span class="sxs-lookup"><span data-stu-id="befe8-102">openGenericCERCall MDA</span></span>
<span data-ttu-id="befe8-103">O Assistente de Depuração Gerenciado de `openGenericCERCall` é ativado para avisar que um gráfico de CER (região de execução restrita) com variáveis de tipo genérico no método raiz está sendo processado em tempo de compilação JIT ou tempo de geração de imagem nativa e pelo menos uma das variáveis de tipo genérico é um tipo de referência de objeto.</span><span class="sxs-lookup"><span data-stu-id="befe8-103">The `openGenericCERCall` managed debugging assistant is activated to warn that a constrained execution region (CER) graph with generic type variables at the root method is being processed at JIT-compilation or native image generation time and at least one of the generic type variables is an object reference type.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="befe8-104">Sintomas</span><span class="sxs-lookup"><span data-stu-id="befe8-104">Symptoms</span></span>  
 <span data-ttu-id="befe8-105">O código de CER não é executado quando um thread é anulado ou um domínio do aplicativo é descarregado.</span><span class="sxs-lookup"><span data-stu-id="befe8-105">CER code does not run when a thread is aborted or when an application domain is unloaded.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="befe8-106">Causa</span><span class="sxs-lookup"><span data-stu-id="befe8-106">Cause</span></span>  
 <span data-ttu-id="befe8-107">Em tempo de compilação JIT, uma instanciação que contém um tipo de referência de objeto é apenas representativo porque o código resultante é compartilhado e cada uma das variáveis de tipo de referência de objeto pode ser qualquer tipo de referência de objeto.</span><span class="sxs-lookup"><span data-stu-id="befe8-107">At JIT-compilation time, an instantiation containing an object reference type is only representative because the resultant code is shared, and each of the object reference type variables might be any object reference type.</span></span> <span data-ttu-id="befe8-108">Isso pode impedir a preparação antecipada de alguns recursos de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="befe8-108">This can prevent the preparation of some run-time resources ahead of time.</span></span>  
  
 <span data-ttu-id="befe8-109">Em particular, os métodos com variáveis de tipo genérico podem lentamente alocar recursos em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="befe8-109">In particular, methods with generic type variables can lazily allocate resources in the background.</span></span> <span data-ttu-id="befe8-110">Essas são chamadas de entradas de dicionário genéricas.</span><span class="sxs-lookup"><span data-stu-id="befe8-110">These are referred to as generic dictionary entries.</span></span> <span data-ttu-id="befe8-111">Por exemplo, para a instrução `List<T> list = new List<T>();` em que `T` é uma variável de tipo genérico, o tempo de execução deve procurar e possivelmente criar a instanciação exata em tempo de execução, por exemplo, `List<Object>, List<String>` e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="befe8-111">For instance, for the statement `List<T> list = new List<T>();` where `T` is a generic type variable the runtime must look up and possibly create the exact instantiation at run time, for example, `List<Object>, List<String>`,and so forth.</span></span> <span data-ttu-id="befe8-112">Isso pode falhar por vários motivos fora do controle do desenvolvedor, tais como falta de memória.</span><span class="sxs-lookup"><span data-stu-id="befe8-112">This can fail for a variety of reasons beyond the developer's control, such as running out of memory.</span></span>  
  
 <span data-ttu-id="befe8-113">Esse MDA só deve ser ativado em tempo de compilação JIT e não quando há uma instanciação exata.</span><span class="sxs-lookup"><span data-stu-id="befe8-113">This MDA should only be activated at JIT-compilation time, not when there is an exact instantiation.</span></span>  
  
 <span data-ttu-id="befe8-114">Quando esse MDA é ativado, os sintomas prováveis são que as CERs não estejam funcionando para as instanciações incorretas.</span><span class="sxs-lookup"><span data-stu-id="befe8-114">When this MDA is activated, the likely symptoms are that CERs are not functional for the bad instantiations.</span></span> <span data-ttu-id="befe8-115">Na verdade, o tempo de execução não tentou implementar uma CER sob as circunstâncias que causaram a ativação do MDA.</span><span class="sxs-lookup"><span data-stu-id="befe8-115">In fact, the runtime has not attempted to implement a CER under the circumstances that caused the MDA to be activated.</span></span> <span data-ttu-id="befe8-116">Portanto, se o desenvolvedor usa uma instanciação compartilhada do CER, então os erros de compilação JIT, erros de carregamento de tipo genéricos ou anulações do thread dentro da região da CER pretendida não são detectados.</span><span class="sxs-lookup"><span data-stu-id="befe8-116">So if the developer uses a shared instantiation of the CER, then JIT-compilation errors, generics type loading errors, or thread aborts within the region of the intended CER are not caught.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="befe8-117">Resolução</span><span class="sxs-lookup"><span data-stu-id="befe8-117">Resolution</span></span>  
 <span data-ttu-id="befe8-118">Não use variáveis de tipo genérico do tipo de referência de objeto para métodos que podem conter uma CER.</span><span class="sxs-lookup"><span data-stu-id="befe8-118">Do not use generic type variables that are of object reference type for methods that may contain a CER.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="befe8-119">Efeito sobre o tempo de execução</span><span class="sxs-lookup"><span data-stu-id="befe8-119">Effect on the Runtime</span></span>  
 <span data-ttu-id="befe8-120">Esse MDA não tem efeito sobre o CLR.</span><span class="sxs-lookup"><span data-stu-id="befe8-120">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="befe8-121">Saída</span><span class="sxs-lookup"><span data-stu-id="befe8-121">Output</span></span>  
 <span data-ttu-id="befe8-122">A seguir temos uma amostra de saída desse MDA.</span><span class="sxs-lookup"><span data-stu-id="befe8-122">The following is a sample of output from this MDA.</span></span>  
  
 `Method 'GenericMethodWithCer', which contains at least one constrained execution region, cannot be prepared automatically since it has one or more unbound generic type parameters.`  
  
 `The caller must ensure this method is prepared explicitly at run time prior to execution.`  
  
 `method name="GenericMethodWithCer"`  
  
 `declaringType name="OpenGenericCERCall"`  
  
## <a name="configuration"></a><span data-ttu-id="befe8-123">Configuração</span><span class="sxs-lookup"><span data-stu-id="befe8-123">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <openGenericCERCall/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="befe8-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="befe8-124">Example</span></span>  
 <span data-ttu-id="befe8-125">O código CER não é executado.</span><span class="sxs-lookup"><span data-stu-id="befe8-125">The CER code is not executed.</span></span>  
  
```  
using System;  
using System.Collections.Generic;  
using System.Runtime.CompilerServices;  
  
class Program  
{  
    static void Main(string[] args)  
    {  
        CallGenericMethods();  
    }  
    static void CallGenericMethods()  
    {  
        // This call is correct. The instantiation of the method  
        // contains only nonreference types.  
        MyClass.GenericMethodWithCer<int>();  
  
        // This call is incorrect. A shared version of the method that  
        // cannot be completely analyzed will be JIT-compiled. The   
        // MDA will be activated at JIT-compile time, not at run time.  
        MyClass.GenericMethodWithCer<String>();  
    }  
}  
  
    class MyClass  
{  
    public static void GenericMethodWithCer<T>()  
    {  
        RuntimeHelpers.PrepareConstrainedRegions();  
        try  
        {  
  
        }  
        finally  
        {  
            // This is the start of the CER.  
            Console.WriteLine("In finally block.");  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="befe8-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="befe8-126">See Also</span></span>  
 <span data-ttu-id="befe8-127"><xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A></span><span class="sxs-lookup"><span data-stu-id="befe8-127"><xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A></span></span>   
 <span data-ttu-id="befe8-128"><xref:System.Runtime.ConstrainedExecution></span><span class="sxs-lookup"><span data-stu-id="befe8-128"><xref:System.Runtime.ConstrainedExecution></span></span>   
 [<span data-ttu-id="befe8-129">Diagnosticando erros com Assistentes de Depuração Gerenciados</span><span class="sxs-lookup"><span data-stu-id="befe8-129">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
