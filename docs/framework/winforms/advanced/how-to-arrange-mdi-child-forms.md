---
title: Como organizar formulários filho MDI
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- child forms [Windows Forms], arranging
- MDI [Windows Forms], arranging child forms
ms.assetid: a0786378-3206-4ccc-898e-7d3b38cc5089
ms.openlocfilehash: d5c0d24ff8a7188a669c218ce8b0dc66ffa56c47
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-arrange-mdi-child-forms"></a>Como organizar formulários filho MDI
Muitas vezes, os aplicativos terão comandos de menu para ações como Lado a lado, Em cascata e Organizar, que controlam o layout dos formulários MDI filhos abertos. Você pode usar o método <xref:System.Windows.Forms.Form.LayoutMdi%2A> com um dos valores de enumeração <xref:System.Windows.Forms.MdiLayout> para reorganizar os formulários MDI filhos em um formulário MDI pai.  
  
 Os valores de enumeração <xref:System.Windows.Forms.MdiLayout> exibem formulários filhos em cascata, lado a lado horizontal ou verticalmente, ou como ícones de formulários filhos organizados na parte inferior do formulário MDI. Esses valores possuem o mesmo efeito que os comandos do Windows **Janelas em cascata**, **Mostrar janelas lado a lado**, **Mostrar janelas empilhadas** e **Mostrar a área de trabalho**, respectivamente.  
  
 Geralmente, esses métodos são usados como manipuladores de evento chamados por um evento <xref:System.Windows.Forms.Control.Click> do item do menu. Dessa forma, um item de menu com o texto "Em cascata" pode ter o efeito desejado em janelas MDI filhas.  
  
### <a name="to-arrange-child-forms"></a>Para organizar formulários filhos  
  
1.  Em um método, use o método <xref:System.Windows.Forms.Form.LayoutMdi%2A> para definir a enumeração <xref:System.Windows.Forms.MdiLayout> para o formulário MDI pai. O exemplo a seguir usa o valor de enumeração <xref:System.Windows.Forms.MdiLayout.Cascade?displayProperty=nameWithType> para as janelas filhas do formulário MDI pai (`Form1`). A enumeração é usada no código durante o manipulador de eventos para o <xref:System.Windows.Forms.Control.Click> evento o **janelas em cascata** item de menu.  
  
    ```vb  
    Protected Sub CascadeWindows_Click(ByVal sender As System.Object, ByVal e As System.EventArgs)  
       Me.LayoutMdi(System.Windows.Forms.MdiLayout.Cascade)  
    End Sub  
    ```  
  
    ```csharp  
    protected void CascadeWindows_Click(object sender, System.EventArgs e){  
       this.LayoutMdi(System.Windows.Forms.MdiLayout.Cascade);  
    }  
    ```  
  
    > [!NOTE]
    >  Você também pode colocar as janelas lado a lado e organizá-las como ícones alterando o valor de enumeração <xref:System.Windows.Forms.MdiLayout> usado.  
  
2.  Se você estiver usando o Visual C#, coloque o seguinte código no construtor do formulário para registrar o manipulador de eventos.  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
## <a name="see-also"></a>Consulte também  
 [Aplicativos da interface MDI (Interface de Vários Documentos)](../../../../docs/framework/winforms/advanced/multiple-document-interface-mdi-applications.md)  
 [Como criar formulários pai MDI](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)  
 [Como criar formulários filho MDI](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)  
 [Como determinar o filho MDI ativo](../../../../docs/framework/winforms/advanced/how-to-determine-the-active-mdi-child.md)  
 [Como Enviar Dados para o Filho MDI Ativo](../../../../docs/framework/winforms/advanced/how-to-send-data-to-the-active-mdi-child.md)
