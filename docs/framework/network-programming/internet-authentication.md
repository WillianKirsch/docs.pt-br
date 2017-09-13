---
title: "Autenticação da Internet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- authentication [.NET Framework], classes
- IAuthenticationModule interface
- ICredentialLookup interface
- CredentialCache class, about CredentialCache class
- receiving data, authentication
- AuthenticationManager class, about AuthenticationManager class
- Internet, authentication
- sending data, authentication
- network resources, authentication
- user authentication, classes for authentication
- NetworkCredential class, about NetworkCredential class
- client authentication, classes for authentication
ms.assetid: d342e87c-f672-4660-a513-41a2f2b80c4a
caps.latest.revision: 11
author: mcleblanc
ms.author: markl
manager: markl
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: a26811b5dd62e30b371af88bc79d06843ef58d05
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="internet-authentication"></a><span data-ttu-id="1f899-102">Autenticação da Internet</span><span class="sxs-lookup"><span data-stu-id="1f899-102">Internet Authentication</span></span>
<span data-ttu-id="1f899-103">As classes <xref:System.Net> dão suporte a uma variedade de mecanismos de autenticação de cliente, incluindo os métodos de autenticação padrão de Internet básico, digest, negotiate, NTLM e a autenticação Kerberos, bem como métodos personalizados criados por você.</span><span class="sxs-lookup"><span data-stu-id="1f899-103">The <xref:System.Net> classes support a variety of client authentication mechanisms, including the standard Internet authentication methods basic, digest, negotiate, NTLM, and Kerberos authentication, as well as custom methods that you can create.</span></span>  
  
 <span data-ttu-id="1f899-104">As credenciais de autenticação são armazenadas nas classes <xref:System.Net.NetworkCredential> e <xref:System.Net.CredentialCache> que implementam a interface <xref:System.Net.ICredentials>.</span><span class="sxs-lookup"><span data-stu-id="1f899-104">Authentication credentials are stored in the <xref:System.Net.NetworkCredential> and <xref:System.Net.CredentialCache> classes, which implement the <xref:System.Net.ICredentials> interface.</span></span> <span data-ttu-id="1f899-105">Quando uma dessas classes é consultada para credenciais, ela retorna uma instância da classe **NetworkCredential**.</span><span class="sxs-lookup"><span data-stu-id="1f899-105">When one of these classes is queried for credentials, it returns an instance of the **NetworkCredential** class.</span></span> <span data-ttu-id="1f899-106">O processo de autenticação é gerenciado pela classe <xref:System.Net.AuthenticationManager> e o processo de autenticação real é executado por uma classe de módulo de autenticação que implementa a interface <xref:System.Net.IAuthenticationModule>.</span><span class="sxs-lookup"><span data-stu-id="1f899-106">The authentication process is managed by the <xref:System.Net.AuthenticationManager> class, and the actual authentication process is performed by an authentication module class that implements the <xref:System.Net.IAuthenticationModule> interface.</span></span> <span data-ttu-id="1f899-107">Você deve registrar um módulo de autenticação personalizado com o **AuthenticationManager** antes que ele possa ser usado; módulos para métodos de autenticação básica, digest, negotiate, NTLM e Kerberos são registrados por padrão.</span><span class="sxs-lookup"><span data-stu-id="1f899-107">You must register a custom authentication module with the **AuthenticationManager** before it can be used; modules for the basic, digest, negotiate, NTLM, and Kerberos authentication methods are registered by default.</span></span>  
  
 <span data-ttu-id="1f899-108">**NetworkCredential** armazena um conjunto de credenciais associadas a um único recurso de Internet identificado por um URI e os retorna em resposta a qualquer chamada para o método <xref:System.Net.NetworkCredential.GetCredential%2A>.</span><span class="sxs-lookup"><span data-stu-id="1f899-108">**NetworkCredential** stores a set of credentials associated with a single Internet resource identified by a URI and returns them in response to any call to the <xref:System.Net.NetworkCredential.GetCredential%2A> method.</span></span> <span data-ttu-id="1f899-109">A classe **NetworkCredential** normalmente é usada por aplicativos que acessam um número limitado de recursos da Internet ou por aplicativos que usam o mesmo conjunto de credenciais em todos os casos.</span><span class="sxs-lookup"><span data-stu-id="1f899-109">The **NetworkCredential** class is typically used by applications that access a limited number of Internet resources or by applications that use the same set of credentials in all cases.</span></span>  
  
 <span data-ttu-id="1f899-110">A classe **CredentialCache** armazena uma coleção de credenciais para vários recursos da Web.</span><span class="sxs-lookup"><span data-stu-id="1f899-110">The **CredentialCache** class stores a collection of credentials for various Web resources.</span></span> <span data-ttu-id="1f899-111">Quando o método <xref:System.Net.CredentialCache.GetCredential%2A> é chamado, **CredentialCache** retorna o conjunto apropriado de credenciais, conforme determinado pelo URI do recurso da Web e o esquema de autenticação solicitado.</span><span class="sxs-lookup"><span data-stu-id="1f899-111">When the <xref:System.Net.CredentialCache.GetCredential%2A> method is called, **CredentialCache** returns the proper set of credentials, as determined by the URI of the Web resource and the requested authentication scheme.</span></span> <span data-ttu-id="1f899-112">Aplicativos que usam uma variedade de recursos de Internet com diferentes esquemas de autenticação se beneficiam do uso da classe **CredentialCache**, visto que ele armazena todas as credenciais e as fornece conforme solicitado.</span><span class="sxs-lookup"><span data-stu-id="1f899-112">Applications that use a variety of Internet resources with different authentication schemes benefit from using the **CredentialCache** class, since it stores all the credentials and provides them as requested.</span></span>  
  
 <span data-ttu-id="1f899-113">Quando um recurso de Internet solicita autenticação, o método <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=fullName> envia o <xref:System.Net.WebRequest> para o **AuthenticationManager** junto com a solicitação de credenciais.</span><span class="sxs-lookup"><span data-stu-id="1f899-113">When an Internet resource requests authentication, the <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=fullName> method sends the <xref:System.Net.WebRequest> to the **AuthenticationManager** along with the request for credentials.</span></span> <span data-ttu-id="1f899-114">A solicitação é então autenticada acordo com o processo a seguir:</span><span class="sxs-lookup"><span data-stu-id="1f899-114">The request is then authenticated according to the following process:</span></span>  
  
1.  <span data-ttu-id="1f899-115">O **AuthenticationManager** chama o método <xref:System.Net.IAuthenticationModule.Authenticate%2A> em cada um dos módulos de autenticação registrados na ordem em que eles foram registrados.</span><span class="sxs-lookup"><span data-stu-id="1f899-115">The **AuthenticationManager** calls the <xref:System.Net.IAuthenticationModule.Authenticate%2A> method on each of the registered authentication modules in the order they were registered.</span></span> <span data-ttu-id="1f899-116">O **AuthenticationManager** usa o primeiro módulo que não retorna **nulo** para executar o processo de autenticação.</span><span class="sxs-lookup"><span data-stu-id="1f899-116">The **AuthenticationManager** uses the first module that does not return **null** to carry out the authentication process.</span></span> <span data-ttu-id="1f899-117">Os detalhes do processo variam dependendo do tipo de módulo de autenticação envolvido.</span><span class="sxs-lookup"><span data-stu-id="1f899-117">The details of the process vary depending on the type of authentication module involved.</span></span>  
  
2.  <span data-ttu-id="1f899-118">Quando o processo de autenticação é concluído, o módulo de autenticação retorna um <xref:System.Net.Authorization> para o **WebRequest** que contém as informações necessárias para acessar o recurso de Internet.</span><span class="sxs-lookup"><span data-stu-id="1f899-118">When the authentication process is complete, the authentication module returns an <xref:System.Net.Authorization> to the **WebRequest** that contains the information needed to access the Internet resource.</span></span>  
  
 <span data-ttu-id="1f899-119">Alguns esquemas de autenticação podem autenticar um usuário sem primeiro fazer uma solicitação para um recurso.</span><span class="sxs-lookup"><span data-stu-id="1f899-119">Some authentication schemes can authenticate a user without first making a request for a resource.</span></span> <span data-ttu-id="1f899-120">Um aplicativo pode economizar tempo pré-autenticando o usuário com o recurso, eliminando assim pelo menos uma viagem de ida e volta ao servidor.</span><span class="sxs-lookup"><span data-stu-id="1f899-120">An application can save time by preauthenticating the user with the resource, thus eliminating at least one round trip to the server.</span></span> <span data-ttu-id="1f899-121">Ou então, pode executar a autenticação durante a inicialização de programa a fim de ser mais responsivo para o usuário mais tarde.</span><span class="sxs-lookup"><span data-stu-id="1f899-121">Or, it can perform authentication during program startup in order to be more responsive to the user later.</span></span> <span data-ttu-id="1f899-122">Esquemas de autenticação que podem usar pré-autenticação definem a propriedade <xref:System.Net.IAuthenticationModule.PreAuthenticate%2A> como **true**.</span><span class="sxs-lookup"><span data-stu-id="1f899-122">Authentication schemes that can use preauthentication set the <xref:System.Net.IAuthenticationModule.PreAuthenticate%2A> property to **true**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f899-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1f899-123">See Also</span></span>  
 <span data-ttu-id="1f899-124">[Autenticação Básica e Digest](../../../docs/framework/network-programming/basic-and-digest-authentication.md) </span><span class="sxs-lookup"><span data-stu-id="1f899-124">[Basic and Digest Authentication](../../../docs/framework/network-programming/basic-and-digest-authentication.md) </span></span>  
 <span data-ttu-id="1f899-125">[Autenticação NTLM e Kerberos](../../../docs/framework/network-programming/ntlm-and-kerberos-authentication.md) </span><span class="sxs-lookup"><span data-stu-id="1f899-125">[NTLM and Kerberos Authentication](../../../docs/framework/network-programming/ntlm-and-kerberos-authentication.md) </span></span>  
 [<span data-ttu-id="1f899-126">Segurança na programação de rede</span><span class="sxs-lookup"><span data-stu-id="1f899-126">Security in Network Programming</span></span>](../../../docs/framework/network-programming/security-in-network-programming.md)
