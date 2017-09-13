---
title: "Diagnosticando erros com assistentes de depuração gerenciados"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- EHMDA
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- run-time error debugging
- managed code, run-time debugging
- resource debugging
- registry, MDAs
- common language runtime, debugging
- MDAs (managed debugging assistants)
- configuration files [.NET Framework], debugging runtime events
- messages, managed debugging assistants
- application configuration files, managed debugging assistants
- debugging [.NET Framework], managed debugging assistants
- environment variables, MDAs
- access violation debugging [.NET Framework]
- diagnostics, managed debugging assistants
- unmanaged code, run-time debugging
- default debug output stream
- memory, debugging
- app.config files, managed debugging assistants
- managed debugging assistants (MDAs)
- debugging [.NET Framework], run-time errors
- trapping events
- runtime, error debugging
- disabling MDAs
- output, managed debugging assistants
- errors [.NET Framework], managed debugging assistants
ms.assetid: 76994ee6-9fa9-4059-b813-26578d24427c
caps.latest.revision: 63
author: mairaw
ms.author: mairaw
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 8afc1ec3d5a1dab4412b16826bb32829f9b42263
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="diagnosing-errors-with-managed-debugging-assistants"></a><span data-ttu-id="f34f9-102">Diagnosticando erros com assistentes de depuração gerenciados</span><span class="sxs-lookup"><span data-stu-id="f34f9-102">Diagnosing Errors with Managed Debugging Assistants</span></span>
<span data-ttu-id="f34f9-103">Os MDAs (Assistentes para depuração gerenciada) são recursos de depuração que trabalham com o CLR (Common Language Runtime) para fornecer informações sobre o estado do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="f34f9-103">Managed debugging assistants (MDAs) are debugging aids that work in conjunction with the common language runtime (CLR) to provide information on runtime state.</span></span> <span data-ttu-id="f34f9-104">Os assistentes geram mensagens informativas sobre eventos de tempo de execução que não podem ser interceptados de outro modo.</span><span class="sxs-lookup"><span data-stu-id="f34f9-104">The assistants generate informational messages about runtime events that you cannot otherwise trap.</span></span> <span data-ttu-id="f34f9-105">É possível usar MDAs para isolar bugs de aplicativos difíceis de encontrar que ocorrem durante a transição entre código gerenciado e não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="f34f9-105">You can use MDAs to isolate hard-to-find application bugs that occur when transitioning between managed and unmanaged code.</span></span> <span data-ttu-id="f34f9-106">É possível habilitar ou desabilitar todos os MDAs adicionando uma chave ao Registro do Windows ou definindo uma variável de ambiente.</span><span class="sxs-lookup"><span data-stu-id="f34f9-106">You can enable or disable all MDAs by adding a key to the Windows registry or by setting an environment variable.</span></span> <span data-ttu-id="f34f9-107">Você pode habilitar MDAs específicos usando definições de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f34f9-107">You can enable specific MDAs by using application configuration settings.</span></span> <span data-ttu-id="f34f9-108">É possível definir configurações adicionais para alguns MDAs individuais no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f34f9-108">You can set additional configuration settings for some individual MDAs in the application's configuration file.</span></span> <span data-ttu-id="f34f9-109">Como esses arquivos de configuração são analisados quando o tempo de execução é carregado, você deve habilitar o MDA antes da inicialização do aplicativo gerenciado.</span><span class="sxs-lookup"><span data-stu-id="f34f9-109">Because these configuration files are parsed when the runtime is loaded, you must enable the MDA before the managed application starts.</span></span> <span data-ttu-id="f34f9-110">Não será possível habilitá-lo para aplicativos já iniciados.</span><span class="sxs-lookup"><span data-stu-id="f34f9-110">You cannot enable it for applications that have already started.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f34f9-111">Quando é habilitado, um MDA permanece ativo mesmo quando o código não está em execução em um depurador.</span><span class="sxs-lookup"><span data-stu-id="f34f9-111">When an MDA is enabled, it is active even when your code is not executing under a debugger.</span></span> <span data-ttu-id="f34f9-112">Se um evento de MDA for acionado quando um depurador não estiver presente, a mensagem do evento será apresentada em uma caixa de diálogo de exceção sem tratamento, ainda que não seja uma exceção sem tratamento.</span><span class="sxs-lookup"><span data-stu-id="f34f9-112">If an MDA event is raised when a debugger is not present, the event message is presented in an unhandled exception dialog box, although it is not an unhandled exception.</span></span> <span data-ttu-id="f34f9-113">Para evitar a caixa de diálogo, remova as configurações de habilitação de MDA quando o código não estiver em execução em um ambiente de depuração.</span><span class="sxs-lookup"><span data-stu-id="f34f9-113">To avoid the dialog box, remove the MDA-enabling settings when your code is not executing in a debugging environment.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f34f9-114">Quando o código estiver em execução no IDE (ambiente de desenvolvimento integrado) do Visual Studio, será possível evitar a exibição da caixa de diálogo da exceção para eventos de MDA específicos.</span><span class="sxs-lookup"><span data-stu-id="f34f9-114">When your code is executing in the Visual Studio integrated development environment (IDE), you can avoid the exception dialog box that appears for specific MDA events.</span></span> <span data-ttu-id="f34f9-115">Para fazer isso, no menu **Depurar**, clique em **Exceções**.</span><span class="sxs-lookup"><span data-stu-id="f34f9-115">To do that, on the **Debug** menu, click **Exceptions**.</span></span> <span data-ttu-id="f34f9-116">(Se o menu **Depurar** não contiver um comando **Exceções**, clique em **Personalizar** no menu **Ferramentas** para adicioná-lo.) Na caixa de diálogo **Exceções**, expanda a lista **Assistentes para Depuração Gerenciada** e, em seguida, desmarque a caixa de seleção **Geradas** do MDA individual.</span><span class="sxs-lookup"><span data-stu-id="f34f9-116">(If the **Debug** menu does not contain an **Exceptions** command, click **Customize** on the **Tools** menu to add it.) In the **Exceptions** dialog box, expand the **Managed Debugging Assistants** list, and then clear the **Thrown** check box for the individual MDA.</span></span> <span data-ttu-id="f34f9-117">Por exemplo, para evitar a caixa de diálogo de exceção de um [contextSwitchDeadlock](../../../docs/framework/debug-trace-profile/contextswitchdeadlock-mda.md), desmarque a caixa de seleção **Geradas** ao lado de seu nome na lista **Assistentes para Depuração Gerenciada**.</span><span class="sxs-lookup"><span data-stu-id="f34f9-117">For example, to avoid the exception dialog box for a [contextSwitchDeadlock](../../../docs/framework/debug-trace-profile/contextswitchdeadlock-mda.md) clear the **Thrown** check box next to its name in the **Managed Debugging Assistants** list.</span></span> <span data-ttu-id="f34f9-118">Também é possível usar essa caixa de diálogo para habilitar a exibição de caixas de diálogo de exceção do MDA.</span><span class="sxs-lookup"><span data-stu-id="f34f9-118">You can also use this dialog box to enable the display of MDA exception dialog boxes.</span></span>  
  
 <span data-ttu-id="f34f9-119">A tabela a seguir lista os MDAs que acompanham o .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f34f9-119">The following table lists the MDAs that ship with the .NET Framework.</span></span>  
  
|||  
|-|-|  
|[<span data-ttu-id="f34f9-120">asynchronousThreadAbort</span><span class="sxs-lookup"><span data-stu-id="f34f9-120">asynchronousThreadAbort</span></span>](../../../docs/framework/debug-trace-profile/asynchronousthreadabort-mda.md)|[<span data-ttu-id="f34f9-121">bindingFailure</span><span class="sxs-lookup"><span data-stu-id="f34f9-121">bindingFailure</span></span>](../../../docs/framework/debug-trace-profile/bindingfailure-mda.md)|  
|[<span data-ttu-id="f34f9-122">callbackOnCollectedDelegate</span><span class="sxs-lookup"><span data-stu-id="f34f9-122">callbackOnCollectedDelegate</span></span>](../../../docs/framework/debug-trace-profile/callbackoncollecteddelegate-mda.md)|[<span data-ttu-id="f34f9-123">contextSwitchDeadlock</span><span class="sxs-lookup"><span data-stu-id="f34f9-123">contextSwitchDeadlock</span></span>](../../../docs/framework/debug-trace-profile/contextswitchdeadlock-mda.md)|  
|[<span data-ttu-id="f34f9-124">dangerousThreadingAPI</span><span class="sxs-lookup"><span data-stu-id="f34f9-124">dangerousThreadingAPI</span></span>](../../../docs/framework/debug-trace-profile/dangerousthreadingapi-mda.md)|[<span data-ttu-id="f34f9-125">dateTimeInvalidLocalFormat</span><span class="sxs-lookup"><span data-stu-id="f34f9-125">dateTimeInvalidLocalFormat</span></span>](../../../docs/framework/debug-trace-profile/datetimeinvalidlocalformat-mda.md)|  
|[<span data-ttu-id="f34f9-126">dirtyCastAndCallOnInterface</span><span class="sxs-lookup"><span data-stu-id="f34f9-126">dirtyCastAndCallOnInterface</span></span>](../../../docs/framework/debug-trace-profile/dirtycastandcalloninterface-mda.md)|[<span data-ttu-id="f34f9-127">disconnectedContext</span><span class="sxs-lookup"><span data-stu-id="f34f9-127">disconnectedContext</span></span>](../../../docs/framework/debug-trace-profile/disconnectedcontext-mda.md)|  
|[<span data-ttu-id="f34f9-128">dllMainReturnsFalse</span><span class="sxs-lookup"><span data-stu-id="f34f9-128">dllMainReturnsFalse</span></span>](../../../docs/framework/debug-trace-profile/dllmainreturnsfalse-mda.md)|[<span data-ttu-id="f34f9-129">exceptionSwallowedOnCallFromCom</span><span class="sxs-lookup"><span data-stu-id="f34f9-129">exceptionSwallowedOnCallFromCom</span></span>](../../../docs/framework/debug-trace-profile/exceptionswallowedoncallfromcom-mda.md)|  
|[<span data-ttu-id="f34f9-130">failedQI</span><span class="sxs-lookup"><span data-stu-id="f34f9-130">failedQI</span></span>](../../../docs/framework/debug-trace-profile/failedqi-mda.md)|[<span data-ttu-id="f34f9-131">fatalExecutionEngineError</span><span class="sxs-lookup"><span data-stu-id="f34f9-131">fatalExecutionEngineError</span></span>](../../../docs/framework/debug-trace-profile/fatalexecutionengineerror-mda.md)|  
|[<span data-ttu-id="f34f9-132">gcManagedToUnmanaged</span><span class="sxs-lookup"><span data-stu-id="f34f9-132">gcManagedToUnmanaged</span></span>](../../../docs/framework/debug-trace-profile/gcmanagedtounmanaged-mda.md)|[<span data-ttu-id="f34f9-133">gcUnmanagedToManaged</span><span class="sxs-lookup"><span data-stu-id="f34f9-133">gcUnmanagedToManaged</span></span>](../../../docs/framework/debug-trace-profile/gcunmanagedtomanaged-mda.md)|  
|[<span data-ttu-id="f34f9-134">illegalPrepareConstrainedRegion</span><span class="sxs-lookup"><span data-stu-id="f34f9-134">illegalPrepareConstrainedRegion</span></span>](../../../docs/framework/debug-trace-profile/illegalprepareconstrainedregion-mda.md)|[<span data-ttu-id="f34f9-135">invalidApartmentStateChange</span><span class="sxs-lookup"><span data-stu-id="f34f9-135">invalidApartmentStateChange</span></span>](../../../docs/framework/debug-trace-profile/invalidapartmentstatechange-mda.md)|  
|[<span data-ttu-id="f34f9-136">invalidCERCall</span><span class="sxs-lookup"><span data-stu-id="f34f9-136">invalidCERCall</span></span>](../../../docs/framework/debug-trace-profile/invalidcercall-mda.md)|[<span data-ttu-id="f34f9-137">invalidFunctionPointerInDelegate</span><span class="sxs-lookup"><span data-stu-id="f34f9-137">invalidFunctionPointerInDelegate</span></span>](../../../docs/framework/debug-trace-profile/invalidfunctionpointerindelegate-mda.md)|  
|[<span data-ttu-id="f34f9-138">invalidGCHandleCookie</span><span class="sxs-lookup"><span data-stu-id="f34f9-138">invalidGCHandleCookie</span></span>](../../../docs/framework/debug-trace-profile/invalidgchandlecookie-mda.md)|[<span data-ttu-id="f34f9-139">invalidIUnknown</span><span class="sxs-lookup"><span data-stu-id="f34f9-139">invalidIUnknown</span></span>](../../../docs/framework/debug-trace-profile/invalidiunknown-mda.md)|  
|[<span data-ttu-id="f34f9-140">invalidMemberDeclaration</span><span class="sxs-lookup"><span data-stu-id="f34f9-140">invalidMemberDeclaration</span></span>](../../../docs/framework/debug-trace-profile/invalidmemberdeclaration-mda.md)|[<span data-ttu-id="f34f9-141">invalidOverlappedToPinvoke</span><span class="sxs-lookup"><span data-stu-id="f34f9-141">invalidOverlappedToPinvoke</span></span>](../../../docs/framework/debug-trace-profile/invalidoverlappedtopinvoke-mda.md)|  
|[<span data-ttu-id="f34f9-142">invalidVariant</span><span class="sxs-lookup"><span data-stu-id="f34f9-142">invalidVariant</span></span>](../../../docs/framework/debug-trace-profile/invalidvariant-mda.md)|[<span data-ttu-id="f34f9-143">jitCompilationStart</span><span class="sxs-lookup"><span data-stu-id="f34f9-143">jitCompilationStart</span></span>](../../../docs/framework/debug-trace-profile/jitcompilationstart-mda.md)|  
|[<span data-ttu-id="f34f9-144">loaderLock</span><span class="sxs-lookup"><span data-stu-id="f34f9-144">loaderLock</span></span>](../../../docs/framework/debug-trace-profile/loaderlock-mda.md)|[<span data-ttu-id="f34f9-145">loadFromContext</span><span class="sxs-lookup"><span data-stu-id="f34f9-145">loadFromContext</span></span>](../../../docs/framework/debug-trace-profile/loadfromcontext-mda.md)|  
|[<span data-ttu-id="f34f9-146">marshalCleanupError</span><span class="sxs-lookup"><span data-stu-id="f34f9-146">marshalCleanupError</span></span>](../../../docs/framework/debug-trace-profile/marshalcleanuperror-mda.md)|[<span data-ttu-id="f34f9-147">marshaling</span><span class="sxs-lookup"><span data-stu-id="f34f9-147">marshaling</span></span>](../../../docs/framework/debug-trace-profile/marshaling-mda.md)|  
|[<span data-ttu-id="f34f9-148">memberInfoCacheCreation</span><span class="sxs-lookup"><span data-stu-id="f34f9-148">memberInfoCacheCreation</span></span>](../../../docs/framework/debug-trace-profile/memberinfocachecreation-mda.md)|[<span data-ttu-id="f34f9-149">moduloObjectHashcode</span><span class="sxs-lookup"><span data-stu-id="f34f9-149">moduloObjectHashcode</span></span>](../../../docs/framework/debug-trace-profile/moduloobjecthashcode-mda.md)|  
|[<span data-ttu-id="f34f9-150">nonComVisibleBaseClass</span><span class="sxs-lookup"><span data-stu-id="f34f9-150">nonComVisibleBaseClass</span></span>](../../../docs/framework/debug-trace-profile/noncomvisiblebaseclass-mda.md)|[<span data-ttu-id="f34f9-151">notMarshalable</span><span class="sxs-lookup"><span data-stu-id="f34f9-151">notMarshalable</span></span>](../../../docs/framework/debug-trace-profile/notmarshalable-mda.md)|  
|[<span data-ttu-id="f34f9-152">openGenericCERCall</span><span class="sxs-lookup"><span data-stu-id="f34f9-152">openGenericCERCall</span></span>](../../../docs/framework/debug-trace-profile/opengenericcercall-mda.md)|[<span data-ttu-id="f34f9-153">overlappedFreeError</span><span class="sxs-lookup"><span data-stu-id="f34f9-153">overlappedFreeError</span></span>](../../../docs/framework/debug-trace-profile/overlappedfreeerror-mda.md)|  
|[<span data-ttu-id="f34f9-154">pInvokeLog</span><span class="sxs-lookup"><span data-stu-id="f34f9-154">pInvokeLog</span></span>](../../../docs/framework/debug-trace-profile/pinvokelog-mda.md)|[<span data-ttu-id="f34f9-155">pInvokeStackImbalance</span><span class="sxs-lookup"><span data-stu-id="f34f9-155">pInvokeStackImbalance</span></span>](../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md)|  
|[<span data-ttu-id="f34f9-156">raceOnRCWCleanup</span><span class="sxs-lookup"><span data-stu-id="f34f9-156">raceOnRCWCleanup</span></span>](../../../docs/framework/debug-trace-profile/raceonrcwcleanup-mda.md)|[<span data-ttu-id="f34f9-157">reentrancy</span><span class="sxs-lookup"><span data-stu-id="f34f9-157">reentrancy</span></span>](../../../docs/framework/debug-trace-profile/reentrancy-mda.md)|  
|[<span data-ttu-id="f34f9-158">releaseHandleFailed</span><span class="sxs-lookup"><span data-stu-id="f34f9-158">releaseHandleFailed</span></span>](../../../docs/framework/debug-trace-profile/releasehandlefailed-mda.md)|[<span data-ttu-id="f34f9-159">reportAvOnComRelease</span><span class="sxs-lookup"><span data-stu-id="f34f9-159">reportAvOnComRelease</span></span>](../../../docs/framework/debug-trace-profile/reportavoncomrelease-mda.md)|  
|[<span data-ttu-id="f34f9-160">streamWriterBufferedDataLost</span><span class="sxs-lookup"><span data-stu-id="f34f9-160">streamWriterBufferedDataLost</span></span>](../../../docs/framework/debug-trace-profile/streamwriterbuffereddatalost-mda.md)|[<span data-ttu-id="f34f9-161">virtualCERCall</span><span class="sxs-lookup"><span data-stu-id="f34f9-161">virtualCERCall</span></span>](../../../docs/framework/debug-trace-profile/virtualcercall-mda.md)|  
  
 <span data-ttu-id="f34f9-162">Por padrão, o .NET Framework ativa um subconjunto de MDAs para todos os depuradores gerenciados.</span><span class="sxs-lookup"><span data-stu-id="f34f9-162">By default, the .NET Framework activates a subset of MDAs for all managed debuggers.</span></span> <span data-ttu-id="f34f9-163">Exiba o conjunto padrão no Visual Studio clicando em **Exceções** no menu **Depurar** e expandindo a lista **Assistentes para Depuração Gerenciada**.</span><span class="sxs-lookup"><span data-stu-id="f34f9-163">You can view the default set in Visual Studio by clicking **Exceptions** on the **Debug** menu and expanding the **Managed Debugging Assistants** list.</span></span>  
  
## <a name="enabling-and-disabling-mdas"></a><span data-ttu-id="f34f9-164">Habilitando e desabilitando MDAs</span><span class="sxs-lookup"><span data-stu-id="f34f9-164">Enabling and Disabling MDAs</span></span>  
 <span data-ttu-id="f34f9-165">É possível habilitar e desabilitar MDAs usando uma chave do Registro, uma variável de ambiente e as definições de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f34f9-165">You can enable and disable MDAs by using a registry key, an environment variable, and application configuration settings.</span></span> <span data-ttu-id="f34f9-166">Você deve habilitar a chave do Registro ou a variável de ambiente para usar as definições de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f34f9-166">You must enable either the registry key or the environment variable to use the application configuration settings.</span></span>  
  
 <span data-ttu-id="f34f9-167">No Visual Studio 2005 e em versões posteriores, quando o processo de hospedagem está habilitado, não é possível desabilitar MDAs que estejam no conjunto padrão ou habilitar MDAs que não estejam no conjunto padrão.</span><span class="sxs-lookup"><span data-stu-id="f34f9-167">In Visual Studio 2005 and later versions, when the hosting process is enabled, you cannot disable MDAs that are in the default set or enable MDAs that are not in the default set.</span></span> <span data-ttu-id="f34f9-168">Como é habilitado por padrão, o processo de hospedagem deve ser desabilitado explicitamente.</span><span class="sxs-lookup"><span data-stu-id="f34f9-168">The hosting process is enabled by default, so it must be explicitly disabled.</span></span>  
  
 <span data-ttu-id="f34f9-169">Para desabilitar o processo de hospedagem no Visual Studio, faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="f34f9-169">To disable the hosting process in Visual Studio, do the following:</span></span>  
  
1.  <span data-ttu-id="f34f9-170">No **Gerenciador de Soluções**, selecione um projeto.</span><span class="sxs-lookup"><span data-stu-id="f34f9-170">In **Solution Explorer**, select a project.</span></span>  
  
2.  <span data-ttu-id="f34f9-171">No menu **Projeto**, clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="f34f9-171">On the **Project** menu, click **Properties**.</span></span>  
  
     <span data-ttu-id="f34f9-172">A janela **Designer de Projeto** é exibida.</span><span class="sxs-lookup"><span data-stu-id="f34f9-172">The **Project Designer** window appears.</span></span>  
  
3.  <span data-ttu-id="f34f9-173">Clique na guia **Depurar**.</span><span class="sxs-lookup"><span data-stu-id="f34f9-173">Click the **Debug** tab.</span></span>  
  
4.  <span data-ttu-id="f34f9-174">Na seção **Habilitar Depuradores**, desmarque a caixa de seleção **Habilitar o processo de hospedagem do Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="f34f9-174">In the **Enable Debuggers** section, clear the **Enable the Visual Studio hosting process** check box.</span></span>  
  
 <span data-ttu-id="f34f9-175">Porém, a desabilitação do processo de hospedagem pode afetar o desempenho.</span><span class="sxs-lookup"><span data-stu-id="f34f9-175">However, disabling the hosting process can affect performance.</span></span> <span data-ttu-id="f34f9-176">Você pode evitar a necessidade de desabilitar MDAs, impedindo que o Visual Studio exiba a caixa de diálogo MDA sempre que uma notificação for recebida.</span><span class="sxs-lookup"><span data-stu-id="f34f9-176">You can avoid the need to disable MDAs by preventing Visual Studio from displaying the MDA dialog box whenever an MDA notification is received.</span></span> <span data-ttu-id="f34f9-177">Para fazer isso, clique em **Exceções** no menu **Depurar**, expanda a lista **Assistentes para Depuração Gerenciada** e, em seguida, marque ou desmarque a caixa de seleção **Geradas** do MDA individual.</span><span class="sxs-lookup"><span data-stu-id="f34f9-177">To do that, click **Exceptions** on the **Debug** menu, expand the **Managed Debugging Assistants** list, and then select or clear the **Thrown** check box for the individual MDA.</span></span>  
  
### <a name="enabling-and-disabling-mdas-by-using-a-registry-key"></a><span data-ttu-id="f34f9-178">Habilitando e desabilitando MDAs usando uma chave do Registro</span><span class="sxs-lookup"><span data-stu-id="f34f9-178">Enabling and Disabling MDAs by Using a Registry Key</span></span>  
 <span data-ttu-id="f34f9-179">Habilite os MDAs adicionando a subchave HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\MDA (digite REG_SZ, valor 1) no Registro do Windows.</span><span class="sxs-lookup"><span data-stu-id="f34f9-179">You can enable MDAs by adding the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\MDA subkey (type REG_SZ, value 1) in the Windows registry.</span></span> <span data-ttu-id="f34f9-180">Copie o exemplo a seguir em um arquivo de texto chamado MDAEnable.reg. Abra o Editor do Registro do Windows (RegEdit.exe) e, no menu **Arquivo**, escolha **Importar**.</span><span class="sxs-lookup"><span data-stu-id="f34f9-180">Copy the following example into a text file named MDAEnable.reg. Open the Windows Registry Editor (RegEdit.exe) and from the **File** menu choose **Import**.</span></span> <span data-ttu-id="f34f9-181">Selecione o arquivo MDAEnable.reg para habilitar MDAs nesse computador.</span><span class="sxs-lookup"><span data-stu-id="f34f9-181">Select the MDAEnable.reg  file to enable MDAs on that computer.</span></span> <span data-ttu-id="f34f9-182">A definição da subchave com o valor de cadeia de caracteres 1 (e não o valor DWORD 1) habilita a leitura das configurações do MDA por meio do arquivo *ApplicationName.suffix*.mda.config file.</span><span class="sxs-lookup"><span data-stu-id="f34f9-182">Setting the subkey to string value of 1 (not DWORD value of 1) enables the reading of MDA settings from the *ApplicationName.suffix*.mda.config file.</span></span> <span data-ttu-id="f34f9-183">(Por exemplo, o arquivo de configuração do MDA para o Bloco de Notas se chamaria notepad.exe.mda.config)</span><span class="sxs-lookup"><span data-stu-id="f34f9-183">(For example the MDA configuration file for Notepad would be named notepad.exe.mda.config)</span></span>  
  
```  
Windows Registry Editor Version 5.00  
  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework]  
"MDA"="1"  
```  
  
 <span data-ttu-id="f34f9-184">Se o computador estiver executando um aplicativo de 32 bits em um sistema operacional de 64 bits, a chave do MDA deverá ser definida da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="f34f9-184">If the computer is running a 32-bit application on a 64-bit operating system, then the MDA key should be set like the following:</span></span>  
  
```  
      Windows Registry Editor Version 5.00   
  
[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\.NETFramework]  
"MDA"="1"  
```  
  
 <span data-ttu-id="f34f9-185">Consulte [Habilitando e desabilitando MDAs usando definições de configuração específicas ao aplicativo](#appConfig) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="f34f9-185">See [Enabling and Disabling MDAs by Using Application-Specific Configuration Settings](#appConfig) for more information.</span></span> <span data-ttu-id="f34f9-186">A configuração do Registro pode ser substituída pela variável de ambiente COMPLUS_MDA.</span><span class="sxs-lookup"><span data-stu-id="f34f9-186">The registry setting can be overridden by the COMPLUS_MDA environment variable.</span></span> <span data-ttu-id="f34f9-187">Consulte [Habilitando e desabilitando MDAs usando uma variável de ambiente](#envVariable) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="f34f9-187">See [Enabling and Disabling MDAs by Using an Environment Variable](#envVariable) for more information.</span></span>  
  
 <span data-ttu-id="f34f9-188">Para desabilitar MDAs, defina a subchave do MDA como 0 (zero) usando o Editor do Registro do Windows.</span><span class="sxs-lookup"><span data-stu-id="f34f9-188">To disable MDAs, set the MDA subkey to 0 (zero) using the Windows Registry Editor.</span></span>  
  
 <span data-ttu-id="f34f9-189">Por padrão, alguns MDAs são habilitados quando você executa um aplicativo anexado a um depurador, mesmo sem adicionar a chave do Registro.</span><span class="sxs-lookup"><span data-stu-id="f34f9-189">By default, some MDAs are enabled when you run an application that is attached to a debugger, even without adding the registry key.</span></span> <span data-ttu-id="f34f9-190">Exemplos de assistentes desse tipo são [pInvokeStackImbalance](../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md) e [invalidApartmentStateChange](../../../docs/framework/debug-trace-profile/invalidapartmentstatechange-mda.md).</span><span class="sxs-lookup"><span data-stu-id="f34f9-190">Examples of such assistants are [pInvokeStackImbalance](../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md) and [invalidApartmentStateChange](../../../docs/framework/debug-trace-profile/invalidapartmentstatechange-mda.md).</span></span> <span data-ttu-id="f34f9-191">Você pode desabilitar esses assistentes executando o arquivo MDADisable.reg, como descrito antes nesta seção.</span><span class="sxs-lookup"><span data-stu-id="f34f9-191">You can disable these assistants by running the MDADisable.reg file as described earlier in this section.</span></span>  
  
<a name="envVariable"></a>   
### <a name="enabling-and-disabling-mdas-by-using-an-environment-variable"></a><span data-ttu-id="f34f9-192">Habilitando e desabilitando MDAs usando uma variável de ambiente</span><span class="sxs-lookup"><span data-stu-id="f34f9-192">Enabling and Disabling MDAs by Using an Environment Variable</span></span>  
 <span data-ttu-id="f34f9-193">A ativação do MDA também pode ser controlada pela variável de ambiente COMPLUS_MDA, que substitui a chave do Registro.</span><span class="sxs-lookup"><span data-stu-id="f34f9-193">MDA activation can also controlled by the environment variable COMPLUS_MDA, which overrides the registry key.</span></span> <span data-ttu-id="f34f9-194">A cadeia de caracteres COMPLUS_MDA é uma lista delimitada por ponto-e-vírgula, que não diferencia maiúsculas de minúsculas, de nomes de MDA ou outras cadeias de caracteres de controle especiais.</span><span class="sxs-lookup"><span data-stu-id="f34f9-194">The COMPLUS_MDA string is a case-insensitive, semicolon-delimited list of MDA names or other special control strings.</span></span> <span data-ttu-id="f34f9-195">A inicialização em um depurador gerenciado ou não gerenciado habilita um conjunto de MDAs por padrão.</span><span class="sxs-lookup"><span data-stu-id="f34f9-195">Starting under a managed or unmanaged debugger enables a set of MDAs by default.</span></span> <span data-ttu-id="f34f9-196">Isso é feito implicitamente precedendo a lista separada por ponto-e-vírgula de MDAs habilitados por padrão nos depuradores ao valor da variável de ambiente ou da chave do Registro.</span><span class="sxs-lookup"><span data-stu-id="f34f9-196">This is done by implicitly prepending the semicolon-delimited list of MDAs enabled by default under debuggers to the value of the environment variable or registry key.</span></span> <span data-ttu-id="f34f9-197">As cadeias de caracteres de controle especiais são as seguintes:</span><span class="sxs-lookup"><span data-stu-id="f34f9-197">The special control strings are the following:</span></span>  
  
-   <span data-ttu-id="f34f9-198">`0` – Desativa todos os MDAs.</span><span class="sxs-lookup"><span data-stu-id="f34f9-198">`0` - Deactivates all MDAs.</span></span>  
  
-   <span data-ttu-id="f34f9-199">`1` – Lê as configurações do MDA por meio de *ApplicationName*.mda.config.</span><span class="sxs-lookup"><span data-stu-id="f34f9-199">`1` - Reads MDA settings from *ApplicationName*.mda.config.</span></span>  
  
-   <span data-ttu-id="f34f9-200">`managedDebugger` – Ativa explicitamente todos os MDAs ativados implicitamente quando um executável gerenciado é iniciado em um depurador.</span><span class="sxs-lookup"><span data-stu-id="f34f9-200">`managedDebugger` - Explicitly activates all MDAs that are implicitly activated when a managed executable is started under a debugger.</span></span>  
  
-   <span data-ttu-id="f34f9-201">`unmanagedDebugger` – Ativa explicitamente todos os MDAs ativados implicitamente quando um executável não gerenciado é iniciado em um depurador.</span><span class="sxs-lookup"><span data-stu-id="f34f9-201">`unmanagedDebugger` - Explicitly activates all MDAs that are implicitly activated when an unmanaged executable is started under a debugger.</span></span>  
  
 <span data-ttu-id="f34f9-202">Se houver configurações conflitantes, as mais recentes substituirão as anteriores:</span><span class="sxs-lookup"><span data-stu-id="f34f9-202">If there are conflicting settings, the most recent settings override previous settings:</span></span>  
  
-   <span data-ttu-id="f34f9-203">`COMPLUS_MDA=0` desabilita todos os MDAs, incluindo aqueles habilitados implicitamente em um depurador.</span><span class="sxs-lookup"><span data-stu-id="f34f9-203">`COMPLUS_MDA=0` disables all MDAs, including those implicitly enabled under a debugger.</span></span>  
  
-   <span data-ttu-id="f34f9-204">`COMPLUS_MDA=gcUnmanagedToManaged` habilita `gcUnmanagedToManaged`, além de todos os MDAs habilitados implicitamente em um depurador.</span><span class="sxs-lookup"><span data-stu-id="f34f9-204">`COMPLUS_MDA=gcUnmanagedToManaged` enables `gcUnmanagedToManaged` in addition to any MDAs that are implicitly enabled under a debugger.</span></span>  
  
-   <span data-ttu-id="f34f9-205">`COMPLUS_MDA=0;gcUnmanagedToManaged` habilita `gcUnmanagedToManaged`, mas desabilita os MDAs que seriam, de outro modo, habilitados implicitamente em um depurador.</span><span class="sxs-lookup"><span data-stu-id="f34f9-205">`COMPLUS_MDA=0;gcUnmanagedToManaged` enables `gcUnmanagedToManaged` but disables MDAs that would otherwise be implicitly enabled under a debugger.</span></span>  
  
<a name="appConfig"></a>   
### <a name="enabling-and-disabling-mdas-by-using-application-specific-configuration-settings"></a><span data-ttu-id="f34f9-206">Habilitando e desabilitando MDAs usando definições de configuração específicas do aplicativo</span><span class="sxs-lookup"><span data-stu-id="f34f9-206">Enabling and Disabling MDAs by Using Application-Specific Configuration Settings</span></span>  
 <span data-ttu-id="f34f9-207">É possível habilitar, desabilitar e configurar alguns assistentes individualmente no arquivo de configuração do MDA para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f34f9-207">You can enable, disable, and configure some assistants individually in the MDA configuration file for the application.</span></span> <span data-ttu-id="f34f9-208">Para habilitar o uso de um arquivo de configuração de aplicativo para configurar MDAs, a chave do Registro do MDA ou a variável de ambiente COMPLUS_MDA deve estar definida.</span><span class="sxs-lookup"><span data-stu-id="f34f9-208">To enable the use of an application configuration file for configuring MDAs, either the MDA registry key or the COMPLUS_MDA environment variable must be set.</span></span> <span data-ttu-id="f34f9-209">O arquivo de configuração de aplicativo costuma ficar localizado no mesmo diretório do arquivo executável do aplicativo (.exe).</span><span class="sxs-lookup"><span data-stu-id="f34f9-209">The application configuration file is typically located in the same directory as the application's executable (.exe) file.</span></span> <span data-ttu-id="f34f9-210">O nome de arquivo usa o formato *ApplicationName*.mda.config; por exemplo, notepad.exe.mda.config. Os assistentes habilitados no arquivo de configuração de aplicativo podem ter atributos ou elementos projetados especificamente para controlar esse comportamento do assistente.</span><span class="sxs-lookup"><span data-stu-id="f34f9-210">The file name takes the form *ApplicationName*.mda.config; for example, notepad.exe.mda.config. Assistants that are enabled in the application configuration file may have attributes or elements specifically designed to control that assistant's behavior.</span></span> <span data-ttu-id="f34f9-211">O exemplo a seguir mostra como habilitar e configurar o [marshaling](../../../docs/framework/debug-trace-profile/marshaling-mda.md).</span><span class="sxs-lookup"><span data-stu-id="f34f9-211">The following example shows how to enable and configure the [marshaling](../../../docs/framework/debug-trace-profile/marshaling-mda.md).</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <marshaling>  
      <methodFilter>  
        <match name="*"/>  
      </methodFilter>  
      <fieldFilter>  
        <match name="*"/>  
      </fieldFilter>  
    </marshaling>  
  </assistants>  
</mdaConfig>  
```  
  
 <span data-ttu-id="f34f9-212">O MDA `Marshaling` emite informações sobre o tipo gerenciado em que o marshaling está sendo realizado para um tipo não gerenciado para a transição gerenciado/não gerenciado no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f34f9-212">The `Marshaling` MDA emits information about the managed type that is being marshaled to an unmanaged type for each managed-to-unmanaged transition in the application.</span></span> <span data-ttu-id="f34f9-213">O MDA `Marshaling` também pode filtrar os nomes do método e os campos de estrutura fornecidos nos elementos filho `<methodFilter>` e `<fieldFilter>`, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="f34f9-213">The `Marshaling` MDA can also filter the names of the method and structure fields supplied in the `<methodFilter>` and `<fieldFilter>` child elements, respectively.</span></span>  
  
 <span data-ttu-id="f34f9-214">O exemplo a seguir mostra como habilitar vários MDAs usando as configurações padrão.</span><span class="sxs-lookup"><span data-stu-id="f34f9-214">The following example shows how to enable multiple MDAs by using their default settings.</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <illegalPrepareConstrainedRegion />  
    <invalidCERCall />  
    <openGenericCERCall />  
    <virtualCERCall />  
  </assistants>  
</mdaConfig>  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="f34f9-215">Ao especificar mais de um assistente em um arquivo de configuração, você deve listá-los em ordem alfabética.</span><span class="sxs-lookup"><span data-stu-id="f34f9-215">When you specify more than one assistant in a configuration file, you must list them in alphabetical order.</span></span> <span data-ttu-id="f34f9-216">Por exemplo, se quiser habilitar os MDAs `virtualCERCall` e `invalidCERCall`, você deverá adicionar a entrada `<invalidCERCall />` antes da entrada `<virtualCERCall />`.</span><span class="sxs-lookup"><span data-stu-id="f34f9-216">For example, if you want to enable both the `virtualCERCall` and the `invalidCERCall` MDAs, you must add the `<invalidCERCall />` entry before the `<virtualCERCall />` entry.</span></span> <span data-ttu-id="f34f9-217">Se as entradas não estiverem em ordem alfabética, será exibida uma mensagem de exceção do arquivo de configuração inválido sem tratamento.</span><span class="sxs-lookup"><span data-stu-id="f34f9-217">If the entries are not in alphabetical order, an unhandled invalid configuration file exception message is displayed.</span></span>  
  
### <a name="mda-output"></a><span data-ttu-id="f34f9-218">Saída do MDA</span><span class="sxs-lookup"><span data-stu-id="f34f9-218">MDA Output</span></span>  
 <span data-ttu-id="f34f9-219">A saída do MDA é semelhante à do exemplo a seguir, que mostra a saída do MDA `pInvokeStackImbalance`.</span><span class="sxs-lookup"><span data-stu-id="f34f9-219">MDA output is similar to the following example, which shows the output from the `pInvokeStackImbalance` MDA.</span></span>  
  
 `A call to PInvoke function 'MDATest!MDATest.Program::StdCall' has unbalanced the stack. This is likely because the managed PInvoke signature does not match the unmanaged target signature. Check that the calling convention and parameters of the PInvoke signature match the target unmanaged signature.`  
  
## <a name="see-also"></a><span data-ttu-id="f34f9-220">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f34f9-220">See Also</span></span>  
 [<span data-ttu-id="f34f9-221">Depuração, rastreamento e criação de perfil</span><span class="sxs-lookup"><span data-stu-id="f34f9-221">Debugging, Tracing, and Profiling</span></span>](../../../docs/framework/debug-trace-profile/index.md)
