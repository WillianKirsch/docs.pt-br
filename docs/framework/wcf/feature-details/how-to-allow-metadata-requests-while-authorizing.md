---
title: Como permitir solicitações de metadados durante a autorização
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- allowing metadata requests while authorizing [WCF]
ms.assetid: 90cec34f-b619-452b-a056-8b1c0de49d05
ms.openlocfilehash: 2f855080cf3ba4cee08470af77c52945e47a2ec4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-allow-metadata-requests-while-authorizing"></a>Como permitir solicitações de metadados durante a autorização
Durante a autorização personalizada, é necessário para permitir que uma solicitação de metadados a serem processadas. O tópico a seguir apresenta as etapas para validar essa solicitação.  
  
 Para obter mais informações sobre a autorização do Windows Communication Foundation (WCF), consulte [autorização](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md).  
  
### <a name="to-allow-metadata-requests-during-authorization"></a>Para permitir solicitações de metadados durante a autorização  
  
1.  Criar uma extensão de <xref:System.ServiceModel.ServiceAuthorizationManager> classe.  
  
2.  Substituir o método <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A>. O método retorna `true` ou `false` dependendo se a autorização é permitida. Obter informações sobre o procedimento atual o <xref:System.ServiceModel.OperationContext> passado como um parâmetro para o método.  
  
3.  Em uma substituição, verifique o nome do contrato, namespace e a ação, conforme mostrado no exemplo a seguir. Se as condições forem válidas, em seguida, retornar `true.`  
  
4.  Use o ponto de extensibilidade para empregar a classe. Para obter mais informações, consulte [como: criar um Gerenciador de autorização personalizada para um serviço](../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra uma substituição do <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> método.  
  
 [!code-csharp[C_HowtoCheckForMexRequestsInAuthorization#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtocheckformexrequestsinauthorization/cs/source.cs#1)]
 [!code-vb[C_HowtoCheckForMexRequestsInAuthorization#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtocheckformexrequestsinauthorization/vb/source.vb#1)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.ServiceAuthorizationManager>  
 [Autorização](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
 [Gerenciando reivindicações e autorização com o modelo de identidade](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
