---
title: "Guia de programação (LINQ to DataSet)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 977aedd7-0084-46a0-b56f-345787a55da1
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 1332bf297dae4baae62d2abd731d236ad49be4ee
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="programming-guide-linq-to-dataset"></a><span data-ttu-id="e2b57-102">Guia de programação (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="e2b57-102">Programming Guide (LINQ to DataSet)</span></span>
<span data-ttu-id="e2b57-103">Esta seção fornece informações e exemplos conceituais para a programação com [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e2b57-103">This section provides conceptual information and examples for programming with [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e2b57-104">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="e2b57-104">In This Section</span></span>  
 [<span data-ttu-id="e2b57-105">Consultas no LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="e2b57-105">Queries in LINQ to DataSet</span></span>](../../../../docs/framework/data/adonet/queries-in-linq-to-dataset.md)  
 <span data-ttu-id="e2b57-106">Fornece informações sobre como escrever consultas [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e2b57-106">Provides information about how to write [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] queries.</span></span>  
  
 [<span data-ttu-id="e2b57-107">Consultando DataSets</span><span class="sxs-lookup"><span data-stu-id="e2b57-107">Querying DataSets</span></span>](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)  
 <span data-ttu-id="e2b57-108">Descreve como consultar objetos <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="e2b57-108">Describes how to query <xref:System.Data.DataSet> objects.</span></span>  
  
 [<span data-ttu-id="e2b57-109">Comparando DataRows</span><span class="sxs-lookup"><span data-stu-id="e2b57-109">Comparing DataRows</span></span>](../../../../docs/framework/data/adonet/comparing-datarows-linq-to-dataset.md)  
 <span data-ttu-id="e2b57-110">Descreve como usar o objeto <xref:System.Data.DataRowComparer> para comparar linhas de dados.</span><span class="sxs-lookup"><span data-stu-id="e2b57-110">Describes how to use the <xref:System.Data.DataRowComparer> object to compare data rows.</span></span>  
  
 [<span data-ttu-id="e2b57-111">Criando um DataTable de uma consulta</span><span class="sxs-lookup"><span data-stu-id="e2b57-111">Creating a DataTable From a Query</span></span>](../../../../docs/framework/data/adonet/creating-a-datatable-from-a-query-linq-to-dataset.md)  
 <span data-ttu-id="e2b57-112">Fornece informações sobre como criar um <xref:System.Data.DataTable> de um [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] consulta usando o <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> método.</span><span class="sxs-lookup"><span data-stu-id="e2b57-112">Provides information about creating a <xref:System.Data.DataTable> from a [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] query by using the <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> method.</span></span>  
  
 [<span data-ttu-id="e2b57-113">Como: implementar CopyToDataTable\<T > onde um tipo genérico T não é um DataRow</span><span class="sxs-lookup"><span data-stu-id="e2b57-113">How to: Implement CopyToDataTable\<T> Where the Generic Type T Is Not a DataRow</span></span>](../../../../docs/framework/data/adonet/implement-copytodatatable-where-type-not-a-datarow.md)  
 <span data-ttu-id="e2b57-114">Descreve como implementar um método `CopyToDataTable<T>` personalizado, onde o parâmetro genérico T não é do tipo <xref:System.Data.DataRow>.</span><span class="sxs-lookup"><span data-stu-id="e2b57-114">Describes how to implement a custom `CopyToDataTable<T>` method where the generic parameter T is not of type <xref:System.Data.DataRow>.</span></span>  
  
 [<span data-ttu-id="e2b57-115">Campo genérico e métodos de SetField</span><span class="sxs-lookup"><span data-stu-id="e2b57-115">Generic Field and SetField Methods</span></span>](../../../../docs/framework/data/adonet/generic-field-and-setfield-methods-linq-to-dataset.md)  
 <span data-ttu-id="e2b57-116">Fornece informações sobre os métodos genéricos <xref:System.Data.DataRowExtensions.Field%2A> e <xref:System.Data.DataRowExtensions.SetField%2A>.</span><span class="sxs-lookup"><span data-stu-id="e2b57-116">Provides information about the generic <xref:System.Data.DataRowExtensions.Field%2A> and <xref:System.Data.DataRowExtensions.SetField%2A> methods.</span></span>  
  
 [<span data-ttu-id="e2b57-117">Associação de dados e LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="e2b57-117">Data Binding and LINQ to DataSet</span></span>](../../../../docs/framework/data/adonet/data-binding-and-linq-to-dataset.md)  
 <span data-ttu-id="e2b57-118">Descreve a vinculação de dados usando o objeto <xref:System.Data.DataView>.</span><span class="sxs-lookup"><span data-stu-id="e2b57-118">Describes databinding using the <xref:System.Data.DataView> object.</span></span>  
  
 [<span data-ttu-id="e2b57-119">Consultas LINQ to DataSet de depuração</span><span class="sxs-lookup"><span data-stu-id="e2b57-119">Debugging LINQ to DataSet Queries</span></span>](../../../../docs/framework/data/adonet/debugging-linq-to-dataset-queries.md)  
 <span data-ttu-id="e2b57-120">Fornece informações sobre depuração e solução de problemas [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] consultas.</span><span class="sxs-lookup"><span data-stu-id="e2b57-120">Provides information about debugging and troubleshooting [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] queries.</span></span>  
  
 [<span data-ttu-id="e2b57-121">Segurança</span><span class="sxs-lookup"><span data-stu-id="e2b57-121">Security</span></span>](../../../../docs/framework/data/adonet/security-linq-to-dataset.md)  
 <span data-ttu-id="e2b57-122">Descreve problemas de segurança no [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e2b57-122">Describes security issues in [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span></span>  
  
 [<span data-ttu-id="e2b57-123">LINQ para exemplos de conjunto de dados</span><span class="sxs-lookup"><span data-stu-id="e2b57-123">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)  
 <span data-ttu-id="e2b57-124">Fornece exemplos de consultas que usam os operadores [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e2b57-124">Provides query examples that use the [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] operators.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="e2b57-125">Referência</span><span class="sxs-lookup"><span data-stu-id="e2b57-125">Reference</span></span>  
 <xref:System.Data.DataRowComparer>  
  
 <xref:System.Data.DataRowExtensions>  
  
 <xref:System.Data.DataTableExtensions>  
  
 <xref:System.Data.DataView>  
  
## <a name="see-also"></a><span data-ttu-id="e2b57-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e2b57-126">See Also</span></span>  
 [<span data-ttu-id="e2b57-127">LINQ to ADO.NET</span><span class="sxs-lookup"><span data-stu-id="e2b57-127">LINQ to ADO.NET</span></span>](http://msdn.microsoft.com/en-us/be3297b9-1b54-4d4c-82a8-add0d79c2006)  
 [<span data-ttu-id="e2b57-128">NÃO está em compilação: Guia de programação geral em LINQ</span><span class="sxs-lookup"><span data-stu-id="e2b57-128">NOT IN BUILD: LINQ General Programming Guide</span></span>](http://msdn.microsoft.com/en-us/609c7a6b-cbdd-429d-99f3-78d13d3bc049)  
 [<span data-ttu-id="e2b57-129">Framework do LINQ</span><span class="sxs-lookup"><span data-stu-id="e2b57-129">LINQ Framework</span></span>](http://msdn.microsoft.com/en-us/897ea0fc-40db-4694-bbe5-7dd339d5bf94)