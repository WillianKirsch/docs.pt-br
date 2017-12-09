---
title: 'Como: Especificar um agendador de tarefas em um bloco de fluxo de dados'
ms.custom: 
ms.date: 03/30/2017
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
- TPL dataflow library, linking to task scheduler in TPL
- Task Parallel Library, dataflows
- task scheduler, linking from TPL
ms.assetid: 27ece374-ed5b-49ef-9cec-b20db34a65e8
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 20faebc8bda3b50c4f762615d84b7a449ae61c6f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-specify-a-task-scheduler-in-a-dataflow-block"></a><span data-ttu-id="24568-102">Como: Especificar um agendador de tarefas em um bloco de fluxo de dados</span><span class="sxs-lookup"><span data-stu-id="24568-102">How to: Specify a Task Scheduler in a Dataflow Block</span></span>
<span data-ttu-id="24568-103">Este documento demonstra como associar um agendador de tarefas específica quando você usa o fluxo de dados em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="24568-103">This document demonstrates how to associate a specific task scheduler when you use dataflow in your application.</span></span> <span data-ttu-id="24568-104">O exemplo usa o <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair?displayProperty=nameWithType> classe em um aplicativo do Windows Forms para mostrar quando as tarefas de leitor estão ativas e quando uma tarefa de gravador está ativa.</span><span class="sxs-lookup"><span data-stu-id="24568-104">The example uses the <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair?displayProperty=nameWithType> class in a Windows Forms application to show when reader tasks are active and when a writer task is active.</span></span> <span data-ttu-id="24568-105">Ele também usa o <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> método para permitir que um bloco de fluxo de dados ser executado no thread da interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="24568-105">It also uses the <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> method to enable a dataflow block to run on the user-interface thread.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="24568-106">A biblioteca de fluxo de dados TPL (<xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType> namespace) não é distribuído com o [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span><span class="sxs-lookup"><span data-stu-id="24568-106">The TPL Dataflow Library (<xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType> namespace) is not distributed with the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span></span> <span data-ttu-id="24568-107">Para instalar o <xref:System.Threading.Tasks.Dataflow> namespace, abra seu projeto no [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], escolha **gerenciar pacotes NuGet** no menu projeto e pesquise online o `Microsoft.Tpl.Dataflow` pacote.</span><span class="sxs-lookup"><span data-stu-id="24568-107">To install the <xref:System.Threading.Tasks.Dataflow> namespace, open your project in [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], choose **Manage NuGet Packages** from the Project menu, and search online for the `Microsoft.Tpl.Dataflow` package.</span></span>  
  
### <a name="to-create-the-windows-forms-application"></a><span data-ttu-id="24568-108">Para criar o Windows Forms de aplicativo</span><span class="sxs-lookup"><span data-stu-id="24568-108">To Create the Windows Forms Application</span></span>  
  
1.  <span data-ttu-id="24568-109">Criar um [!INCLUDE[csprcs](../../../includes/csprcs-md.md)] ou Visual Basic **aplicativo do Windows Forms** projeto.</span><span class="sxs-lookup"><span data-stu-id="24568-109">Create a [!INCLUDE[csprcs](../../../includes/csprcs-md.md)] or Visual Basic **Windows Forms Application** project.</span></span> <span data-ttu-id="24568-110">As etapas a seguir, o projeto é denominado `WriterReadersWinForms`.</span><span class="sxs-lookup"><span data-stu-id="24568-110">In the following steps, the project is named `WriterReadersWinForms`.</span></span>  
  
2.  <span data-ttu-id="24568-111">No designer de formulário para o formulário principal, Form1 (Form1. vb para [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), adicionar quatro <xref:System.Windows.Forms.CheckBox> controles.</span><span class="sxs-lookup"><span data-stu-id="24568-111">On the form designer for the main form, Form1.cs (Form1.vb for [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), add four <xref:System.Windows.Forms.CheckBox> controls.</span></span> <span data-ttu-id="24568-112">Definir o <xref:System.Windows.Forms.Control.Text%2A> propriedade **leitor 1** para `checkBox1`, **Reader 2** para `checkBox2`, **leitor 3** para `checkBox3`, e  **Gravador** para `checkBox4`.</span><span class="sxs-lookup"><span data-stu-id="24568-112">Set the <xref:System.Windows.Forms.Control.Text%2A> property to **Reader 1** for `checkBox1`, **Reader 2** for `checkBox2`, **Reader 3** for `checkBox3`, and **Writer** for `checkBox4`.</span></span> <span data-ttu-id="24568-113">Definir o <xref:System.Windows.Forms.Control.Enabled%2A> propriedade para cada controle `False`.</span><span class="sxs-lookup"><span data-stu-id="24568-113">Set the <xref:System.Windows.Forms.Control.Enabled%2A> property for each control to `False`.</span></span>  
  
3.  <span data-ttu-id="24568-114">Adicionar um <xref:System.Windows.Forms.Timer> controle no formulário.</span><span class="sxs-lookup"><span data-stu-id="24568-114">Add a <xref:System.Windows.Forms.Timer> control to the form.</span></span> <span data-ttu-id="24568-115">Defina a propriedade <xref:System.Windows.Forms.Timer.Interval%2A> como `2500`.</span><span class="sxs-lookup"><span data-stu-id="24568-115">Set the <xref:System.Windows.Forms.Timer.Interval%2A> property to `2500`.</span></span>  
  
## <a name="adding-dataflow-functionality"></a><span data-ttu-id="24568-116">Adicionando funcionalidade de fluxo de dados</span><span class="sxs-lookup"><span data-stu-id="24568-116">Adding Dataflow Functionality</span></span>  
 <span data-ttu-id="24568-117">Esta seção descreve como criar os blocos de fluxo de dados que participam no aplicativo e como associar cada um com um agendador de tarefas.</span><span class="sxs-lookup"><span data-stu-id="24568-117">This section describes how to create the dataflow blocks that participate in the application and how to associate each one with a task scheduler.</span></span>  
  
#### <a name="to-add-dataflow-functionality-to-the-application"></a><span data-ttu-id="24568-118">Para adicionar a funcionalidade de fluxo de dados para o aplicativo</span><span class="sxs-lookup"><span data-stu-id="24568-118">To Add Dataflow Functionality to the Application</span></span>  
  
1.  <span data-ttu-id="24568-119">No seu projeto, adicione uma referência a System.Threading.Tasks.Dataflow.dll.</span><span class="sxs-lookup"><span data-stu-id="24568-119">In your project, add a reference to System.Threading.Tasks.Dataflow.dll.</span></span>  
  
2.  <span data-ttu-id="24568-120">Certifique-se de que Form1 (Form1. vb para [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) contém o seguinte `using` instruções (`Imports` em [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]).</span><span class="sxs-lookup"><span data-stu-id="24568-120">Ensure that Form1.cs (Form1.vb for [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) contains the following `using` statements (`Imports` in [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]).</span></span>  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#1)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#1)]  
  
3.  <span data-ttu-id="24568-121">Adicionar um <xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601> membro de dados para o `Form1` classe.</span><span class="sxs-lookup"><span data-stu-id="24568-121">Add a <xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601> data member to the `Form1` class.</span></span>  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#2)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#2)]  
  
4.  <span data-ttu-id="24568-122">No `Form1` construtor, após a chamada a `InitializeComponent`, crie um <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> que alterna o estado do objeto <xref:System.Windows.Forms.CheckBox> objetos.</span><span class="sxs-lookup"><span data-stu-id="24568-122">In the `Form1` constructor, after the call to `InitializeComponent`, create an <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object that toggles the state of <xref:System.Windows.Forms.CheckBox> objects.</span></span>  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#3)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#3)]  
  
5.  <span data-ttu-id="24568-123">No `Form1` construtor, criar um <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> objeto e quatro <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objetos, um <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objeto para cada <xref:System.Windows.Forms.CheckBox> objeto.</span><span class="sxs-lookup"><span data-stu-id="24568-123">In the `Form1` constructor, create a <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> object and four <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objects, one <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object for each <xref:System.Windows.Forms.CheckBox> object.</span></span> <span data-ttu-id="24568-124">Para cada <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> de objeto, especifique um <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> objeto que tem o <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> propriedade definida como o <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair.ConcurrentScheduler%2A> propriedade para os leitores e o <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair.ExclusiveScheduler%2A> propriedade para o gravador.</span><span class="sxs-lookup"><span data-stu-id="24568-124">For each <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object, specify a <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> object that has the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> property set to the <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair.ConcurrentScheduler%2A> property for the readers, and the <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair.ExclusiveScheduler%2A> property for the writer.</span></span>  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#4)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#4)]  
  
6.  <span data-ttu-id="24568-125">No `Form1` construtor, iniciar o <xref:System.Windows.Forms.Timer> objeto.</span><span class="sxs-lookup"><span data-stu-id="24568-125">In the `Form1` constructor, start the <xref:System.Windows.Forms.Timer> object.</span></span>  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#5)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#5)]  
  
7.  <span data-ttu-id="24568-126">No designer de formulário para o formulário principal, crie um manipulador de eventos para o <xref:System.Windows.Forms.Timer.Tick> evento para o temporizador.</span><span class="sxs-lookup"><span data-stu-id="24568-126">On the form designer for the main form, create an event handler for the <xref:System.Windows.Forms.Timer.Tick> event for the timer.</span></span>  
  
8.  <span data-ttu-id="24568-127">Implementar o <xref:System.Windows.Forms.Timer.Tick> evento para o temporizador.</span><span class="sxs-lookup"><span data-stu-id="24568-127">Implement the <xref:System.Windows.Forms.Timer.Tick> event for the timer.</span></span>  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#6)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#6)]  
  
 <span data-ttu-id="24568-128">Porque o `toggleCheckBox` atos de bloco de fluxo de dados na interface do usuário, é importante que essa ação ocorre no thread da interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="24568-128">Because the `toggleCheckBox` dataflow block acts on the user interface, it is important that this action occur on the user-interface thread.</span></span> <span data-ttu-id="24568-129">Para fazer isso, durante a construção esse objeto fornece um <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> objeto que tem o <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> propriedade definida como <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="24568-129">To accomplish this, during construction this object provides a <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> object that has the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> property set to <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="24568-130">O <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A> método cria um <xref:System.Threading.Tasks.TaskScheduler> objeto que executa o trabalho no contexto de sincronização atual.</span><span class="sxs-lookup"><span data-stu-id="24568-130">The <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A> method creates a <xref:System.Threading.Tasks.TaskScheduler> object that performs work on the current synchronization context.</span></span> <span data-ttu-id="24568-131">Porque o `Form1` construtor é chamado do thread de interface do usuário, a ação para o `toggleCheckBox` bloco de fluxo de dados também é executado no thread da interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="24568-131">Because the `Form1` constructor is called from the user-interface thread, the action for the `toggleCheckBox` dataflow block also runs on the user-interface thread.</span></span>  
  
 <span data-ttu-id="24568-132">Este exemplo também usa o <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> classe para habilitar alguns blocos de fluxo de dados funcione simultaneamente e outro bloco de fluxo de dados para atuar exclusivo em relação a todos os outros blocos de fluxo de dados que são executados no mesmo <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> objeto.</span><span class="sxs-lookup"><span data-stu-id="24568-132">This example also uses the <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> class to enable some dataflow blocks to act concurrently, and another dataflow block to act exclusive with respect to all other dataflow blocks that run on the same <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> object.</span></span> <span data-ttu-id="24568-133">Essa técnica é útil quando um recurso de compartilhamento de vários blocos de fluxo de dados e alguns exigem acesso exclusivo para esse recurso, pois elimina a necessidade de sincronizar manualmente o acesso a esse recurso.</span><span class="sxs-lookup"><span data-stu-id="24568-133">This technique is useful when multiple dataflow blocks share a resource and some require exclusive access to that resource, because it eliminates the requirement to manually synchronize access to that resource.</span></span> <span data-ttu-id="24568-134">A eliminação de sincronização manual pode tornar o código mais eficiente.</span><span class="sxs-lookup"><span data-stu-id="24568-134">The elimination of manual synchronization can make code more efficient.</span></span>  
  
## <a name="example"></a><span data-ttu-id="24568-135">Exemplo</span><span class="sxs-lookup"><span data-stu-id="24568-135">Example</span></span>  
 <span data-ttu-id="24568-136">O exemplo a seguir mostra o código completo para Form1 (Form1. vb para [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]).</span><span class="sxs-lookup"><span data-stu-id="24568-136">The following example shows the complete code for Form1.cs (Form1.vb for [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]).</span></span>  
  
 [!code-csharp[TPLDataflow_WriterReadersWinForms#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#100)]
 [!code-vb[TPLDataflow_WriterReadersWinForms#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#100)]  
  
## <a name="see-also"></a><span data-ttu-id="24568-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="24568-137">See Also</span></span>  
 [<span data-ttu-id="24568-138">Fluxo de dados</span><span class="sxs-lookup"><span data-stu-id="24568-138">Dataflow</span></span>](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)