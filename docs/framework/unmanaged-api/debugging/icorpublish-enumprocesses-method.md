---
title: Método ICorPublish::EnumProcesses
ms.date: 03/30/2017
api_name:
- ICorPublish.EnumProcesses
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublish::EnumProcesses
helpviewer_keywords:
- ICorPublish::EnumProcesses method [.NET Framework debugging]
- EnumProcesses method [.NET Framework debugging]
ms.assetid: 4ae765f0-93b2-4b6f-aea1-7b0cf44e04a7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2779138a0999e34ad6424d76ddfebbcfdf611d58
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icorpublishenumprocesses-method"></a>Método ICorPublish::EnumProcesses
Obtém um enumerador para os processos gerenciados em execução neste computador.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT EnumProcesses (  
    [in] COR_PUB_ENUMPROCESS       Type,  
    [out] ICorPublishProcessEnum   **ppIEnum  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `Type`  
 Um valor de [COR_PUB_ENUMPROCESS](../../../../docs/framework/unmanaged-api/debugging/cor-pub-enumprocess-enumeration.md) enumeração que especifica o tipo de processo a ser recuperado. Na versão atual, COR_PUB_MANAGEDONLY só é válido.  
  
 `ppIEnum`  
 Um ponteiro para o endereço de um [ICorPublishProcessEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md) instância que o enumerador dos processos.  
  
## <a name="remarks"></a>Comentários  
 Coleção do enumerador de processos é baseada em um instantâneo dos processos que estão em execução quando o `EnumProcesses` método é chamado. O enumerador não incluirá todos os processos que terminar antes ou iniciarem após `EnumProcesses` é chamado.  
  
 O `EnumProcesses` método pode ser chamado mais de uma vez neste [ICorPublish](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md) instância para criar uma nova coleção atualizada de processos. Coleções existentes não serão afetadas por chamadas subsequentes a `EnumProcesses` método.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorPub.idl, CorPub.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorPublish](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)
