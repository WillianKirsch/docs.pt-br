---
title: Globalização e localização de aplicativos do .NET Framework
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- international applications [.NET Framework]
- globalization [.NET Framework], encoding
- global applications
- internationalization
- world-ready applications
- application development [.NET Framework], globalization
- multilingual application development
ms.assetid: 9a59696b-d89b-45bd-946d-c75da4732d02
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 26c237d082a56d17b2d8493bff52dbac6faca8b2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="globalizing-and-localizing-net-framework-applications"></a>Globalização e localização de aplicativos do .NET Framework
O desenvolvimento de um [aplicativo pronto para o mundo](http://msdn.microsoft.com/goglobal/bb978433.aspx), incluindo um aplicativo que possa ser localizado em um ou mais idiomas, envolve três etapas: globalização, análise de possibilidade de localização e localização.  
  
 [Globalização](../../../docs/standard/globalization-localization/globalization.md)  
 Esta etapa envolve a criação e a codificação de um aplicativo que seja independente de cultura e idioma, bem como que ofereça suporte a interfaces de usuário localizadas e dados regionais para todos os usuários. Ela envolve a tomada de decisões de design e de programação que não sejam baseadas em suposições para culturas específicas. Mesmo quando um aplicativo globalizado não está localizado, ele foi criado e escrito para que possa ser localizado posteriormente em um ou mais idiomas com relativa facilidade.  
  
 [Análise de possibilidade de localização](../../../docs/standard/globalization-localization/localizability-review.md)  
 Essa etapa envolve a verificação do código e do design de um aplicativo para garantir que ele possa ser facilmente localizado e para identificar potenciais obstáculos à localização, bem como verificar se o código executável do aplicativo está separado de seus recursos. Se a fase de globalização foi eficaz, a análise de capacidade de localização confirmará as opções de design e codificação feitas durante a globalização. O estágio de localizabilidade também pode identificar todos os problemas restantes para que o código-fonte do aplicativo não precise ser modificado durante o estágio de localização.  
  
 [Localização](../../../docs/standard/globalization-localization/localization.md)  
 Essa etapa envolve a personalização de um aplicativo para culturas ou regiões específicas. Se as etapas de globalização e localizabilidade tiverem sido feitas corretamente, a localização consistirá principalmente na tradução da interface de usuário.  
  
 Seguir estas três etapas oferece duas vantagens:  
  
-   Libera você de ter que readaptar um aplicativo projetado para uma única cultura, como inglês dos EUA, para oferecer suporte a culturas adicionais.  
  
-   Isso resulta em aplicativos localizados que são mais estáveis e possuem menos bugs.  
  
 O .NET Framework fornece suporte abrangente ao desenvolvimento de aplicativos preparados para o mundo e localizados. Em particular, muitos tipos membros de tipos na biblioteca de classes do .NET Framework auxiliam na globalização ao retornarem valores que refletem as convenções da cultura do usuário atual ou de uma cultura específica. Além disso, o .NET Framework oferece suporte assemblies satélites que facilitam o processo de localizar um aplicativo.  
  
 Confira mais informações na [Documentação de globalização](/globalization/).  
  
## <a name="in-this-section"></a>Nesta seção  
 [Globalização](../../../docs/standard/globalization-localization/globalization.md)  
 Discute o primeiro estágio da criação de um aplicativo pronto para o mundo, o que envolve o projeto e a codificação de um aplicativo independente de cultura e idioma.  
  
 [Análise de possibilidade de localização](../../../docs/standard/globalization-localization/localizability-review.md)  
 Discute o segundo estágio da criação de um aplicativo localizado, o que envolve a identificação de obstáculos potenciais à localização.  
  
 [Localização](../../../docs/standard/globalization-localization/localization.md)  
 Discute o estágio final da criação de um aplicativo localizado, o que envolve a personalização da interface de usuário de um aplicativo para regiões ou culturas específicas.  
  
 [Operações de cadeia de caracteres que não levam em conta a cultura](../../../docs/standard/globalization-localization/culture-insensitive-string-operations.md)  
 Descreve como usar métodos e classes do .NET Framework sensíveis a culturas por padrão para obter resultados que não diferenciam culturas.  
  
 [Melhores práticas para o desenvolvimento de aplicativos prontos para o mundo](../../../docs/standard/globalization-localization/best-practices-for-developing-world-ready-apps.md)  
 Descreve as práticas recomendadas a serem seguidas para globalização, localização e desenvolvimento de aplicativos ASP.NET prontos para o mundo.  
  
## <a name="reference"></a>Referência  
 Namespace <xref:System.Globalization?displayProperty=nameWithType>  
 Contém classes que definem informações relacionadas à cultura, incluindo idioma, país/região, calendários em uso, padrões de formato para datas, moeda, números e ordem de classificação para cadeias de caracteres.  
  
 Namespace <xref:System.Resources>  
 Fornece classes para a criação, manipulação e utilização de recursos.  
  
 Namespace <xref:System.Text>  
 Contém classes que representam ASCII, ANSI, Unicode e outras codificações de caracteres.  
  
 [Resgen.exe (Gerador de Arquivo de Recurso)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md)  
 Descreve como usar Resgen.exe para converter arquivos .txt e XML (.resx) para arquivos .resources binários do Common Language Runtime.  
  
 [Winres.exe (Editor de Recursos do Windows Forms)](../../../docs/framework/tools/winres-exe-windows-forms-resource-editor.md)  
 Descreve como usar Winres.exe para localizar formulários do Windows Forms.
