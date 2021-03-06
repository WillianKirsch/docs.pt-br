---
title: Método ICorDebugCode2::GetCodeChunks
ms.date: 03/30/2017
api_name:
- ICorDebugCode2.GetCodeChunks
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode2::GetCodeChunks
helpviewer_keywords:
- GetCodeChunks method [.NET Framework debugging]
- ICorDebugCode2::GetCodeChunks method [.NET Framework debugging]
ms.assetid: 210a2f02-2678-4555-bc4a-78a0408764c8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bdfcd45b15ddc1491b12de0fa42901b6d3f7fe9b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugcode2getcodechunks-method"></a>Método ICorDebugCode2::GetCodeChunks
Obtém as partes do código que é composto por esse objeto de código.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetCodeChunks (  
    [in]  ULONG32     cbufSize,  
    [out] ULONG32     *pcnumChunks,  
    [out, size_is(cbufSize), length_is(*pcnumChunks)]   
        CodeChunkInfo chunks[]  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `cbufSize`  
 [in] Tamanho do `chunks` matriz.  
  
 `pcnumChunks`  
 [out] O número de partes retornado no `chunks` matriz.  
  
 `chunks`  
 [out] Uma matriz de estruturas de "CodeChunkInfo", cada uma representando um único bloco de código. Se o valor de `cbufSize` for 0, esse parâmetro pode ser nulo.  
  
## <a name="remarks"></a>Comentários  
 Os blocos de código nunca serão sobrepostos e eles seguirão a ordem na qual eles seriam tenham sido concatenados por [: Getcode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getcode-method.md). Um objeto de código Microsoft intermediate language (MSIL) no .NET Framework versão 2.0 compõem um bloco de código único.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 
