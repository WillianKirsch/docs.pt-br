---
title: SpinLock
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- synchronization primitives, SpinLock
ms.assetid: f9af93bb-7a0d-4ba5-afe8-74f48b6b6958
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f7d1d95030d2bc9f9288ae134471c150a37291b9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="spinlock"></a>SpinLock
A estrutura <xref:System.Threading.SpinLock> é uma primitiva de sincronização de nível inferior com exclusão mútua que gira enquanto aguarda adquirir um bloqueio. Em computadores com vários núcleos, quando os tempos de espera devem ser curtos e a contenção mínima, o <xref:System.Threading.SpinLock> pode ter melhor desempenho que outros tipos de bloqueios. No entanto, recomendamos usar o <xref:System.Threading.SpinLock> somente quando você determinar pela criação de perfil que o método <xref:System.Threading.Monitor?displayProperty=nameWithType> ou os métodos <xref:System.Threading.Interlocked> estejam causando lentidão significativa no desempenho do seu programa.  
  
 O <xref:System.Threading.SpinLock> pode resultar no fracionamento de tempo do thread mesmo que ainda não tenha adquirido o bloqueio. Isso é feito para evitar a inversão de prioridade de thread e para habilitar o progresso do coletor de lixo. Ao usar um <xref:System.Threading.SpinLock>, nenhum thread deverá manter o bloqueio por mais do que um breve intervalo de tempo ou fechar enquanto mantém o bloqueio.  
  
 Como o SpinLock é um tipo de valor, você deve passá-lo explicitamente por referência se quiser que as duas cópias referenciem o mesmo bloqueio.  
  
 Confira mais informações sobre como usar este tipo em <xref:System.Threading.SpinLock?displayProperty=nameWithType>. Veja um exemplo em [Como: usar o SpinLock para sincronização de nível inferior](../../../docs/standard/threading/how-to-use-spinlock-for-low-level-synchronization.md).  
  
 O <xref:System.Threading.SpinLock> oferece suporte a um modo de *controle* de *thread*- que pode ser usado durante a fase de desenvolvimento para ajudar a controlar o thread que está mantendo o bloqueio em um momento específico. O modo de controle de thread é muito útil para depuração, mas é recomendável desativá-lo na versão de lançamento do seu programa porque ele pode reduzir o desempenho. Confira mais informações em [Como: habilitar o modo de controle de thread no SpinLock](../../../docs/standard/threading/how-to-enable-thread-tracking-mode-in-spinlock.md).  
  
## <a name="see-also"></a>Consulte também  
 [Objetos e recursos de threading](../../../docs/standard/threading/threading-objects-and-features.md)
