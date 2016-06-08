---
# required metadata

title: Compreender as cadeias de certificados | Azure RMS
description: A aplicação com capacidade para direitos requer um par de chaves públicas e uma cadeia de certificados que reconduz a um certificado da Microsoft na raiz da fidedignidade
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 6AEA2162-82BF-4867-9285-111CD3FCD2F6
# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---
** Este conteúdo do SDK não está atualizado. Durante um curto período de tempo, pode encontrar a [versão atual](https://msdn.microsoft.com/library/windows/desktop/hh535290(v=vs.85).aspx) da documentação no MSDN. **
# Compreender as cadeias de certificados

A programação de uma aplicação com capacidade para direitos requer um par de chaves públicas e uma cadeia de certificados que reconduz a um certificado da Microsoft na raiz da fidedignidade.

## Tipos de Certificado

Cada licença e certificado utilizados num ambiente do Rights Management Services (RMS) consiste numa cadeia de certificados que reconduz a um certificado de uma autoridade de certificação (AC) da Microsoft. A Microsoft fornece duas cadeias nas quais é possível aninhar uma licença ou um certificado, uma cadeia de certificados de pré-produção e uma cadeia de produção. Recomendamos que utilize a hierarquia de pré-produção quando desenvolver uma aplicação para que possa trabalhar sem assinar um *Contrato de Licença de Produção* com a Microsoft. Tenha em atenção que o servidor RMS também deve ser configurado para pré-produção.

Tem de mudar para uma cadeia de produção antes de lançar a sua aplicação. O conteúdo protegido por um certificado de pré-produção é menos seguro do que um certificado de produção.

As chaves públicas e privadas e o certificado de pré-produção são incluídos com o SDK nos seguintes ficheiros localizados na pasta `%MsipcSDKDir%\Bin`.

- **ISVTier5AppSigningPrivKey.dat** contém a chave privada utilizada para assinar um manifesto para utilização durante a programação de aplicações.
- **ISVTier5AppSigningPubKey.dat** contém a chave pública assinada na hierarquia de certificados de pré-produção.
- **ISVTier5AppSignSDK_Client.xml** contém o certificado de pré-produção utilizado para gerar um manifesto para utilização durante a programação de aplicações.

 

Pode utilizar o certificado e a chave privada para criar e assinar um manifesto que identifica os ficheiros que podem ou têm de ser carregados para o espaço de processamento da sua aplicação e os que não têm de ser carregados. O manifesto é então carregado pela plataforma.

Independentemente de ter utilizado um certificado de pré-produção durante a programação de aplicações, quando estiver preparado para lançar a aplicação, tem de gerar um novo par de chaves, adquirir um certificado de produção da Microsoft e utilizar a nova chave privada e o certificado para criar e assinar um manifesto de aplicação.

Para obter mais informações acerca de como trabalhar com cadeias de certificados e assinatura de aplicações, consulte [Mudar para o ambiente de produção](switching-to-the-production-environment.md).

## Tópicos relacionados

* [Conceitos do programador](ad-rms-concepts-nav.md)
* [Mudar para o ambiente de produção](switching-to-the-production-environment.md)
 

 


<!--HONumber=Jun16_HO1-->


