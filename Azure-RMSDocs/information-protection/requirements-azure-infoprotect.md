---
title: Requisitos para o Azure Information Protection | Azure RMS
description: "Para avaliar a versão de pré-visualização do Azure Information Protection, certifique-se de que tem os seguintes pré-requisitos."
author: cabailey
manager: mbaldwin
ms.date: 08/22/2016
ms.topic: get-started-article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: aa4353e5-c5b0-47f6-a6f9-87d13e8f075f
ms.reviewer: eymanor
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: c9f9211e7c1dcf293caf81475515114b5433d6a7
ms.openlocfilehash: cc1ec2b2544ac368821155b7e0c3c0e179982d1d


---

# Requisitos para o Azure Information Protection

>*Aplica-se a: pré-visualização do Azure Information Protection*

**[Estas informações são preliminares e estão sujeitas a alterações. ]**

Para avaliar a versão de pré-visualização do Azure Information Protection, certifique-se de que tem os seguintes pré-requisitos. 

|Requisito|Mais informações|
|---------------|--------------------|
|Uma subscrição do Office 365 que inclua o Azure Rights Management|Por exemplo, uma subscrição do Office 365 E3, E4 ou E5.<br /><br />Para obter mais informações sobre as subscrições e ligações disponíveis para as versões de avaliação gratuitas, veja a secção [Subscrição do Office 365](../get-started/requirements-subscriptions.md#office-365-subscription) da documentação de requisitos do Azure RMS.|
|Diretório do Azure AD|A sua organização tem de ter um diretório do Azure AD para suportar a autenticação de utilizador para Azure RMS e Azure Information Protection. Além disso, se pretender utilizar as contas de utilizador do seu diretório no local (AD DS), tem também de configurar a integração de diretórios.<br /><br />A Multi-Factor Authentication (MFA) é suportada com o Azure RMS quando tem o software de cliente necessário e a infraestrutura de suporte de MFA corretamente configurada.<br /><br />Para obter mais informações, veja o artigo [Diretório do Azure AD](../get-started/requirements-azure-ad.md), onde as informações do Azure RMS também se aplicam ao Azure Information Protection.|
|Dispositivos cliente|São suportados os seguintes dispositivos de cliente para esta pré-visualização:<br /><br />- Windows 10 (x86, x64)<br /><br />- Windows 8.1 (x86, x64)<br /><br />- Windows 8 (x86, x64)<br /><br />- Windows 7 Service Pack 1 (x86, x64)<br /><br />Quando protege os dados, que podem ser consumidos pelos próprios dispositivos (Windows, Mac, iOS, Android), que suportam o Azure Rights Management. Para obter uma lista destes dispositivos e versões suportados, veja [Requisitos do Azure RMS: dispositivos cliente que suportam o Azure RMS](../get-started/requirements-client-devices.md).|
|Aplicações|Para a versão de pré-visualização e na disponibilidade geral (DG), o Azure Information Protection suporta etiquetagem e proteção de ficheiros e os e-mails que são criados pelas seguintes aplicações do Office: **Word**, **Excel**, **PowerPoint**, e **Outlook** a partir dos seguintes conjuntos de aplicações do Office:<br /><br />- Office Professional Plus 2016<br /><br />- Office Professional Plus 2013 com o Service Pack 1<br /><br />- Office Professional Plus 2010<br /><br />Depois de disponibilidade geral, procure um anúncio [Blogue do Enterprise Mobility e Security](https://blogs.technet.microsoft.com/enterprisemobility/?product=azure-rights-management-services) a indicar quando o Azure Information Protection suporta tipos de ficheiro adicionais, como PDF, áudio, vídeo e ficheiros de imagem.|
|Infraestrutura que suporta a conetividade à Internet e a serviços em nuvem dependentes|Se tiver uma firewall ou um dispositivo interveniente semelhante que deve ser configurado para permitir ligações específicas, veja as informações do **Azure Rights Management (RMS)** na secção [Portal do Office 365 e partilhado](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2#BKMK_Portal-identity) do seguinte artigo do Office: [URL do Office 365 e intervalos de endereços IP](https://support.office.com/en-US/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2)<br /><br />Além disso:<br /><br />- Permitir tráfego HTTPS em TCP 443 para **informationprotection.azure.com**.<br /><br />- Não termine a ligação cliente para serviço TLS (por exemplo, para fazer uma inspeção ao nível do pacote). <br /><br />- Se utilizar um proxy Web que requer autenticação, tem de o configurar para utilizar a autenticação integrada do Windows com as credenciais de início de sessão do utilizador do Active Directory.|

## Passos seguintes

Caso cumpra estes requisitos, experimente a nossa demonstração auto-configurada para configurar e experimentar o Azure Information Protection: [Tutorial de início rápido do Azure Information Protection](infoprotect-quick-start-tutorial.md).




<!--HONumber=Aug16_HO4-->


