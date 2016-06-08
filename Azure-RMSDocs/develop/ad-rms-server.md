---
# required metadata

title: Servidor AD RMS | Azure RMS
description: O componente de servidor do Rights Management Services (RMS) é implementado por um conjunto de serviços Web que são executados nos Serviços de Informação de Internet da Microsoft.
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 17B05780-B0EF-4805-8304-52DCDEB3AADB
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

# Servidor AD RMS
Este tópico descreve a finalidade e as funções do Servidor RMS.

O componente de servidor do Rights Management Services (RMS) é implementado por um conjunto de serviços Web que são executados nos [Serviços de Informação de Internet da Microsoft](http://www.iis.net/overview) (IIS). Também pode utilizar a implementação baseada na nuvem através do RMS no Azure. Para obter mais informações sobre como utilizar o serviço Azure Rights Management, consulte [Permitir que a aplicação do serviço funcione com o RMS baseado na nuvem](how-to-use-file-api-with-aadrm-cloud.md).

Nos servidores no local, a começar pelo Windows Server 2008, pode instalar e configurar o serviço RMS ao adicioná-lo como uma função. Para instalar o serviço em sistemas operativos anteriores, transfira-o do centro de transferências da Microsoft em [Microsoft Windows Rights Management Services com Service Pack 2](http://www.microsoft.com/download/en/details.aspx?id=4909).

Dos vários serviços Web instalados, os que se seguem são importantes para o desenvolvimento de aplicações.

**Administração** – Aloja o Web site de Administração que lhe permite gerir o RMS. O serviço é executado em servidores de certificação de raiz e em servidores de licenciamento. Pode utilizar a [API de Scripting dos Serviços de Gestão de Direitos do Active Directory](https://msdn.microsoft.com/library/Bb968797) para escrever scripts de administração.

**Certificação de Contas** – Cria certificados de computadores que identificam os computadores na hierarquia de certificados de RMS e certificados de conta de direitos que associem utilizadores a computadores específicos. Para obter mais informações, consulte [Ativar um Utilizador](https://msdn.microsoft.com/library/Cc530378).

Este serviço é executado no servidor de certificação de raiz.

**Licenciamento** – Emite uma licença de utilizador final que permite que os utilizadores finais consumam conteúdo protegido. O serviço é executado em servidores de certificação de raiz e em servidores de licenciamento.

**Publicar** – Cria uma página [Criar uma Licença de Emissão](https://msdn.microsoft.com/library/Aa362355). O serviço é executado em servidores de certificação de raiz e em servidores de licenciamento.

**Pré-certificação** – Permite que um servidor peça um Certificado de Conta de Direitos (RAC) em nome de um utilizador. Um RAC utiliza o certificado do computador da ativação do RMS para vincular contas de utilizador a computadores específicos ou grupos de computadores e é utilizado para permitir que os consumidores utilizem conteúdo protegido. O serviço é executado em servidores de certificação de raiz e em servidores de licenciamento.

**Localizador de Serviço** – Fornece o URL da certificação de contas, do licenciamento e dos serviços de publicação ao Active Directory para que possam ser detetados por clientes de RMS. O serviço é executado em servidores de certificação de raiz e em servidores de licenciamento.

 

## Tópicos relacionados ##
* [Descrição Geral](ad-rms-overview.md)
* [Serviços de Informação Internet da Microsoft](http://www.iis.net/overview)
* [Permitir que a aplicação do serviço funcione com o RMS baseado na nuvem](how-to-use-file-api-with-aadrm-cloud.md)
* [Microsoft Windows Rights Management Services com Service Pack 2](http://www.microsoft.com/download/en/details.aspx?id=4909)
* [API de Scripting dos Serviços de Gestão de Direitos do Active Directory](https://msdn.microsoft.com/library/Bb968797)
* [Ativar um Computador](https://msdn.microsoft.com/library/Cc530377)
* [Ativar um Utilizador](https://msdn.microsoft.com/library/Cc530378)
* [Criar uma Licença de Emissão](https://msdn.microsoft.com/library/Aa362355)

 

 


<!--HONumber=Jun16_HO1-->


