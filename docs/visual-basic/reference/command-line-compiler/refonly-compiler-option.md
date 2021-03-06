---
title: -refonly (Visual Basic)
ms.date: 03/16/2018
f1_keywords:
- -refonly
helpviewer_keywords:
- /refonly compiler option [Visual Basic]
- -refonly compiler option [Visual Basic]
- refonly compiler option [Visual Basic]
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e8f6c15084ac9b1a07aef8a0311edfcc4a93337c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="-refonly-visual-basic"></a>-refonly (Visual Basic)

O **- refonly** opção indica que a saída primária da compilação deve ser uma referência de assembly em vez de um assembly de implementação. O parâmetro `-refonly` silenciosamente desabilita a geração de PDBs, uma vez que assemblies de referência não podem ser executados.

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]

## <a name="syntax"></a>Sintaxe

```console
-refonly
```

## <a name="remarks"></a>Comentários

Visual Basic oferece suporte a `-refout` alternar a partir da versão 15,3.

Assemblies de referência são somente metadados assemblies que contêm metadados, mas nenhum código de implementação. Eles incluem informações de tipo e membro para tudo, exceto tipos anônimos. O motivo para usar corpos `throw null` (em vez de nenhum corpo) é que PEVerify poderia ser executado e passado (validando, assim, a integridade dos metadados).

Assemblies de referência incluem um nível de conjunto [ReferenceAssembly](xref:System.Runtime.CompilerServices.ReferenceAssemblyAttribute) atributo. Esse atributo pode ser especificado na origem (assim, o compilador não precisará sintetizá-lo). Devido a esse atributo, tempos de execução irá recusar carregar assemblies de referência para execução (mas ainda pode ser carregados em um contexto exclusivo de reflexão). Ferramentas que refletem em assemblies precisam garantir que eles carregam assemblies de referência como somente reflexão; Caso contrário, o tempo de execução gera um <xref:System.BadImageFormatException>.

As opções `-refonly` e [`-refout`](refout-compiler-option.md) são mutualmente exclusivas.

## <a name="see-also"></a>Consulte também
[-refout](refout-compiler-option.md)   
[Compilador de linha de comando do Visual Basic](index.md)  
[Linhas de Comando de Compilação de Exemplo](sample-compilation-command-lines.md)   
