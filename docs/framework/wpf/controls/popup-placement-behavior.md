---
title: Comportamento de posicionamento do pop-up
ms.date: 03/30/2017
helpviewer_keywords:
- popups [WPF]
- Popup control [WPF], placing
- placing popups [WPF]
- positioning popups [WPF]
ms.assetid: fbf642e9-f670-4efd-a7af-a67468a1c8e1
ms.openlocfilehash: 3aef3d7863bc02aa4164b1fc9ef4464fbe799cb8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="popup-placement-behavior"></a>Comportamento de posicionamento do pop-up
Um <xref:System.Windows.Controls.Primitives.Popup> controle exibe o conteúdo em uma janela separada que flutua sobre um aplicativo. Você pode especificar a posição de um <xref:System.Windows.Controls.Primitives.Popup> em relação a um controle, o mouse ou a tela usando o <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>, <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>, <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>, e <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> propriedades.  Essas propriedades funcionam em conjunto para fornecer flexibilidade para especificar a posição do <xref:System.Windows.Controls.Primitives.Popup>.  
  
> [!NOTE]
>  O <xref:System.Windows.Controls.ToolTip> e <xref:System.Windows.Controls.ContextMenu> classes também definir essas cinco propriedades e se comportam da mesma forma.  
  

  
<a name="Positioning"></a>   
## <a name="positioning-the-popup"></a>Posicionamento do pop-up  
 O posicionamento de um <xref:System.Windows.Controls.Primitives.Popup> pode ser relativo a um <xref:System.Windows.UIElement> ou para a tela inteira.  O exemplo a seguir cria quatro <xref:System.Windows.Controls.Primitives.Popup> controles relativo a um <xref:System.Windows.UIElement>— neste caso, uma imagem. Todos os <xref:System.Windows.Controls.Primitives.Popup> controles têm o <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> propriedade definida como `image1`, mas cada <xref:System.Windows.Controls.Primitives.Popup> tem um valor diferente para a propriedade de posicionamento.  
  
 [!code-xaml[PopupPositionSnippet#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#3)]  
  
 A ilustração a seguir mostra a imagem e o <xref:System.Windows.Controls.Primitives.Popup> controles  
  
 ![Imagem com quatro controles de pop-up](../../../../docs/framework/wpf/controls/media/popupplacementintro.png "PopupPlacementIntro")  
Imagem com quatro pop-ups  
  
 Esse exemplo simples demonstra como definir a <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> e <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> propriedades, mas usando o <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>, e <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> propriedades, você tem mais controle sobre onde o <xref:System.Windows.Controls.Primitives.Popup> é posicionado.  
  
<a name="Definitions"></a>   
## <a name="definitions-of-terms-the-anatomy-of-a-popup"></a>Definições de termos: a anatomia de um pop-up  
 Os seguintes termos são útil para entender como o <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>, <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>, <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>, e <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> propriedades se relacionam entre si e o <xref:System.Windows.Controls.Primitives.Popup>:  
  
-   Objeto de destino  
  
-   Área de destino  
  
-   Origem do destino  
  
-   Ponto de alinhamento do pop-up  
  
 Estes termos fornecem uma maneira conveniente para se referir a vários aspectos do <xref:System.Windows.Controls.Primitives.Popup> e o controle que está associado.  
  
### <a name="target-object"></a>Objeto de destino  
 O *o objeto de destino* é o elemento que o <xref:System.Windows.Controls.Primitives.Popup> está associado. Se o <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> estiver definida, ela especifica o objeto de destino.  Se <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> não estiver definida e o <xref:System.Windows.Controls.Primitives.Popup> tem um pai, o pai é o objeto de destino.  Se não houver nenhum <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> valor e nenhum pai, não há nenhum objeto de destino e o <xref:System.Windows.Controls.Primitives.Popup> é posicionado em relação à tela.  
  
 O exemplo a seguir cria um <xref:System.Windows.Controls.Primitives.Popup> que é o filho de um <xref:System.Windows.Controls.Canvas>.  O exemplo não define o <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> propriedade o <xref:System.Windows.Controls.Primitives.Popup>. O valor padrão para <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> é <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom?displayProperty=nameWithType>, portanto, o <xref:System.Windows.Controls.Primitives.Popup> aparece abaixo do <xref:System.Windows.Controls.Canvas>.  
  
 [!code-xaml[PopupPositionSnippet#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#1)]  
  
 A ilustração a seguir mostra que o <xref:System.Windows.Controls.Primitives.Popup> é posicionado relativo a <xref:System.Windows.Controls.Canvas>.  
  
 ![Controle Popup sem PlacementTarget](../../../../docs/framework/wpf/controls/media/popupplacementnoplacementtarget.PNG "PopupPlacementNoPlacementTarget")  
Pop-up sem PlacementTarget  
  
 O exemplo a seguir cria um <xref:System.Windows.Controls.Primitives.Popup> que é o filho de um <xref:System.Windows.Controls.Canvas>, mas desta vez o <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> é definido como `ellipse1`, portanto, o pop-up é exibido abaixo de <xref:System.Windows.Shapes.Ellipse>.  
  
 [!code-xaml[PopupPositionSnippet#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#2)]  
  
 A ilustração a seguir mostra que o <xref:System.Windows.Controls.Primitives.Popup> é posicionado relativo a <xref:System.Windows.Shapes.Ellipse>.  
  
 ![Pop-up posicionado em relação uma elipse](../../../../docs/framework/wpf/controls/media/popupplacementwithplacementtarget.PNG "PopupPlacementWithPlacementTarget")  
Pop-up com PlacementTarget  
  
> [!NOTE]
>  Para <xref:System.Windows.Controls.ToolTip>, o valor padrão de <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> é <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>.  Para <xref:System.Windows.Controls.ContextMenu>, o valor padrão de <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> é <xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>. Esses valores são explicados posteriormente, em “Como as propriedades funcionam juntas”.  
  
### <a name="target-area"></a>Área de destino  
 O *área de destino* é a área na tela que o <xref:System.Windows.Controls.Primitives.Popup> é relativo. Nos exemplos anteriores, o <xref:System.Windows.Controls.Primitives.Popup> está alinhada com os limites do objeto de destino, mas em alguns casos, o <xref:System.Windows.Controls.Primitives.Popup> será alinhado à outros limites, mesmo se o <xref:System.Windows.Controls.Primitives.Popup> tem um objeto de destino.  Se o <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> estiver definida, a área de destino é diferente dos limites do objeto de destino.  
  
 O exemplo a seguir cria dois <xref:System.Windows.Controls.Canvas> objetos, cada um contendo uma <xref:System.Windows.Shapes.Rectangle> e um <xref:System.Windows.Controls.Primitives.Popup>.  Em ambos os casos, o destino do objeto para o <xref:System.Windows.Controls.Primitives.Popup> é o <xref:System.Windows.Controls.Canvas>. O <xref:System.Windows.Controls.Primitives.Popup> na primeira <xref:System.Windows.Controls.Canvas> tem o <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> definido, com seus <xref:System.Windows.Rect.X%2A>, <xref:System.Windows.Rect.Y%2A>, <xref:System.Windows.Rect.Width%2A>, e <xref:System.Windows.Rect.Height%2A> propriedades definidas como 50, 50, 50 e 100, respectivamente. O <xref:System.Windows.Controls.Primitives.Popup> no segundo <xref:System.Windows.Controls.Canvas> não tem o <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> definido.  Como resultado, a primeira <xref:System.Windows.Controls.Primitives.Popup> é posicionada abaixo o <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> e a segunda <xref:System.Windows.Controls.Primitives.Popup> é posicionada abaixo o <xref:System.Windows.Controls.Canvas>. Cada <xref:System.Windows.Controls.Canvas> também contém um <xref:System.Windows.Shapes.Rectangle> que tem os mesmos limites como o <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> para o primeiro <xref:System.Windows.Controls.Primitives.Popup>.  Observe que o <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> não cria um elemento visível no aplicativo; o exemplo cria um <xref:System.Windows.Shapes.Rectangle> representar o <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>.  
  
 [!code-xaml[PopupPositionSnippet#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#4)]  
  
 A ilustração a seguir mostra o resultado do exemplo anterior.  
  
 ![Pop-up com e sem PlacementRectangle](../../../../docs/framework/wpf/controls/media/popupplacementplacementrectangle.PNG "PopupPlacementPlacementRectangle")  
Pop-up com e sem PlacementRectangle  
  
### <a name="target-origin-and-popup-alignment-point"></a>Origem do destino e ponto de alinhamento do pop-up  
 A *origem do destino* e o *ponto de alinhamento do pop-up* são pontos de referência na área de destino e no pop-up, respectivamente, usados para posicionamento. Você pode usar o <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> e <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> propriedades para deslocar o pop-up da área de destino.  O <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> e <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> são relativas à origem de destino e o ponto de alinhamento de pop-up. O valor de <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> propriedade determina onde o ponto de alinhamento de origem e o pop-up de destino estão localizados.  
  
 O exemplo a seguir cria um <xref:System.Windows.Controls.Primitives.Popup> e define o <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> e <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> propriedades para 20.  O <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> está definida como <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom> (o padrão), portanto, a origem de destino é o canto inferior esquerdo da área de destino e o ponto de alinhamento de pop-up é o canto superior esquerdo do <xref:System.Windows.Controls.Primitives.Popup>.  
  
 [!code-xaml[PopupPositionSnippet#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#5)]  
  
 A ilustração a seguir mostra o resultado do exemplo anterior.  
  
 ![Posicionamento de pop-up com ponto de alinhamento de origem de destino](../../../../docs/framework/wpf/controls/media/popupplacementtargetoriginalignmentpoint.PNG "PopupPlacementTargetOriginAlignmentPoint")  
Pop-up com HorizontalOffset e VerticalOffset  
  
<a name="How"></a>   
## <a name="how-the-properties-work-together"></a>Como as propriedades trabalham juntas  
 Os valores de <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>, <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, e <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> devem ser consideradas em conjunto para calcular a área de destino correto, a origem de destino e o ponto de alinhamento de pop-up.  Por exemplo, se o valor de <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> é <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>, não há nenhum objeto de destino, o <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> é ignorado, e a área de destino é os limites do ponteiro do mouse. Por outro lado, se <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> é <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>, o <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> ou pai determina o objeto de destino e <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> determina a área de destino.  
  
 A tabela a seguir descreve o objeto de destino, área de destino, origem de destino e ponto de alinhamento de pop-up e indica se <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> e <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> são usados para cada <xref:System.Windows.Controls.Primitives.PlacementMode> valor de enumeração.  
  
|PlacementMode|Objeto de destino|Área de destino|Origem do destino|Ponto de alinhamento do pop-up|  
|-------------------|-------------------|-----------------|-------------------|---------------------------|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>|Não aplicável. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> é ignorado.|A tela ou <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> se ele está definido.  O <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> é em relação à tela.|O canto superior esquerdo da área de destino.|O canto superior esquerdo do <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>|Não aplicável. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> é ignorado.|A tela ou <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> se ele está definido.  O <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> é em relação à tela.|O canto superior esquerdo da área de destino.|O canto superior esquerdo do <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> ou pai.|O objeto de destino, ou <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> se ele está definido.  O <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> é relativo ao objeto de destino.|O canto inferior esquerdo da área de destino.|O canto superior esquerdo do <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Center>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> ou pai.|O objeto de destino, ou <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> se ele está definido.  O <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> é relativo ao objeto de destino.|O centro da área de destino.|O centro do <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Custom>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> ou pai.|O objeto de destino, ou <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> se ele está definido.  O <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> é relativo ao objeto de destino.|Definido pelo <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>.|Definido pelo <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Left>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> ou pai.|O objeto de destino, ou <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> se ele está definido.  O <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> é relativo ao objeto de destino.|O canto superior esquerdo da área de destino.|O canto superior direito do <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>|Não aplicável. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> é ignorado.|Os limites do ponteiro do mouse. <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> é ignorado.|O canto inferior esquerdo da área de destino.|O canto superior esquerdo do <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>|Não aplicável. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> é ignorado.|Os limites do ponteiro do mouse. <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> é ignorado.|O canto superior esquerdo da área de destino.|O canto superior esquerdo do <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Relative>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> ou pai.|O objeto de destino, ou <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> se ele está definido.  O <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> é relativo ao objeto de destino.|O canto superior esquerdo da área de destino.|O canto superior esquerdo do <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> ou pai.|O objeto de destino, ou <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> se ele está definido.  O <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> é relativo ao objeto de destino.|O canto superior esquerdo da área de destino.|O canto superior esquerdo do <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Right>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> ou pai.|O objeto de destino, ou <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> se ele está definido.  O <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> é relativo ao objeto de destino.|O canto superior direito da área de destino.|O canto superior esquerdo do <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Top>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> ou pai.|O objeto de destino, ou <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> se ele está definido.  O <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> é relativo ao objeto de destino.|O canto superior esquerdo da área de destino.|O canto inferior esquerdo do <xref:System.Windows.Controls.Primitives.Popup>.|  
  
 O ilustrações a seguir mostram o <xref:System.Windows.Controls.Primitives.Popup>, aponte a área de destino, origem de destino e o alinhamento de pop-up para cada <xref:System.Windows.Controls.Primitives.PlacementMode> valor. Na figura, a área de destino estiver amarela e o <xref:System.Windows.Controls.Primitives.Popup> é azul.  
  
 ![Pop-up com posicionamento absoluto ou AbsolutePoint](../../../../docs/framework/wpf/controls/media/popupplacementabsolute.png "PopupPlacementAbsolute")  
O posicionamento é Absolute ou AbsolutePoint  
  
 ![Pop-up com posicionamento Bottom](../../../../docs/framework/wpf/controls/media/popupplacementbottom.png "PopupPlacementBottom")  
O posicionamento é Bottom  
  
 ![Pop-up com posicionamento Center](../../../../docs/framework/wpf/controls/media/popupplacementcenter.png "PopupPlacementCenter")  
O posicionamento é Center  
  
 ![Pop-up com posicionamento Left](../../../../docs/framework/wpf/controls/media/popupplacementleft.png "PopupPlacementLeft")  
O posicionamento é Left  
  
 ![Pop-up com posicionamento Mouse](../../../../docs/framework/wpf/controls/media/popupplacementmouse.png "PopupPlacementMouse")  
O posicionamento é Mouse  
  
 ![Pop-up com posicionamento do ponteiro do mouse](../../../../docs/framework/wpf/controls/media/popupplacementmousepoint.png "PopupPlacementMousePoint")  
O posicionamento é MousePoint  
  
 ![Pop-up com posicionamento Relative ou RelativePoint](../../../../docs/framework/wpf/controls/media/popupplacementrelative.png "PopupPlacementRelative")  
O posicionamento é Relative ou RelativePoint  
  
 ![Pop-up com posicionamento direito](../../../../docs/framework/wpf/controls/media/popupplacementright.png "PopupPlacementRight")  
O posicionamento é Right  
  
 ![Pop-up com posicionamento Top](../../../../docs/framework/wpf/controls/media/popupplacementtop.png "PopupPlacementTop")  
O posicionamento é Top  
  
<a name="When"></a>   
## <a name="when-the-popup-encounters-the-edge-of-the-screen"></a>Quando o pop-up encontra a borda da tela  
 Por motivos de segurança, um <xref:System.Windows.Controls.Primitives.Popup> não pode ser ocultada pela borda da tela. Uma das três ações a seguir ocorre quando o <xref:System.Windows.Controls.Primitives.Popup> encontra uma borda de tela:  
  
-   O pop-up própria se realinhará ao longo da borda da tela que seria obscurecer a <xref:System.Windows.Controls.Primitives.Popup>.  
  
-   O pop-up usa um ponto de alinhamento do pop-up diferente.  
  
-   O pop-up usa uma origem do destino e um ponto de alinhamento do pop-up diferentes.  
  
 Essas opções são descritas detalhadamente mais adiante nesta seção.  
  
 O comportamento do <xref:System.Windows.Controls.Primitives.Popup> quando ele encontra uma borda da tela depende do valor da <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> propriedade e qual borda encontra o pop-up de tela. A tabela a seguir resume o comportamento quando o <xref:System.Windows.Controls.Primitives.Popup> encontra uma borda da tela para cada <xref:System.Windows.Controls.Primitives.PlacementMode> valor.  
  
|PlacementMode|Borda superior|Borda inferior|Borda esquerda|Borda direita|  
|-------------------|--------------|-----------------|---------------|----------------|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>|Alinha-se com a borda superior.|Alinha-se com a borda inferior.|Alinha-se com a borda esquerda.|Alinha-se com a borda direita.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>|Alinha-se com a borda superior.|O ponto de alinhamento de pop-up é alterado para o canto inferior esquerdo do <xref:System.Windows.Controls.Primitives.Popup>.|Alinha-se com a borda esquerda.|O ponto de alinhamento de pop-up é alterado para o canto superior direito do <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>|Alinha-se com a borda superior.|A origem de destino é alterado para o canto superior esquerdo da área de destino e o ponto de alinhamento de pop-up é alterado para o canto inferior esquerdo do <xref:System.Windows.Controls.Primitives.Popup>.|Alinha-se com a borda esquerda.|Alinha-se com a borda direita.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Center>|Alinha-se com a borda superior.|Alinha-se com a borda inferior.|Alinha-se com a borda esquerda.|Alinha-se com a borda direita.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Left>|Alinha-se com a borda superior.|Alinha-se com a borda inferior.|A origem de destino é alterado para o canto superior direito da área de destino e o ponto de alinhamento de pop-up é alterado para o canto superior esquerdo do <xref:System.Windows.Controls.Primitives.Popup>.|Alinha-se com a borda direita.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>|Alinha-se com a borda superior.|A origem de destino é alterado para o canto superior esquerdo da área de destino (os limites do ponteiro do mouse) e o ponto de alinhamento de pop-up é alterado para o canto inferior esquerdo do <xref:System.Windows.Controls.Primitives.Popup>.|Alinha-se com a borda esquerda.|Alinha-se com a borda direita.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>|Alinha-se com a borda superior.|O ponto de alinhamento de pop-up é alterado para o canto inferior esquerdo do <xref:System.Windows.Controls.Primitives.Popup>.|Alinha-se com a borda esquerda.|O ponto de alinhamento do pop-up muda para o canto superior direito do pop-up.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Relative>|Alinha-se com a borda superior.|Alinha-se com a borda inferior.|Alinha-se com a borda esquerda.|Alinha-se com a borda direita.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>|Alinha-se com a borda superior.|O ponto de alinhamento de pop-up é alterado para o canto inferior esquerdo do <xref:System.Windows.Controls.Primitives.Popup>.|Alinha-se com a borda esquerda.|O ponto de alinhamento do pop-up muda para o canto superior direito do pop-up.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Right>|Alinha-se com a borda superior.|Alinha-se com a borda inferior.|Alinha-se com a borda esquerda.|A origem de destino é alterado para o canto superior esquerdo da área de destino e o ponto de alinhamento de pop-up é alterado para o canto superior direito do <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Top>|A origem de destino é alterado para o canto inferior esquerdo da área de destino e o ponto de alinhamento de pop-up é alterado para o canto superior esquerdo do <xref:System.Windows.Controls.Primitives.Popup>. Na verdade, isso é o mesmo que quando <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> é <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>.|Alinha-se com a borda inferior.|Alinha-se com a borda esquerda.|Alinha-se com a borda direita.|  
  
### <a name="aligning-to-the-screen-edge"></a>Alinhamento com a borda da tela  
 Um <xref:System.Windows.Controls.Primitives.Popup> pode alinhar à borda da tela reposicionamento em si para todo o <xref:System.Windows.Controls.Primitives.Popup> é visível na tela.  Quando isso ocorre, a distância entre o ponto de alinhamento de origem e o pop-up de destino pode ser diferentes dos valores de <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> e <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>. Quando <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> é <xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>, <xref:System.Windows.Controls.Primitives.PlacementMode.Center>, ou <xref:System.Windows.Controls.Primitives.PlacementMode.Relative>, o <xref:System.Windows.Controls.Primitives.Popup> alinha próprio para cada borda da tela.  Por exemplo, suponha que um <xref:System.Windows.Controls.Primitives.Popup> tem <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> definida como <xref:System.Windows.Controls.Primitives.PlacementMode.Relative> e <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> definido como 100.  Se a parte inferior da tela oculta todo ou parte do <xref:System.Windows.Controls.Primitives.Popup>, o <xref:System.Windows.Controls.Primitives.Popup> reposiciona a mesmo ao longo da borda inferior da tela e a distância vertical entre a origem de destino e o pop-up de ponto de alinhamento é menor que 100. A ilustração a seguir demonstra isso.  
  
 ![Pop-up que se alinha à borda da tela](../../../../docs/framework/wpf/controls/media/popupplacementrelativescreenedge.png "PopupPlacementRelativeScreenEdge")  
Pop-up alinhado com a borda da tela  
  
### <a name="changing-the-popup-alignment-point"></a>Alterando o ponto de alinhamento do pop-up  
 Se <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> é <xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>, <xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>, ou <xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>, o ponto de alinhamento de pop-up é alterado quando o pop-up encontra inferior ou da borda direita da tela.  
  
 A ilustração a seguir demonstra que quando a borda inferior da tela oculta todo ou parte do <xref:System.Windows.Controls.Primitives.Popup>, o ponto de alinhamento de pop-up é o canto inferior esquerdo do <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Novo ponto de alinhamento devido à borda inferior da tela](../../../../docs/framework/wpf/controls/media/popupplacementrelativepointscreenedge.png "PopupPlacementRelativePointScreenEdge")  
O pop-up encontra a borda inferior da tela e altera o ponto de alinhamento do pop-up  
  
 A ilustração a seguir demonstra que, quando o <xref:System.Windows.Controls.Primitives.Popup> está oculto por borda direita da tela, o ponto de alinhamento de pop-up é o canto superior direito do <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Novo ponto de alinhamento de pop-up devido à borda da tela](../../../../docs/framework/wpf/controls/media/popupplacementrelativepointrightscreenedge.png "PopupPlacementRelativePointRightScreenEdge")  
O pop-up encontra a borda direita da tela e altera o ponto de alinhamento do pop-up  
  
 Se o <xref:System.Windows.Controls.Primitives.Popup> encontra bordas inferior e direita de tela, o ponto de alinhamento de pop-up é o canto inferior direito do <xref:System.Windows.Controls.Primitives.Popup>.  
  
### <a name="changing-the-target-origin-and-popup-alignment-point"></a>Mudando a origem do destino e o ponto de alinhamento do pop-up  
 Quando <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> é <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>, <xref:System.Windows.Controls.Primitives.PlacementMode.Left>, <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>, <xref:System.Windows.Controls.Primitives.PlacementMode.Right>, ou <xref:System.Windows.Controls.Primitives.PlacementMode.Top>, o alinhamento de origem e o pop-up de destino do ponto de alteração se for encontrada uma determinada borda da tela.  Depende da borda da tela que faz com que a posição alterar o <xref:System.Windows.Controls.Primitives.PlacementMode> valor.  
  
 A ilustração a seguir demonstra que quando <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> é <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom> e o <xref:System.Windows.Controls.Primitives.Popup> encontra a borda inferior da tela, a origem de destino é o canto superior esquerdo da área de destino e o ponto de alinhamento de pop-up é o canto inferior esquerdo das <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Novo ponto de alinhamento devido à borda inferior da tela](../../../../docs/framework/wpf/controls/media/popupplacementbottomscreenedge.png "PopupPlacementBottomScreenEdge")  
O posicionamento é Bottom e o pop-up encontra a borda inferior da tela  
  
 A ilustração a seguir demonstra que quando <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> é <xref:System.Windows.Controls.Primitives.PlacementMode.Left> e <xref:System.Windows.Controls.Primitives.Popup> encontra a borda esquerda da tela, a origem de destino é o canto superior direito da área de destino e o ponto de alinhamento de pop-up é o canto superior esquerdo do <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Novo ponto de alinhamento devido à borda esquerda da tela](../../../../docs/framework/wpf/controls/media/popupplacementleftscreenedge.png "PopupPlacementLeftScreenEdge")  
O posicionamento é Left e o pop-up encontra a borda esquerda da tela  
  
 A ilustração a seguir demonstra que, quando <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> é <xref:System.Windows.Controls.Primitives.PlacementMode.Right> e <xref:System.Windows.Controls.Primitives.Popup> encontra a borda direita da tela, a origem de destino é o canto superior esquerdo da área de destino e o ponto de alinhamento de pop-up é o canto superior direito das <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Novo ponto de alinhamento devido à borda direita da tela](../../../../docs/framework/wpf/controls/media/popupplacementrightscreenedge.png "PopupPlacementRightScreenEdge")  
O posicionamento é Right e o pop-up encontra a borda direita da tela  
  
 A ilustração a seguir demonstra que, quando <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> é <xref:System.Windows.Controls.Primitives.PlacementMode.Top> e <xref:System.Windows.Controls.Primitives.Popup> encontra a borda superior da tela, a origem de destino é o canto inferior esquerdo da área de destino e o ponto de alinhamento de pop-up é o canto superior esquerdo das <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Novo ponto de alinhamento devido à borda superior da tela](../../../../docs/framework/wpf/controls/media/popupplacementtopscreenedge.png "PopupPlacementTopScreenEdge")  
O posicionamento é Top e o pop-up encontra a borda superior da tela  
  
 A ilustração a seguir demonstra que quando <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> é <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse> e <xref:System.Windows.Controls.Primitives.Popup> encontra a borda inferior da tela, a origem de destino é o canto superior esquerdo da área de destino (os limites do ponteiro do mouse) e o alinhamento de pop-up ponto é o canto inferior esquerdo do <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![novo ponto de alinhamento devido à borda da tela perto do mouse](../../../../docs/framework/wpf/controls/media/popupplacementmousescreenedge.png "PopupPlacementMouseScreenEdge")  
O posicionamento é Mouse e o pop-up encontra a borda inferior da tela  
  
### <a name="customizing-popup-placement"></a>Personalizando o posicionamento do pop-up  
 Você pode personalizar o ponto de alinhamento de origem e o pop-up de destino, definindo o <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> propriedade <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>. Em seguida, defina um <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> delegado que retorna um conjunto de pontos possíveis para posicionamento e eixos principais (em ordem de preferência) para o <xref:System.Windows.Controls.Primitives.Popup>. O ponto que mostra a maior parte do <xref:System.Windows.Controls.Primitives.Popup> está selecionado.  A posição do <xref:System.Windows.Controls.Primitives.Popup> é ajustada automaticamente se o <xref:System.Windows.Controls.Primitives.Popup> está oculto pela borda da tela. Para ver um exemplo, consulte [Especificar uma posição de pop-up personalizada](../../../../docs/framework/wpf/controls/how-to-specify-a-custom-popup-position.md).  
  
## <a name="see-also"></a>Consulte também  
 [Amostra de posicionamento do pop-up](http://go.microsoft.com/fwlink/?LinkID=160032)
