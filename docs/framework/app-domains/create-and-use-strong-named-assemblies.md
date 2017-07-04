---
title: Criando e usando assemblies de nomes fortes | Microsoft Docs
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- strong-name bypass feature
- strong-named assemblies, about strong-named assemblies
- strong-named assemblies
- signing assemblies
- assemblies [.NET Framework], signing
- strong-named assemblies, scenarios
- assemblies [.NET Framework], strong-named
- strong-named assemblies, loading into trusted application domains
- assembly binding, strong-named
ms.assetid: ffbf6d9e-4a88-4a8a-9645-4ce0ee1ee5f9
caps.latest.revision: 17
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 7c694fc26d65fee277c7a6873494c8d1900408b2
ms.contentlocale: pt-br
ms.lasthandoff: 06/02/2017

---
# <a name="creating-and-using-strong-named-assemblies"></a>Criando e usando assemblies de nomes fortes
<a name="top"></a> Um nome forte consiste na identidade do assembly — seu nome de texto simples, número de versão e informações de cultura (se fornecidas) — mais uma chave pública e uma assinatura digital. Ela é gerada de um arquivo do assembly usando a chave privada correspondente. (O arquivo do assembly inclui o manifesto do assembly, que contém os nomes e os hashes de todos os arquivos que compõem o assembly.)  
  
 Assembly de nome forte só pode usar tipos de outros assemblies de nome forte. Caso contrário, a segurança do assembly de nome forte estaria comprometida.  
  
 Esta visão geral contém as seguintes seções:  
  
-   [Cenário de nome forte](#strong_name_scenario)  
  
-   [Ignorando a verificação de assinatura de assemblies confiáveis](#bypassing_signature_verification)  
  
-   [Tópicos relacionados](#related_topics)  
  
<a name="strong_name_scenario"></a>   
## <a name="strong-name-scenario"></a>Cenário de nome forte  
 O cenário a seguir descreve o processo de assinar um assembly com um nome forte e posteriormente referencia-lo por esse nome.  
  
1.  O Assembly A é criado com um nome forte usando um dos seguintes métodos:  
  
    -   Usando um ambiente de desenvolvimento que dá suporte à criação de nomes fortes, como [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)].  
  
    -   Criando um par de chaves de criptografia usando a [ferramenta Nome Forte (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) e atribuindo esse par de chaves ao assembly usando um compilador de linha de comando ou o [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md). O Software Development Kit do Windows (SDK do Windows) fornece o Sn.exe e AI.exe.  
  
2.  O ambiente de desenvolvimento ou a ferramenta assina o hash do arquivo que contém o manifesto do assembly com a chave privada do desenvolvedor. Esta assinatura digital é armazenada no arquivo PE que contém o manifesto do Assembly A.  
  
3.  O Assembly B é um consumidor do Assembly A. A seção de referência do manifesto do Assembly B inclui um token que representa a chave pública do Assembly A. Um token é uma parte da chave pública completa e é usado em vez da chave em si para economizar espaço.  
  
4.  O Common Language Runtime verifica a assinatura do nome forte quando o assembly é colocado no cache de assembly global. Ao associar por nome forte no tempo de execução, o Common Language Runtime compara a chave armazenada no manifesto do Assembly B com a chave usada para gerar o nome forte do Assembly A. Se as verificações de segurança do .NET Framework e a associação forem bem-sucedidas, o Assembly B terá uma garantia de que os bits do Assembly A não foram violados e que esses bits na verdade vêm dos desenvolvedores do Assembly A.  
  
> [!NOTE]
>  Este cenário não aborda questões de confiança. Os assemblies podem carregar assinaturas Microsoft Authenticode completas além de um nome forte. As assinaturas Authenticode incluem um certificado que estabelece a relação de confiança. É importante observar que os nomes fortes não exigem que o código esteja assinado dessa maneira. Na verdade, as chaves usadas para gerar a assinatura do nome forte não precisam ser as mesmas chaves usadas para gerar uma assinatura Authenticode.  
  
 [Voltar ao início](#top)  
  
<a name="bypassing_signature_verification"></a>   
## <a name="bypassing-signature-verification-of-trusted-assemblies"></a>Ignorando a verificação de assinatura de assemblies confiáveis  
 Desde o [!INCLUDE[net_v35SP1_long](../../../includes/net-v35sp1-long-md.md)], as assinaturas de nome forte não são validadas quando um assembly é carregado em um domínio do aplicativo de confiança total, como o domínio do aplicativo padrão para a zona `MyComputer`. Isso é conhecido como o recurso de desvio de nome forte. Em um ambiente de confiança total, as exigências de <xref:System.Security.Permissions.StrongNameIdentityPermission> sempre têm êxito para assemblies assinados de confiança total, independentemente de sua assinatura. O recurso de desvio de nome forte evita a sobrecarga desnecessária de verificação de assinatura de nome forte dos assemblies de confiança total nessa situação, permitindo que os assemblies carreguem mais rapidamente.  
  
 O recurso de desvio se aplica a qualquer assembly que está assinado com um nome forte e que tem as seguintes características:  
  
-   Totalmente confiável sem a evidência <xref:System.Security.Policy.StrongName> (por exemplo, tem a evidência de zona `MyComputer`).  
  
-   Carregado em um <xref:System.AppDomain> totalmente confiável.  
  
-   Carregado de um local sob a propriedade <xref:System.AppDomainSetup.ApplicationBase%2A> desse <xref:System.AppDomain>.  
  
-   Não assinado com atraso.  
  
 Esse recurso pode ser desabilitado para aplicativos individuais ou para um computador. Consulte [Como desabilitar o recurso de desvio de nome forte](../../../docs/framework/app-domains/how-to-disable-the-strong-name-bypass-feature.md).  
  
 [Voltar ao início](#top)  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>Tópicos relacionados  
  
|Título|Descrição|  
|-----------|-----------------|  
|[Como criar um par de chaves pública/privada](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md)|Descreve como criar um par de chaves de criptografia para assinar um assembly.|  
|[Como assinar um assembly com um nome forte](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)|Descreve como criar um assembly de nome forte.|  
|[Aprimoramento da nomenclatura forte](../../../docs/framework/app-domains/enhanced-strong-naming.md)|Descreve aprimoramentos para nomes fortes no [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].|  
|[Como referenciar um assembly de nome forte](../../../docs/framework/app-domains/how-to-reference-a-strong-named-assembly.md)|Descreve como referenciar tipos ou recursos em um assembly de nome forte no tempo de compilação ou no tempo de execução.|  
|[Como desabilitar o recurso de desvio de nome forte](../../../docs/framework/app-domains/how-to-disable-the-strong-name-bypass-feature.md)|Descreve como desabilitar o recurso que ignora a validação de assinaturas de nome forte. Esse recurso pode ser desabilitado para todos ou para aplicativos específicos.|  
|[Criação de assemblies](../../../docs/framework/app-domains/create-assemblies.md)|Fornece uma visão geral dos assemblies de arquivo único e vários arquivos.|  
|[NIB: Como: Atrasar a assinatura de um assembly (Visual Studio)](http://msdn.microsoft.com/en-us/cab63b7a-591e-4674-b236-d77cd29a79ea)|Explica como assinar um assembly com um nome forte, depois que o assembly foi criado.|  
|[Sn.exe (Ferramenta Nome Forte)](../../../docs/framework/tools/sn-exe-strong-name-tool.md)|Descreve a ferramenta incluída no .NET Framework que ajuda a criar assemblies com nomes fortes. Esta ferramenta oferece opções para o gerenciamento de chaves, geração de assinaturas e verificação de assinaturas.|  
|[Al.exe (Assembly Linker)](../../../docs/framework/tools/al-exe-assembly-linker.md)|Descreve a ferramenta incluída no .NET Framework que gera um arquivo que tem um manifesto do assembly de módulos ou arquivos de recurso.|