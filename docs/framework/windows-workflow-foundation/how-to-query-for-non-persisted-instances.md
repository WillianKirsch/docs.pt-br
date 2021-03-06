---
title: 'Como: Consulta para instâncias são persistentes'
ms.date: 03/30/2017
ms.assetid: 294019b1-c1a7-4b81-a14f-b47c106cd723
ms.openlocfilehash: 000342013be4380e1a038fb8233050523f6bc758
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-query-for-non-persisted-instances"></a>Como: Consulta para instâncias são persistentes
Quando uma nova instância de um serviço é criada e o serviço tem o comportamento de Store de instância de fluxo de trabalho do SQL definido, o host serviço cria uma entrada inicial para essa instância do serviço no armazenamento de instância. Posteriormente quando a instância do serviço persiste pela primeira vez, o comportamento de Store de instância de fluxo de trabalho do SQL armazena o estado atual da instância juntamente com os dados adicionais que são necessários para ativação, a recuperação, e o controle.  
  
 Se uma instância não é mantido depois que a entrada inicial para a instância é criada, a instância do serviço no estado não é mantido. Todas as instâncias de serviço persistentes podem ser consultadas e controlado. As instâncias são persistentes de serviço podem acessar não sejam consultadas ou controladas. Se uma instância não é mantida suspendida por causa de uma exceção sem tratamento pode ser consultada mas não controlado.  
  
 As instâncias duráveis de serviço que não são mantidas ainda permanece em um estado não mantido nas seguintes situações:  
  
-   O host serviço falha antes da instância mantidas pela primeira vez. A entrada inicial para a instância permanece no armazenamento de instância. A instância é não recuperável. Se uma mensagem correlacionada chega, a instância ficará ativa novamente.  
  
-   A instância apresentou uma exceção não tratada antes que persistiu pela primeira vez. Os seguintes cenários ocorrem  
  
    -   Se o valor da **UnhandledExceptionAction** está definida como **abandonar**, as informações de implantação do serviço foi criadas para o armazenamento de instância e a instância é descarregada da memória. A instância permanece no estado não persistente na base de dados de persistência.  
  
    -   Se o valor da **UnhandledExceptionAction** está definida como **AbandonAndSuspsend**, as informações de implantação do serviço são gravadas no banco de dados de persistência e o estado da instância é definido como  **Suspenso**. A instância não pode ser continuada, cancelado, ou encerrado. O host serviço não pode carregar a instância porque a instância não persistiu ainda e, portanto a entrada de base de dados para a instância não concluída.  
  
    -   Se o valor da **UnhandledExceptionAction** está definida como **Cancelar** ou **Terminate**, as informações de implantação do serviço são gravadas no armazenamento de instância e o estado da instância é definido como **concluído**.  
  
 As seções a seguir fornecem consultas de exemplo para localizar ocorrências são mantidas na base de dados do SQL e para excluir essas instâncias de base de dados.  
  
## <a name="to-find-all-instances-not-persisted-yet"></a>Para localizar todas as instâncias ainda não persistentes  
 A seguinte consulta SQL retorna a hora de identificação e de criação para todas as instâncias que não são mantidas na base de dados de persistência ainda.  
  
```  
select InstanceId, CreationTime from [System.Activities.DurableInstancing].[Instances] where IsInitialized = 0;  
```  
  
## <a name="to-find-all-instances-not-persisted-yet-and-also-not-loaded"></a>Para localizar todas as instâncias não persistentes ainda e também não carregadas  
 Os seguintes tempo de identificação e de criação de retornos de consulta SQL para todas as instâncias que não são mantidas e também não são carregadas.  
  
```  
select InstanceId, CreationTime from [System.Activities.DurableInstancing].[Instances] where IsInitialized = 0 and CurrentMachine is NULL;  
```  
  
## <a name="to-find-all-suspended-instances-not-persisted-yet"></a>Para localizar todas as instâncias suspensas ainda não persistentes  
 A seguinte consulta SQL retorna a identificação, o tempo de design, a razão de suspensão, e o nome da exceção de suspensão para todas as instâncias que não são mantidas e também em um estado suspenso.  
  
```  
select InstanceId, CreationTime, SuspensionReason, SuspensionExceptionName from [System.Activities.DurableInstancing].[Instances] where IsInitialized = 0 and IsSuspended = 1;  
```  
  
## <a name="to-delete-non-persisted-instances-from-the-persistence-database"></a>Para excluir não persistiu instâncias de base de dados de persistência  
 Você deve periodicamente verificar o armazenamento de instância para instâncias são persistentes e remover as instâncias da instância se você tiver certeza que a instância não receberá uma mensagem correlacionada. Por exemplo, se a instância foi na base de dados por vários meses e você souber que o fluxo de trabalho normalmente tem um tempo de vida de alguns dias, seria seguro suponha que esta é uma instância não inicializado que falhasse.  
  
 Geralmente, é seguro as instâncias não atributos que não são suspensas ou não são carregadas. Você não deve excluir **todas as** as instâncias são persistentes porque esse conjunto de instância inclui instâncias que acabou de criar, mas não são persistidos ainda. Você deve apenas excluir as instâncias são persistentes que são deixadas sobre como o host serviço de fluxo de trabalho que tinha a instância carregada causou uma exceção ou a própria instância causou uma exceção.  
  
> [!WARNING]
>  Excluindo instâncias são persistentes da instância diminui o tamanho de armazenamento e pode melhorar o desempenho de operações de armazenamento.
