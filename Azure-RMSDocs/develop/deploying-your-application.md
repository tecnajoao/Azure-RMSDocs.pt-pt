---
# required metadata

title: Implementar a aplicação | Azure RMS
description: Este tópico descreve e serve de orientação nas opções de implementação da sua aplicação com capacidade para direitos
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 4B785564-6839-49ED-A243-E2A6DFF88B2E
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
# Implementar a aplicação


Este tópico descreve e serve de orientação nas opções de implementação da sua aplicação com capacidade para direitos.

> [!IMPORTANT]
> Recomenda-se que teste primeiro a aplicação Rights Management Services SDK 2.1 com o ambiente de pré-produção do RMS num Servidor RMS. Em seguida, se pretender que o cliente tenha a capacidade de utilizar a aplicação com o Serviço Azure RMS, avance para o teste nesse ambiente. Para obter mais informações, consulte [Permitir que a aplicação do serviço funcione com o RMS baseado na nuvem](how-to-use-file-api-with-aadrm-cloud.md).

 

## Opções de instalação do Cliente dos Serviços de Gestão de Direitos do Active Directory 2.1

Depois de criar o ficheiro de manifesto utilizando um certificado de produção, a aplicação está pronta para ser implementada. Dado que utilizou o SDK RMS 2.1, será necessário que o Cliente dos Serviços de Gestão de Direitos do Active Directory 2.1 seja implementado no computador do utilizador final.

### Cliente de AD RMS 2.1

O Cliente de AD RMS 2.1 é um software concebido para os computadores cliente para ajudar a proteger o acesso e a utilização de informações que circulam pelas aplicações que utilizam o RMS, independentemente de estar instalado no local ou num datacenter Microsoft.

O Cliente de AD RMS 2.1 não é um componente do sistema operativo Windows. O Cliente de AD RMS 2.1 é incluído como uma transferência opcional que pode ser, com o reconhecimento e a aceitação do respetivo contrato de licença, distribuído gratuitamente com o seu software de terceiros para permitir o acesso de cliente a conteúdo que foi protegido por direitos através da utilização e implementação de servidores RMS no seu ambiente.

> [!IMPORTANT] O Cliente de AD RMS 2.1 é de arquitetura específica e tem de corresponder à arquitetura do seu sistema operativo de destino.


## Opções de instalação do Cliente de AD RMS 2.1

-   **Redistribuir o Cliente de AD RMS 2.1**

    A abordagem recomendada é agrupar o pacote instalador do Cliente do RMS com a sua aplicação ou solução utilizando a sua tecnologia de instalação preferencial. O Cliente do RMS pode ser livremente redistribuído e agrupado com outras aplicações e soluções de TI.

    Pode optar por instalar o Cliente de AD RMS 2.1 de forma interativa ao iniciar o instalador do Cliente de AD RMS 2.1 ou ao instalá-lo silenciosamente. Os passos de integração serão:

    -   Transferir o instalador do Cliente do RMS 2.1
    -   Integrar o instalador do Cliente de AD RMS 2.1 executado com o instalador da sua aplicação

    Dois bons exemplos de integração do Cliente de AD RMS 2.1 com a sua aplicação são o pacote instalador do SDK RMS 2.1 e o pacote do Explorador de Pastas Protegidas por Direitos. Tente instalá-los por si para compreender a abordagem.

-   **Tornar o Cliente de AD RMS 2.1 um pré-requisito para a instalação da sua aplicação**

    Neste caso, irá criar um pré-requisito de forma que a instalação da aplicação falhe se o Cliente de AD RMS 2.1 não estiver presente no computador do utilizador final.

    Se o cliente não estiver presente, forneça uma mensagem de erro a informar o utilizador onde pode transferir uma cópia do Cliente de AD RMS 2.1

    Se o cliente estiver presente, prossiga com a instalação da aplicação.

## Ativar Serviços de Gestão de Direitos do Azure com a sua aplicação

> [!NOTE]
> Se tiver migrado para o novo modelo da ADAL para autenticação, não tem de instalar o SIA. Para obter mais informações, consulte Autenticação ADAL para a aplicação com suporte RMS

- **Certificar a sua aplicação para o Windows 10**: ao atualizar a sua aplicação para utilizar a autenticação ADAL em vez do Assistente de Início de Sessão Online da Microsoft, o utilizador e os seus clientes poderão:
  - Utilizar a autenticação multifator
  - Instalar o cliente RMS 2.1 sem necessidade de privilégios administrativos para o computador
 
  Para o utilizador final tirar partido dos serviços de Gestão de Direitos do Azure, tem de implementar o *Assistente de Início de Sessão do Online Services*. Na qualidade de programador da aplicação, não sabe se o utilizador final irá utilizar o RMS (no local) ou os serviços de Gestão de Direitos do Azure (serviço em nuvem).

> [!IMPORTANT]
> Executar a aplicação de cliente do SDK RMS 2.1 com o Azure RMS requer que solicite um Inquilino do Azure RMS. Envie um e-mail para <rmcstbeta@microsoft.com> com o seu pedido de inquilino.

-   Transfira o [Assistente de Início de Sessão do Microsoft Online Services](http://www.microsoft.com/en-us/download/details.aspx?id=28177) do Centro de Transferências da Microsoft.
-   Certifique-se de que a implementação de uma aplicação com capacidade para direitos inclui uma verificação de pré-requisitos para esta seleção de serviço.
-   Para os seus próprios testes e para a utilização do serviço online por parte dos utilizadores finais, consulte o tópico da TechNet [Configurar o Rights Management](https://TechNet.Microsoft.Com/en-us/library/jj585002.aspx).

Para obter mais informações sobre como permitir que a aplicação utilize o RMS para serviços de Gestão de Direitos do Azure, consulte [Permitir que a aplicação funcione com o RMS baseado na nuvem](how-to-use-file-api-with-aadrm-cloud.md).

## Tópicos relacionados

* [Como utilizar](how-to-use-msipc.md)
* [Assistente de Início de Sessão do Microsoft Online Services](http://www.microsoft.com/en-us/download/details.aspx?id=28177)
* [Configurar o Rights Management](https://TechNet.Microsoft.Com/en-us/library/jj585002.aspx)
* [Permitir que a aplicação funcione com o RMS baseado na nuvem](how-to-use-file-api-with-aadrm-cloud.md)
 

 





<!--HONumber=Jun16_HO1-->


