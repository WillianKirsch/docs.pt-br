---
title: Método ICorDebugThread::SetDebugState
ms.date: 03/30/2017
api_name:
- ICorDebugThread.SetDebugState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::SetDebugState
helpviewer_keywords:
- ICorDebugThread::SetDebugState method [.NET Framework debugging]
- SetDebugState method [.NET Framework debugging]
ms.assetid: 6382bdf6-d488-4952-b653-cb09b6e1c6c2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ada120b9cb4100bfadff83d96e0226f911958bf7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugthreadsetdebugstate-method"></a>Método ICorDebugThread::SetDebugState
Define os sinalizadores que descrevem o estado de depuração deste ICorDebugThread.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT SetDebugState (  
    [in] CorDebugThreadState state  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `state`  
 [in] Uma combinação bit a bit dos valores de enumeração CorDebugThreadState que especificam o estado de depuração deste thread.  
  
## <a name="remarks"></a>Comentários  
 `SetDebugState` Define o estado de depuração atual do thread. (O "estado atual de depuração" representa o estado de depuração se o processo continuar, não o estado atual propriamente dito.) O valor normal é THREAD_RUNNING. Somente o depurador pode afetar o estado de depuração de um thread. Estados de depuração última em continuar, portanto, se você deseja manter um thread continua THREAD_SUSPENDed em vários, você pode defini-la uma vez e depois disso não precisa se preocupar sobre ele. Suspendendo threads e retomar o processo podem causar deadlocks, embora seja improvável normalmente. Essa é uma qualidade intrínseca de threads e processos e é por design. Um depurador assincronamente pode interromper e retomar os threads para quebrar o deadlock. Se o estado do usuário do thread inclui USER_UNSAFE_POINT, o thread pode bloquear uma coleta de lixo (GC). Isso significa que o thread suspenso tem uma maior possibilidade de causar um deadlock. Isso pode não afetar depuração eventos já está na fila. Assim, um depurador deve esvaziar a fila de eventos todo (chamando [: Hasqueuedcallbacks](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-hasqueuedcallbacks-method.md)) antes de suspender ou retomar os threads. Caso contrário ele pode receber eventos em um thread que ele acredita que já foi suspenso.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
