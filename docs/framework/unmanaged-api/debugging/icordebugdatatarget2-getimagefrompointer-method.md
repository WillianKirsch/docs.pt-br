---
title: Método ICorDebugDataTarget2::GetImageFromPointer
ms.date: 03/30/2017
ms.assetid: 939cabe1-b647-4090-b662-eeec23c6c58d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5ddb891091988a21013ee71272d489e7fd1f1283
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugdatatarget2getimagefrompointer-method"></a>Método ICorDebugDataTarget2::GetImageFromPointer
Retorna o endereço base do módulo e o tamanho de um endereço no módulo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetImageFromPointer(  
   [in] CORDB_ADDRESS addr,   
   [out] CORDB_ADDRESS *pImageBase,   
   [out] ULONG32 *pSize  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `addr`  
 Um [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) valor que representa um endereço em um módulo.  
  
 `pImageBase`  
 [out] Um [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) valor que representa o endereço base do módulo.  
  
 `pSize`  
 Um ponteiro para o tamanho do módulo.  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
>  Esse método só está disponível com o .NET Native.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorDebugDataTarget2](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)  
 [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
