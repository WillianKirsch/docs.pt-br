---
title: '&lt;adicionar&gt; elemento &lt;declaredTypes&gt;'
ms.date: 03/30/2017
helpviewer_keywords:
- data contracts
- dataContractSerializer element
- DataContractSerializer
- DataContractAttribute
ms.assetid: c3d37ae4-8f1c-463f-b195-658c5a7e90a1
ms.openlocfilehash: 90eaf11ce8b9e3675a23ed3875680b03f149b56b
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltaddgt-of-ltdeclaredtypesgt-element"></a>&lt;adicionar&gt; elemento &lt;declaredTypes&gt;
Adiciona um tipo usado pelo <xref:System.Runtime.Serialization.DataContractSerializer> durante a desserialização. Cada tipo declarado inclui os tipos conhecidos que serão retornados como um campo ou propriedade do tipo declarado.  
  
 system.runtime.serialization  
\<dataContractSerializer >  
\<declaredTypes >  
\<Adicionar > de \<declaredTypes >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<add type="String">  
   <knownType type="String">  
       <parameter index="Integer"  
                  type="String" />  
   </knownType>  
</add>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|tipo|Atributo de cadeia de caracteres obrigatória.<br /><br /> Especifica o nome de tipo (incluindo namespace), nome do assembly, número de versão, cultura e token de chave pública.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<knownType >](../../../../../docs/framework/configure-apps/file-schema/wcf/knowntype.md)|Especifica o tipo conhecido para o tipo declarado que está sendo adicionado. Se o tipo declarado é um tipo genérico, você também deve adicionar um elemento de parâmetro para o `<knownType>` elemento para especificar o parâmetro genérico é usado para retornar o tipo conhecido.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<declaredTypes >](../../../../../docs/framework/configure-apps/file-schema/wcf/declaredtypes.md)|Contém os tipos que exigem tipos conhecidos durante a desserialização, o <xref:System.Runtime.Serialization.DataContractSerializer>.|  
  
## <a name="remarks"></a>Comentários  
 Para obter mais informações sobre tipos conhecidos, consulte [tipos conhecidos de contrato de dados](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) e <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
 Consulte o [ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) para obter um exemplo de como usar esse elemento.  
  
> [!NOTE]
>  Se você adicionar o <xref:System.Object> tipo como um `<declaredType>`, um <xref:System.Configuration.ConfigurationErrorsException> é gerada. Isso ocorre porque o <xref:System.Object> tipo não pode ser usado como um tipo declarado em configuração.  
  
## <a name="example"></a>Exemplo  
  
```xml  
<add type="MyCompany.Library.Shape,   
           MyAssembly, Version=2.0.0.0, Culture=neutral,  
           PublicKeyToken=XXXXXX, processorArchitecture=MSIL">  
           <knownType type="MyCompany.Library.Circle,   
                      MyAssembly, Version=2.0.0.0, Culture=neutral,  
                      PublicKeyToken=XXXXXX,  
                      processorArchitecture=MSIL"/>  
</add>  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 [Tipos conhecidos de contrato de dados](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [\<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)  
 [\<Adicionar > de \<declaredTypes >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
