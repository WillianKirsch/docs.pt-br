---
title: Interface ICorDebugRemoteTarget
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugRemoteTarget
api_location: CorDebug.dll
api_type: COM
f1_keywords: ICorDebugRemoteTarget
helpviewer_keywords: ICorDebugRemoteTarget interface [.NET Framework debugging]
ms.assetid: bd9936a6-cc24-4869-8761-0988664464e6
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 38357072b3a6e8e8a326a16600b2d7ed56cdcb2e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugremotetarget-interface"></a>Interface ICorDebugRemoteTarget
Fornece métodos que permitem aos desenvolvedores depurar aplicativos baseados no Silverlight no ambiente do common language runtime (CLR).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
interface ICorDebugRemoteTarget  : IUnknown  
{  
    HRESULT GetHostName (  
        [in]  ULONG32                    cchHostName,  
        [out] ULONG32*                   pcchHostName,  
        [out, size_is(cchHostName),  
              length_is(*pcchHostName)]  
                  WCHAR szHostName[]  
        );  
};  
```  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método Icordebugremotetarget::](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-gethostname-method.md)|Retorna o nome do host ou o endereço IP de um computador remoto.|  
  
## <a name="remarks"></a>Comentários  
 Não há suporte para a depuração (ou seja, código gerenciado e nativo) de modo misto no Windows 95, Windows 98 ou Windows ME ou em plataformas x86 não (como IA-64 e AMD64).  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl  
  
 **Biblioteca:** : CorGuids.lib  
  
 **Versões do .NET framework:** 3.5 SP1  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorDebugRemote](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)  
 [Interface ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
 [Interfaces de depuração](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)