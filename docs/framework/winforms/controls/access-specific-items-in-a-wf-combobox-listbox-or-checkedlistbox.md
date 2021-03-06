---
title: Como acessar itens específicos em um controle ComboBox, ListBox ou CheckedListBox dos Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ComboBox control [Windows Forms], accessing items
- ListBox control [Windows Forms], returning item information
- list boxes [Windows Forms], accessing items
- ListBox control [Windows Forms], accessing items
- combo boxes [Windows Forms], accessing items
- CheckedListBox control [Windows Forms], accessing items
ms.assetid: 1216742f-bcf9-4ff8-8a62-d7c9053c2b96
ms.openlocfilehash: 731527f2d6adb206fa4d8bc4bc2e488c61b86200
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-access-specific-items-in-a-windows-forms-combobox-listbox-or-checkedlistbox-control"></a>Como acessar itens específicos em um controle ComboBox, ListBox ou CheckedListBox dos Windows Forms
Acessar itens específicos em uma caixa de combinação de Windows Forms, caixa de listagem ou caixa de listagem marcada é uma tarefa essencial. Ele permite que você programaticamente determine o que está em uma lista, em qualquer posição determinada.  
  
### <a name="to-access-a-specific-item"></a>Para acessar um item específico  
  
1.  Consulta o `Items` coleção usando o índice do item específico:  
  
    ```vb  
    Private Function GetItemText(i As Integer) As String  
       ' Return the text of the item using the index:  
       Return ComboBox1.Items(i).ToString  
    End Function  
    ```  
  
    ```csharp  
    private string GetItemText(int i)  
    {  
       // Return the text of the item using the index:  
       return (comboBox1.Items[i].ToString());  
    }  
    ```  
  
    ```cpp  
    private:  
       String^ GetItemText(int i)  
       {  
          // Return the text of the item using the index:  
          return (comboBox1->Items->Item[i]->ToString());  
       }  
    ```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.ComboBox>  
 <xref:System.Windows.Forms.ListBox>  
 <xref:System.Windows.Forms.CheckedListBox>  
 [Controles dos Windows Forms usados para listar opções](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)
