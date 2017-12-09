---
title: Diretiva x:Member
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4d8394ef-644c-4331-b6c5-be855d392980
caps.latest.revision: "5"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: eafb222dd5d3afcc751bae7799f0d17279aed14f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="xmember-directive"></a><span data-ttu-id="5138a-102">Diretiva x:Member</span><span class="sxs-lookup"><span data-stu-id="5138a-102">x:Member Directive</span></span>
<span data-ttu-id="5138a-103">Declara o membro na marcação XAML.</span><span class="sxs-lookup"><span data-stu-id="5138a-103">Declares a XAML member in markup.</span></span>  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="5138a-104">Uso de elemento Object do XAML</span><span class="sxs-lookup"><span data-stu-id="5138a-104">XAML Object Element Usage</span></span>  
  
```  
<object x:Class="className">  
  <x:Members>  
    <x:Member Name="propertyName"/>  
    additionalMembers  
  </x:Members>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="5138a-105">Valores XAML</span><span class="sxs-lookup"><span data-stu-id="5138a-105">XAML Values</span></span>  
  
|||  
|-|-|  
|`className`|<span data-ttu-id="5138a-106">Nome da classe de backup ou classe parcial para a produção de XAML.</span><span class="sxs-lookup"><span data-stu-id="5138a-106">Name of the backing class or partial class for the XAML production.</span></span>|  
|`memberName`|<span data-ttu-id="5138a-107">Nome da propriedade que está sendo definida.</span><span class="sxs-lookup"><span data-stu-id="5138a-107">Member name of the property being defined.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5138a-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="5138a-108">Remarks</span></span>  
 <span data-ttu-id="5138a-109">Na implementação de serviços XAML do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5138a-109">In the .NET Framework XAML Services implementation, .</span></span> <span data-ttu-id="5138a-110">`x:Member`não tem um tipo direto fazendo, mas há suporte para o <xref:System.Windows.Markup.MemberDefinition> classe.</span><span class="sxs-lookup"><span data-stu-id="5138a-110">`x:Member` does not have a direct type backing, but is supported by the <xref:System.Windows.Markup.MemberDefinition> class.</span></span> <span data-ttu-id="5138a-111">Em um fluxo do nó XAML, uma `x:Member` elemento é representado como um membro chamado `Member`, do namespace XAML de linguagem XAML.</span><span class="sxs-lookup"><span data-stu-id="5138a-111">In a XAML node stream, an `x:Member` element is represented as a member named `Member`, from the XAML language XAML namespace.</span></span> <span data-ttu-id="5138a-112">O membro `Member` contém atributos como declarado pela marcação.</span><span class="sxs-lookup"><span data-stu-id="5138a-112">The member `Member` holds attributes as declared by markup.</span></span>  
  
 <span data-ttu-id="5138a-113">O significado de `Name` e `Type` não são atribuídos no nível de serviços XAML do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5138a-113">The meaning of `Name` and `Type` are not assigned at the .NET Framework XAML Services level.</span></span> <span data-ttu-id="5138a-114">Eles são armazenados no fluxo do nó XAML inicial como valores de cadeia de caracteres, deve ser interpretado posteriormente com as regras que podem ser impostas por estruturas específicas.</span><span class="sxs-lookup"><span data-stu-id="5138a-114">They are stored in the initial XAML node stream as string values, to be interpreted later under the rules that might be imposed by specific frameworks.</span></span> <span data-ttu-id="5138a-115">O significado pode alinhar um nome XAML e o tipo XAML que significa ou somente pode ser válido em um sistema de tipo de backup, dependendo da implementação.</span><span class="sxs-lookup"><span data-stu-id="5138a-115">The meaning might align to a XAML name and XAML type meaning, or might only be valid in a backing type system, depending on the implementation.</span></span>  
  
 <span data-ttu-id="5138a-116">Para dar suporte a um uso prático de `x:Members` como um meio para especificar definições de membro na marcação, os membros devem ser associados uma classe que pode ser modificada.</span><span class="sxs-lookup"><span data-stu-id="5138a-116">To support a practical usage of `x:Members` as a means to specify member definitions in markup, the members must be associated with a class that can be modified.</span></span> <span data-ttu-id="5138a-117">O modelo desejado é que `x:Members` existe como um membro de um tipo que especifica um `x:Class`.</span><span class="sxs-lookup"><span data-stu-id="5138a-117">The intended model is that `x:Members` exists as a member of a type that specifies an `x:Class`.</span></span> <span data-ttu-id="5138a-118">No entanto, o mecanismo para a associação de tipos e membros ou para a produção de definições de membro dinâmico não tem suporte no nível de serviços XAML do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5138a-118">However, the mechanism for associating types and members or for producing dynamic member definitions is not supported at the .NET Framework XAML Services level.</span></span> <span data-ttu-id="5138a-119">Isso é da esquerda para estruturas individuais que têm modelos de aplicativos que dão suporte a definições de membro de XAML.</span><span class="sxs-lookup"><span data-stu-id="5138a-119">This is left to individual frameworks that have application models that support member definitions from XAML.</span></span> <span data-ttu-id="5138a-120">Normalmente, as ações de compilação MSBUILD que a compilação de marcação XAML e um integração-lo com code-behind ou produzir somente de XAML assemblies são necessários para dar suporte a esse recurso.</span><span class="sxs-lookup"><span data-stu-id="5138a-120">Typically, MSBUILD build actions that markup-compile the XAML and either integrate it with code-behind or produce pure from-XAML assemblies are needed to support that feature.</span></span>  
  
## <a name="xproperty-for-windows-workflow-foundation"></a><span data-ttu-id="5138a-121">Propriedade x: para Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="5138a-121">x:Property for Windows Workflow Foundation</span></span>  
 <span data-ttu-id="5138a-122">Para Windows Workflow Foundation, `x:Property` define os membros de uma atividade personalizada composta inteiramente em XAML ou XAML – definido membros dinâmicos para um designer de atividade com code-behind.</span><span class="sxs-lookup"><span data-stu-id="5138a-122">For Windows Workflow Foundation, `x:Property` defines the members of a custom activity composed entirely in XAML, or XAML –defined dynamic members for an activity designer with code-behind.</span></span> <span data-ttu-id="5138a-123">`x:Class`também deve ser especificado no elemento raiz da produção XAML.</span><span class="sxs-lookup"><span data-stu-id="5138a-123">`x:Class` must also be specified on the root element of the XAML production.</span></span> <span data-ttu-id="5138a-124">Isso não é um requisito no nível de serviços XAML do .NET Framework, mas se torna um requisito quando a produção de XAML é carregada pelas ações de compilação do MSBUILD que dão suporte a atividades personalizadas e XAML do Windows Workflow Foundation em geral.</span><span class="sxs-lookup"><span data-stu-id="5138a-124">This is not a requirement at the .NET Framework XAML Services level, but becomes a requirement when the XAML production is loaded by the MSBUILD build actions that support custom activities and Windows Workflow Foundation XAML in general.</span></span> <span data-ttu-id="5138a-125">O Windows Workflow Foundation não usa o nome de tipo XAML puro como seu valor desejado para o `x:Property` `Type` de atributo e, em vez disso, usa uma convenção de que não está documentada aqui.</span><span class="sxs-lookup"><span data-stu-id="5138a-125">Windows Workflow Foundation does not use the pure XAML type name as its intended value for the `x:Property` `Type` attribute, and instead uses a convention that is not documented here.</span></span> <span data-ttu-id="5138a-126">Para obter mais informações, consulte [criação dinâmica de atividade](http://msdn.microsoft.com/library/dd807392.aspx).</span><span class="sxs-lookup"><span data-stu-id="5138a-126">For more information, see [Dynamic Activity Creation](http://msdn.microsoft.com/library/dd807392.aspx).</span></span>