---
title: Armazenando tinta
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ISF (Ink Serialized Format)
- storing ink [WPF]
- ink [WPF], storing
- retrieving ink [WPF]
- Ink Serialized Format (ISF)
ms.assetid: a3f6d16b-d682-4680-9965-907332b4d2b8
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 244a4bfa5def1319438d66a52120e36aab0e753b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="storing-ink"></a>Armazenando tinta
O <xref:System.Windows.Ink.StrokeCollection.Save%2A> métodos oferecem suporte para armazenar a tinta em Ink serializado Format (ISF). Construtores para o <xref:System.Windows.Ink.StrokeCollection> classe dão suporte para leitura de dados de tinta.  
  
## <a name="ink-storage-and-retrieval"></a>Armazenamento de tinta e recuperação  
 Esta seção descreve como armazenar e recuperar tinta no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] plataforma.  
  
 O exemplo a seguir implementa um manipulador de eventos de clique do botão que apresenta ao usuário uma caixa de diálogo Salvar arquivo e salva a tinta de um <xref:System.Windows.Controls.InkCanvas> em um arquivo.  
  
 [!code-csharp[DigitalInkTopics#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#12)]
 [!code-vb[DigitalInkTopics#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#12)]  
  
 O exemplo a seguir implementa um manipulador de eventos de clique do botão que apresenta ao usuário uma caixa de diálogo Abrir arquivo e lê a tinta do arquivo em um <xref:System.Windows.Controls.InkCanvas> elemento.  
  
 [!code-csharp[DigitalInkTopics#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#13)]
 [!code-vb[DigitalInkTopics#13](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#13)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Controls.InkCanvas>  
 [Windows Presentation Foundation](../../../../docs/framework/wpf/index.md)