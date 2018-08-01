---
title: Servidor AD RMS | Azure RMS
description: O componente de servidor do Rights Management Services (RMS) é implementado por um conjunto de serviços Web que são executados nos Serviços de Informação de Internet da Microsoft.
keywords: ''
author: lleonard-msft
ms.author: alleonar
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 17B05780-B0EF-4805-8304-52DCDEB3AADB
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: bb8ff34d90d531f11aae56509c46b6377383c21d
ms.sourcegitcommit: 44ff610dec678604c449d42cc0b0863ca8224009
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/31/2018
ms.locfileid: "39370453"
---
# <a name="server"></a>Servidor

Este tópico descreve a finalidade e as funções do RMS Server para o Azure e Windows Server.

**Azure RMS** - Para obter informações sobre a utilização do serviço Azure Rights Management, consulte [Ativar a aplicação de serviço para suportar o RMS baseado na nuvem](how-to-use-file-api-with-aadrm-cloud.md).

> [!IMPORTANT] 
> Recomendamos que desenvolva e teste a sua aplicação através do Azure RMS.

**Windows Server** - Nos servidores de RMS no local, a partir do Windows Server 2008, pode instalar e configurar o serviço RMS adicionando-o como uma função. Para instalar o serviço em sistemas operativos anteriores, transfira-o do centro de transferências da Microsoft em [Microsoft Windows Rights Management Services com Service Pack 2](http://www.microsoft.com/download/en/details.aspx?id=4909).

Entre os diversos serviços Web instalados, os que se seguem são importantes para o desenvolvimento de aplicações para o RMS Server no Windows Server.

| Serviço | Descrição |
|---------|-------------|
| Administration | Aloja o site de Administração que permite gerir o RMS. O serviço é executado em servidores de certificação de raiz e em servidores de licenciamento. Pode utilizar a API de Scripts dos Serviços de Gestão de Direitos do Active Directory para escrever scripts de administração.|
| Certificação de Conta |Cria certificados de computador que identificam os computadores na hierarquia de certificados de RMS e certificados de conta de direitos que associam utilizadores a computadores específicos. Para obter mais informações, consulte Ativar um Computador e Ativar um Utilizador.<p><p>Este serviço é executado no servidor de certificação de raiz. |
|Licenciamento | Emite um *contrato de licença do utilizador final*. O serviço é executado em servidores de certificação de raiz e em servidores de licenciamento.|
|Publicação | Cria uma *licença de emissão* que define as políticas que podem ser enumeradas numa licença do utilizador final. Para obter mais informações, consulte [Criar uma Licença de Emissão](https://msdn.microsoft.com/library/Aa362355).<p><p>O serviço é executado em servidores de certificação de raiz e em servidores de licenciamento.|
|Pré-certificação | Permite que um servidor peça um *certificado de conta de direitos* em nome de um utilizador. O serviço é executado em servidores de certificação de raiz e em servidores de licenciamento.|
|Localizador de Serviço | Fornece o URL dos serviços de certificação de conta, licenciamento e publicação ao Active Directory para que possam ser detetados pelos clientes RMS. O serviço é executado em servidores de certificação de raiz e em servidores de licenciamento.|

## <a name="related-topics"></a>Tópicos relacionados ##
* [Descrição Geral](ad-rms-overview.md)
* [Serviços de Informação Internet da Microsoft](http://www.iis.net/overview)
* [Permitir que a aplicação do serviço funcione com o RMS baseado na nuvem](how-to-use-file-api-with-aadrm-cloud.md)
* [Microsoft Windows Rights Management Services com Service Pack 2](http://www.microsoft.com/download/en/details.aspx?id=4909)
* [API de Scripting dos Serviços de Gestão de Direitos do Active Directory](https://msdn.microsoft.com/library/Bb968797)
* [Ativar um Computador](https://msdn.microsoft.com/library/Cc530377)
* [Ativar um Utilizador](https://msdn.microsoft.com/library/Cc530378)
* [Criar uma Licença de Emissão](https://msdn.microsoft.com/library/Aa362355)
