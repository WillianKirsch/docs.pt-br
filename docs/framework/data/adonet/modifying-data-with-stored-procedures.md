---
title: Modificando dados com procedimentos armazenados
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7d8e9a46-1af6-4a02-bf61-969d77ae07e0
ms.openlocfilehash: d9dcda6b93fbc036818ad2ad43da4bfac95f6833
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="modifying-data-with-stored-procedures"></a>Modificando dados com procedimentos armazenados
Os procedimentos armazenados podem aceitar dados como parâmetros de entrada e podem retornar dados como parâmetros de saída, conjuntos de resultados ou valores de retorno. O exemplo a seguir ilustra como o ADO.NET envia e recebe parâmetros de entrada, parâmetros de saída e valores de retorno. O exemplo insere um novo registro em uma tabela onde a coluna de chave primária é uma coluna de identidade em um banco de dados do SQL Server.  
  
> [!NOTE]
>  Se você estiver usando procedimentos armazenados do SQL Server para editar ou excluir dados usando um <xref:System.Data.SqlClient.SqlDataAdapter>, não use SET NOCOUNT ON na definição do procedimento armazenado. Isso faz com que a contagem retornada de linhas afetadas seja zero, o que o `DataAdapter` interpreta como um conflito de simultaneidade. Nesse caso, será gerada uma <xref:System.Data.DBConcurrencyException>.  
  
## <a name="example"></a>Exemplo  
 O exemplo usa o procedimento armazenado a seguir para inserir uma nova categoria para o **Northwind** **categorias** tabela. O procedimento armazenado assume o valor de **CategoryName** coluna como um parâmetro de entrada e usa o SCOPE_IDENTITY () de função para recuperar o novo valor do campo de identidade, **CategoryID**e retorná-lo um parâmetro de saída. A instrução de retorno usa o @@ROWCOUNT função para retornar o número de linhas inseridas.  
  
```  
CREATE PROCEDURE dbo.InsertCategory  
  @CategoryName nvarchar(15),  
  @Identity int OUT  
AS  
INSERT INTO Categories (CategoryName) VALUES(@CategoryName)  
SET @Identity = SCOPE_IDENTITY()  
RETURN @@ROWCOUNT  
```  
  
 O código de exemplo a seguir usa o procedimento armazenado `InsertCategory` mostrado acima como a origem de <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> de <xref:System.Data.SqlClient.SqlDataAdapter>. O parâmetro de saída `@Identity` será refletido em <xref:System.Data.DataSet> após a inserção do registro no banco de dados quando o método `Update` de <xref:System.Data.SqlClient.SqlDataAdapter> for chamado. O código também recupera o valor de retorno.  
  
> [!NOTE]
>  Ao usar o <xref:System.Data.OleDb.OleDbDataAdapter>, você deve especificar parâmetros com um <xref:System.Data.ParameterDirection> de **ReturnValue** antes dos outros parâmetros.  
  
 [!code-csharp[DataWorks SqlClient.SprocIdentityReturn#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.SprocIdentityReturn/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.SprocIdentityReturn#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.SprocIdentityReturn/VB/source.vb#1)]  
  
## <a name="see-also"></a>Consulte também  
 [Retrieving and Modifying Data in ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md) (Recuperando e modificando dados no ADO.NET)  
 [DataAdapters e DataReaders](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [Executar um comando](../../../../docs/framework/data/adonet/executing-a-command.md)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
