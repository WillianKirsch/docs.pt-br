---
title: Testar a saída publicada com dotnet vstest
description: Saiba como executar testes na saída publicada com o comando dotnet vstest.
author: kendrahavens
ms.author: kehavens
ms.date: 10/18/2017
ms.openlocfilehash: dbce1b6e616916e60e56318b773e8fcecbc55580
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="test-published-output-with-dotnet-vstest"></a>Testar a saída publicada com dotnet vstest

Você pode executar testes na saída já publicada usando o comando `dotnet vstest`. Isso funcionará em testes xUnit, MSTest e NUnit. Basta localizar o arquivo DLL que fazia parte de sua saída publicada e execute:

```
dotnet vstest <MyPublishedTests>.dll
```

em que `<MyPublishedTests>` é o nome de seu projeto de teste publicado.

## <a name="example-of-running-tests-on-a-published-dll"></a>Exemplo de execução de testes em uma DLL publicada

```
dotnet new mstest -o MyProject.Tests
cd MyProject.Tests
dotnet publish -o out
dotnet vstest out/MyProject.Tests.dll
```

> [!NOTE]
> Observação: se o seu aplicativo for direcionado a uma estrutura diferente de `netcoreapp`, ainda será possível executar o comando `dotnet vstest`, passando a estrutura de destino com um sinalizador de estrutura. Por exemplo, `dotnet vstest <MyPublishedTests>.dll  --Framework:".NETFramework,Version=v4.6"`. No Visual Studio 2017 Atualização 5, a estrutura desejada é detectada automaticamente.

## <a name="see-also"></a>Consulte também
 [Teste de unidade com dotnet test e xUnit](unit-testing-with-dotnet-test.md)  
 [Teste de unidade com dotnet test e MSTest](unit-testing-with-mstest.md)  
