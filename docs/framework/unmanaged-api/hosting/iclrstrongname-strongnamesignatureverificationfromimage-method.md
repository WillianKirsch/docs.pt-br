---
title: Método ICLRStrongName::StrongNameSignatureVerificationFromImage
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameSignatureVerificationFromImage
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureVerificationFromImage
helpviewer_keywords:
- ICLRStrongName::StrongNameSignatureVerificationFromImage method [.NET Framework hosting]
- StrongNameSignatureVerificationFromImage method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: da91c138-ee30-4fd4-a040-464d97d7e41a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 60dbb8d8461015c791a70d6c2617b1c81e5ba17f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="iclrstrongnamestrongnamesignatureverificationfromimage-method"></a>Método ICLRStrongName::StrongNameSignatureVerificationFromImage
Verifica se um assembly que já foi mapeado para a memória é válido para a chave pública associada.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT StrongNameSignatureVerificationFromImage (  
    [in]  BYTE    *pbBase,  
    [in]  DWORD   dwLength,  
    [in]  DWORD   dwInFlags,  
    [out] DWORD   *pdwOutFlags  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pbBase`  
 [in] O endereço virtual relativo do manifesto do assembly mapeados.  
  
 `dwLength`  
 [in] O tamanho, em bytes, da imagem mapeada.  
  
 `dwInFlags`  
 [in] Sinalizadores que influenciam o comportamento de verificação. Há suporte para os seguintes valores:  
  
-   `SN_INFLAG_FORCE_VER` (0x00000001) - força a verificação mesmo se for necessário substituir as configurações do registro.  
  
-   `SN_INFLAG_INSTALL` (0x00000002) - Especifica que esta é a primeira verificação executada nesta imagem.  
  
-   `SN_INFLAG_ADMIN_ACCESS` (0x00000004) - Especifica que o cache permite acesso somente aos usuários que têm privilégios administrativos.  
  
-   `SN_INFLAG_USER_ACCESS` (0x00000008) - Especifica que o assembly será acessível somente para o usuário atual.  
  
-   `SN_INFLAG_ALL_ACCESS` (0x00000010) - Especifica que o cache não fornecem nenhuma garantia de restrição de acesso.  
  
-   `SN_INFLAG_RUNTIME` (0x80000000) - reservado para a depuração.  
  
 `pdwOutFlags`  
 [out] Um sinalizador para obter informações de saída adicionais. Há suporte para o seguinte valor:  
  
-   `SN_OUTFLAG_WAS_VERIFIED` (0x00000001) - Este valor é definido como `false` para especificar se a verificação foi bem-sucedida devido às configurações do registro.  
  
## <a name="return-value"></a>Valor de retorno  
 `S_OK` Se o método foi concluída com êxito; Caso contrário, um valor HRESULT que indica uma falha (consulte [valores HRESULT comuns](http://go.microsoft.com/fwlink/?LinkId=213878) para obter uma lista).  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MetaHost.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
