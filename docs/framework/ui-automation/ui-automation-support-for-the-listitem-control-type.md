---
title: Suporte de automação de interface de usuário para o tipo de controle ListItem
ms.date: 03/30/2017
helpviewer_keywords:
- control types, List
- List Item control type
- UI Automation, List Item control type
ms.assetid: 34f533bf-fc14-4e78-8fee-fb7107345fab
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 2ad93923ecc41b7a8b564d2f53129a09a78b1085
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="ui-automation-support-for-the-listitem-control-type"></a>Suporte de automação de interface de usuário para o tipo de controle ListItem
> [!NOTE]
>  Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Este tópico fornece informações sobre [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] suporte para o <xref:System.Windows.Automation.ControlType.ListItem> tipo de controle. Em [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], um tipo de controle é um conjunto de condições que um controle precisa atender para usar o <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> propriedade. As condições incluem diretrizes específicas para [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] estrutura de árvore [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] valores de propriedade e padrões de controle.  
  
 Controles de item de lista são um exemplo de controles que implementam o tipo de controle.  
  
 As seções a seguir definem as [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] estrutura, propriedades, padrões de controle e eventos para o tipo de controle de árvore. O [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] requisitos se aplicam a todos os controles de lista, se [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], ou [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Estrutura de árvore de automação da interface do usuário necessário  
 A tabela a seguir descreve o modo de exibição de controle e exibição de conteúdo de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] controla de árvore que se refere ao item de lista e descreve o que pode ser contido em cada modo de exibição. Para obter mais informações sobre o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] de árvore, consulte [visão geral de árvore de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
|Exibição de controle|Exibição de conteúdo|  
|------------------|------------------|  
|Item de lista<br /><br /> -Imagem (0 ou mais)<br />-Texto (0 ou mais)<br />-Editar (0 ou mais)|Item de lista|  
  
 Os filhos de um controle de item de lista na exibição de conteúdo do [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] árvore sempre deve ser "0". Se a estrutura do controle é tal que outros itens estão sob o item de lista, em seguida, você deve seguir os requisitos para o [suporte de automação de interface do usuário para o tipo de controle TreeItem](../../../docs/framework/ui-automation/ui-automation-support-for-the-treeitem-control-type.md) tipo de controle.  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Propriedades de automação de interface do usuário necessário  
 A seguinte tabela lista o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] propriedades cujos valores ou definição são especialmente relevantes para controles de item de lista. Para obter mais informações sobre [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] propriedades, consulte [propriedades de automação de interface do usuário para clientes](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Propriedade|Valor|Observações|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Consulte as observações.|O valor dessa propriedade deve ser exclusivo em todos os controles em um aplicativo.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Consulte as observações.|Esse valor dessa propriedade deve incluir a área do conteúdo da imagem e texto do item da lista.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Depende|Se o controle de lista tem um ponto clicável (um ponto que pode ser clicado para fazer com que a lista definir o foco) desse ponto deve ser exposto através desta propriedade. Se o controle de lista é completamente coberto por itens de lista descendentes, ele gerará um <xref:System.Windows.Automation.NoClickablePointException> para indicar que o cliente deve solicitar um item dentro do controle de lista um ponto clicável.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Consulte as observações.|O valor da propriedade de nome de um controle item de lista vem do conteúdo de texto do item.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Consulte as observações.|Se houver um rótulo de texto estático, em seguida, essa propriedade deve expor uma referência para esse controle.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Item de lista|Esse valor é o mesmo para todas as estruturas de interface do usuário.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"item de lista"|Cadeia de caracteres localizada correspondente ao tipo de controle.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|verdadeiro|O controle de lista é sempre incluído na exibição de conteúdo do [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] árvore.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|verdadeiro|O controle de lista é sempre incluído na exibição de controle de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] árvore.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|verdadeiro|Se o contêiner pode aceitar a entrada do teclado, em seguida, o valor da propriedade deve ser verdadeiro.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>|""|O texto de ajuda para controles de lista deve explicar por que o usuário está sendo solicitado a fazer uma escolha de uma lista de opções, que normalmente é o mesmo tipo de informações apresentadas por meio de uma dica de ferramenta. Por exemplo, "Selecione um item para definir a resolução de vídeo para o monitor".|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ItemTypeProperty>|Depende|Essa propriedade deve ser exposta para controles de item de lista que estão representando um objeto subjacente. Esses controles de item de lista normalmente têm um ícone associado ao controle que o usuário associa ao objeto subjacente.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>|Depende|Esta propriedade deve retornar um valor para se o item de lista no momento é colocado na exibição dentro do contêiner pai que implementa o padrão de controle Scroll.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns"></a>Padrões de controle de automação de interface do usuário necessário  
 A seguinte tabela lista o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] devem ser suportados por controles de item de lista de padrões de controle. Para obter mais informações sobre padrões de controle, consulte [visão geral de padrões de controle de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
|Padrão de controle|Suporte|Observações|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionItemProvider>|Sim|Controle de item de lista deve implementar esse padrão de controle. Isso permite que lista os controles de itens transmitir quando eles estiverem selecionados.|  
|<xref:System.Windows.Automation.Provider.IScrollItemProvider>|Depende|Se o item de lista estiver contido em um contêiner rolável esse padrão de controle deve ser implementado.|  
|<xref:System.Windows.Automation.Provider.IToggleProvider>|Depende|Se o item de lista é selecionável e a ação não executará uma alteração de estado de seleção então este padrão de controle precisa ser implementado.|  
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|Depende|Se o item pode ser manipulado para mostrar ou ocultar informações esse padrão de controle deve ser implementado.|  
|<xref:System.Windows.Automation.Provider.IValueProvider>|Depende|Se o item pode ser editado então este padrão de controle precisa ser implementado. As alterações no controle de item de lista fará com que as alterações dos valores de <xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>, e <xref:System.Windows.Automation.Provider.IValueProvider.Value%2A>.|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider>|Depende|Se navegação espacial item a item tem suporte dentro do contêiner de lista e o contêiner estiver disposto em linhas e colunas então o padrão de controle Item de grade deve ser implementado.|  
|<xref:System.Windows.Automation.Provider.IInvokeProvider>|Depende|Se o item tiver um comando que pode ser executado nele, diferente da seleção, então esse padrão deve ser implementado. Normalmente, isso é uma ação associada a duas vezes no controle de item de lista. Exemplos seriam lançar um documento de [!INCLUDE[TLA#tla_winexpl](../../../includes/tlasharptla-winexpl-md.md)], ou a execução de um arquivo de música [!INCLUDE[TLA#tla_wmp](../../../includes/tlasharptla-wmp-md.md)].|  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Eventos de automação de interface do usuário necessário  
 A seguinte tabela lista o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] devem ser suportados por todos os controles de item de lista de eventos. Para obter mais informações sobre eventos, consulte [visão geral sobre eventos de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Evento|Suporte|Observações|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent>|Depende|Nenhum|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent>|Necessária|Nenhum|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent>|Necessária|Nenhum|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent>|Necessária|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> evento de propriedade alterada.|Necessária|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty> evento de propriedade alterada.|Necessária|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> evento de propriedade alterada.|Necessária|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Necessária|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ItemStatusProperty> evento de propriedade alterada.|Depende|Nenhum|  
|<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers.ExpandCollapseStateProperty> evento de propriedade alterada.|Depende|Nenhum|  
|<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty> evento de propriedade alterada.|Depende|Nenhum|  
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty> evento de propriedade alterada.|Depende|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Necessária|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Necessária|Nenhum|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Automation.ControlType.ListItem>  
 [Visão geral de tipos de controle de automação da interface do usuário](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)  
 [Visão geral de Automação da Interface do Usuário](../../../docs/framework/ui-automation/ui-automation-overview.md)
