---
title: -recurso (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- /resource compiler option [Visual Basic]
- -resource compiler option [Visual Basic]
- /res compiler option [Visual Basic]
- res compiler option [Visual Basic]
- -res compiler option [Visual Basic]
- resource compiler option [Visual Basic]
ms.assetid: eee2f227-91f2-4f2b-a9d6-1c51c5320858
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ab5593455546e65bdd760d9e60532031dc1f12a9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="-resource-visual-basic"></a>-recurso (Visual Basic)
Insere um recurso gerenciado em um assembly.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
-resource:filename[,identifier[,public|private]]  
' -or-  
-res:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termo|Definição|  
|---|---|  
|`filename`|Necessário. O nome do arquivo de recurso para inserir no arquivo de saída. Por padrão, `filename` é público no assembly. Coloque o nome do arquivo entre aspas ("") se ele contiver um espaço.|  
|`identifier`|Opcional. O nome lógico para o recurso. o nome usado para carregá-lo. O padrão é o nome do arquivo. Opcionalmente, você pode especificar se o recurso é pública ou privada no manifesto do assembly, assim como acontece com o seguinte: `-res:filename.res, myname.res, public`|  
  
## <a name="remarks"></a>Comentários  
 Use `-linkresource` para vincular um recurso a um assembly sem colocar o arquivo de recurso no arquivo de saída.  
  
 Se `filename` é um [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] arquivo de recursos criado, por exemplo, pelo [Resgen.exe (gerador de arquivo)](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4) ou no ambiente de desenvolvimento, ele pode ser acessado com membros no <xref:System.Resources> namespace (consulte <xref:System.Resources.ResourceManager> para obter mais informações). Para acessar todos os outros recursos em tempo de execução, use um dos seguintes métodos: <xref:System.Reflection.Assembly.GetManifestResourceInfo%2A>, <xref:System.Reflection.Assembly.GetManifestResourceNames%2A>, ou <xref:System.Reflection.Assembly.GetManifestResourceStream%2A>.  
  
 A forma abreviada de `-resource` é `-res`.  
  
 Para obter informações sobre como definir `-resource` no IDE do Visual Studio, consulte [recursos de gerenciamento de aplicativo (.NET)](/visualstudio/ide/managing-application-resources-dotnet).  
  
## <a name="example"></a>Exemplo  
 O código a seguir compila `In.vb` e anexa arquivos de recurso `Rf.resource`.  
  
```console
vbc -res:rf.resource in.vb  
```  
  
## <a name="see-also"></a>Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md)  
 [-linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md)  
 [-alvo (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)  
 [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
