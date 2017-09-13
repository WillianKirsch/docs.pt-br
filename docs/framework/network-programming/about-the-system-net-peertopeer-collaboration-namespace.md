---
title: Sobre o namespace System.Net.PeerToPeer.Collaboration
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
ms.assetid: b5d8c1c1-6844-4947-9759-c7f1b564bded
caps.latest.revision: 4
author: mcleblanc
ms.author: markl
manager: markl
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: f446e20f37a83e9effd2a378ce576640bca99763
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="about-the-systemnetpeertopeercollaboration-namespace"></a><span data-ttu-id="25156-102">Sobre o namespace System.Net.PeerToPeer.Collaboration</span><span class="sxs-lookup"><span data-stu-id="25156-102">About the System.Net.PeerToPeer.Collaboration Namespace</span></span>
<span data-ttu-id="25156-103">O namespace <xref:System.Net.PeerToPeer.Collaboration> fornece classes e APIs que são usadas para implementar as atividades de colaboração de pares usando a infraestrutura de Colaboração Ponto a Ponto.</span><span class="sxs-lookup"><span data-stu-id="25156-103">The <xref:System.Net.PeerToPeer.Collaboration> namespace provides classes and APIs that are used to implement peer collaboration activities using the Peer-to-Peer Collaboration Infrastructure.</span></span>  
  
## <a name="classes"></a><span data-ttu-id="25156-104">Classes</span><span class="sxs-lookup"><span data-stu-id="25156-104">Classes</span></span>  
 <span data-ttu-id="25156-105">As principais classes usadas na implementação de uma atividade de Colaboração Ponto a Ponto são:</span><span class="sxs-lookup"><span data-stu-id="25156-105">The main classes used in the implementation of a Peer-to-Peer Collaboration activity are:</span></span>  
  
-   <span data-ttu-id="25156-106">O <xref:System.Net.PeerToPeer.Collaboration.ContactManager>, que pode ser usado para armazenar contatos de pares.</span><span class="sxs-lookup"><span data-stu-id="25156-106">The <xref:System.Net.PeerToPeer.Collaboration.ContactManager>, which can be used to store peer contacts.</span></span>  
  
-   <span data-ttu-id="25156-107">O <xref:System.Net.PeerToPeer.Collaboration.PeerApplication> no qual a colaboração ocorre, como um jogo, cliente de chat ou solução de conferência.</span><span class="sxs-lookup"><span data-stu-id="25156-107">The <xref:System.Net.PeerToPeer.Collaboration.PeerApplication> in which to collaborate, such as a game, chat client, or conferencing solution.</span></span>  
  
-   <span data-ttu-id="25156-108">Os pares que colaborarão em uma atividade.</span><span class="sxs-lookup"><span data-stu-id="25156-108">The peers that will be collaborating in an activity.</span></span>  <span data-ttu-id="25156-109">Esses pares podem ser representados como objetos <xref:System.Net.PeerToPeer.Collaboration.PeerContact>, <xref:System.Net.PeerToPeer.Collaboration.PeerNearMe> ou <xref:System.Net.PeerToPeer.Collaboration.PeerEndPoint>.</span><span class="sxs-lookup"><span data-stu-id="25156-109">These peers can be represented as <xref:System.Net.PeerToPeer.Collaboration.PeerContact>, <xref:System.Net.PeerToPeer.Collaboration.PeerNearMe>, or <xref:System.Net.PeerToPeer.Collaboration.PeerEndPoint> objects.</span></span>  
  
-   <span data-ttu-id="25156-110">A classe <xref:System.Net.PeerToPeer.Collaboration.PeerCollaboration> estática em si, que especifica quais aplicativos estão disponíveis e quais pares participam deles.</span><span class="sxs-lookup"><span data-stu-id="25156-110">The static <xref:System.Net.PeerToPeer.Collaboration.PeerCollaboration> class itself, which specifies which applications are available and which peers are participating in them.</span></span>  
  
 <span data-ttu-id="25156-111">Os métodos <xref:System.Net.PeerToPeer.Collaboration.PeerContact.Invite%2A> são usados para convidar pares para uma sessão de colaboração.</span><span class="sxs-lookup"><span data-stu-id="25156-111">The <xref:System.Net.PeerToPeer.Collaboration.PeerContact.Invite%2A> methods are used to invite peers to a collaboration session.</span></span>  <span data-ttu-id="25156-112">Um par de chamada pode assinar outro par para eventos que sinalizam atualizações para informações de aplicativo, objeto ou presença, afiliadas à sessão de colaboração.</span><span class="sxs-lookup"><span data-stu-id="25156-112">A calling peer can subscribe to another peer for events that signal updates to application, object, or presence information affiliated with the collaboration session.</span></span> <span data-ttu-id="25156-113">Classes de presença especificam se um <xref:System.Net.PeerToPeer.Collaboration.Peer> está disponível para colaboração e a classe <xref:System.Net.PeerToPeer.Collaboration.PeerScope> é usada para especificar a quantidade de participação permitida para um par: <xref:System.Net.PeerToPeer.Collaboration.PeerScope.Internet> (global), <xref:System.Net.PeerToPeer.Collaboration.PeerScope.NearMe>, (sub-rede) ou <xref:System.Net.PeerToPeer.Collaboration.PeerScope.None>.</span><span class="sxs-lookup"><span data-stu-id="25156-113">Presence classes specify whether a <xref:System.Net.PeerToPeer.Collaboration.Peer> is available for collaboration, and the <xref:System.Net.PeerToPeer.Collaboration.PeerScope> class is used to specify how much participation is allowed for a peer:  <xref:System.Net.PeerToPeer.Collaboration.PeerScope.Internet> (global), <xref:System.Net.PeerToPeer.Collaboration.PeerScope.NearMe>, (subnet) or <xref:System.Net.PeerToPeer.Collaboration.PeerScope.None>.</span></span>  
  
 <span data-ttu-id="25156-114">Uma sessão de colaboração é composta por quatro etapas:</span><span class="sxs-lookup"><span data-stu-id="25156-114">A collaboration session is comprised of four steps:</span></span>  
  
-   <span data-ttu-id="25156-115">Descoberta.</span><span class="sxs-lookup"><span data-stu-id="25156-115">Discovery.</span></span> <span data-ttu-id="25156-116">Descubra ou publique aplicativos, pares e informações de presença.</span><span class="sxs-lookup"><span data-stu-id="25156-116">Discover or publish applications, peers, and presence information.</span></span>  <span data-ttu-id="25156-117">Por exemplo, encontre outras pessoas na sub-rede local que têm os mesmos jogos instalados.</span><span class="sxs-lookup"><span data-stu-id="25156-117">For instance, find other people on the local subnet that have the same games installed.</span></span>  
  
-   <span data-ttu-id="25156-118">Convite.</span><span class="sxs-lookup"><span data-stu-id="25156-118">Invitation.</span></span> <span data-ttu-id="25156-119">Envie e aceite convites seguros de pares remotos para iniciar ou participar de sessões de <xref:System.Net.PeerToPeer.Collaboration.PeerCollaboration>.</span><span class="sxs-lookup"><span data-stu-id="25156-119">Send and accept secure invitations for remote peer(s) to start or join <xref:System.Net.PeerToPeer.Collaboration.PeerCollaboration> sessions.</span></span>  
  
-   <span data-ttu-id="25156-120">Gerenciamento de contatos.</span><span class="sxs-lookup"><span data-stu-id="25156-120">Contact Management.</span></span> <span data-ttu-id="25156-121">Adicione pares descobertos como um contato a um <xref:System.Net.PeerToPeer.Collaboration.ContactManager>.</span><span class="sxs-lookup"><span data-stu-id="25156-121">Add discovered peers as a contact to a <xref:System.Net.PeerToPeer.Collaboration.ContactManager>.</span></span>  
  
-   <span data-ttu-id="25156-122">Comunicação.</span><span class="sxs-lookup"><span data-stu-id="25156-122">Communication.</span></span> <span data-ttu-id="25156-123">Quando a comunicação for estabelecida, use as APIs <xref:System.Net>, a API <xref:System.Net.PeerToPeer> ou as classes de Canal Par do Windows Communication Foundation para comunicações com vários participantes.</span><span class="sxs-lookup"><span data-stu-id="25156-123">When communication is established, use the <xref:System.Net> APIs, the <xref:System.Net.PeerToPeer> API, or the Windows Communication Foundation Peer Channel classes for multiparty communications.</span></span>  
  
 <span data-ttu-id="25156-124">Por exemplo, o par de host inicia uma sessão de colaboração e utiliza o método <xref:System.Net.PeerToPeer.Collaboration.ContactManager.CreateContact%2A> para adicionar um par remoto e um de seus pares locais ao Gerenciador de Contatos do par de host.</span><span class="sxs-lookup"><span data-stu-id="25156-124">For example, the host peer starts a collaboration session, and utilizes the <xref:System.Net.PeerToPeer.Collaboration.ContactManager.CreateContact%2A> method to add a remote peer and one of its local peers to the Contact Manager of the host peer.</span></span>  <span data-ttu-id="25156-125">Em seguida, os três usuários participarão em sua própria sessão de colaboração particular.</span><span class="sxs-lookup"><span data-stu-id="25156-125">The three users will then participate in their own private collaboration session.</span></span>  
  
 <span data-ttu-id="25156-126">Os aplicativos P2P típicos são: chamadas em conferência para anotações ou quadro de comunicações de colaboração, aplicativos de chat sem servidor, anúncios interativos e sessões de jogos online.</span><span class="sxs-lookup"><span data-stu-id="25156-126">Typical P2P applications are: conference calls for collaborative note-taking or whiteboarding, serverless chat applications, interactive advertisements, and online gaming sessions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25156-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="25156-127">See Also</span></span>  
 <xref:System.Net.PeerToPeer.Collaboration>
