---
title: Como desenvolver um controle simples dos Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms]
- custom controls [Windows Forms], creating simple controls using code
- Control class [Windows Forms], Windows Forms
ms.assetid: 86cbe435-45b7-4cb4-9b5a-47418369758d
ms.openlocfilehash: 04cedc0df60ef95acb79b651ddcbcbb34ae5e920
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-develop-a-simple-windows-forms-control"></a>Como desenvolver um controle simples dos Windows Forms
Esta seção explica as etapas principais para a criação de um controle personalizado dos Windows Forms. O controle simple desenvolvido neste passo a passo permite que o alinhamento do seu <xref:System.Windows.Forms.Control.Text%2A> propriedade a ser alterada. Ele não gera ou manipula eventos.  
  
### <a name="to-create-a-simple-custom-control"></a>Para criar um controle personalizado simples  
  
1.  Defina uma classe derivada de <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.  
  
    ```vb  
    Public Class FirstControl  
       Inherits Control  
  
    End Class  
    ```  
  
    ```csharp  
    public class FirstControl:Control{}  
    ```  
  
2.  Defina as propriedades. (Não é necessário para definir propriedades, como muitas propriedades de um controle é herdada do <xref:System.Windows.Forms.Control> classe, mas a maioria dos controles personalizados geralmente definem propriedades adicionais.) O fragmento de código a seguir define uma propriedade chamada `TextAlignment` que `FirstControl` usa para formatar a exibição do <xref:System.Windows.Forms.Control.Text%2A> propriedade herdada de <xref:System.Windows.Forms.Control>. Para obter mais informações sobre como definir as propriedades, consulte [Properties Overview](http://msdn.microsoft.com/library/8f1a1ff1-0f05-40e0-bfdf-80de8fff7d52) (Visão geral das propriedades).  
  
     [!code-csharp[System.Windows.Forms.FirstControl#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#3)]
     [!code-vb[System.Windows.Forms.FirstControl#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#3)]  
  
     Quando você define uma propriedade que altera a exibição visual do controle, você deve chamar o <xref:System.Windows.Forms.Control.Invalidate%2A> método redesenhar o controle. <xref:System.Windows.Forms.Control.Invalidate%2A> é definido na classe base <xref:System.Windows.Forms.Control>.  
  
3.  Substituir protegido <xref:System.Windows.Forms.Control.OnPaint%2A> método herdado do <xref:System.Windows.Forms.Control> para fornecer lógica de processamento para o controle. Se você não substituir <xref:System.Windows.Forms.Control.OnPaint%2A>, o controle não será possível desenhar a próprio. No fragmento de código a seguir, o <xref:System.Windows.Forms.Control.OnPaint%2A> método exibe o <xref:System.Windows.Forms.Control.Text%2A> propriedade herdada de <xref:System.Windows.Forms.Control> com o alinhamento especificado pelo `alignmentValue` campo.  
  
     [!code-csharp[System.Windows.Forms.FirstControl#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#4)]
     [!code-vb[System.Windows.Forms.FirstControl#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#4)]  
  
4.  Forneça atributos para o seu controle. Os atributos permitem que um designer visual exiba adequadamente seu controle, suas propriedades e eventos no tempo de design. O fragmento de código a seguir se aplica aos atributos para a propriedade `TextAlignment`. Em um designer como o Visual Studio, o <xref:System.ComponentModel.CategoryAttribute.Category%2A> atributo (mostrado no fragmento de código) faz com que a propriedade a ser exibida em uma categoria lógica. O <xref:System.ComponentModel.DescriptionAttribute.Description%2A> atributo faz com que uma cadeia de caracteres descritiva a ser exibida na parte inferior da **propriedades** janela quando o `TextAlignment` propriedade está selecionada. Para obter mais informações sobre atributos, consulte [Design-Time Attributes for Components](http://msdn.microsoft.com/library/12050fe3-9327-4509-9e21-4ee2494b95c3) (Atributos de tempo de design para componentes).  
  
     [!code-csharp[System.Windows.Forms.FirstControl#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#5)]
     [!code-vb[System.Windows.Forms.FirstControl#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#5)]  
  
5.  (opcional) Forneça recursos para o seu controle. Você pode fornecer um recurso, como um bitmap, para seu controle usando uma opção do compilador (`/res` para C#) para recursos de pacote com seu controle. Em tempo de execução, o recurso pode ser recuperado usando os métodos do <xref:System.Resources.ResourceManager> classe. Para obter mais informações sobre a criação e o uso de recursos, consulte [Resources in Desktop Apps](../../../../docs/framework/resources/index.md) (Recursos em aplicativos da Área de Trabalho).  
  
6.  Compile e implante seu controle. Para compilar e implantar `FirstControl,`, execute as seguintes etapas:  
  
    1.  Salve o código no exemplo a seguir em um arquivo de origem (como FirstControl.cs ou FirstControl.vb).  
  
    2.  Compile o código-fonte em um assembly e salve-o no diretório do aplicativo. Para fazer isso, execute o seguinte comando do diretório que contém o arquivo de origem.  
  
        ```console  
        vbc -t:library -out:[path to your application's directory]/CustomWinControls.dll -r:System.dll -r:System.Windows.Forms.dll -r:System.Drawing.dll FirstControl.vb  
        ```  
  
        ```console 
        csc -t:library -out:[path to your application's directory]/CustomWinControls.dll -r:System.dll -r:System.Windows.Forms.dll -r:System.Drawing.dll FirstControl.cs  
        ```  
  
         A opção do compilador `/t:library` informa o compilador que o assembly que você está criando é uma biblioteca (e não um executável). A opção `/out` especifica o caminho e o nome do assembly. A opção `/r` fornece o nome dos assemblies referenciados pelo seu código. Neste exemplo, você cria um assembly particular que somente os seus aplicativos podem usar. Portanto, você precisa salvá-lo no diretório do aplicativo. Para obter mais informações sobre o empacotamento e a implantação de um controle para distribuição, consulte [Implantação](../../../../docs/framework/deployment/index.md).  
  
 O exemplo a seguir mostra o código para `FirstControl`. O controle é colocado no namespace `CustomWinControls`. Um namespace fornece um agrupamento lógico de tipos relacionados. Você pode criar seu controle em um namespace novo ou existente. Em C#, a declaração `using` (no Visual Basic, `Imports`) permite que os tipos sejam acessados de um namespace sem usar o nome totalmente qualificado do tipo. No exemplo a seguir, o `using` declaração permite que o código acessar a classe <xref:System.Windows.Forms.Control> de <xref:System.Windows.Forms?displayProperty=nameWithType> simplesmente <xref:System.Windows.Forms.Control> em vez de usar o nome totalmente qualificado <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.  
  
 [!code-csharp[System.Windows.Forms.FirstControl#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#1)]
 [!code-vb[System.Windows.Forms.FirstControl#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#1)]  
  
## <a name="using-the-custom-control-on-a-form"></a>Usando o controle personalizado em um formulário  
 O exemplo a seguir mostra um formulário simples que usa `FirstControl`. Ele cria três instâncias de `FirstControl`, cada uma com um valor diferente para a propriedade `TextAlignment`.  
  
#### <a name="to-compile-and-run-this-sample"></a>Para compilar e executar esse exemplo  
  
1.  Salve o código no exemplo a seguir em um arquivo de origem (SimpleForm.cs ou SimpleForms.vb).  
  
2.  Compile o código-fonte em um assembly executável, executando o seguinte comando do diretório que contém o arquivo de origem.  
  
    ```console  
    vbc -r:CustomWinControls.dll -r:System.dll -r:System.Windows.Forms.dll -r:System.Drawing.dll SimpleForm.vb  
    ```  
  
    ```console 
    csc -r:CustomWinControls.dll -r:System.dll -r:System.Windows.Forms.dll -r:System.Drawing.dll SimpleForm.cs  
    ```  
  
     CustomWinControls.dll é o assembly que contém a classe `FirstControl`. Esse assembly deve estar no mesmo diretório que o arquivo de origem para o formulário que o acessa (SimpleForm.cs ou SimpleForms.vb).  
  
3.  Execute SimpleForm.exe usando o seguinte comando.  
  
    ```console
    SimpleForm  
    ```  
  
 [!code-csharp[System.Windows.Forms.FirstControl#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/SimpleForm.cs#10)]
 [!code-vb[System.Windows.Forms.FirstControl#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/SimpleForm.vb#10)]  
  
## <a name="see-also"></a>Consulte também  
 [Propriedades em controles do Windows Forms](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)  
 [Eventos em controles do Windows Forms](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md)
