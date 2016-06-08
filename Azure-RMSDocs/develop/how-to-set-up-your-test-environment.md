---
# required metadata

title: Configurar o ambiente de teste | Azure RMS
description: A aplicação com capacidade para direitos pode ser testada com opções de servidor diferentes.
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: E480D8D6-F070-43D1-B2B0-6921459C3437
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
# Configurar o ambiente de teste

A aplicação com capacidade para direitos pode ser testada com opções de servidor diferentes.

**Importante** Recomenda-se que teste primeiro a aplicação SDK Rights Management Services 2.1 com o ambiente de pré-produção do AD RMS num Servidor AD RMS. Em seguida, se pretender que o cliente tenha a capacidade de utilizar a aplicação com o Serviço Azure RMS, passe para o teste nesse ambiente. Para obter mais informações, consulte [Permitir que a aplicação do serviço funcione com o RMS baseado na nuvem](how-to-use-file-api-with-aadrm-cloud.md).

 

### Pré-requisitos

-   [Instalar o SDK](create-your-first-rights-aware-application.md)

Instruções

### Passo 1: configurar o ambiente de teste

Para testar a aplicação com capacidade para direitos, tem de a executar num servidor RMS que esteja configurado para pré-produção. Um servidor RMS de pré-produção utiliza a hierarquia de certificados ISV/pré-produção para encriptar e desencriptar ficheiros.

Para mais informações sobre a hierarquia de certificados do AD RMS, consulte [Compreender as cadeias de certificados](understanding-certificate-chains.md).

Existem duas opções disponíveis para testar a aplicação num servidor RMS:

-   **Pode executar a aplicação no ambiente do ISV do AD RMS de 1 só caixa**. Se estiver a executar o Windows Server 2012, Windows Server 2008 R2 ou Windows Server 2008 e tiver o Hyper-V instalado, pode implementar o ambiente do ISV do AD RMS de 1 só caixa ao criar uma máquina virtual utilizando o VHD de 1 só caixa do AD RMS. O ambiente do ISV do AD RMS de 1 só caixa fornece um servidor RMS configurado para pré-produção e também tem o Cliente dos Serviços de Gestão de Direitos do Active Directory 2.1 instalado. As definições de registo para o servidor RMS e o cliente já estão configuradas. Para testar a aplicação, pode executá-la no computador virtual no qual está implementado o ambiente de 1 só caixa.
-   **Pode executar a aplicação num servidor RMS que esteja configurado para pré-produção e que esteja implementado na sua rede**. Neste caso, também tem de instalar e configurar o Cliente de AD RMS 2.1 no computador onde a aplicação será executada. Para obter informações sobre como o fazer, consulte [Configurar cliente](how-to-configure-the-ad-rms-client-2-0.md). Para obter informações sobre como implementar um servidor RMS e configurá-lo para pré-produção, consulte [Instalar e configurar o servidor](how-to-install-and-configure-an-rms-server.md).

## Tópicos relacionados

* [Como utilizar](how-to-use-msipc.md)
* [Página de transferências colaterais do Webinar do SDK AD RMS](https://connect.microsoft.com/site1170/Downloads/DownloadDetails.aspx?DownloadID=42440)
* [Configurar cliente](how-to-configure-the-ad-rms-client-2-0.md)
* [Instalar o SDK](create-your-first-rights-aware-application.md)
* [Instalar e configurar o servidor](how-to-install-and-configure-an-rms-server.md)
* [Compreender as cadeias de certificados](understanding-certificate-chains.md)
 

 





<!--HONumber=Jun16_HO1-->


