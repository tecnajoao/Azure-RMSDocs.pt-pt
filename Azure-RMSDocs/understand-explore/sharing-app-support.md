---
title: Aplicação de partilha RMS para Windows e plataformas móveis – AIP
description: Como a aplicação de partilha RMS suporta o Azure RMS como uma aplicação gratuita e transferível que é necessária para suportar o Office 2010, mas que também é recomendada para computadores com o Windows, computadores Mac e dispositivos móveis.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 16/01/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 1da6e372-2b3f-4af7-80f7-6b9073dff7f5
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: f0b7204695ade31df0f6132684fd379704a4b338
ms.sourcegitcommit: dbbfadc72f4005f81c9f28c515119bc3098201ce
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/28/2018
ms.locfileid: "30206922"
---
# <a name="rms-sharing-application-for-windows-and-mobile-platforms"></a>Aplicação de partilha RMS para Windows e plataformas móveis

>*Aplica-se a: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

> [!IMPORTANT]
> **Notificação de fim do suporte**: a aplicação de partilha Rights Management para Windows está a ser substituída pelo [cliente do Azure Information Protection](../rms-client/aip-client.md). Suporte para esta aplicação anterior irá parar 31 de Janeiro de 2019. 
 
A aplicação de partilha RMS é uma aplicação transferível que suporta o Office 2010 para computadores Windows e era recomendada para todos os dispositivos móveis e computadores Windows. Continua a ser recomendada para computadores Mac e dispositivos Windows Phone. Uma das suas vantagens é o facto de poder aplicar proteção genérica a aplicações e ficheiros que não suportam nativamente o serviço Azure Rights Management, o que significa que todos os ficheiros podem ser protegidos. Para obter mais informações sobre os diferentes níveis de proteção, consulte a secção [Níveis de proteção – nativa e genérica](../rms-client/sharing-app-admin-guide-technical.md#levels-of-protection--native-and-generic) no [Guia do administrador da aplicação de partilha Rights Management](../rms-client/sharing-app-admin-guide.md).

Quando os utilizadores protegem os seus ficheiros com a aplicação de partilha RMS, também podem controlar os documentos que protegeram e, se for necessário, revogar o acesso aos mesmos. Para tal, utilizam o [site de controlo de documentos](http://go.microsoft.com/fwlink/?LinkId=529562).

Nos computadores com o Windows, a aplicação de partilha RMS integra-se de forma discreta nas aplicações que os utilizadores já utilizam e melhora-as:

-   É instalado um suplemento do Office para Word, Excel, PowerPoint e Outlook. Isto proporciona aos utilizadores um botão **Partilhar Protegido** no friso, que invoca uma caixa de diálogo fácil de utilizar de definições que são normalmente utilizadas para proteger ficheiros a enviar por e-mail. Este botão também fornece uma forma rápida de aceder ao site de controlo de documentos.

-   Uma nova opção de clique com o botão direito do rato do Explorador de Ficheiros. Isto proporciona aos utilizadores uma opção **Proteger no local**, que invoca uma caixa de diálogo fácil de utilizar de definições que são normalmente utilizadas para proteger ficheiros armazenados num disco.

-   Um visualizador para abrir ficheiros protegidos pelo serviço Azure Rights Management. Este visualizador é invocado automaticamente quando não existe outra aplicação instalada capaz de abrir o ficheiro protegido.

-   Configuração de back-end para o Office 2010, que permite que o Word, Excel, PowerPoint e Outlook deste conjunto de aplicações funcionem de forma totalmente integrada no serviço Azure Rights Management.

Embora a aplicação de partilha RMS para o Windows possa ser transferida e instalada para um único computador a partir da [página do Microsoft Rights Management](http://go.microsoft.com/fwlink/?LinkId=303970), também suporta uma implementação empresarial para instalação automática e configuração personalizada. Para mais informações, consulte os seguintes recursos:

-   [Guia do administrador da aplicação de partilha Rights Management](../rms-client/sharing-app-admin-guide.md)

-   [Guia do utilizador da aplicação de partilha Rights Management](../rms-client/sharing-app-user-guide.md)

A aplicação de partilha RMS para dispositivos móveis suporta os dispositivos móveis utilizados com maior frequência, tal como iPad e iPhone, Android, Windows Phone e Windows RT. Os utilizadores podem transferir esta aplicação nas lojas relevantes e existem ligações para cada uma delas na [página do Microsoft Rights Management](http://go.microsoft.com/fwlink/?LinkId=303970).

**Se tiver o Microsoft Intune**: uma vez que a aplicação de partilha RMS inclui o Microsoft Intune App Software Development Kit, pode utilizar as seguintes opções:

-   Implementar e gerir a aplicação para os dispositivos iOS e Android inscritos pelo Intune.

-   Gerir a aplicação para os dispositivos Android não inscritos pelo Intune.


## <a name="next-steps"></a>Próximos passos
Para ver como outras aplicações e serviços suportam o serviço Azure Rights Management do Azure Information Protection, consulte [Como as aplicações suportam o serviço Azure Rights Management](applications-support.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
