---
title: Como usar o provedor de função do gerenciador de autorização ASP.NET com um serviço
ms.date: 03/30/2017
ms.assetid: f21deb81-91ef-49ef-94d6-494785143271
ms.openlocfilehash: 39103e86090ed57354efaf9c410a2733a58f06bc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service"></a>Como usar o provedor de função do gerenciador de autorização ASP.NET com um serviço
Quando [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] hospeda um serviço Web, você pode integrar o Gerenciador de autorização do aplicativo para fornecer autorização para o serviço. Gerenciador de autorização permite que um desenvolvedor de aplicativos definir as operações individuais, que podem ser agrupadas para tarefas de formulário. Um administrador pode, então, autorizar funções para executar tarefas específicas ou operações individuais. Gerenciador de autorização oferece uma ferramenta de administração como um snap-in do Console de gerenciamento Microsoft (MMC) para gerenciar usuários, tarefas, operações e funções. Os administradores configurar um repositório de política do Gerenciador de autorização em um arquivo XML, o Active Directory, ou em um armazenamento de modo de aplicativo do Active Directory (ADAM).  
  
 O Gerenciador de autorização é integrado no aplicativo configurando o Gerenciador de autorização [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] provedor de função para a [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplicativo que está hospedando o serviço Web. Assim como outros [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] provedores de função, o Gerenciador de autorização [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] provedor de função é configurado usando o <`providers`> elemento.  
  
 O exemplo de código a seguir é uma parte de um arquivo de configuração para um serviço Web que integra o Gerenciador de autorização para o aplicativo.  
  
```xml  
<system.web>  
    <roleManager enabled="true" defaultProvider="AzManRoleProvider">  
      <providers>  
        <add name="AzManRoleProvider"  
             type="System.Web.Security.AuthorizationStoreRoleProvider, System.Web, Version=2.0.0.0, Culture=neutral, publicKeyToken=b03f5f7f11d50a3a"  
             connectionStringName="AzManPolicyStoreConnectionString"   
             applicationName="SecureService"/>  
      </providers>  
    </roleManager>  
</system.web>  
```  
  
 Para obter mais informações sobre como integrar um [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] provedor de função com um aplicativo WCF, consulte [como: usar o provedor de função ASP.NET com um serviço](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md). Para obter mais informações sobre como usar o Gerenciador de autorização com [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], consulte [como: Use o Gerenciador de autorização (AzMan) com o ASP.NET 2.0](http://go.microsoft.com/fwlink/?LinkId=71303).  
  
## <a name="see-also"></a>Consulte também  
 [Como usar o provedor de função ASP.NET com um serviço](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
