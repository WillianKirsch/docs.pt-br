---
title: Seleção e validação de certificado
ms.date: 03/30/2017
ms.assetid: c933aca2-4cd0-4ff1-9df9-267143f25a6f
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: f163de89a3edbf3a4ca8509fdecd10f1aa1adf1b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="certificate-selection-and-validation"></a>Seleção e validação de certificado
As classes <xref:System.Net> dão suporte a várias maneiras de selecionar e validar <xref:System.Security.Cryptography.X509Certificates> para conexões SSL. Um cliente pode selecionar um ou mais certificados para se autenticar em um servidor. Um servidor pode exigir que um certificado do cliente tenha um ou mais atributos específicos para autenticação.  
  
## <a name="definition"></a>Definição  
 Um certificado é um fluxo de bytes ASCII que contém uma chave pública, atributos (como o número de versão, número de série e data de expiração) e uma assinatura digital de uma Autoridade de Certificação. Os certificados são usados para estabelecer uma conexão criptografada ou para autenticar um cliente em um servidor.  
  
## <a name="client-certificate-selection-and-validation"></a>Seleção e validação de certificado do cliente  
 Um cliente pode selecionar um ou mais certificados para uma conexão SSL específica. Os certificados do cliente podem ser associados à conexão SSL para um servidor Web ou um servidor de email SMTP. Um cliente adiciona certificados a uma coleção de objetos da classe <xref:System.Security.Cryptography.X509Certificates.X509Certificate> ou <xref:System.Security.Cryptography.X509Certificates.X509Certificate2>. Usando o email como um exemplo, a coleção de certificados é uma instância de um <xref:System.Security.Cryptography.X509Certificates.X509CertificateCollection> associada à propriedade <xref:System.Net.Mail.SmtpClient.ClientCertificates%2A> da classe <xref:System.Net.Mail.SmtpClient>. A classe <xref:System.Net.HttpWebRequest> tem uma propriedade <xref:System.Net.HttpWebRequest.ClientCertificates%2A> semelhante.  
  
 A principal diferença entre a classe <xref:System.Security.Cryptography.X509Certificates.X509Certificate> e <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> é que a chave privada deve residir no repositório de certificados da classe <xref:System.Security.Cryptography.X509Certificates.X509Certificate>.  
  
 Mesmo se os certificados forem adicionados a uma coleção e associados a uma conexão SSL específica, nenhum certificado será enviado para o servidor, a menos que o servidor os solicite. Se vários certificados do cliente forem definidos em uma conexão, o melhor será usado com base em um algoritmo que considera a correspondência entre a lista de emissores do certificado fornecida pelo servidor e o nome do emissor do certificado do cliente.  
  
 A classe <xref:System.Net.Security.SslStream> fornece ainda mais controle sobre o handshake SSL. Um cliente pode especificar um representante para escolher qual certificado do cliente deve ser usado.  
  
 Um servidor remoto pode verificar se um certificado do cliente é válido, atual e assinado pela Autoridade de Certificação apropriada. Um representante pode ser adicionado ao <xref:System.Net.ServicePointManager.ServerCertificateValidationCallback%2A> para impor a validação do certificado.  
  
## <a name="client-certificate-selection"></a>Seleção de certificado do cliente  
 O .NET Framework seleciona o certificado do cliente para apresentar ao servidor da seguinte maneira:  
  
1.  Se um certificado do cliente foi apresentado anteriormente ao servidor, o certificado é armazenado em cache quando apresentado pela primeira vez e reutilizado para as solicitações de certificado do cliente posteriores.  
  
2.  Se houver um representante, sempre use o resultado do representante como o certificado do cliente a ser selecionado. Tente usar um certificado armazenado em cache quando possível, mas não use credenciais anônimas armazenadas em cache se o representante retornou nulo e a coleção de certificados não estiver vazia.  
  
3.  Se esse for o primeiro desafio para um certificado do cliente, o Framework enumerará os certificados nos objetos da classe <xref:System.Security.Cryptography.X509Certificates.X509Certificate> ou <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> associados à conexão, procurando uma correspondência entre a lista de emissores do certificado fornecida pelo servidor e o nome do emissor do certificado do cliente. O primeiro certificado correspondente é enviado ao servidor. Se não houver nenhuma correspondência de certificado ou a coleção de certificados estiver vazia, uma credencial anônima será enviada ao servidor.  
  
## <a name="tools-for-certificate-configuration"></a>Ferramentas de configuração de certificado  
 Várias ferramentas estão disponíveis para a configuração de certificado do cliente e do servidor.  
  
 A ferramenta *Winhttpcertcfg.exe* pode ser usada para configurar certificados do cliente. A ferramenta *Winhttpcertcfg.exe* é fornecida como uma das ferramentas com o Windows Server 2003 Resource Kit. Essa ferramenta também está disponível como um download como parte das Ferramentas do Windows Server 2003 Resource Kit em www.microsoft.com.  
  
 A ferramenta *HttpCfg.exe* pode ser usada para configurar certificados do servidor para a classe <xref:System.Net.HttpListener>. A ferramenta *HttpCfg.exe* é fornecida como uma das ferramentas de suporte do Windows Server 2003 e Windows XP Service Pack 2. *HttpCfg.exe* e as outras ferramentas de suporte não são instaladas por padrão no Windows Server 2003 ou Windows XP. No Windows Server 2003. as ferramentas de suporte são instaladas separadamente nas seguintes pasta e arquivo no CD-ROM do Windows Server 2003:  
  
 \Support\Tools\Suptools.msi  
  
 Para uso com o Windows XP Service Pack 2, as Ferramentas de Suporte do Windows XP estão disponíveis como um download em www.microsoft.com.  
  
 O código-fonte de uma versão da ferramenta *HttpCfg.exe* também é fornecido como uma amostra com o SDK do Windows Server. O código-fonte da amostra de *HttpCfg.exe* é instalado por padrão com as amostras de rede como parte do SDK do Windows na seguinte pasta:  
  
 *C:\Program Files\Microsoft SDKs\Windows\v1.0\Samples\NetDS\http\serviceconfig*  
  
 Além dessas ferramentas, as classes <xref:System.Security.Cryptography.X509Certificates.X509Certificate> e <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> fornecem métodos para carregar um certificado do sistema de arquivos.  
  
## <a name="see-also"></a>Consulte também  
 [Segurança na programação de rede](../../../docs/framework/network-programming/security-in-network-programming.md)  
 [Programação de rede no .NET Framework](../../../docs/framework/network-programming/index.md)
