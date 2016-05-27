---
# required metadata

title: Obter uma licença de produção | Azure RMS
description: O lançamento de uma aplicação desenvolvida utilizando o SDK RMS 2.1 requer um Contrato de Licença de Produção.
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 6749817E-FF34-4384-BF63-39AEA5C372CA
# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Obter uma licença de produção

Antes de poder lançar uma aplicação desenvolvida utilizando o SDK Rights Management Services 2.1, tem de solicitar um Contrato de Licença de Produção para obter um certificado de produção.

> [!IMPORTANT]
> Se executar a aplicação cliente com o RMS com base no Azure, terá de solicitar um Inquilino do Azure RMS. Envie um e-mail para <rmcstbeta@microsoft.com> com o seu pedido de inquilino.

Para obter mais informações sobre a execução com o Azure RMS, consulte [Permitir que a aplicação do serviço funcione com o RMS baseado na nuvem](how-to-use-file-api-with-aadrm-cloud.md).


O certificado de produção e o certificado de pré-produção realizam uma função semelhante, mas destinam-se a uma utilização em ambientes diferentes. Ambos contêm uma cadeia de certificados com uma autoridade de certificação (AC) da Microsoft na raiz de fidedignidade, mas o certificado de pré-produção é utilizado apenas para desenvolver uma aplicação do RMS. O certificado de produção é utilizado em ambientes de pós-lançamento. O certificado de produção e a chave privada associada são utilizados para criar e assinar um manifesto que identifica os ficheiros que podem ou que têm de ser carregados para o espaço de processamento da sua aplicação e os que não têm de ser carregados.

Para obter mais informações sobre as chaves, consulte [Testar a aplicação com capacidade para direitos](running-your-first-application.md).

Pode obter o certificado ao solicitar um Contrato de Licença de Produção.

## Solicitar um Contrato de Licença de Produção

-   Envie uma mensagem de e-mail para [RMLA@microsoft.com](mailto:rmla@microsoft.com) e inclua as seguintes informações:

    -   Nome da empresa completo

    -   Endereço físico da empresa (inclua a cidade, o estado, o país ou a região e o código postal)
    -   Morada de correio postal da empresa (inclua a cidade, o estado, o país ou a região e o código postal)
    -   Números de telefone e fax da empresa
    -   URL da empresa
    -   País ou região de constituição
    -   Nome da aplicação ou produto
    -   Nome próprio e apelido do autor do pedido
    -   Título ou cargo do autor do pedido
    -   Endereço de e-mail do autor do pedido

    Embora uma conta de e-mail não seja estritamente necessária, o processo de candidatura normalmente depende do e-mail para a comunicação. Pode obter uma conta de e-mail gratuita em Microsoft Outlook.com. Se não tiver uma conta e não pretender uma, pode enviar uma candidatura datilografada para o seguinte endereço:

    `Active Directory Rights Management License Agreements (ADRMLA)`

    `Microsoft Corporation`

    `One Microsoft Way`

    `Redmond, WA 98052-6399`

    Quando solicitar um contrato, efetue o seguinte:

    -   Submeta as informações em inglês, conforme deve aparecer no contrato.
    -   Envie todas as informações necessárias. As informações em falta ou incompletas podem atrasar o processamento do pedido.

    A equipa do Contrato de Licença do Active Directory Rights Management (ADRMLA) responderá ao seu pedido por e-mail no prazo de três dias úteis ou superior se enviar o pedido utilizando um serviço postal. A resposta irá incluir o formulário do contrato de licença e mais instruções. Leia, assine e devolva todas as páginas do contrato à equipa do ADRMLA. Não altere os tipos de letra nem reformate os parágrafos do contrato de licença.

    Certifique-se de que segue as instruções que recebe da equipa do ADRMLA. As instruções listam os itens de informações digitais necessários para satisfazer o pedido de certificado. Ao seguir as instruções passo a passo, reduzirá os atrasos.

    A equipa do ADRMLA irá reencaminhar o certificado de produção para si depois de ser criado. O certificado é criado com base no contrato de licença e nas informações digitais (incluindo uma chave pública) que fornecer. Tenha em atenção que poderá demorar até 15 dias úteis para a equipa do ADRMLA responder com o certificado por e-mail ou mais se a comunicação for pelo serviço postal.

## Tópicos relacionados

* [Como utilizar](how-to-use-msipc.md)
* [Testar a aplicação com capacidade para direitos](running-your-first-application.md)
 

 





<!--HONumber=Apr16_HO4-->


