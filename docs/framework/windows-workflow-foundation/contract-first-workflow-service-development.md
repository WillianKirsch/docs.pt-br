---
title: Desenvolvimento de serviço de fluxo de trabalho de primeiro contrato
ms.date: 03/30/2017
ms.assetid: e5dbaa7b-005f-4330-848d-58ac4f42f093
ms.openlocfilehash: 10129fcb40d86d1ca7e42bce68b072e9118bcc88
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="contract-first-workflow-service-development"></a>Desenvolvimento de serviço de fluxo de trabalho de primeiro contrato
Começando com [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], recursos do Windows Workflow Foundation (WF) melhor integração entre serviços web e fluxos de trabalho na forma de desenvolvimento de fluxo de trabalho do contrato, primeiro. A ferramenta de desenvolvimento de fluxo de trabalho de primeiro contrato permite que você crie o contrato no código primeiro. A ferramenta em seguida gera automaticamente um modelo de atividade na caixa de ferramentas para as operações no contrato. Este tópico fornece uma visão geral de como as atividades e as propriedades em um mapa do serviço de fluxo de trabalho para os atributos de um contrato de serviço. Para obter um exemplo passo a passo de criação de um serviço de fluxo de trabalho do contrato, primeiro, consulte [como: criar um serviço de fluxo de trabalho que consome um contrato de serviço existente](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md).  
  
## <a name="in-this-topic"></a>Neste tópico  
  
-   [Mapeamento de atributos de contrato de serviço para atributos de fluxo de trabalho](../../../docs/framework/windows-workflow-foundation/contract-first-workflow-service-development.md#MappingAttributes)  
  
    -   [Atributos de contrato de serviço](../../../docs/framework/windows-workflow-foundation/contract-first-workflow-service-development.md#ServiceContract)  
  
    -   [Atributos de contrato de operação](../../../docs/framework/windows-workflow-foundation/contract-first-workflow-service-development.md#OperationContract)  
  
    -   [Atributos de contrato de mensagem](../../../docs/framework/windows-workflow-foundation/contract-first-workflow-service-development.md#MessageContract)  
  
    -   [Atributos de contrato de dados](../../../docs/framework/windows-workflow-foundation/contract-first-workflow-service-development.md#DataContract)  
  
    -   [Atributos de contrato de falha](../../../docs/framework/windows-workflow-foundation/contract-first-workflow-service-development.md#FaultContract)  
  
-   [Informações de implementação e suporte adicional](../../../docs/framework/windows-workflow-foundation/contract-first-workflow-service-development.md#AdditionalSupport)  
  
    -   [Recursos de contrato de serviço sem suporte](../../../docs/framework/windows-workflow-foundation/contract-first-workflow-service-development.md#UnsupportedFeatures)  
  
    -   [Geração de atividades de mensagens configuradas](../../../docs/framework/windows-workflow-foundation/contract-first-workflow-service-development.md#ActivityGeneration)  
  
##  <a name="MappingAttributes"></a> Mapeamento de atributos de contrato de serviço para atributos de fluxo de trabalho  
 As tabelas nas seções a seguir especificam os atributos de WCF diferentes e as propriedades e como eles são mapeados para as atividades e as propriedades de mensagem em um fluxo de trabalho de primeiro contrato.  
  
-   [Atributos de contrato de serviço](../../../docs/framework/windows-workflow-foundation/contract-first-workflow-service-development.md#ServiceContract)  
  
-   [Atributos de contrato de operação](../../../docs/framework/windows-workflow-foundation/contract-first-workflow-service-development.md#OperationContract)  
  
-   [Atributos de contrato de mensagem](../../../docs/framework/windows-workflow-foundation/contract-first-workflow-service-development.md#MessageContract)  
  
-   [Atributos de contrato de dados](../../../docs/framework/windows-workflow-foundation/contract-first-workflow-service-development.md#DataContract)  
  
-   [Atributos de contrato de falha](../../../docs/framework/windows-workflow-foundation/contract-first-workflow-service-development.md#FaultContract)  
  
###  <a name="ServiceContract"></a> Atributos de contrato de serviço  
  
|Nome da Propriedade|Com suporte|Descrição|Validação de WF|  
|-------------------|---------------|-----------------|-------------------|  
|CallbackContract|Não|Obtém ou define o tipo de contrato de retorno de chamada quando o contrato é do tipo duplex.|(N/D)|  
|ConfigurationName|Não|Obtém ou define o nome usado para localizar o serviço em um arquivo de configuração do aplicativo.|(N/D)|  
|HasProtectionLevel|Sim|Obtém um valor que indica se o membro tem um nível de proteção atribuído.|Receive.ProtectionLevel não pode ser nulo.|  
|Nome|Sim|Obtém ou define o nome para o \<portType > no WSDL Web Services Description Language () do elemento.|Receive.ServiceContractName.LocalName deve corresponder.|  
|Namespace|Sim|Obtém ou define o namespace a \<portType > no WSDL Web Services Description Language () do elemento.|Receive.ServiceContractName.NameSpace deve corresponder|  
|ProtectionLevel|Sim|Especifica se a associação para o contrato deve oferecer suporte ao valor da propriedade ProtectionLevel.|Receive.ProtectionLevel deve corresponder.|  
|SessionMode|Não|Obtém ou define se as sessões são permitidas, não são permitidas ou são necessárias.|(N/D)|  
|TypeId|Não|Quando implementado em uma classe derivada, obtém um identificador exclusivo para este atributo. (Herdada de atributo.)|(N/D)|  
  
 Inserir o corpo da subseção aqui.  
  
###  <a name="OperationContract"></a> Atributos de contrato de operação  
  
|Nome da Propriedade|Com suporte|Descrição|Validação de WF|  
|-------------------|---------------|-----------------|-------------------|  
|Ação|Sim|Obtém ou define a ação WS-Addressing da mensagem de solicitação.|Receive.Action deve corresponder.|  
|AsyncPattern|Não|Indica que uma operação é implementada de forma assíncrona usando Begin\<methodName > e End\<methodName > par de métodos em um contrato de serviço.|(N/D)|  
|HasProtectionLevel|Sim|Obtém um valor que indica se as mensagens para essa operação devem ser criptografadas, assinadas ou ambos.|Receive.ProtectionLevel não pode ser nulo.|  
|IsInitiating|Não|Obtém ou define um valor que indica se o método implementa uma operação que pode iniciar uma sessão no servidor (se essa sessão existir).|(N/D)|  
|IsOneWay|Sim|Obtém ou define um valor que indica se uma operação retorna uma mensagem de resposta.|(Nenhum SendReply para este Receive OR nenhum ReceiveReply para este Send).|  
|IsTerminating|Não|Obtém ou define um valor que indica se a operação de serviço faz o servidor fechar a sessão depois que a mensagem de resposta, se houver, for enviada.|(N/D)|  
|Nome|Sim|Obtém ou define o nome da operação.|Receive.OperationName deve corresponder.|  
|ProtectionLevel|Sim|Obtém ou define um valor que especifica se as mensagens de uma operação devem ser criptografadas, assinadas ou ambos.|Receive.ProtectionLevel deve corresponder.|  
|ReplyAction|Sim|Obtém ou define o valor da ação de SOAP para a mensagem de resposta da operação.|SendReply.Action deve corresponder.|  
|TypeId|Não|Quando implementado em uma classe derivada, obtém um identificador exclusivo para este atributo. (Herdada de atributo.)|(N/D)|  
  
###  <a name="MessageContract"></a> Atributos de contrato de mensagem  
  
|Nome da Propriedade|Com suporte|Descrição|Validação de WF|  
|-------------------|---------------|-----------------|-------------------|  
|HasProtectionLevel|Sim|Obtém um valor que indica se a mensagem tem um nível de proteção.|Sem validação (Receive.Content e SendReply.Content devem corresponder ao tipo do contrato de mensagem).|  
|IsWrapped|Sim|Obtém ou define um valor que especifica se o corpo da mensagem tem um elemento wrapper.|Sem validação (Receive.Content e Sendreply.Content devem corresponder ao tipo do contrato de mensagem).|  
|ProtectionLevel|Não|Obtém ou define um valor que especifica se a mensagem deve ser criptografada, assinada ou ambos.|(N/D)|  
|TypeId|Sim|Quando implementado em uma classe derivada, obtém um identificador exclusivo para este atributo. (Herdada de atributo.)|Sem validação (Receive.Content e SendReply.Content devem corresponder ao tipo do contrato de mensagem).|  
|WrapperName|Sim|Obtém ou define o nome do elemento wrapper do corpo da mensagem.|Sem validação (Receive.Content e SendReply.Content devem corresponder ao tipo do contrato de mensagem).|  
|WrapperNamespace|Não|Obtém ou define o namespace do elemento wrapper do corpo da mensagem.|(N/D)|  
  
###  <a name="DataContract"></a> Atributos de contrato de dados  
  
|Nome da Propriedade|Com suporte|Descrição|Validação de WF|  
|-------------------|---------------|-----------------|-------------------|  
|IsReference|Não|Obtém ou define um valor que indica se deve preservar os dados de referência do objeto.|(N/D)|  
|Nome|Sim|Obtém ou define o nome do contrato de dados para o tipo.|Sem validação (Receive.Content e SendReply.Content devem corresponder ao tipo do contrato de mensagem).|  
|Namespace|Sim|Obtém ou define o namespace para o contrato de dados para o tipo.|Sem validação (Receive.Content e SendReply.Content devem corresponder ao tipo do contrato de mensagem).|  
|TypeId|Não|Quando implementado em uma classe derivada, obtém um identificador exclusivo para este atributo. (Herdada de atributo.)|(N/D)|  
  
###  <a name="FaultContract"></a> Atributos de contrato de falha  
  
|Nome da Propriedade|Com suporte|Descrição|Validação de WF|  
|-------------------|---------------|-----------------|-------------------|  
|Ação|Sim|Obtém ou define a ação da mensagem de falha de SOAP que é especificada como parte do contrato de operação.|SendReply.Action deve corresponder.|  
|DetailType|Sim|Obtém o tipo de um objeto serializável que contém informações de erro.|SendReply.Content deve corresponder ao tipo|  
|HasProtectionLevel|Não|Obtém um valor que indica se a mensagem de falha de SOAP tem um nível de proteção atribuído.|(N/D)|  
|Nome|Não|Obtém ou define o nome da mensagem de falha na linguagem WSDL.|(N/D)|  
|Namespace|Não|Obtém ou define o namespace da falha de SOAP.|(N/D)|  
|ProtectionLevel|Não|Especifica o nível de proteção que a falha de SOAP exige da associação.|(N/D)|  
|TypeId|Não|Quando implementado em uma classe derivada, obtém um identificador exclusivo para este atributo. (Herdada de atributo.)|(N/D)|  
  
##  <a name="AdditionalSupport"></a> Informações de implementação e suporte adicional  
  
-   [Recursos de contrato de serviço sem suporte](../../../docs/framework/windows-workflow-foundation/contract-first-workflow-service-development.md#UnsupportedFeatures)  
  
-   [Geração de atividades de mensagens configuradas](../../../docs/framework/windows-workflow-foundation/contract-first-workflow-service-development.md#ActivityGeneration)  
  
###  <a name="UnsupportedFeatures"></a> Recursos de contrato de serviço sem suporte  
  
-   O uso de tarefas de TPL (Task Parallel Library) nos contratos não tem suporte.  
  
-   A herança em contratos de serviço não tem suporte.  
  
###  <a name="ActivityGeneration"></a> Geração de atividades de mensagens configuradas  
 Dois métodos estáticos públicos são adicionados às atividades <xref:System.ServiceModel.Activities.Receive> e <xref:System.ServiceModel.Activities.SendReply> para dar suporte à geração de atividades de mensagens pré-configuradas ao usar serviços de fluxo de trabalho de primeiro contrato.  
  
-   <xref:System.ServiceModel.Activities.Receive.FromOperationDescription%2A?displayProperty=nameWithType>  
  
-   <xref:System.ServiceModel.Activities.SendReply.FromOperationDescription%2A?displayProperty=nameWithType>  
  
 A atividade gerada por esses métodos deve passar a validação do contrato e, consequentemente, esses métodos são usados internamente como parte da lógica de validação para <xref:System.ServiceModel.Activities.Receive> e <xref:System.ServiceModel.Activities.SendReply>. <xref:System.ServiceModel.Activities.Receive.OperationName%2A>, <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A>, <xref:System.ServiceModel.Activities.Receive.Action%2A>, <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A>, <xref:System.ServiceModel.Activities.Receive.ProtectionLevel%2A> e <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> são todos pré-configurados para corresponder ao contrato importado. Na página de propriedades de conteúdo para as atividades no designer de fluxo de trabalho, o **mensagem** ou **parâmetros** seções também são pré-configurados para coincidir com o contrato.  
  
 Falha WCF contratos também são manipulados, retornando um conjunto separado de configurado <xref:System.ServiceModel.Activities.SendReply> atividades para cada uma das falhas que aparecem no <xref:System.ServiceModel.Description.OperationDescription.Faults%2A> <xref:System.ServiceModel.Description.FaultDescriptionCollection>.  
  
 Para outras partes do <xref:System.ServiceModel.Description.OperationDescription> que não é suportado pelos serviços do WF hoje (por exemplo, WebGet/WebInvoke comportamentos ou comportamentos de operação personalizada), a API irá ignorar esses valores como parte da geração e configuração. Nenhuma exceção será gerada.
