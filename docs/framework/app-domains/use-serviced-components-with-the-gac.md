---
title: Usando componentes atendidos com o cache de assemblies global
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- GAC (global assembly cache), serviced components
- serviced components, global assembly cache
- global assembly cache, serviced components
ms.assetid: 3423e5d9-234c-4571-8161-e35f6d130128
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 703e71661c7a679b85e60726f53b275fce1a4d6a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="using-serviced-components-with-the-global-assembly-cache"></a>Usando componentes atendidos com o cache de assemblies global
Componentes atendidos (componentes COM+ com código gerenciado) devem ser colocados no Cache de Assembly Global. Em alguns cenários, o Common Language Runtime e os Serviços COM+ podem manipular componentes atendidos que não estão no Cache de Assembly Global; em outros cenários, eles não podem. Os seguintes cenários ilustram isso:  
  
-   Para componentes atendidos em um aplicativo COM+ para Servidor, o assembly que contém os componentes deve estar no Cache de Assembly Global, pois Dllhost.exe não é executado no mesmo diretório que contém os componentes atendidos.  
  
-   Para componentes atendidos em um aplicativo de COM+ Library, o tempo de execução e COM+ Services podem resolver as referências ao assembly que contém os componentes pesquisando o diretório atual. Nesse caso, o assembly não precisa estar no cache de assembly global.  
  
-   Para componentes atendidos em um aplicativo ASP.NET, a situação é diferente. Se você colocar o assembly que contém os componentes atendidos no diretório bin da base de aplicativo e usar o registro sob demanda, o assembly será copiado por sombra para o cache de download, pois o ASP.NET aproveita os recursos de sombra do tempo de execução.  
  
## <a name="see-also"></a>Consulte também  
 [Como trabalhar com assemblies e o cache de assembly global](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 [Gacutil.exe (Ferramenta do Cache de Assemblies Global)](../../../docs/framework/tools/gacutil-exe-gac-tool.md)
