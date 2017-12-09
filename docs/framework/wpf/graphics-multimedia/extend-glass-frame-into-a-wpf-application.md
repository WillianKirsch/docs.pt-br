---
title: "Estender quadro com efeito de transparência em um aplicativo WPF"
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
- applications [WPF], extending glass frames into
- graphics [WPF], extending glass frames into applications
- extending glass frames into applications [WPF]
- glass frames [WPF], extending into applications
ms.assetid: 74388a3a-4b69-4a9d-ba1f-e107636bd660
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d943d0b91d6f740144399d758a5ed80460f0eb6d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="extend-glass-frame-into-a-wpf-application"></a><span data-ttu-id="538b2-102">Estender quadro com efeito de transparência em um aplicativo WPF</span><span class="sxs-lookup"><span data-stu-id="538b2-102">Extend Glass Frame Into a WPF Application</span></span>
<span data-ttu-id="538b2-103">Este tópico demonstra como estender o quadro com efeito de transparência do [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)] para a área de cliente de um aplicativo [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)].</span><span class="sxs-lookup"><span data-stu-id="538b2-103">This topic demonstrates how to extend the [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)] glass frame into the client area of a [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="538b2-104">Este exemplo só funcionará em um computador [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] que executa o DWM (Gerenciador de Janelas da Área de Trabalho) com efeito de transparência habilitado.</span><span class="sxs-lookup"><span data-stu-id="538b2-104">This example will only work on a [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] machine running the Desktop Window Manager (DWM) with glass enabled.</span></span> <span data-ttu-id="538b2-105">O [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] Home Basic edition não dá suporte ao efeito de transparência.</span><span class="sxs-lookup"><span data-stu-id="538b2-105">[!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] Home Basic edition does not support the transparent glass effect.</span></span> <span data-ttu-id="538b2-106">Áreas que normalmente seriam renderizadas com efeito de transparência nas outras edições do [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] são renderizadas opacas.</span><span class="sxs-lookup"><span data-stu-id="538b2-106">Areas that would typically render with the transparent glass effect on other editions of [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] are rendered opaque.</span></span>  
  
## <a name="example"></a><span data-ttu-id="538b2-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="538b2-107">Example</span></span>  
 <span data-ttu-id="538b2-108">A imagem a seguir ilustra o quadro com efeito de transparência estendido na barra de endereços do Internet Explorer 7.</span><span class="sxs-lookup"><span data-stu-id="538b2-108">The following image illustrates the glass frame extended into the address bar of Internet Explorer 7.</span></span>  
  
 <span data-ttu-id="538b2-109">**Internet Explorer com quadro com efeito de transparência estendido atrás da barra de endereços.**</span><span class="sxs-lookup"><span data-stu-id="538b2-109">**Internet Explorer with extended glass frame behind address bar.**</span></span>  
  
 <span data-ttu-id="538b2-110">![IE7 com quadro com efeito de transparência estendido por trás da barra de endereços.](../../../../docs/framework/wpf/graphics-multimedia/media/ie7glasstopbar.PNG "IE7glasstopbar")</span><span class="sxs-lookup"><span data-stu-id="538b2-110">![IE7 with glass frame extended behind address bar.](../../../../docs/framework/wpf/graphics-multimedia/media/ie7glasstopbar.PNG "IE7glasstopbar")</span></span>  
  
 <span data-ttu-id="538b2-111">Para estender o quadro com efeito de transparência em um aplicativo [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], é necessário obter acesso ao [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="538b2-111">To extend the glass frame on a [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] application, access to unmanaged [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] is needed.</span></span> <span data-ttu-id="538b2-112">O exemplo de código a seguir faz uma invocação de plataforma (pinvoke) para os dois [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] necessários para estender o quadro para a área de cliente.</span><span class="sxs-lookup"><span data-stu-id="538b2-112">The following code example does a Platform Invoke (pinvoke) for the two [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] needed to extend the frame into the client area.</span></span> <span data-ttu-id="538b2-113">Cada um desses [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] são declarados em uma classe chamada **NonClientRegionAPI**.</span><span class="sxs-lookup"><span data-stu-id="538b2-113">Each of these [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] are declared in a class called **NonClientRegionAPI**.</span></span>  
  
```csharp  
[StructLayout(LayoutKind.Sequential)]  
public struct MARGINS  
{  
    public int cxLeftWidth;      // width of left border that retains its size  
    public int cxRightWidth;     // width of right border that retains its size  
    public int cyTopHeight;      // height of top border that retains its size  
    public int cyBottomHeight;   // height of bottom border that retains its size  
};  
  
[DllImport("DwmApi.dll")]  
public static extern int DwmExtendFrameIntoClientArea(  
    IntPtr hwnd,  
    ref MARGINS pMarInset);  
```  
  
```vb  
<StructLayout(LayoutKind.Sequential)>  
        Public Structure MARGINS  
            Public cxLeftWidth As Integer ' width of left border that retains its size  
            Public cxRightWidth As Integer ' width of right border that retains its size  
            Public cyTopHeight As Integer ' height of top border that retains its size  
            Public cyBottomHeight As Integer ' height of bottom border that retains its size  
        End Structure  
  
        <DllImport("DwmApi.dll")>  
        Public Shared Function DwmExtendFrameIntoClientArea(ByVal hwnd As IntPtr, ByRef pMarInset As MARGINS) As Integer  
        End Function  
```  
  
 <span data-ttu-id="538b2-114">[DwmExtendFrameIntoClientArea](https://msdn.microsoft.com/library/aa969512.aspx) é a função de DWM que estende o quadro para a área de cliente.</span><span class="sxs-lookup"><span data-stu-id="538b2-114">[DwmExtendFrameIntoClientArea](https://msdn.microsoft.com/library/aa969512.aspx) is the DWM function that extends the frame into the client area.</span></span> <span data-ttu-id="538b2-115">Ela recebe dois parâmetros: um identificador de janela e uma estrutura [MARGINS](https://msdn.microsoft.com/library/bb773244.aspx).</span><span class="sxs-lookup"><span data-stu-id="538b2-115">It takes two parameters; a window handle and a [MARGINS](https://msdn.microsoft.com/library/bb773244.aspx) structure.</span></span> <span data-ttu-id="538b2-116">[MARGINS](https://msdn.microsoft.com/library/bb773244.aspx) é usado para instruir o DWM sobre quanto a mais o quadro deve ser estendido para a área de cliente.</span><span class="sxs-lookup"><span data-stu-id="538b2-116">[MARGINS](https://msdn.microsoft.com/library/bb773244.aspx) is used to tell the DWM how much extra the frame should be extended into the client area.</span></span>  
  
## <a name="example"></a><span data-ttu-id="538b2-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="538b2-117">Example</span></span>  
 <span data-ttu-id="538b2-118">Para usar a função [DwmExtendFrameIntoClientArea](https://msdn.microsoft.com/library/aa969512.aspx), é necessário obter um identificador de janela.</span><span class="sxs-lookup"><span data-stu-id="538b2-118">To use the [DwmExtendFrameIntoClientArea](https://msdn.microsoft.com/library/aa969512.aspx) function, a window handle must be obtained.</span></span> <span data-ttu-id="538b2-119">Em [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], o identificador de janela pode ser obtido o <xref:System.Windows.Interop.HwndSource.Handle%2A> propriedade de um <xref:System.Windows.Interop.HwndSource>.</span><span class="sxs-lookup"><span data-stu-id="538b2-119">In [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], the window handle can be obtained from the <xref:System.Windows.Interop.HwndSource.Handle%2A> property of an <xref:System.Windows.Interop.HwndSource>.</span></span> <span data-ttu-id="538b2-120">No exemplo a seguir, o quadro é estendido para a área cliente sobre o <xref:System.Windows.FrameworkElement.Loaded> eventos da janela.</span><span class="sxs-lookup"><span data-stu-id="538b2-120">In the following example, the frame is extended into the client area on the <xref:System.Windows.FrameworkElement.Loaded> event of the window.</span></span>  
  
```csharp  
void OnLoaded(object sender, RoutedEventArgs e)  
{  
   try  
   {  
      // Obtain the window handle for WPF application  
      IntPtr mainWindowPtr = new WindowInteropHelper(this).Handle;  
      HwndSource mainWindowSrc = HwndSource.FromHwnd(mainWindowPtr);  
      mainWindowSrc.CompositionTarget.BackgroundColor = Color.FromArgb(0, 0, 0, 0);  
  
      // Get System Dpi  
      System.Drawing.Graphics desktop = System.Drawing.Graphics.FromHwnd(mainWindowPtr);  
      float DesktopDpiX = desktop.DpiX;  
      float DesktopDpiY = desktop.DpiY;  
  
      // Set Margins  
      NonClientRegionAPI.MARGINS margins = new NonClientRegionAPI.MARGINS();  
  
      // Extend glass frame into client area  
      // Note that the default desktop Dpi is 96dpi. The  margins are  
      // adjusted for the system Dpi.  
      margins.cxLeftWidth = Convert.ToInt32(5 * (DesktopDpiX / 96));  
      margins.cxRightWidth = Convert.ToInt32(5 * (DesktopDpiX / 96));  
      margins.cyTopHeight = Convert.ToInt32(((int)topBar.ActualHeight + 5) * (DesktopDpiX / 96));  
      margins.cyBottomHeight = Convert.ToInt32(5 * (DesktopDpiX / 96));  
  
      int hr = NonClientRegionAPI.DwmExtendFrameIntoClientArea(mainWindowSrc.Handle, ref margins);  
      //  
      if (hr < 0)  
      {  
         //DwmExtendFrameIntoClientArea Failed  
      }  
   }  
   // If not Vista, paint background white.  
   catch (DllNotFoundException)  
   {  
      Application.Current.MainWindow.Background = Brushes.White;  
   }  
}  
```  
  
## <a name="example"></a><span data-ttu-id="538b2-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="538b2-121">Example</span></span>  
 <span data-ttu-id="538b2-122">O exemplo a seguir mostra uma janela simples em que o quadro é estendido para a área de cliente.</span><span class="sxs-lookup"><span data-stu-id="538b2-122">The following example shows a simple window in which the frame is extended into the client area.</span></span> <span data-ttu-id="538b2-123">O quadro é estendido por trás da borda superior que contém os dois <xref:System.Windows.Controls.TextBox> objetos.</span><span class="sxs-lookup"><span data-stu-id="538b2-123">The frame is extended behind the top border that contains the two <xref:System.Windows.Controls.TextBox> objects.</span></span>  
  
```xaml  
<Window x:Class="SDKSample.Window1"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    Title="Extended Glass in WPF" Height="300" Width="400"   
    Loaded="OnLoaded" Background="Transparent"  
    >  
  <Grid ShowGridLines="True">  
    <DockPanel Name="mainDock">  
      <!-- The border is used to compute the rendered height with margins.  
           topBar contents will be displayed on the extended glass frame.-->  
      <Border Name="topBar" DockPanel.Dock="Top" >  
        <Grid Name="grid">  
          <Grid.ColumnDefinitions>  
            <ColumnDefinition MinWidth="100" Width="*"/>  
            <ColumnDefinition Width="Auto"/>  
          </Grid.ColumnDefinitions>  
          <TextBox Grid.Column="0" MinWidth="100" Margin="0,0,10,5">Path</TextBox>  
          <TextBox Grid.Column="1" MinWidth="75" Margin="0,0,0,5">Search</TextBox>  
        </Grid>  
      </Border>  
      <Grid DockPanel.Dock="Top" >  
        <Grid.ColumnDefinitions>  
          <ColumnDefinition/>  
        </Grid.ColumnDefinitions>  
        <TextBox Grid.Column="0" AcceptsReturn="True"/>  
      </Grid>  
    </DockPanel>  
  </Grid>  
</Window>  
```  
  
 <span data-ttu-id="538b2-124">A imagem a seguir ilustra o quadro com efeito de transparência estendido em um aplicativo [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].</span><span class="sxs-lookup"><span data-stu-id="538b2-124">The following image illustrates the glass frame extended into a [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] application.</span></span>  
  
 <span data-ttu-id="538b2-125">**Quadro com efeito de transparência estendido para um**  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]  **aplicativo.**</span><span class="sxs-lookup"><span data-stu-id="538b2-125">**Glass Frame Extended into a**  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]  **Application.**</span></span>  
  
 <span data-ttu-id="538b2-126">![Quadro com efeito de transparência estendido em um aplicativo WPF.](../../../../docs/framework/wpf/graphics-multimedia/media/wpfextendedglassintoclient.PNG "WPFextendedGlassIntoClient")</span><span class="sxs-lookup"><span data-stu-id="538b2-126">![Glass Frame Extended into a WPF application.](../../../../docs/framework/wpf/graphics-multimedia/media/wpfextendedglassintoclient.PNG "WPFextendedGlassIntoClient")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="538b2-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="538b2-127">See Also</span></span>  
 [<span data-ttu-id="538b2-128">Visão geral do Gerenciador de janelas da área de trabalho</span><span class="sxs-lookup"><span data-stu-id="538b2-128">Desktop Window Manager Overview</span></span>](https://msdn.microsoft.com/library/aa969540.aspx)  
 [<span data-ttu-id="538b2-129">Visão geral do Gerenciador de janelas da área de trabalho Desfoque</span><span class="sxs-lookup"><span data-stu-id="538b2-129">Desktop Window Manager Blur Overview</span></span>](https://msdn.microsoft.com/library/aa969537.aspx)  
 [<span data-ttu-id="538b2-130">DwmExtendFrameIntoClientArea</span><span class="sxs-lookup"><span data-stu-id="538b2-130">DwmExtendFrameIntoClientArea</span></span>](https://msdn.microsoft.com/library/aa969512.aspx)