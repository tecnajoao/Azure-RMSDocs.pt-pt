---
title: "Implementar a aplicação – AIP"
description: "Este tópico descreve e fornece orientações sobre como implementar a sua aplicação"
keywords: implementar, RMS, AIP
author: bruceperlerms
ms.author: bruceper
manager: mbaldwin
ms.date: 03/13/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 4B785564-6839-49ED-A243-E2A6DFF88B2E
audience: developer
ms.reviewer: kartikk
ms.suite: ems
ms.openlocfilehash: a78520f3cdf316c7264cb0ca88460858b5a2bf07
ms.sourcegitcommit: 262f88c4f46e29f3747271276c62913b4cefe4f7
translationtype: HT
---
# <a name="deploy-into-production"></a>Implementar em produção

Este tópico ajuda-o com o processo de implementação da sua aplicação com suporte para Azure Information Protection (AIP)/Rights Management Services (RMS).

## <a name="request-an-information-protection-integration-agreement-ipia"></a>Pedir um Contrato de Integração do Information Protection (IPIA)
Para poder disponibilizar uma aplicação desenvolvida com AIP/RMS, tem de pedir e celebrar um contrato formal com a Microsoft.

### <a name="begin-the-process"></a>Início do processo
Obtenha o seu IPIA ao enviar um e-mail para **IPIA@microsoft.com** com as seguintes informações:

**Assunto:** pedido de IPIA para *Nome da Empresa*

No corpo do e-mail, inclua:
- Nome da aplicação e do produto
- Nome próprio e apelido do autor do pedido
- Endereço de e-mail do autor do pedido

### <a name="next-steps"></a>Próximos passos
Após a receção do seu pedido de IPIA, ser-lhe-á enviado um formulário (como um documento do Word).
Analise os termos e condições do IPIA e devolva o formulário para o e-mail **IPIA@microsoft.com** com as seguintes informações:
- Denominação legal da Empresa
- Estado/Distrito (E.U.A./Canadá) ou País de Registo
- URL da empresa
- Endereço de e-mail do contacto
- Endereços adicionais da empresa (opcional)
- Nome da Aplicação da Empresa
- Breve Descrição da Aplicação
- *ID do Inquilino do Azure*
- *ID da Aplicação*
- Contactos, e-mail e telefone da empresa para Correspondência em Situações Críticas

### <a name="completing-the-agreement"></a>Celebração do contrato
Quando recebermos o seu formulário, ser-lhe-á enviada a ligação final do IPIA para assinar digitalmente. Depois de assinar, o contrato será assinado pelo devido representante da Microsoft, dando-se por concluída a celebração do contrato.

### <a name="already-have-a-signed-ipia"></a>Já tem um IPIA assinado?
Se já tiver um IPIA assinado e quiser adicionar um novo *ID da Aplicação* a uma aplicação que irá disponibilizar, envie um e-mail para **IPIA@microsoft.com** e forneça-nos as seguintes informações:
- Nome da Aplicação da Empresa
- Breve Descrição da Aplicação
- ID do Inquilino do Azure (mesmo que seja igual ao anterior)
- ID da Aplicação
- Contactos, e-mail e telefone da empresa para Correspondência em Situações Críticas

Depois de nos enviar o e-mail, aguarde até 72 horas para receber um aviso de receção.

## <a name="deploying-to-the-client-environment"></a>Implementação no ambiente do cliente

Para poder implementar a sua aplicação, desenvolvida com as ferramentas Azure Information Protection (AIP)/Rights Management Services (RMS), terá de implementar o RMS Client 2.1 no computador do utilizador final.

### <a name="rms-client-21"></a>RMS Client 2.1
O RMS Client 2.1 foi concebido para proteger o acesso e a utilização das informações que circulam nas aplicações com suporte para AIP/RMS, quer estejam instaladas no local ou num datacenter da Microsoft.

O RMS Client 2.1 não é um componente de sistema operativo Windows. O cliente é fornecido como uma transferência opcional que pode ser distribuída livremente com a sua aplicação, com o reconhecimento e a aceitação do respetivo contrato de licença.

> [!IMPORTANT]
> O RMS Client 2.1 tem uma arquitetura específica e tem de corresponder à arquitetura do seu sistema operativo de destino.


## <a name="rms-client-21-installation-options"></a>Opções de instalação do RMS Client 2.1

### <a name="creating-your-deployment-package"></a>Criar o seu pacote de implementação

Recomendamos que agrupe o pacote instalador do RMS Client com a sua aplicação ou solução através da sua tecnologia de instalação preferencial. O RMS Client pode ser redistribuído livremente noutras aplicações e soluções.

Pode optar por instalar o RMS Client 2.1 de forma interativa ao iniciar o instalador do RMS Client 2.1 ou por instalá-lo silenciosamente. Os passos de integração serão:

-   Transferir o instalador do RMS Client 2.1
-   Integrar o instalador do RMS Client 2.1 para ser executado com o instalador da sua aplicação

Um exemplo da integração do RMS Client 2.1 com a sua aplicação é o pacote [Rights Protected Folder Explorer](https://technet.microsoft.com/en-us/library/rights-protected-folder-explorer(v=ws.10).aspx). Tente instalá-lo por si para compreender a abordagem.

### <a name="make-rms-client-21-a-pre-requisite-for-your-application-install"></a>Tornar o RMS Client 2.1 um pré-requisito para a instalação da sua aplicação

Neste caso, irá criar um pré-requisito de forma que a instalação da aplicação falhe se o RMS Client 2.1 não estiver presente no computador do utilizador final.

Se o cliente não estiver presente, forneça uma mensagem de erro a informar o utilizador onde pode transferir uma cópia do RMS Client 2.1

Se o cliente estiver presente, prossiga com a instalação da aplicação.

## <a name="enabling-azure-information-protection-services-with-your-application"></a>Ativar o Azure Information Protection Services na aplicação

> [!NOTE]
> Se tiver migrado para o novo modelo de autenticação da ADAL, não tem de instalar o **SIA**. Para obter mais informações, consulte [Autenticação ADAL para a aplicação com suporte RMS](adal-auth.md).
> Além disso, pode **certificar a sua aplicação para o Windows 10** - através da atualização da sua aplicação para utilizar a autenticação ADAL em vez do Assistente de Início de Sessão do Microsoft Online, o utilizador e os seus clientes poderão: utilizar a autenticação multifator Instale o RMS Client 2.1 sem necessidade de privilégios administrativos para a máquina

Para o utilizador final tirar partido dos serviços do Information Protection, terá de implementar o *Assistente de Início de Sessão (SIA) do Online Services*. Enquanto programador da aplicação, não sabe se o utilizador final irá utilizar o Information Protection através do RMS (no local) ou através do Azure Information Protection.


> [!IMPORTANT]
> Se executar a aplicação cliente com o RMS baseado no Azure, terá de solicitar os seus próprios inquilinos. Para obter mais informações, consulte [Requisitos do Azure RMS: Subscrições na cloud que suportam o Azure RMS](../get-started/requirements-subscriptions.md).
> Para obter mais informações sobre a execução com o Azure RMS, consulte [Permitir que a aplicação do serviço funcione com o RMS baseado na cloud](how-to-use-file-api-with-aadrm-cloud.md).

-   Transfira o [Assistente de Início de Sessão do Microsoft Online Services](http://www.microsoft.com/en-us/download/details.aspx?id=28177) do Centro de Transferências da Microsoft.
-   Certifique-se de que a implementação de uma aplicação com capacidade para direitos inclui uma verificação de pré-requisitos para esta seleção de serviço.
-   Para os seus próprios testes e para a utilização do serviço online por parte dos utilizadores finais, consulte o tópico da TechNet [Configurar o Rights Management](https://TechNet.Microsoft.Com/en-us/library/jj585002.aspx).

Também terá de utilizar este guia para configurar a sua aplicação – [How to configure your App Service application to use Azure Active Directory login (Como configurar a aplicação do Serviço de Aplicações para utilizar o início de sessão do Azure Active Directory)](https://docs.microsoft.com/en-us/azure/app-service-mobile/app-service-mobile-how-to-configure-active-directory-authentication).

Para obter mais informações sobre como permitir que a aplicação utilize o RMS para serviços de Gestão de Direitos do Azure, consulte [Permitir que a aplicação funcione com o RMS baseado na cloud](how-to-use-file-api-with-aadrm-cloud.md).

## <a name="related-topics"></a>Tópicos relacionados

* [Assistente de Início de Sessão do Microsoft Online Services](http://www.microsoft.com/en-us/download/details.aspx?id=28177)
* [Configurar o Rights Management](https://TechNet.Microsoft.Com/en-us/library/jj585002.aspx)
* [Permitir que a aplicação funcione com o RMS baseado na cloud](how-to-use-file-api-with-aadrm-cloud.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]