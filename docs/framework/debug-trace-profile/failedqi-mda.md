---
title: MDA failedQI
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
- failed QueryInterface
- FailedQI MDA
- QueryInterface call failures
- MDAs (managed debugging assistants), failed QueryInterface
- managed debugging assistants (MDAs), failed QueryInterface
ms.assetid: 902dc863-34b3-477c-b433-b8a6bb6133c6
caps.latest.revision: 15
author: mairaw
ms.author: mairaw
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 313676abe0732fcd4f3285c5c1f935302695d3cc
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="failedqi-mda"></a><span data-ttu-id="69cfa-102">MDA failedQI</span><span class="sxs-lookup"><span data-stu-id="69cfa-102">failedQI MDA</span></span>
<span data-ttu-id="69cfa-103">O MDA (assistente para depuração gerenciada) `failedQI` é ativado quando o tempo de execução chama `QueryInterface` em um ponteiro de interface COM em nome de um RCW (Runtime Callable Wrapper) e a chamada `QueryInterface` falha.</span><span class="sxs-lookup"><span data-stu-id="69cfa-103">The `failedQI` managed debugging assistant (MDA) is activated when the runtime calls `QueryInterface` on a COM interface pointer on behalf of a runtime callable wrapper (RCW), and the `QueryInterface` call fails.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="69cfa-104">Sintomas</span><span class="sxs-lookup"><span data-stu-id="69cfa-104">Symptoms</span></span>  
 <span data-ttu-id="69cfa-105">Uma conversão em um RCW falha ou uma chamada ao COM em um RCW falha inesperadamente.</span><span class="sxs-lookup"><span data-stu-id="69cfa-105">A cast on an RCW fails, or a call to COM from an RCW fails unexpectedly.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="69cfa-106">Causa</span><span class="sxs-lookup"><span data-stu-id="69cfa-106">Cause</span></span>  
  
-   <span data-ttu-id="69cfa-107">A chamada é feita do contexto incorreto.</span><span class="sxs-lookup"><span data-stu-id="69cfa-107">The call is made from the wrong context.</span></span>  
  
-   <span data-ttu-id="69cfa-108">O proxy registrado está falhando a chamada `QueryInterface` porque houve uma tentativa de realizar a chamada no contexto incorreto.</span><span class="sxs-lookup"><span data-stu-id="69cfa-108">The registered proxy is failing the `QueryInterface` call because the call was attempted in the wrong context.</span></span>  
  
-   <span data-ttu-id="69cfa-109">Um proxy de propriedade do OLE retornou uma falha HRESULT.</span><span class="sxs-lookup"><span data-stu-id="69cfa-109">An OLE-owned proxy returned a failure HRESULT.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="69cfa-110">Resolução</span><span class="sxs-lookup"><span data-stu-id="69cfa-110">Resolution</span></span>  
 <span data-ttu-id="69cfa-111">Consulte a documentação do MSDN sobre as regras do COM.</span><span class="sxs-lookup"><span data-stu-id="69cfa-111">See the MSDN documentation on COM rules.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="69cfa-112">Efeito sobre o tempo de execução</span><span class="sxs-lookup"><span data-stu-id="69cfa-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="69cfa-113">Se uma chamada `QueryInterface` falhar, o contexto será alternado e haverá uma tentativa de realizar a chamada `QueryInterface` novamente para ver se um contexto incorreto estava com uma falha.</span><span class="sxs-lookup"><span data-stu-id="69cfa-113">If a `QueryInterface` call fails, the context is switched and the `QueryInterface` call is attempted again to see if an incorrect context was at fault.</span></span>  
  
## <a name="output"></a><span data-ttu-id="69cfa-114">Saída</span><span class="sxs-lookup"><span data-stu-id="69cfa-114">Output</span></span>  
 <span data-ttu-id="69cfa-115">O nome gerenciado da interface, o GUID da interface e o HRESULT da falha.</span><span class="sxs-lookup"><span data-stu-id="69cfa-115">The managed name of the interface, the GUID of the interface, and the HRESULT of the failure.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="69cfa-116">Configuração</span><span class="sxs-lookup"><span data-stu-id="69cfa-116">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <failedQI/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="69cfa-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="69cfa-117">See Also</span></span>  
 <span data-ttu-id="69cfa-118"><xref:System.Runtime.InteropServices.MarshalAsAttribute></span><span class="sxs-lookup"><span data-stu-id="69cfa-118"><xref:System.Runtime.InteropServices.MarshalAsAttribute></span></span>   
 <span data-ttu-id="69cfa-119">[Diagnosticando erros com Assistentes de Depuração Gerenciados](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md) </span><span class="sxs-lookup"><span data-stu-id="69cfa-119">[Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md) </span></span>  
 [<span data-ttu-id="69cfa-120">Marshaling de interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="69cfa-120">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
