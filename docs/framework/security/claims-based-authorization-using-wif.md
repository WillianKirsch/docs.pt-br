---
title: "Autorização baseada em declarações usando o WIF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e24000a3-8fd8-4c0e-bdf0-39882cc0f6d8
caps.latest.revision: 6
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: f1086958a56aadbddf54f20295b91e885adf71c4
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="claims-based-authorization-using-wif"></a><span data-ttu-id="42a04-102">Autorização baseada em declarações usando o WIF</span><span class="sxs-lookup"><span data-stu-id="42a04-102">Claims Based Authorization Using WIF</span></span>
<span data-ttu-id="42a04-103">Em um aplicativo de terceira parte confiável, a autorização determina quais recursos uma identidade autenticada pode acessar e quais operações ela pode executar nesses recursos.</span><span class="sxs-lookup"><span data-stu-id="42a04-103">In a relying party application, authorization determines what resources an authenticated identity is allowed to access and what operations it is allowed to perform on those resources.</span></span> <span data-ttu-id="42a04-104">A autorização inadequada ou fraca leva à divulgação de informações e à violação de dados.</span><span class="sxs-lookup"><span data-stu-id="42a04-104">Improper or weak authorization leads to information disclosure and data tampering.</span></span> <span data-ttu-id="42a04-105">Este tópico descreve as abordagens disponíveis para implementar a autorização para aplicativos e serviços Web ASP.NET com reconhecimento de declarações usando o Windows Identity Foundation (WIF) e um Serviço de Token de Segurança (STS), por exemplo, o Serviço de Controle de Acesso (ACS) do Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="42a04-105">This topic outlines the available approaches to implementing authorization for claims-aware ASP.NET web applications and services using Windows Identity Foundation (WIF) and a Security Token Service (STS), for example, the Windows Azure Access Control Service (ACS).</span></span>  
  
## <a name="overview"></a><span data-ttu-id="42a04-106">Visão Geral</span><span class="sxs-lookup"><span data-stu-id="42a04-106">Overview</span></span>  
 <span data-ttu-id="42a04-107">Desde sua primeira versão, o .NET Framework oferece um mecanismo flexível para implementar a autorização.</span><span class="sxs-lookup"><span data-stu-id="42a04-107">Since its first version, the .NET Framework has offered a flexible mechanism for implementing authorization.</span></span> <span data-ttu-id="42a04-108">Esse mecanismo se baseia em duas interfaces simples – **IPrincipal** e **IIdentity**.</span><span class="sxs-lookup"><span data-stu-id="42a04-108">This mechanism is based on two simple interfaces—**IPrincipal** and **IIdentity**.</span></span> <span data-ttu-id="42a04-109">As implementações concretas de **IIdentity** representam um usuário autenticado.</span><span class="sxs-lookup"><span data-stu-id="42a04-109">Concrete implementations of **IIdentity** represent an authenticated user.</span></span> <span data-ttu-id="42a04-110">Por exemplo, a implementação de **WindowsIdentity** representa um usuário que é autenticado pelo Active Directory e **GenericIdentity** representa um usuário cuja identidade é verificada por meio de um processo de autenticação personalizada.</span><span class="sxs-lookup"><span data-stu-id="42a04-110">For example, the **WindowsIdentity** implementation represents a user who is authenticated by Active Directory, and **GenericIdentity** represents a user whose identity is verified via a custom authentication process.</span></span> <span data-ttu-id="42a04-111">As implementações concretas de **IPrincipal** ajudam a verificar as permissões usando funções, dependendo do repositório de funções.</span><span class="sxs-lookup"><span data-stu-id="42a04-111">Concrete implementations of **IPrincipal** help to check permissions using roles depending on the role store.</span></span> <span data-ttu-id="42a04-112">Por exemplo, **WindowsPrincipal** verifica **WindowsIdentity** para obter a associação em grupos do Active Directory.</span><span class="sxs-lookup"><span data-stu-id="42a04-112">For example, **WindowsPrincipal** checks **WindowsIdentity** for membership in Active Directory groups.</span></span> <span data-ttu-id="42a04-113">Essa verificação é executada com uma chamada ao método **IsInRole** na interface **IPrincipal**.</span><span class="sxs-lookup"><span data-stu-id="42a04-113">This check is performed by calling the **IsInRole** method on the **IPrincipal** interface.</span></span> <span data-ttu-id="42a04-114">A verificação do acesso com base em funções é chamada de RBAC (Controle de Acesso Baseado em Função).</span><span class="sxs-lookup"><span data-stu-id="42a04-114">Checking access based on roles is called Role-Based Access Control (RBAC).</span></span> <span data-ttu-id="42a04-115">Para obter mais informações, consulte [Controle de acesso baseado em função](../../../docs/framework/security/claims-based-authorization-using-wif.md#BKMK_1).</span><span class="sxs-lookup"><span data-stu-id="42a04-115">For more information, see [Role-Based Access Control](../../../docs/framework/security/claims-based-authorization-using-wif.md#BKMK_1).</span></span>  <span data-ttu-id="42a04-116">As declarações podem ser usadas para transportar informações sobre funções para oferecer suporte a mecanismos de autorização com base em função.</span><span class="sxs-lookup"><span data-stu-id="42a04-116">Claims can be used to carry information about roles to support familiar, role-based authorization mechanisms.</span></span>  
  
 <span data-ttu-id="42a04-117">As reivindicações também podem ser usadas para habilitar decisões de autorização mais complicadas, além de funções.</span><span class="sxs-lookup"><span data-stu-id="42a04-117">Claims can also be used to enable more complicated authorization decisions beyond roles.</span></span> <span data-ttu-id="42a04-118">As declarações podem ser baseada em praticamente todas as informações sobre o usuário – idade, CEP, tamanho de sapato, etc. Um mecanismo de controle de acesso baseado em declarações arbitrárias é chamado de autorização baseada em declarações.</span><span class="sxs-lookup"><span data-stu-id="42a04-118">Claims can be based on virtually any information about the user - age, zip code, shoe size, etc. An access control mechanism that is based on arbitrary claims is called claims-based authorization.</span></span> <span data-ttu-id="42a04-119">Para obter mais informações, consulte [Autorização baseada em declarações](../../../docs/framework/security/claims-based-authorization-using-wif.md#BKMK_2).</span><span class="sxs-lookup"><span data-stu-id="42a04-119">For more information, see [Claims-based Authorization](../../../docs/framework/security/claims-based-authorization-using-wif.md#BKMK_2).</span></span>  
  
<a name="BKMK_1"></a>   
## <a name="role-based-access-control"></a><span data-ttu-id="42a04-120">Controle de acesso baseado em funções</span><span class="sxs-lookup"><span data-stu-id="42a04-120">Role-Based Access Control</span></span>  
 <span data-ttu-id="42a04-121">O RBAC é uma abordagem de autorização em que as permissões de usuário são gerenciadas e impostas por um aplicativo baseado em funções de usuário.</span><span class="sxs-lookup"><span data-stu-id="42a04-121">RBAC is an authorization approach in which user permissions are managed and enforced by an application based on user roles.</span></span> <span data-ttu-id="42a04-122">Se um usuário tem a função necessária para executar uma ação, o acesso é concedido; caso contrário, o acesso é negado.</span><span class="sxs-lookup"><span data-stu-id="42a04-122">If a user has a role that is required to perform an action, the access is granted; otherwise, access is denied.</span></span>  
  
### <a name="iprincipalisinrole-method"></a><span data-ttu-id="42a04-123">Método IPrincipal.IsInRole</span><span class="sxs-lookup"><span data-stu-id="42a04-123">IPrincipal.IsInRole Method</span></span>  
 <span data-ttu-id="42a04-124">Para implementar a abordagem RBAC em aplicativos baseados em declarações, use o método **IsInRole()** na interface **IPrinicpal**, assim como você faria em aplicativos não baseados em declarações.</span><span class="sxs-lookup"><span data-stu-id="42a04-124">To implement the RBAC approach in claims-aware applications, use the **IsInRole()** method in the **IPrinicpal** interface, just as you would in non-claims-aware applications.</span></span> <span data-ttu-id="42a04-125">Há várias maneiras de usar o método **IsInRole()**:</span><span class="sxs-lookup"><span data-stu-id="42a04-125">There are several ways of using the **IsInRole()** method:</span></span>  
  
-   <span data-ttu-id="42a04-126">Chamando **IPrincipal.IsInRole("Administrator")** explicitamente.</span><span class="sxs-lookup"><span data-stu-id="42a04-126">Explicitly calling on **IPrincipal.IsInRole("Administrator")**.</span></span> <span data-ttu-id="42a04-127">Nessa abordagem, o resultado é um booleano.</span><span class="sxs-lookup"><span data-stu-id="42a04-127">In this approach, the outcome is a Boolean.</span></span> <span data-ttu-id="42a04-128">Use-a em suas instruções condicionais.</span><span class="sxs-lookup"><span data-stu-id="42a04-128">Use it in your conditional statements.</span></span> <span data-ttu-id="42a04-129">Ela pode ser usada arbitrariamente em qualquer local de seu código.</span><span class="sxs-lookup"><span data-stu-id="42a04-129">It can be used arbitrarily any place in your code.</span></span>  
  
-   <span data-ttu-id="42a04-130">Usando a demanda de segurança **PrincipalPermission.Demand()**.</span><span class="sxs-lookup"><span data-stu-id="42a04-130">Using the security demand **PrincipalPermission.Demand()**.</span></span> <span data-ttu-id="42a04-131">Nessa abordagem, o resultado é uma exceção caso a demanda não seja atendida.</span><span class="sxs-lookup"><span data-stu-id="42a04-131">In this approach, the outcome is an exception in case the demand is not satisfied.</span></span> <span data-ttu-id="42a04-132">Isso deve se ajustar à sua estratégia de tratamento de exceções.</span><span class="sxs-lookup"><span data-stu-id="42a04-132">This should fit your exception handling strategy.</span></span> <span data-ttu-id="42a04-133">A geração de exceções é muito mais cara, de uma perspectiva de desempenho, comparada ao retorno do booliano.</span><span class="sxs-lookup"><span data-stu-id="42a04-133">Throwing exceptions is much more expensive from a performance perspective compared to returning Boolean.</span></span> <span data-ttu-id="42a04-134">Isso pode ser usado em qualquer local de seu código.</span><span class="sxs-lookup"><span data-stu-id="42a04-134">This can be used any place in your code.</span></span>  
  
-   <span data-ttu-id="42a04-135">Usando os atributos declarativos **[PrincipalPermission(SecurityAction.Demand, Role = "Administrator")]**.</span><span class="sxs-lookup"><span data-stu-id="42a04-135">Using the declarative attributes **[PrincipalPermission(SecurityAction.Demand, Role = "Administrator")]**.</span></span> <span data-ttu-id="42a04-136">Essa abordagem é chamada declarativa porque é usada para decorar métodos.</span><span class="sxs-lookup"><span data-stu-id="42a04-136">This approach is called declarative, because it is used to decorate methods.</span></span> <span data-ttu-id="42a04-137">Ela não pode ser usada em blocos de códigos dentro das implementações do método.</span><span class="sxs-lookup"><span data-stu-id="42a04-137">It cannot be used in code blocks inside the method’s implementations.</span></span> <span data-ttu-id="42a04-138">O resultado é uma exceção caso a demanda não seja atendida.</span><span class="sxs-lookup"><span data-stu-id="42a04-138">The outcome is an exception in case the demand is not satisfied.</span></span> <span data-ttu-id="42a04-139">Você deve se certificar de que ela se ajuste à sua estratégia de tratamento de exceções.</span><span class="sxs-lookup"><span data-stu-id="42a04-139">You should make sure that it fits your exception-handling strategy.</span></span>  
  
-   <span data-ttu-id="42a04-140">Usando a autorização de URL, usando a seção **\<authorization>** em **web.config**. Essa abordagem é apropriada quando você está gerenciando a autorização no nível de URL.</span><span class="sxs-lookup"><span data-stu-id="42a04-140">Using URL authorization, using the **\<authorization>** section in **web.config**. This approach is suitable when you are managing authorization on a URL level.</span></span> <span data-ttu-id="42a04-141">Esse é o nível mais grosseiro entre os mencionados anteriormente.</span><span class="sxs-lookup"><span data-stu-id="42a04-141">This is the most coarse level among those previously mentioned.</span></span> <span data-ttu-id="42a04-142">A vantagem dessa abordagem é que as alterações são feitas no arquivo de configuração, o que significa que o código não deve ser compilado para se beneficiar da alteração.</span><span class="sxs-lookup"><span data-stu-id="42a04-142">The advantage of this approach is that changes are made in the configuration file, which means that the code should not be compiled to take advantage of the change.</span></span>  
  
### <a name="expressing-roles-as-claims"></a><span data-ttu-id="42a04-143">Expressando funções como declarações</span><span class="sxs-lookup"><span data-stu-id="42a04-143">Expressing Roles as Claims</span></span>  
 <span data-ttu-id="42a04-144">Quando o método **IsInRole()** é chamado, há uma verificação feita para ver se o usuário atual tem essa função.</span><span class="sxs-lookup"><span data-stu-id="42a04-144">When the **IsInRole()** method is called, there is a check made to see if the current user has that role.</span></span> <span data-ttu-id="42a04-145">Em aplicativos com reconhecimento de declarações, a função é expressa por um tipo de declaração de função que deve estar disponível no token.</span><span class="sxs-lookup"><span data-stu-id="42a04-145">In claims-aware applications, the role is expressed by a role claim type that should be available in the token.</span></span> <span data-ttu-id="42a04-146">O tipo de declaração de função é expresso usando o seguinte URI:</span><span class="sxs-lookup"><span data-stu-id="42a04-146">The role claim type is expressed using the following URI:</span></span>  
  
 <span data-ttu-id="42a04-147">http://schemas.microsoft.com/ws/2008/06/identity/claims/role</span><span class="sxs-lookup"><span data-stu-id="42a04-147">http://schemas.microsoft.com/ws/2008/06/identity/claims/role</span></span>  
  
 <span data-ttu-id="42a04-148">Há várias maneiras de enriquecer um token com um tipo de declaração de função:</span><span class="sxs-lookup"><span data-stu-id="42a04-148">There are several ways to enrich a token with a role claim type:</span></span>  
  
-   <span data-ttu-id="42a04-149">**Durante a emissão de token**.</span><span class="sxs-lookup"><span data-stu-id="42a04-149">**During token issuance**.</span></span> <span data-ttu-id="42a04-150">Quando um usuário é autenticado, a declaração de função pode ser emitida pelo STS do provedor de identidade ou por um provedor de federação, como o ACS (Serviço de Controle de Acesso) do Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="42a04-150">When a user is authenticated the role claim can be issued by the identity provider STS or by a federation provider such as the Windows Azure Access Control Service (ACS).</span></span>  
  
-   <span data-ttu-id="42a04-151">**Transformando declarações arbitrárias em um tipo de declaração de função usando ClaimsAuthenticationManager**.</span><span class="sxs-lookup"><span data-stu-id="42a04-151">**Transforming arbitrary claims into of claims role type using ClaimsAuthenticationManager**.</span></span> <span data-ttu-id="42a04-152">O ClaimsAuthenticationManager é um componente fornecido como parte do WIF.</span><span class="sxs-lookup"><span data-stu-id="42a04-152">The ClaimsAuthenticationManager is a component that ships as part of WIF.</span></span> <span data-ttu-id="42a04-153">Ele permite que as solicitações sejam interceptadas quando iniciam um aplicativo, inspecionando os tokens e transformando-os adicionando, alterando ou removendo declarações.</span><span class="sxs-lookup"><span data-stu-id="42a04-153">It allows requests to be intercepted when they launch an application, inspecting tokens and transforming them by adding, changing, or removing claims.</span></span> <span data-ttu-id="42a04-154">Para obter mais informações sobre como usar o ClaimsAuthenticationManager para transformar declarações, consulte [Como implementar o RBAC (Controle de Acesso Baseado em Função) em um aplicativo ASP.NET baseado em declarações usando o WIF e o ACS](http://go.microsoft.com/fwlink/?LinkID=247445) (http://go.microsoft.com/fwlink/?LinkID=247444).</span><span class="sxs-lookup"><span data-stu-id="42a04-154">For more information about how to use ClaimsAuthenticationManager for transforming claims, see [How To: Implement Role Based Access Control (RBAC) in a Claims Aware ASP.NET Application Using WIF and ACS](http://go.microsoft.com/fwlink/?LinkID=247445) (http://go.microsoft.com/fwlink/?LinkID=247444).</span></span>  
  
-   <span data-ttu-id="42a04-155">**Mapeando declarações arbitrárias para um tipo de função usando a seção de configuração samlSecurityTokenRequirement** – uma abordagem declarativa em que a transformação de declarações é feita usando apenas a configuração, sem a necessidade de codificação.</span><span class="sxs-lookup"><span data-stu-id="42a04-155">**Mapping arbitrary claims to a role type using the samlSecurityTokenRequirement configuration section**—A declarative approach where the claims transformation is done using only the configuration and no coding is required.</span></span>  
  
<a name="BKMK_2"></a>   
## <a name="claims-based-authorization"></a><span data-ttu-id="42a04-156">Autorização baseada em declarações</span><span class="sxs-lookup"><span data-stu-id="42a04-156">Claims-based Authorization</span></span>  
 <span data-ttu-id="42a04-157">A autorização baseada em declarações é uma abordagem em que a decisão de autorização para conceder ou negar acesso é baseada na lógica arbitrária que usa os dados disponíveis nas declarações para tomar a decisão.</span><span class="sxs-lookup"><span data-stu-id="42a04-157">Claims-based authorization is an approach where the authorization decision to grant or deny access is based on arbitrary logic that uses data available in claims to make the decision.</span></span> <span data-ttu-id="42a04-158">Lembre-se de que, no caso do RBAC, a única declaração usada foi a do tipo de função.</span><span class="sxs-lookup"><span data-stu-id="42a04-158">Recall that in the case of RBAC, the only claim used was role type claim.</span></span> <span data-ttu-id="42a04-159">Uma declaração de tipo de função foi usada para verificar se o usuário pertence à função específica ou não.</span><span class="sxs-lookup"><span data-stu-id="42a04-159">A role type claim was used to check if the user belongs to specific role or not.</span></span> <span data-ttu-id="42a04-160">Para ilustrar o processo de tomada de decisões de autorização usando a abordagem de autorização baseada em declarações, considere as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="42a04-160">To illustrate the process of making the authorization decisions using claims-based authorization approach, consider the following steps:</span></span>  
  
1.  <span data-ttu-id="42a04-161">O aplicativo recebe uma solicitação que exige que o usuário seja autenticado.</span><span class="sxs-lookup"><span data-stu-id="42a04-161">The application receives a request that requires the user is authenticated.</span></span>  
  
2.  <span data-ttu-id="42a04-162">O WIF redireciona o usuário ao seu provedor de identidade. Depois de autenticado, a solicitação do aplicativo é feita com um token de segurança associado representando o usuário que contém declarações sobre ele.</span><span class="sxs-lookup"><span data-stu-id="42a04-162">WIF redirects the user to their identity provider, after they are authenticated the application request is made with an associated security token representing the user containing claims about them.</span></span> <span data-ttu-id="42a04-163">O WIF associa essas declarações à entidade de segurança que representa o usuário.</span><span class="sxs-lookup"><span data-stu-id="42a04-163">WIF associates those claims with the principal that represents the user.</span></span>  
  
3.  <span data-ttu-id="42a04-164">O aplicativo passa as declarações para o mecanismo de lógica de decisão.</span><span class="sxs-lookup"><span data-stu-id="42a04-164">The application passes the claims to the decision logic mechanism.</span></span> <span data-ttu-id="42a04-165">Ele pode ser um código na memória, uma chamada para um serviço Web, uma consulta em um banco de dados, um mecanismo sofisticado de regras, ou usando o ClaimsAuthorizationManager.</span><span class="sxs-lookup"><span data-stu-id="42a04-165">It can be in-memory code, a call to a web service, a query to a database, a sophisticated rules engine, or using the ClaimsAuthorizationManager.</span></span>  
  
4.  <span data-ttu-id="42a04-166">O mecanismo de decisão calcula o resultado com base nas declarações.</span><span class="sxs-lookup"><span data-stu-id="42a04-166">The decision mechanism calculates the outcome based on the claims.</span></span>  
  
5.  <span data-ttu-id="42a04-167">O acesso será concedido se o resultado for true, e negado se for false.</span><span class="sxs-lookup"><span data-stu-id="42a04-167">Access is granted if the outcome is true and denied if it is false.</span></span> <span data-ttu-id="42a04-168">Por exemplo, a regra pode ser que o usuário tenha 21 anos ou mais e more no estado de Washington.</span><span class="sxs-lookup"><span data-stu-id="42a04-168">For example, the rule might be that the user is of age 21 or above and lives in Washington State.</span></span>  
  
 <span data-ttu-id="42a04-169">O <xref:System.Security.Claims.ClaimsAuthorizationManager> é útil para exteriorizar a lógica de decisão para autorização baseada em declarações em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="42a04-169"><xref:System.Security.Claims.ClaimsAuthorizationManager> is useful for externalizing the decision logic for  claims-based authorization in your applications.</span></span> <span data-ttu-id="42a04-170">O ClaimsAuthenticationManager é um componente do WIF que envia como parte do .NET 4.5.</span><span class="sxs-lookup"><span data-stu-id="42a04-170">ClaimsAuthorizationManager is a WIF component that ships as part of .NET 4.5.</span></span> <span data-ttu-id="42a04-171">O ClaimsAuthorizationManager permite interceptar as solicitações recebidas e implementa as lógicas de sua escolha para tomar decisões de autorização com base nas declarações recebidas.</span><span class="sxs-lookup"><span data-stu-id="42a04-171">ClaimsAuthorizationManager allows you to intercept incoming requests and implement any logic of your choice to make authorization decisions based on the incoming claims.</span></span> <span data-ttu-id="42a04-172">Isso é importante quando a lógica de autorização precisa ser modificada.</span><span class="sxs-lookup"><span data-stu-id="42a04-172">This becomes important when authorization logic needs to be changed.</span></span> <span data-ttu-id="42a04-173">Nesse caso, usar o ClaimsAuthorizationManager não afetará a integridade do aplicativo, reduzindo a probabilidade de um erro do aplicativo em resultado da alteração.</span><span class="sxs-lookup"><span data-stu-id="42a04-173">In that case, using ClaimsAuthorizationManager will not affect the application’s integrity, thereby reducing the likelihood of an application error as a result of the change.</span></span> <span data-ttu-id="42a04-174">Para saber mais sobre como usar ClaimsAuthorizationManager para implementar o controle de acesso baseado em declarações, consulte [Como implementar a autorização de declarações em um aplicativo ASP.NET baseado em declarações usando o WIF e o ACS](http://go.microsoft.com/fwlink/?LinkID=247446).</span><span class="sxs-lookup"><span data-stu-id="42a04-174">To learn more about how to use ClaimsAuthorizationManager to implement claims-based access control, see [How To: Implement Claims Authorization in a Claims Aware ASP.NET Application Using WIF and ACS](http://go.microsoft.com/fwlink/?LinkID=247446).</span></span>
