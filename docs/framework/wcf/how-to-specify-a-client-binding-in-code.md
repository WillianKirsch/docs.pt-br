---
title: Como especificar uma associação de cliente em código
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6bee5da4-adf7-42e6-8f78-63a9e5c6dbad
ms.openlocfilehash: 3a05c60b6e68f87c31e74774bf0b50e535477b56
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-specify-a-client-binding-in-code"></a>Como especificar uma associação de cliente em código
Neste exemplo, um cliente é criado para usar um serviço de cálculo e a associação para esse cliente é especificada imperativa no código. O cliente acessa o `CalculatorService`, que implementa o `ICalculator` interface e o serviço e o cliente use o <xref:System.ServiceModel.BasicHttpBinding> classe.  
  
 Este procedimento pressupõe que a Calculadora está sendo executado. Para obter informações sobre o serviço, consulte [como: especificar uma associação de serviço na configuração](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md). Ele também usa o [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)fornece Windows Communication Foundation (WCF) para gerar automaticamente os componentes do cliente. A ferramenta gera o código do cliente para acessar o serviço.  
  
 O cliente é criado em duas partes. Svcutil.exe gera o `ClientCalculator` que implementa o `ICalculator` interface. Este aplicativo cliente é construído, criando uma instância de `ClientCalculator` e, em seguida, especificando a associação e o endereço para o serviço no código.  
  
 Para a cópia de origem deste exemplo, consulte o [BasicBinding](../../../docs/framework/wcf/samples/basicbinding.md) exemplo.  
  
### <a name="to-specify-a-custom-binding-in-code"></a>Para especificar uma associação personalizada em código  
  
1.  Use o Svcutil.exe da linha de comando para gerar o código de metadados de serviço.  
  
    ```  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>   
    ```  
  
2.  O cliente que é gerado contém o `ICalculator` interface que define o contrato de serviço que deve atender a implementação do cliente.  
  
     [!code-csharp[C_HowTo_CodeClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#1)]
     [!code-vb[C_HowTo_CodeClientBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#1)]  
  
3.  O cliente gerado também contém a implementação de `ClientCalculator`.  
  
     [!code-csharp[C_HowTo_CodeClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#2)]
     [!code-vb[C_HowTo_CodeClientBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#2)]  
  
4.  Criar uma instância do `ClientCalculator` que usa o <xref:System.ServiceModel.BasicHttpBinding> de classe em um aplicativo cliente e, em seguida, chamar as operações de serviço no endereço especificado.  
  
     [!code-csharp[C_HowTo_CodeClientBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#3)]
     [!code-vb[C_HowTo_CodeClientBinding#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#3)]  
  
5.  Compile e execute o cliente.  
  
## <a name="see-also"></a>Consulte também  
 [Usando associações para configurar serviços e clientes](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
