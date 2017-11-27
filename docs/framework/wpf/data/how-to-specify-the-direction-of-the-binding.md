---
title: "Como especificar a direção da associação"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- direction of binding [WPF]
- binding direction [WPF]
- data binding [WPF], direction of binding
ms.assetid: 37334478-028b-4514-86c9-1420709f4818
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bdcda02a61f0114bfbbe5d5c411cb397cddcf683
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-specify-the-direction-of-the-binding"></a>Como especificar a direção da associação
Este exemplo mostra como especificar se a associação atualiza apenas a propriedade de destino da associação (destino), a propriedade de origem da associação (origem) ou a propriedade de destino e a propriedade de origem.  
  
## <a name="example"></a>Exemplo  
 Você usa o <xref:System.Windows.Data.Binding.Mode%2A> propriedade para especificar a direção da associação. A lista de enumeração a seguir mostra as opções disponíveis para atualizações de associação:  
  
-   <xref:System.Windows.Data.BindingMode.TwoWay>Atualiza a propriedade de destino ou a propriedade sempre que a propriedade de destino ou a propriedade de origem é alterado.  
  
-   <xref:System.Windows.Data.BindingMode.OneWay>Atualiza a propriedade de destino somente quando a propriedade de origem for alterada.  
  
-   <xref:System.Windows.Data.BindingMode.OneTime>Atualiza a propriedade de destino somente quando o aplicativo for iniciado ou quando o <xref:System.Windows.FrameworkElement.DataContext%2A> sofrer uma alteração.  
  
-   <xref:System.Windows.Data.BindingMode.OneWayToSource>Atualiza a propriedade de origem quando a propriedade de destino é alterado.  
  
-   <xref:System.Windows.Data.BindingMode.Default>faz com que o padrão <xref:System.Windows.Data.Binding.Mode%2A> valor da propriedade de destino a ser usado.  
  
 Para obter mais informações, consulte a enumeração <xref:System.Windows.Data.BindingMode>.  
  
 O exemplo a seguir mostra como definir o <xref:System.Windows.Data.Binding.Mode%2A> propriedade.  
  
 [!code-xaml[DirectionalBinding#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#4)]  
  
 Para detectar alterações de origem (aplicáveis a <xref:System.Windows.Data.BindingMode.OneWay> e <xref:System.Windows.Data.BindingMode.TwoWay> associações), a fonte deve implementar um mecanismo de notificação de alteração de propriedade adequado, como <xref:System.ComponentModel.INotifyPropertyChanged>. Consulte [implementar notificação de alteração de propriedade](../../../../docs/framework/wpf/data/how-to-implement-property-change-notification.md) para obter um exemplo de um <xref:System.ComponentModel.INotifyPropertyChanged> implementação.  
  
 Para <xref:System.Windows.Data.BindingMode.TwoWay> ou <xref:System.Windows.Data.BindingMode.OneWayToSource> associações, você pode controlar o intervalo das atualizações na origem definindo o <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> propriedade. Consulte <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> para obter mais informações.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Data.Binding>  
 [Visão geral da vinculação de dados](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Tópicos explicativos](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)