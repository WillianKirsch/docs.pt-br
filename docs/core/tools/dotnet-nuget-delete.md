---
title: Comando dotnet nuget delete – CLI do .NET Core
description: O comando dotnet-nuget-delete exclui ou retira da lista um pacote do servidor.
author: karann-msft
ms.author: mairaw
ms.date: 08/14/2017
ms.openlocfilehash: 639ade54bfed5eb2de89bdb3b7f451393b4be187
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="dotnet-nuget-delete"></a>dotnet nuget delete

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nome

`dotnet nuget delete` – Exclui ou retira da lista um pacote do servidor.

## <a name="synopsis"></a>Sinopse

`dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [-s|--source] [--non-interactive] [-k|--api-key] [--force-english-output] [-h|--help]`

## <a name="description"></a>Descrição

O comando `dotnet nuget delete` exclui ou retira da lista um pacote do servidor. Para [nuget.org](https://www.nuget.org/), a ação é remover o pacote da lista.

## <a name="arguments"></a>Arguments

`PACKAGE_NAME`

Pacote a ser excluído.

`PACKAGE_VERSION`

Versão do pacote a ser excluído.

## <a name="options"></a>Opções

`-h|--help`

Imprime uma ajuda breve para o comando.

`-s|--source <SOURCE>`

Especifica a URL do servidor. URLs com suporte para nuget.org incluem `http://www.nuget.org`, `http://www.nuget.org/api/v3` e `http://www.nuget.org/api/v2/package`. Para feeds privados, substitua o nome do host (por exemplo, `%hostname%/api/v3`).

`--non-interactive`

Não solicita entrada do usuário ou confirmações.

`-k|--api-key <API_KEY>`

A chave da API para o servidor.

`--force-english-output`

Força a saída da linha de comando em inglês.

## <a name="examples"></a>Exemplos

Exclui a versão 1.0 do pacote `Microsoft.AspNetCore.Mvc`:

`dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0` 

Exclui a versão 1.0 do pacote `Microsoft.AspNetCore.Mvc`, não solicita ao usuário credenciais ou outra entrada:

`dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0 --non-interactive`