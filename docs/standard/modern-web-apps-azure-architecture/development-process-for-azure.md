---
title: Processo de desenvolvimento do Azure
description: Projetar aplicativos Web modernos com ASP.NET Core e o Azure | Processo de desenvolvimento do Azure
author: ardalis
ms.author: wiwagn
ms.date: 10/08/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.openlocfilehash: e676c1225f7d11381808040cf101e897e0726ad4
ms.sourcegitcommit: bbde43da655ae7bea1977f7af7345eb87bd7fd5f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/21/2017
---
# <a name="development-process-for-azure"></a><span data-ttu-id="d7cba-103">Processo de desenvolvimento do Azure</span><span class="sxs-lookup"><span data-stu-id="d7cba-103">Development process for Azure</span></span>

> <span data-ttu-id="d7cba-104">_"Com a nuvem, pessoas e pequenas empresas podem ajustar seus dedos e instantaneamente configurar serviços de classe empresarial."_</span><span class="sxs-lookup"><span data-stu-id="d7cba-104">_"With the cloud, individuals and small businesses can snap their fingers and instantly set up enterprise-class services."_</span></span>  
> <span data-ttu-id="d7cba-105">_-Roy Stephan_</span><span class="sxs-lookup"><span data-stu-id="d7cba-105">_- Roy Stephan_</span></span>

 ## <a name="vision"></a><span data-ttu-id="d7cba-106">Visão</span><span class="sxs-lookup"><span data-stu-id="d7cba-106">Vision</span></span>

> <span data-ttu-id="d7cba-107">*Desenvolva aplicativos de ASP .NET Core bem projetados da maneira desejada, usando o Visual Studio ou o CLI dotnet e código do Visual Studio ou o editor escolhido.*</span><span class="sxs-lookup"><span data-stu-id="d7cba-107">*Develop well-designed ASP .NET Core applications the way you like, using Visual Studio or the dotnet CLI and Visual Studio Code or your editor of choice.*</span></span>

## <a name="development-environment-for-aspnet-core-apps"></a><span data-ttu-id="d7cba-108">Ambiente de desenvolvimento para aplicativos do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="d7cba-108">Development environment for ASP.NET Core apps</span></span>

### <a name="development-tools-choices-ide-or-editor"></a><span data-ttu-id="d7cba-109">Opções de ferramentas de desenvolvimento: IDE ou editor</span><span class="sxs-lookup"><span data-stu-id="d7cba-109">Development tools choices: IDE or editor</span></span>

<span data-ttu-id="d7cba-110">Se você preferir um IDE avançado e completo ou um editor leve e ágeis, a Microsoft tem suas necessidades de desenvolvimento de aplicativos do ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="d7cba-110">Whether you prefer a full and powerful IDE or a lightweight and agile editor, Microsoft has you covered when developing ASP.NET Core applications.</span></span>

<span data-ttu-id="d7cba-111">**2017 do Visual Studio.**</span><span class="sxs-lookup"><span data-stu-id="d7cba-111">**Visual Studio 2017.**</span></span> <span data-ttu-id="d7cba-112">Se você estiver usando *2017 do Visual Studio* podem criar ASP.NET Core aplicativos desde que você tenha o *desenvolvimento de plataforma cruzada do .NET Core* instalada da carga de trabalho.</span><span class="sxs-lookup"><span data-stu-id="d7cba-112">If you're using *Visual Studio 2017* you can build ASP.NET Core applications as long as you have the *.NET Core cross-platform development* workload installed.</span></span> <span data-ttu-id="d7cba-113">Figura 10-1 mostra a carga de trabalho necessária na caixa de diálogo de instalação 2017 do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d7cba-113">Figure 10-1 shows the required workload in the Visual Studio 2017 setup dialog.</span></span>

![](./media/image10-1.png)

<span data-ttu-id="d7cba-114">**Figura 10-1.**</span><span class="sxs-lookup"><span data-stu-id="d7cba-114">**Figure 10-1.**</span></span> <span data-ttu-id="d7cba-115">Instalando a carga de trabalho do núcleo do .NET no Visual Studio de 2017.</span><span class="sxs-lookup"><span data-stu-id="d7cba-115">Installing the .NET Core workload in Visual Studio 2017.</span></span>

[<span data-ttu-id="d7cba-116">Baixe o Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="d7cba-116">Download Visual Studio 2017</span></span>](https://www.visualstudio.com/downloads/)

<span data-ttu-id="d7cba-117">**O Visual Studio Code e dotnet CLI** (ferramentas de plataforma cruzada para Mac, Linux e Windows).</span><span class="sxs-lookup"><span data-stu-id="d7cba-117">**Visual Studio Code and dotnet CLI** (Cross-Platform Tools for Mac, Linux and Windows).</span></span> <span data-ttu-id="d7cba-118">Se você preferir um editor leve e várias plataformas com suporte a qualquer linguagem de desenvolvimento, você pode usar o código do Microsoft Visual Studio e o dotnet CLI.</span><span class="sxs-lookup"><span data-stu-id="d7cba-118">If you prefer a lightweight and cross-platform editor supporting any development language, you can use Microsoft Visual Studio Code and the dotnet CLI.</span></span> <span data-ttu-id="d7cba-119">Esses produtos fornecem uma experiência simple, porém robusta que simplifica o fluxo de trabalho do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="d7cba-119">These products provide a simple yet robust experience that streamlines the developer workflow.</span></span> <span data-ttu-id="d7cba-120">Além disso, o código do Visual Studio oferece suporte a extensões para C\# e desenvolvimento da web, fornecendo o intellisense e tarefas de atalho dentro do editor.</span><span class="sxs-lookup"><span data-stu-id="d7cba-120">Additionally, Visual Studio Code supports extensions for C\# and web development, providing intellisense and shortcut-tasks within the editor.</span></span>

[<span data-ttu-id="d7cba-121">Baixe o SDK do .NET Core</span><span class="sxs-lookup"><span data-stu-id="d7cba-121">Download the .NET Core SDK</span></span>](https://www.microsoft.com/net/download/core)

[<span data-ttu-id="d7cba-122">Baixar o código do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d7cba-122">Download Visual Studio Code</span></span>](https://code.visualstudio.com/download)



## <a name="development-workflow-for-azure-hosted-aspnet-core-apps"></a><span data-ttu-id="d7cba-123">Fluxo de trabalho de desenvolvimento para aplicativos hospedados do Azure ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="d7cba-123">Development workflow for Azure-hosted ASP.NET Core apps</span></span>

<span data-ttu-id="d7cba-124">O ciclo de vida de desenvolvimento de aplicativo começa em cada computador de um desenvolvedor, codificar o aplicativo usando o seu idioma preferencial e testá-lo localmente.</span><span class="sxs-lookup"><span data-stu-id="d7cba-124">The application development lifecycle starts from each developer's machine, coding the app using their preferred language and testing it locally.</span></span> <span data-ttu-id="d7cba-125">Os desenvolvedores podem escolher seu sistema de controle de origem preferencial e podem configurar CI (integração contínua) e/ou entrega/implantação contínua (CD) usando um servidor de compilação ou com base em recursos internos do Azure.</span><span class="sxs-lookup"><span data-stu-id="d7cba-125">Developers may choose their preferred source control system and can configure Continuous Integration (CI) and/or Continuous Delivery/Deployment (CD) using a build server or based on built-in Azure features.</span></span>

<span data-ttu-id="d7cba-126">Para começar a desenvolver um aplicativo ASP.NET Core usando CI/CD, você pode usar o Visual Studio Team Services ou sua organização possuir o Team Foundation Server (TFS).</span><span class="sxs-lookup"><span data-stu-id="d7cba-126">To get started with developing an ASP.NET Core application using CI/CD, you can use Visual Studio Team Services or your organization's own Team Foundation Server (TFS).</span></span>

### <a name="initial-setup"></a><span data-ttu-id="d7cba-127">Configuração inicial</span><span class="sxs-lookup"><span data-stu-id="d7cba-127">Initial Setup</span></span>

<span data-ttu-id="d7cba-128">Para criar um pipeline de versão para o seu aplicativo, você precisa ter o código do aplicativo no controle de origem.</span><span class="sxs-lookup"><span data-stu-id="d7cba-128">To create a release pipeline for your app, you need to have your application code in source control.</span></span> <span data-ttu-id="d7cba-129">Configurar um repositório local e conectá-lo em um repositório remoto em um projeto de equipe.</span><span class="sxs-lookup"><span data-stu-id="d7cba-129">Set up a local repository and connect it to a remote repository in a team project.</span></span> <span data-ttu-id="d7cba-130">Siga estas instruções:</span><span class="sxs-lookup"><span data-stu-id="d7cba-130">Follow these instructions:</span></span>

-   <span data-ttu-id="d7cba-131">[Compartilhar seu código com o Visual Studio e o Git](https://www.visualstudio.com/docs/git/share-your-code-in-git-vs) ou</span><span class="sxs-lookup"><span data-stu-id="d7cba-131">[Share your code with Git and Visual Studio](https://www.visualstudio.com/docs/git/share-your-code-in-git-vs) or</span></span>

-   [<span data-ttu-id="d7cba-132">Compartilhe seu código com TFVC e o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d7cba-132">Share your code with TFVC and Visual Studio</span></span>](https://www.visualstudio.com/docs/tfvc/share-your-code-in-tfvc-vs)

<span data-ttu-id="d7cba-133">Crie um serviço de aplicativo do Azure onde você implantará o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d7cba-133">Create an Azure App Service where you'll deploy your application.</span></span> <span data-ttu-id="d7cba-134">Crie um aplicativo Web, vá para a folha de serviços de aplicativos no portal do Azure.</span><span class="sxs-lookup"><span data-stu-id="d7cba-134">Create a Web App by going to the App Services blade on the Azure portal.</span></span> <span data-ttu-id="d7cba-135">Clique em + Adicionar, selecione o modelo de aplicativo Web, clique em criar e fornecer um nome e outros detalhes.</span><span class="sxs-lookup"><span data-stu-id="d7cba-135">Click +Add, select the Web App template, click Create, and provide a name and other details.</span></span> <span data-ttu-id="d7cba-136">O aplicativo web poderá ser acessado de {name}. azurewebsites.net.</span><span class="sxs-lookup"><span data-stu-id="d7cba-136">The web app will be accessible from {name}.azurewebsites.net.</span></span>

![AzureWebApp](./media/image10-2.png)

<span data-ttu-id="d7cba-138">**Figura 10-2.**</span><span class="sxs-lookup"><span data-stu-id="d7cba-138">**Figure 10-2.**</span></span> <span data-ttu-id="d7cba-139">Criando um novo aplicativo de Web de serviço de aplicativo do Azure no Portal do Azure.</span><span class="sxs-lookup"><span data-stu-id="d7cba-139">Creating a new Azure App Service Web App in the Azure Portal.</span></span>

<span data-ttu-id="d7cba-140">O processo de compilação de CI realizará uma compilação automatizada sempre que o novo código é confirmado para o repositório de controle de origem do projeto.</span><span class="sxs-lookup"><span data-stu-id="d7cba-140">Your CI build process will perform an automated build whenever new code is committed to the project's source control repository.</span></span> <span data-ttu-id="d7cba-141">Isso fornece um feedback imediato que cria o código (e, idealmente, passa testes automatizados) e potencialmente pode ser implantado.</span><span class="sxs-lookup"><span data-stu-id="d7cba-141">This gives you immediate feedback that the code builds (and, ideally, passes automated tests) and can potentially be deployed.</span></span> <span data-ttu-id="d7cba-142">Esta compilação de CI produzirá uma web implantar artefato de pacote e publicá-lo para consumo pelo seu processo de CD.</span><span class="sxs-lookup"><span data-stu-id="d7cba-142">This CI build will produce a web deploy package artifact and publish it for consumption by your CD process.</span></span>

[<span data-ttu-id="d7cba-143">Definir o processo de compilação de CI</span><span class="sxs-lookup"><span data-stu-id="d7cba-143">Define your CI build process</span></span>](https://www.visualstudio.com/docs/build/apps/aspnet/aspnetcore-to-azure#ci)

<span data-ttu-id="d7cba-144">Certifique-se de habilitar a integração contínua para que o sistema irá enfileirar uma compilação sempre que alguém de sua equipe confirma o novo código.</span><span class="sxs-lookup"><span data-stu-id="d7cba-144">Be sure to enable continuous integration so the system will queue a build whenever someone on your team commits new code.</span></span> <span data-ttu-id="d7cba-145">Testar a compilação e verificar se ele está produzindo um web implantar o pacote como um de seus artefatos.</span><span class="sxs-lookup"><span data-stu-id="d7cba-145">Test the build and verify that it is producing a web deploy package as one of its artifacts.</span></span>

<span data-ttu-id="d7cba-146">Quando uma compilação for bem-sucedida, o processo de CD implantará os resultados de sua compilação de CI ao seu aplicativo web do Azure.</span><span class="sxs-lookup"><span data-stu-id="d7cba-146">When a build succeeds, your CD process will deploy the results of your CI build to your Azure web app.</span></span> <span data-ttu-id="d7cba-147">Para configurar isso, você pode criar e configurar um *versão*, que será implantado para o serviço de aplicativo do Azure.</span><span class="sxs-lookup"><span data-stu-id="d7cba-147">To configure this, you create and configure a *Release*, which will deploy to your Azure App Service.</span></span>

[<span data-ttu-id="d7cba-148">Definir o processo de lançamento do CD</span><span class="sxs-lookup"><span data-stu-id="d7cba-148">Define your CD release process</span></span>](https://www.visualstudio.com/docs/build/apps/aspnet/aspnetcore-to-azure#cd)

<span data-ttu-id="d7cba-149">Depois que o pipeline de CI/CD estiver configurado, você pode simplesmente fazer atualizações em seu aplicativo web e confirmá-las ao controle de origem tê-los implantado.</span><span class="sxs-lookup"><span data-stu-id="d7cba-149">Once your CI/CD pipeline is configured, you can simply make updates to your web app and commit them to source control to have them deployed.</span></span>

### <a name="workflow-for-developing-azure-hosted-aspnet-core-applications"></a><span data-ttu-id="d7cba-150">Fluxo de trabalho para o desenvolvimento de aplicativos hospedados do Azure ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="d7cba-150">Workflow for developing Azure-hosted ASP.NET Core applications</span></span>

<span data-ttu-id="d7cba-151">Depois que você configurou sua conta do Azure e o processo de CI/CD, desenvolvimento de aplicativos hospedados do Azure ASP.NET Core é simple.</span><span class="sxs-lookup"><span data-stu-id="d7cba-151">Once you have configured your Azure account and your CI/CD process, developing Azure-hosted ASP.NET Core applications is simple.</span></span> <span data-ttu-id="d7cba-152">A seguir estão as etapas básicas normalmente ao criar um aplicativo do ASP.NET Core, hospedado no serviço de aplicativo do Azure como um aplicativo Web, conforme ilustrado na Figura 10-3.</span><span class="sxs-lookup"><span data-stu-id="d7cba-152">The following are the basic steps you usually take when building an ASP.NET Core app, hosted in Azure App Service as a Web App, as illustrated in Figure 10-3.</span></span>

![EndToEndDevDeployWorkflow](./media/image10-3.png)

<span data-ttu-id="d7cba-154">**Figura 10-3.**</span><span class="sxs-lookup"><span data-stu-id="d7cba-154">**Figure 10-3.**</span></span> <span data-ttu-id="d7cba-155">Fluxo de trabalho passo a passo para criar aplicativos de ASP.NET Core e hospedá-los no Azure</span><span class="sxs-lookup"><span data-stu-id="d7cba-155">Step-by-step workflow for building ASP.NET Core apps and hosting them in Azure</span></span>

#### <a name="step-1-local-dev-environment-inner-loop"></a><span data-ttu-id="d7cba-156">Etapa 1.</span><span class="sxs-lookup"><span data-stu-id="d7cba-156">Step 1.</span></span> <span data-ttu-id="d7cba-157">Loop interno do ambiente de desenvolvimento local</span><span class="sxs-lookup"><span data-stu-id="d7cba-157">Local Dev Environment Inner Loop</span></span>

<span data-ttu-id="d7cba-158">Desenvolvendo seu aplicativo ASP.NET Core para implantação no Azure não é diferente de desenvolvimento de seu aplicativo caso contrário.</span><span class="sxs-lookup"><span data-stu-id="d7cba-158">Developing your ASP.NET Core application for deployment to Azure is no different from developing your application otherwise.</span></span> <span data-ttu-id="d7cba-159">Use o ambiente de desenvolvimento local que você estiver familiarizado com, seja 2017 do Visual Studio ou o CLI dotnet e código do Visual Studio ou seu editor preferido.</span><span class="sxs-lookup"><span data-stu-id="d7cba-159">Use the local development environment you're comfortable with, whether that's Visual Studio 2017 or the dotnet CLI and Visual Studio Code or your preferred editor.</span></span> <span data-ttu-id="d7cba-160">Você pode escrever código, executar e depurar suas alterações, executar testes automatizados e fazer confirmações locais ao controle de origem até que você está pronto para enviar por push as alterações ao seu repositório de controle de origem compartilhada.</span><span class="sxs-lookup"><span data-stu-id="d7cba-160">You can write code, run and debug your changes, run automated tests, and make local commits to source control until you're ready to push your changes to your shared source control repository.</span></span>

#### <a name="step-2-application-code-repository"></a><span data-ttu-id="d7cba-161">Etapa 2.</span><span class="sxs-lookup"><span data-stu-id="d7cba-161">Step 2.</span></span> <span data-ttu-id="d7cba-162">Repositório de código do aplicativo</span><span class="sxs-lookup"><span data-stu-id="d7cba-162">Application Code Repository</span></span>

<span data-ttu-id="d7cba-163">Sempre que você está pronto para compartilhar seu código com sua equipe, você deve enviar por push as alterações do seu repositório local de origem para o repositório de origem compartilhada da sua equipe.</span><span class="sxs-lookup"><span data-stu-id="d7cba-163">Whenever you're ready to share your code with your team, you should push your changes from your local source repository to your team's shared source repository.</span></span> <span data-ttu-id="d7cba-164">Se você já trabalhou em uma ramificação personalizada, essa etapa geralmente envolve mesclar seu código em uma ramificação compartilhada (talvez por meio de um [solicitação pull](https://www.visualstudio.com/docs/git/pull-requests)).</span><span class="sxs-lookup"><span data-stu-id="d7cba-164">If you've been working in a custom branch, this step usually involves merging your code into a shared branch (perhaps by means of a [pull request](https://www.visualstudio.com/docs/git/pull-requests)).</span></span>

#### <a name="step-3-build-server-continuous-integration-build-test-package"></a><span data-ttu-id="d7cba-165">Etapa 3.</span><span class="sxs-lookup"><span data-stu-id="d7cba-165">Step 3.</span></span> <span data-ttu-id="d7cba-166">Servidor de compilação: A integração contínua.</span><span class="sxs-lookup"><span data-stu-id="d7cba-166">Build Server: Continuous Integration.</span></span> <span data-ttu-id="d7cba-167">Pacote de compilação, teste,</span><span class="sxs-lookup"><span data-stu-id="d7cba-167">Build, Test, Package</span></span>

<span data-ttu-id="d7cba-168">Uma nova compilação é acionada no servidor de compilação sempre que uma nova confirmação é feita para o repositório de código de aplicativo compartilhado.</span><span class="sxs-lookup"><span data-stu-id="d7cba-168">A new build is triggered on the build server whenever a new commit is made to the shared application code repository.</span></span> <span data-ttu-id="d7cba-169">Como parte do processo de CI, esta compilação totalmente deve compilar o aplicativo e executar testes automatizados para confirmar se que tudo está funcionando conforme o esperado.</span><span class="sxs-lookup"><span data-stu-id="d7cba-169">As part of the CI process, this build should fully compile the application and run automated tests to confirm everything is working as expected.</span></span> <span data-ttu-id="d7cba-170">O resultado final do processo de CI deve ser uma versão de pacote do aplicativo web, pronto para a implantação.</span><span class="sxs-lookup"><span data-stu-id="d7cba-170">The end result of the CI process should be a packaged version of the web app, ready for deployment.</span></span>

#### <a name="step-4-build-server-continuous-delivery"></a><span data-ttu-id="d7cba-171">Etapa 4.</span><span class="sxs-lookup"><span data-stu-id="d7cba-171">Step 4.</span></span> <span data-ttu-id="d7cba-172">Servidor de compilação: Fornecimento contínuo</span><span class="sxs-lookup"><span data-stu-id="d7cba-172">Build Server: Continuous Delivery</span></span>

<span data-ttu-id="d7cba-173">Uma vez uma compilação como bem-sucedida, o processo de CD selecionará os artefatos de compilação produzidos.</span><span class="sxs-lookup"><span data-stu-id="d7cba-173">Once a build as succeeded, the CD process will pick up the build artifacts produced.</span></span> <span data-ttu-id="d7cba-174">Isso incluirá uma web implantar o pacote.</span><span class="sxs-lookup"><span data-stu-id="d7cba-174">This will include a web deploy package.</span></span> <span data-ttu-id="d7cba-175">O servidor de compilação implantará esse pacote para o serviço de aplicativo do Azure, substituindo qualquer serviço existente com o recém-criado.</span><span class="sxs-lookup"><span data-stu-id="d7cba-175">The build server will deploy this package to Azure App Service, replacing any existing service with the newly created one.</span></span> <span data-ttu-id="d7cba-176">Normalmente esta etapa tem como alvo um ambiente de preparo, mas alguns aplicativos implantar diretamente para a produção por meio de um processo do CD.</span><span class="sxs-lookup"><span data-stu-id="d7cba-176">Typically this step targets a staging environment, but some applications deploy directly to production through a CD process.</span></span>

#### <a name="step-5-azure-app-service-web-app"></a><span data-ttu-id="d7cba-177">Etapa 5.</span><span class="sxs-lookup"><span data-stu-id="d7cba-177">Step 5.</span></span> <span data-ttu-id="d7cba-178">Serviço de aplicativo do Azure.</span><span class="sxs-lookup"><span data-stu-id="d7cba-178">Azure App Service.</span></span> <span data-ttu-id="d7cba-179">Aplicativo Web.</span><span class="sxs-lookup"><span data-stu-id="d7cba-179">Web App.</span></span>

<span data-ttu-id="d7cba-180">Uma vez implantado, o aplicativo do ASP.NET Core é executado dentro do contexto de um aplicativo de Web do serviço de aplicativo do Azure.</span><span class="sxs-lookup"><span data-stu-id="d7cba-180">Once deployed, the ASP.NET Core application runs within the context of an Azure App Service Web App.</span></span> <span data-ttu-id="d7cba-181">Este aplicativo Web pode ser monitorado e configurado usando o Portal do Azure.</span><span class="sxs-lookup"><span data-stu-id="d7cba-181">This Web App can be monitored and further configured using the Azure Portal.</span></span>

#### <a name="step-6-production-monitoring-and-diagnostics"></a><span data-ttu-id="d7cba-182">Etapa 6.</span><span class="sxs-lookup"><span data-stu-id="d7cba-182">Step 6.</span></span> <span data-ttu-id="d7cba-183">Produção de monitoramento e diagnóstico</span><span class="sxs-lookup"><span data-stu-id="d7cba-183">Production Monitoring and Diagnostics</span></span>

<span data-ttu-id="d7cba-184">Durante a execução do aplicativo Web, você pode monitorar a integridade do aplicativo e coletar dados de comportamento do usuário e de diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="d7cba-184">While the Web App is running, you can monitor the health of the application and collect diagnostics and user behavior data.</span></span> <span data-ttu-id="d7cba-185">Application Insights está incluído no Visual Studio e oferece a instrumentação automática para aplicativos ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="d7cba-185">Application Insights is included in Visual Studio, and offers automatic instrumentation for ASP.NET apps.</span></span> <span data-ttu-id="d7cba-186">Ele pode fornecer informações sobre uso, exceções, solicitações, desempenho e logs.</span><span class="sxs-lookup"><span data-stu-id="d7cba-186">It can provide you with information on usage, exceptions, requests, performance, and logs.</span></span>

## <a name="references"></a><span data-ttu-id="d7cba-187">Referências</span><span class="sxs-lookup"><span data-stu-id="d7cba-187">References</span></span>

<span data-ttu-id="d7cba-188">**Criar e implantar seu aplicativo ASP.NET Core para o Azure**</span><span class="sxs-lookup"><span data-stu-id="d7cba-188">**Build and Deploy Your ASP.NET Core App to Azure**</span></span>  
<span data-ttu-id="d7cba-189"><https://www.VisualStudio.com/docs/Build/Apps/ASPNET/aspnetcore-to-Azure></span><span class="sxs-lookup"><span data-stu-id="d7cba-189"><https://www.visualstudio.com/docs/build/apps/aspnet/aspnetcore-to-azure></span></span>


>[!div class="step-by-step"]
<span data-ttu-id="d7cba-190">[Anterior] (test-asp-net-core-mvc-apps.md) [Avançar] (azure-hosting-recommendations-for-asp-net-web-apps.md)</span><span class="sxs-lookup"><span data-stu-id="d7cba-190">[Previous] (test-asp-net-core-mvc-apps.md) [Next] (azure-hosting-recommendations-for-asp-net-web-apps.md)</span></span>