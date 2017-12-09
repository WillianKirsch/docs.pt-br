---
title: Como baixar um arquivo no segundo plano
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- BackgroundWorker component
- background tasks
- Asynchronous Pattern
- forms [Windows Forms], multithreading
- components [Windows Forms], asynchronous
- forms [Windows Forms], background operations
- threading [Windows Forms], background operations
- background operations
ms.assetid: 9b7bc5ae-051c-4904-9720-18f6667388bd
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4b83f5ae935ed9ba6c5351d48175ee7747e7b01b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-download-a-file-in-the-background"></a><span data-ttu-id="dbcfe-102">Como baixar um arquivo no segundo plano</span><span class="sxs-lookup"><span data-stu-id="dbcfe-102">How to: Download a File in the Background</span></span>
<span data-ttu-id="dbcfe-103">Baixar um arquivo é uma tarefa comum e costuma ser útil executar esta operação potencialmente demorada em um thread separado.</span><span class="sxs-lookup"><span data-stu-id="dbcfe-103">Downloading a file is a common task, and it is often useful to run this potentially time-consuming operation on a separate thread.</span></span> <span data-ttu-id="dbcfe-104">Use o <xref:System.ComponentModel.BackgroundWorker> componente para realizar essa tarefa com muito pouco código.</span><span class="sxs-lookup"><span data-stu-id="dbcfe-104">Use the <xref:System.ComponentModel.BackgroundWorker> component to accomplish this task with very little code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dbcfe-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="dbcfe-105">Example</span></span>  
 <span data-ttu-id="dbcfe-106">O exemplo de código a seguir demonstra como usar um <xref:System.ComponentModel.BackgroundWorker> componente para carregar um arquivo XML de uma URL.</span><span class="sxs-lookup"><span data-stu-id="dbcfe-106">The following code example demonstrates how to use a <xref:System.ComponentModel.BackgroundWorker> component to load an XML file from a URL.</span></span> <span data-ttu-id="dbcfe-107">Quando o usuário clica o **baixar** botão, o <xref:System.Windows.Forms.Control.Click> chamadas de manipulador de eventos de <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> método de um <xref:System.ComponentModel.BackgroundWorker> componente para iniciar a operação de download.</span><span class="sxs-lookup"><span data-stu-id="dbcfe-107">When the user clicks the **Download** button, the <xref:System.Windows.Forms.Control.Click> event handler calls the <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> method of a <xref:System.ComponentModel.BackgroundWorker> component to start the download operation.</span></span> <span data-ttu-id="dbcfe-108">O botão é desabilitado durante o download e então habilitado quando o download for concluído.</span><span class="sxs-lookup"><span data-stu-id="dbcfe-108">The button is disabled for the duration of the download, and then enabled when the download is complete.</span></span> <span data-ttu-id="dbcfe-109">Um <xref:System.Windows.Forms.MessageBox> exibe o conteúdo do arquivo.</span><span class="sxs-lookup"><span data-stu-id="dbcfe-109">A <xref:System.Windows.Forms.MessageBox> displays the contents of the file.</span></span>  
  
 [!code-csharp[System.ComponentModel.BackgroundWorker.IsBusy#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.BackgroundWorker.IsBusy#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/VB/Form1.vb#1)]  
  
 <span data-ttu-id="dbcfe-110">**Baixando o arquivo**</span><span class="sxs-lookup"><span data-stu-id="dbcfe-110">**Downloading the file**</span></span>  
  
 <span data-ttu-id="dbcfe-111">O arquivo é baixado no <xref:System.ComponentModel.BackgroundWorker> thread de trabalho do componente, que executa o <xref:System.ComponentModel.BackgroundWorker.DoWork> manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="dbcfe-111">The file is downloaded on the <xref:System.ComponentModel.BackgroundWorker> component's worker thread, which runs the <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler.</span></span> <span data-ttu-id="dbcfe-112">Esse thread é iniciado quando seu código chama o <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> método.</span><span class="sxs-lookup"><span data-stu-id="dbcfe-112">This thread starts when your code calls the <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> method.</span></span>  
  
 [!code-csharp[System.ComponentModel.BackgroundWorker.IsBusy#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/CS/Form1.cs#3)]
 [!code-vb[System.ComponentModel.BackgroundWorker.IsBusy#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/VB/Form1.vb#3)]  
  
 <span data-ttu-id="dbcfe-113">**Aguardando a conclusão de um BackgroundWorker**</span><span class="sxs-lookup"><span data-stu-id="dbcfe-113">**Waiting for a BackgroundWorker to finish**</span></span>  
  
 <span data-ttu-id="dbcfe-114">O `downloadButton_Click` manipulador de eventos demonstra como aguardar um <xref:System.ComponentModel.BackgroundWorker> componente para concluir sua tarefa assíncrona.</span><span class="sxs-lookup"><span data-stu-id="dbcfe-114">The `downloadButton_Click` event handler demonstrates how to wait for a <xref:System.ComponentModel.BackgroundWorker> component to finish its asynchronous task.</span></span>  
  
 <span data-ttu-id="dbcfe-115">Se você só deseja que o aplicativo responda a eventos e não quer realizar trabalhos no thread principal enquanto aguarda o thread em segundo plano concluir, basta sair do manipulador.</span><span class="sxs-lookup"><span data-stu-id="dbcfe-115">If you only want the application to respond to events and do not want to do any work in the main thread while you wait for the background thread to complete, just exit the handler.</span></span>  
  
 <span data-ttu-id="dbcfe-116">Se você quiser continuar a fazer o trabalho do thread principal, use o <xref:System.ComponentModel.BackgroundWorker.IsBusy%2A> propriedade para determinar se o <xref:System.ComponentModel.BackgroundWorker> thread ainda está em execução.</span><span class="sxs-lookup"><span data-stu-id="dbcfe-116">If you want to continue doing work in the main thread, use the <xref:System.ComponentModel.BackgroundWorker.IsBusy%2A> property to determine whether the <xref:System.ComponentModel.BackgroundWorker> thread is still running.</span></span> <span data-ttu-id="dbcfe-117">No exemplo, uma barra de progresso é atualizada enquanto o download é processado.</span><span class="sxs-lookup"><span data-stu-id="dbcfe-117">In the example, a progress bar is updated while the download is processing.</span></span> <span data-ttu-id="dbcfe-118">Certifique-se de chamar o <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> método para manter a interface do usuário responsiva.</span><span class="sxs-lookup"><span data-stu-id="dbcfe-118">Be sure to call the <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> method to keep the UI responsive.</span></span>  
  
 [!code-csharp[System.ComponentModel.BackgroundWorker.IsBusy#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/CS/Form1.cs#2)]
 [!code-vb[System.ComponentModel.BackgroundWorker.IsBusy#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/VB/Form1.vb#2)]  
  
 <span data-ttu-id="dbcfe-119">**Exibindo o resultado**</span><span class="sxs-lookup"><span data-stu-id="dbcfe-119">**Displaying the result**</span></span>  
  
 <span data-ttu-id="dbcfe-120">O `backgroundWorker1_RunWorkerCompleted` método trata o <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> eventos e é chamado quando a operação em segundo plano é concluída.</span><span class="sxs-lookup"><span data-stu-id="dbcfe-120">The `backgroundWorker1_RunWorkerCompleted` method handles the <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event and is called when the background operation is completed.</span></span> <span data-ttu-id="dbcfe-121">Este método verifica primeiro o <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> propriedade.</span><span class="sxs-lookup"><span data-stu-id="dbcfe-121">This method first checks the <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="dbcfe-122">Se <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> é `null`, em seguida, esse método exibe o conteúdo do arquivo.</span><span class="sxs-lookup"><span data-stu-id="dbcfe-122">If <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> is `null`, then this method displays the contents of the file.</span></span> <span data-ttu-id="dbcfe-123">Ele habilita então o botão de download, que estava desabilitado quando o download começou, e reinicia a barra de progresso.</span><span class="sxs-lookup"><span data-stu-id="dbcfe-123">It then enables the download button, which was disabled when the download began, and it resets the progress bar.</span></span>  
  
 [!code-csharp[System.ComponentModel.BackgroundWorker.IsBusy#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/CS/Form1.cs#4)]
 [!code-vb[System.ComponentModel.BackgroundWorker.IsBusy#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/VB/Form1.vb#4)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="dbcfe-124">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="dbcfe-124">Compiling the Code</span></span>  
 <span data-ttu-id="dbcfe-125">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="dbcfe-125">This example requires:</span></span>  
  
-   <span data-ttu-id="dbcfe-126">Referências aos assemblies System.Drawing, System.Windows.Forms e System.Xml.</span><span class="sxs-lookup"><span data-stu-id="dbcfe-126">References to the System.Drawing, System.Windows.Forms, and System.Xml assemblies.</span></span>  
  
 <span data-ttu-id="dbcfe-127">Para obter informações sobre como compilar este exemplo na linha de comando para [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] ou [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], consulte [Building from the Command Line (Compilando na linha de comando)](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [Compilando pela linha de comando com csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="dbcfe-127">For information about building this example from the command line for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="dbcfe-128">Também é possível compilar este exemplo em [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] colando o código em um novo projeto.</span><span class="sxs-lookup"><span data-stu-id="dbcfe-128">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="dbcfe-129">Consulte também [Como compilar e executar um exemplo completo de código do Windows Forms usando o Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="dbcfe-129">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="dbcfe-130">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="dbcfe-130">Robust Programming</span></span>  
 <span data-ttu-id="dbcfe-131">Sempre verifique o <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> propriedade em seu <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> manipulador de eventos antes de tentar acessar o <xref:System.ComponentModel.RunWorkerCompletedEventArgs.Result%2A?displayProperty=nameWithType> propriedade ou qualquer outro objeto afetado pelo <xref:System.ComponentModel.BackgroundWorker.DoWork> manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="dbcfe-131">Always check the <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> property in your <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event handler before attempting to access the <xref:System.ComponentModel.RunWorkerCompletedEventArgs.Result%2A?displayProperty=nameWithType> property or any other object that may have been affected by the <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbcfe-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dbcfe-132">See Also</span></span>  
 <xref:System.ComponentModel.BackgroundWorker>  
 [<span data-ttu-id="dbcfe-133">Como executar uma operação em segundo plano</span><span class="sxs-lookup"><span data-stu-id="dbcfe-133">How to: Run an Operation in the Background</span></span>](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 [<span data-ttu-id="dbcfe-134">Como implementar um formulário que usa uma operação em segundo plano</span><span class="sxs-lookup"><span data-stu-id="dbcfe-134">How to: Implement a Form That Uses a Background Operation</span></span>](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)