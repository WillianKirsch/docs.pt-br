---
title: "Serialização XML e SOAP"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- SOAP, XML serialization
- XML serialization, SOAP
- serialization, SOAP
- serialization, about serialization
- XML serialization
- serialization
ms.assetid: 832ac524-21bc-419a-a27b-ca8bfc45840f
caps.latest.revision: 4
author: Erikre
ms.author: erikre
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 717bcb6f9f72a728d77e2847096ea558a9c50902
ms.openlocfilehash: 412468a03c15cedaa77a5e10be41793565039c4d
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="xml-and-soap-serialization"></a><span data-ttu-id="14c5b-102">Serialização XML e SOAP</span><span class="sxs-lookup"><span data-stu-id="14c5b-102">XML and SOAP Serialization</span></span>
<span data-ttu-id="14c5b-103">A serialização XML converte (serializa) as propriedades e os campos públicos de um objeto (ou os parâmetros e valores de retorno de métodos) em um fluxo XML que esteja de acordo com um documento XSD (linguagem de definição de esquema XML) específico.</span><span class="sxs-lookup"><span data-stu-id="14c5b-103">XML serialization converts (serializes) the public fields and properties of an object, or the parameters and return values of methods, into an XML stream that conforms to a specific XML Schema definition language (XSD) document.</span></span> <span data-ttu-id="14c5b-104">A serialização XML resulta em classes fortemente tipadas com propriedades e campos públicos que são convertidos em um formato serial (neste caso, em XML) para armazenamento ou transporte.</span><span class="sxs-lookup"><span data-stu-id="14c5b-104">XML serialization results in strongly typed classes with public properties and fields that are converted to a serial format (in this case, XML) for storage or transport.</span></span>  
  
 <span data-ttu-id="14c5b-105">Como XML é um padrão aberto, o fluxo XML pode ser processado por qualquer aplicativo, quando necessário, independentemente da plataforma.</span><span class="sxs-lookup"><span data-stu-id="14c5b-105">Because XML is an open standard, the XML stream can be processed by any application, as needed, regardless of platform.</span></span> <span data-ttu-id="14c5b-106">Por exemplo, serviços Web XML criados com ASP.NET usam a classe <xref:System.Xml.Serialization.XmlSerializer> para criar fluxos XML que passam dados entre aplicativos de serviço Web XML por toda a Internet ou entre intranets.</span><span class="sxs-lookup"><span data-stu-id="14c5b-106">For example, XML Web services created using ASP.NET use the <xref:System.Xml.Serialization.XmlSerializer> class to create XML streams that pass data between XML Web service applications throughout the Internet or on intranets.</span></span> <span data-ttu-id="14c5b-107">Por outro lado, a desserialização obtém esse fluxo XML e reconstrói o objeto.</span><span class="sxs-lookup"><span data-stu-id="14c5b-107">Conversely, deserialization takes such an XML stream and reconstructs the object.</span></span>  
  
 <span data-ttu-id="14c5b-108">A serialização XML também pode ser usada para serializar objetos em fluxos XML que atendam à especificação SOAP.</span><span class="sxs-lookup"><span data-stu-id="14c5b-108">XML serialization can also be used to serialize objects into XML streams that conform to the SOAP specification.</span></span> <span data-ttu-id="14c5b-109">SOAP é um protocolo baseado em XML, projetado especificamente para transportar chamadas de procedimentos usando XML.</span><span class="sxs-lookup"><span data-stu-id="14c5b-109">SOAP is a protocol based on XML, designed specifically to transport procedure calls using XML.</span></span>  
  
 <span data-ttu-id="14c5b-110">Para serializar e desserializar objetos, use a classe <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="14c5b-110">To serialize or deserialize objects, use the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span> <span data-ttu-id="14c5b-111">Para criar as classes a serem serializadas, use a ferramenta de definição de esquema XML.</span><span class="sxs-lookup"><span data-stu-id="14c5b-111">To create the classes to be serialized, use the XML Schema Definition tool.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="14c5b-112">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="14c5b-112">In This Section</span></span>  
 [<span data-ttu-id="14c5b-113">Apresentando a serialização XML</span><span class="sxs-lookup"><span data-stu-id="14c5b-113">Introducing XML Serialization</span></span>](../../../docs/standard/serialization/introducing-xml-serialization.md)  
 <span data-ttu-id="14c5b-114">Fornece uma definição geral de serialização, particularmente da serialização XML.</span><span class="sxs-lookup"><span data-stu-id="14c5b-114">Provides a general definition of serialization, particularly XML serialization.</span></span>  
  
 [<span data-ttu-id="14c5b-115">Como serializar um objeto</span><span class="sxs-lookup"><span data-stu-id="14c5b-115">How to: Serialize an Object</span></span>](../../../docs/standard/serialization/how-to-serialize-an-object.md)  
 <span data-ttu-id="14c5b-116">Fornece instruções passo a passo para serializar um objeto.</span><span class="sxs-lookup"><span data-stu-id="14c5b-116">Provides step-by-step instructions for serializing an object.</span></span>  
  
 [<span data-ttu-id="14c5b-117">Como desserializar um objeto</span><span class="sxs-lookup"><span data-stu-id="14c5b-117">How to: Deserialize an Object</span></span>](../../../docs/standard/serialization/how-to-deserialize-an-object.md)  
 <span data-ttu-id="14c5b-118">Fornece instruções passo a passo para desserializar um objeto.</span><span class="sxs-lookup"><span data-stu-id="14c5b-118">Provides step-by-step instructions for deserializing an object.</span></span>  
  
 [<span data-ttu-id="14c5b-119">Exemplos de serialização XML</span><span class="sxs-lookup"><span data-stu-id="14c5b-119">Examples of XML Serialization</span></span>](../../../docs/standard/serialization/examples-of-xml-serialization.md)  
 <span data-ttu-id="14c5b-120">Fornece exemplos que demonstram os conceitos básicos da serialização XML.</span><span class="sxs-lookup"><span data-stu-id="14c5b-120">Provides examples that demonstrate the basics of XML serialization.</span></span>  
  
 [<span data-ttu-id="14c5b-121">A ferramenta de definição de esquema XML e a serialização XML</span><span class="sxs-lookup"><span data-stu-id="14c5b-121">The XML Schema Definition Tool and XML Serialization</span></span>](../../../docs/standard/serialization/the-xml-schema-definition-tool-and-xml-serialization.md)  
 <span data-ttu-id="14c5b-122">Descreve como usar a ferramenta de definição de esquema XML para criar classes que aderem a um esquema XSD específico ou para gerar um esquema XML de um arquivo .dll.</span><span class="sxs-lookup"><span data-stu-id="14c5b-122">Describes how to use the XML Schema Definition tool to create classes that adhere to a particular XML Schema definition language (XSD) schema, or to generate an XML Schema from a .dll file.</span></span>  
  
 [<span data-ttu-id="14c5b-123">Controlando a serialização XML usando atributos</span><span class="sxs-lookup"><span data-stu-id="14c5b-123">Controlling XML Serialization Using Attributes</span></span>](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md)  
 <span data-ttu-id="14c5b-124">Descreve como controlar a serialização usando atributos.</span><span class="sxs-lookup"><span data-stu-id="14c5b-124">Describes how to control serialization by using attributes.</span></span>  
  
 [<span data-ttu-id="14c5b-125">Atributos que controlam a serialização XML</span><span class="sxs-lookup"><span data-stu-id="14c5b-125">Attributes That Control XML Serialization</span></span>](../../../docs/standard/serialization/attributes-that-control-xml-serialization.md)  
 <span data-ttu-id="14c5b-126">Lista os atributos que são usados para controlar a serialização XML.</span><span class="sxs-lookup"><span data-stu-id="14c5b-126">Lists the attributes that are used to control XML serialization.</span></span>  
  
 [<span data-ttu-id="14c5b-127">Como especificar um nome de elemento alternativo para um fluxo XML</span><span class="sxs-lookup"><span data-stu-id="14c5b-127">How to: Specify an Alternate Element Name for an XML Stream</span></span>](../../../docs/standard/serialization/how-to-specify-an-alternate-element-name-for-an-xml-stream.md)  
 <span data-ttu-id="14c5b-128">Apresenta um cenário avançado de como gerar vários fluxos XML substituindo a serialização.</span><span class="sxs-lookup"><span data-stu-id="14c5b-128">Presents an advanced scenario showing how to generate multiple XML streams by overriding the serialization.</span></span>  
  
 [<span data-ttu-id="14c5b-129">Como controlar a serialização de classes derivadas</span><span class="sxs-lookup"><span data-stu-id="14c5b-129">How to: Control Serialization of Derived Classes</span></span>](../../../docs/standard/serialization/how-to-control-serialization-of-derived-classes.md)  
 <span data-ttu-id="14c5b-130">Fornece um exemplo de como controlar a serialização de classes derivadas.</span><span class="sxs-lookup"><span data-stu-id="14c5b-130">Provides an example of how to control the serialization of derived classes.</span></span>  
  
 [<span data-ttu-id="14c5b-131">Como qualificar elementos XML e nomes de atributos XML</span><span class="sxs-lookup"><span data-stu-id="14c5b-131">How to: Qualify XML Element and XML Attribute Names</span></span>](../../../docs/standard/serialization/how-to-qualify-xml-element-and-xml-attribute-names.md)  
 <span data-ttu-id="14c5b-132">Descreve como definir e controlar a maneira como namespaces XML são usados no fluxo XML.</span><span class="sxs-lookup"><span data-stu-id="14c5b-132">Describes how to define and control the way in which XML namespaces are used in the XML stream.</span></span>  
  
 [<span data-ttu-id="14c5b-133">Serialização XML com Serviços Web XML</span><span class="sxs-lookup"><span data-stu-id="14c5b-133">XML Serialization with XML Web Services</span></span>](../../../docs/standard/serialization/xml-serialization-with-xml-web-services.md)  
 <span data-ttu-id="14c5b-134">Explica como a serialização XML é usada em serviços Web XML.</span><span class="sxs-lookup"><span data-stu-id="14c5b-134">Explains how XML serialization is used in XML Web services.</span></span>  
  
 [<span data-ttu-id="14c5b-135">Como serializar um objeto como um fluxo XML codificado para SOAP</span><span class="sxs-lookup"><span data-stu-id="14c5b-135">How to: Serialize an Object as a SOAP-Encoded XML Stream</span></span>](../../../docs/standard/serialization/how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md)  
 <span data-ttu-id="14c5b-136">Descreve como usar a classe <xref:System.Xml.Serialization.XmlSerializer> para criar fluxos XML SOAP codificados em conformidade com a seção 5 do documento "Simple Object Access Protocol (SOAP) 1.1" do World Wide Web Consortium (www.w3.org).</span><span class="sxs-lookup"><span data-stu-id="14c5b-136">Describes how to use the <xref:System.Xml.Serialization.XmlSerializer> class to create encoded SOAP XML streams that conform to section 5 of the World Wide Web Consortium (www.w3.org) document titled "Simple Object Access Protocol (SOAP) 1.1."</span></span>  
  
 [<span data-ttu-id="14c5b-137">Como substituir a serialização XML de SOAP codificada</span><span class="sxs-lookup"><span data-stu-id="14c5b-137">How to: Override Encoded SOAP XML Serialization</span></span>](../../../docs/standard/serialization/how-to-override-encoded-soap-xml-serialization.md)  
 <span data-ttu-id="14c5b-138">Descreve o processo para substituir a serialização XML de objetos, como mensagens SOAP.</span><span class="sxs-lookup"><span data-stu-id="14c5b-138">Describes the process for overriding XML serialization of objects as SOAP messages.</span></span>  
  
 [<span data-ttu-id="14c5b-139">Atributos que controlam a serialização SOAP codificada</span><span class="sxs-lookup"><span data-stu-id="14c5b-139">Attributes That Control Encoded SOAP Serialization</span></span>](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md)  
 <span data-ttu-id="14c5b-140">Lista os atributos que são usados para controlar a serialização codificada por SOAP.</span><span class="sxs-lookup"><span data-stu-id="14c5b-140">Lists the attributes that are used to control SOAP-encoded serialization.</span></span>  
  
 [<span data-ttu-id="14c5b-141">\<Elemento system.xml.serialization></span><span class="sxs-lookup"><span data-stu-id="14c5b-141">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)  
 <span data-ttu-id="14c5b-142">O elemento de configuração de nível superior para controlar a serialização XML.</span><span class="sxs-lookup"><span data-stu-id="14c5b-142">The top-level configuration element for controlling XML serialization.</span></span>  
  
 <span data-ttu-id="14c5b-143">Elemento [\<dateTimeSerialization>](../../../docs/standard/serialization/datetimeserialization-element.md)</span><span class="sxs-lookup"><span data-stu-id="14c5b-143">[\<dateTimeSerialization> Element](../../../docs/standard/serialization/datetimeserialization-element.md)</span></span>  
 <span data-ttu-id="14c5b-144">Controla o modo de serialização de objetos <xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="14c5b-144">Controls the serialization mode of <xref:System.DateTime> objects.</span></span>  
  
 <span data-ttu-id="14c5b-145">Elemento [\<schemaImporterExtensions>](../../../docs/standard/serialization/schemaimporterextensions-element.md)</span><span class="sxs-lookup"><span data-stu-id="14c5b-145">[\<schemaImporterExtensions> Element](../../../docs/standard/serialization/schemaimporterextensions-element.md)</span></span>  
 <span data-ttu-id="14c5b-146">Contém tipos que são usados pela classe <xref:System.Xml.Serialization.XmlSchemaImporter>.</span><span class="sxs-lookup"><span data-stu-id="14c5b-146">Contains types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> class.</span></span>  
  
 [<span data-ttu-id="14c5b-147">Elemento \<add> para \<xmlSchemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="14c5b-147">\<add> Element for \<xmlSchemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-xmlschemaimporterextensions.md)  
 <span data-ttu-id="14c5b-148">Adiciona tipos que são usados pela classe <xref:System.Xml.Serialization.XmlSchemaImporter>.</span><span class="sxs-lookup"><span data-stu-id="14c5b-148">Adds types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> class.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="14c5b-149">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="14c5b-149">Related Sections</span></span>  
 [<span data-ttu-id="14c5b-150">Tecnologias de desenvolvimento avançadas</span><span class="sxs-lookup"><span data-stu-id="14c5b-150">Advanced Development Technologies</span></span>](http://msdn.microsoft.com/en-us/c4a7e341-f0c6-4df4-a74f-223387ac6e4e)  
 <span data-ttu-id="14c5b-151">Fornece links para obter mais informações sobre tarefas e técnicas sofisticadas de desenvolvimento no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="14c5b-151">Provides links to more information on sophisticated development tasks and techniques in the .NET Framework.</span></span>  
  
 [<span data-ttu-id="14c5b-152">Serviços Web XML criados com o ASP.NET e clientes de serviços Web XML</span><span class="sxs-lookup"><span data-stu-id="14c5b-152">XML Web Services Created Using ASP.NET and XML Web Service Clients</span></span>](http://msdn.microsoft.com/en-us/1e64af78-d705-4384-b08d-591a45f4379c)  
 <span data-ttu-id="14c5b-153">Fornece tópicos que descrevem e explicam como programar serviços Web XML usando ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="14c5b-153">Provides topics that describe and explain how to program XML Web services using ASP.NET.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14c5b-154">Consulte também</span><span class="sxs-lookup"><span data-stu-id="14c5b-154">See Also</span></span>  
 [<span data-ttu-id="14c5b-155">Serialização binária</span><span class="sxs-lookup"><span data-stu-id="14c5b-155">Binary Serialization</span></span>](../../../docs/standard/serialization/binary-serialization.md)
