---
title: "Etapas do processo de serialização"
ms.date: 08/07/2017
ms.prod: .net
ms.topic: article
helpviewer_keywords:
- binary serialization, steps
- serialization, steps
ms.assetid: 4bcbc883-2a91-418f-b968-6c86a25e9737
caps.latest.revision: 6
author: Erikre
ms.author: erikre
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 717bcb6f9f72a728d77e2847096ea558a9c50902
ms.openlocfilehash: a4c125493e1b59d329bf4626c45f48b2b222d308
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="steps-in-the-serialization-process"></a><span data-ttu-id="d58e8-102">Etapas do processo de serialização</span><span class="sxs-lookup"><span data-stu-id="d58e8-102">Steps in the serialization process</span></span>
<span data-ttu-id="d58e8-103">Quando o método <xref:System.Runtime.Serialization.Formatter.Serialize*> é chamado em um [formatador](xref:System.Runtime.Serialization.Formatter), a serialização do objeto procede de acordo com a seguinte sequência de regras:</span><span class="sxs-lookup"><span data-stu-id="d58e8-103">When the <xref:System.Runtime.Serialization.Formatter.Serialize*> method is called on a [formatter](xref:System.Runtime.Serialization.Formatter), object serialization proceeds according to the following sequence of rules:</span></span>

- <span data-ttu-id="d58e8-104">Uma verificação é feita para determinar se o formatador tem um seletor substituto.</span><span class="sxs-lookup"><span data-stu-id="d58e8-104">A check is made to determine whether the formatter has a surrogate selector.</span></span> <span data-ttu-id="d58e8-105">Se tiver, verifique se o seletor substituto administra objetos do tipo determinado.</span><span class="sxs-lookup"><span data-stu-id="d58e8-105">If the formatter does, check whether the surrogate selector handles objects of the given type.</span></span> <span data-ttu-id="d58e8-106">Se o seletor manipular o tipo de objeto, <xref:System.Runtime.Serialization.ISerializable.GetObjectData*?displayProperty=fullName> será chamado no seletor alternativo.</span><span class="sxs-lookup"><span data-stu-id="d58e8-106">If the selector handles the object type, <xref:System.Runtime.Serialization.ISerializable.GetObjectData*?displayProperty=fullName> is called on the surrogate selector.</span></span>

- <span data-ttu-id="d58e8-107">Se não houver nenhum seletor alternativo ou se ele não manipular o tipo de objeto, uma verificação será feita para determinar se o objeto está marcado com o atributo [Serializable](xref:System.SerializableAttribute).</span><span class="sxs-lookup"><span data-stu-id="d58e8-107">If there is no surrogate selector or if it does not handle the object type, a check is made to determine whether the object is marked with the [Serializable](xref:System.SerializableAttribute) attribute.</span></span> <span data-ttu-id="d58e8-108">Se o objeto não estiver marcado, uma <xref:System.Runtime.Serialization.SerializationException> será gerada.</span><span class="sxs-lookup"><span data-stu-id="d58e8-108">If the object is not, a <xref:System.Runtime.Serialization.SerializationException> is thrown.</span></span>

- <span data-ttu-id="d58e8-109">Se o objeto estiver marcado corretamente, verifique se ele implementa a interface <xref:System.Runtime.Serialization.ISerializable>.</span><span class="sxs-lookup"><span data-stu-id="d58e8-109">If the object is marked appropriately, check whether the object implements the <xref:System.Runtime.Serialization.ISerializable> interface.</span></span> <span data-ttu-id="d58e8-110">Se o objeto implementá-la, <xref:System.Runtime.Serialization.ISerializable.GetObjectData*> será chamado no objeto.</span><span class="sxs-lookup"><span data-stu-id="d58e8-110">If the object does, <xref:System.Runtime.Serialization.ISerializable.GetObjectData*> is called on the object.</span></span>
  
- <span data-ttu-id="d58e8-111">Se o objeto não implementar <xref:System.Runtime.Serialization.ISerializable>, a política de serialização padrão será usada, serializando todos os campos não marcados como [NonSerialized](xref:System.NonSerializedAttribute).</span><span class="sxs-lookup"><span data-stu-id="d58e8-111">If the object does not implement <xref:System.Runtime.Serialization.ISerializable>, the default serialization policy is used, serializing all fields not marked as [NonSerialized](xref:System.NonSerializedAttribute).</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]
  
## <a name="see-also"></a><span data-ttu-id="d58e8-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d58e8-112">See Also</span></span>  
 <span data-ttu-id="d58e8-113">[Serialização Binária](binary-serialization.md) </span><span class="sxs-lookup"><span data-stu-id="d58e8-113">[Binary Serialization](binary-serialization.md) </span></span>  
 [<span data-ttu-id="d58e8-114">Serialização XML e SOAP</span><span class="sxs-lookup"><span data-stu-id="d58e8-114">XML and SOAP Serialization</span></span>](xml-and-soap-serialization.md)