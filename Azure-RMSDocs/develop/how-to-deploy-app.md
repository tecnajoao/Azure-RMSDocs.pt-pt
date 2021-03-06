---
title: Como implementar uma aplicação – AIP
description: Este artigo descreve o processo de implementação de uma aplicação de serviço num inquilino diferente daquele com que a aplicação foi desenvolvida de origem.
keywords: ''
author: kkanakas
ms.author: kartikka
manager: barbkess
ms.date: 02/27/2017
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 34dc6d6f-cfe4-4848-9b11-8d90c4b38ef7
audience: developer
ms.reviewer: kartikka
ms.suite: ems
ms.openlocfilehash: 5be6785c86cfeb104acc7f12d4cb7b830e9c9d36
ms.sourcegitcommit: a78d4236cbeff743703c44b150e69c1625a2e9f4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/14/2019
ms.locfileid: "56251880"
---
# <a name="deploying-a-service-application-into-a-different-tenant"></a>Implementar uma aplicação de serviço num inquilino diferente

Este artigo descreve o processo de implementação de uma aplicação de serviço. Neste cenário, mudámos o registo da aplicação com o inquilino de desenvolvimento do AD inicial para registá-la com um inquilino de produção do AD da empresa diferente.

> [!Note]
> Este cenário só é relevante se a aplicação de serviço utilizar a autenticação através de uma chave simétrica.

## <a name="scenario"></a>Cenário
A empresa *CoolApp* desenvolveu uma aplicação de serviço com o Azure Information Protection (AIP) que encripta, atribui etiquetas e protege documentos quando os utilizadores estão a exportar ficheiros a partir de uma aplicação empresarial como a Dynamics, SAP ou a Salesforce. Neste cenário, a empresa de grande dimensão *ABC* compra a nova aplicação da *CoolApp*, pelo que a equipa da *CoolApp* precisa de implementar a sua solução no ambiente da empresa *ABC*. 

![Fluxo de exemplo para criar uma chave simétrica num inquilino diferente](../media/develop/service-app-provision.jpg)

## <a name="flow-1-coolapp-provides-a-ui-dialog-to-abc-to-implement-the-deployment"></a>Fluxo 1: *CoolApp* fornece uma caixa de diálogo da interface do Usuário para *ABC* a implementação

Assim que a *ABC* comprar a solução da *CoolApp*, o administrador de TI da *ABC* tem de criar o principal de serviço da *CoolApp* e registar a aplicação no inquilino do Azure AD da *ABC*. 

Os passos para este procedimento encontram-se descritos na secção **Criar um Principal de serviço** do artigo [Desenvolver a sua aplicação](developing-your-application.md).

![Exemplo de um elemento de IU para que o Administrador de TI possa implementar a sua aplicação](../media/develop/how-to-deploy-app-UI.png)

> [!Note]
> Para criar um Principal de Serviço num inquilino precisa de ter direitos de administrador do inquilino

Em seguida, o administrador de TI da *ABC* lança a aplicação da *CoolApp* como um serviço no respetivo ambiente e incorpora os detalhes para que a aplicação da *CoolApp* possa funcionar, tais como: o ID da aplicação, o ID do inquilino e a chave simétrica.

Se a experiência pretendida não tiver como objetivo fornecer ao administrador de TI da *ABC* uma caixa de diálogo de IU para introduzir as informações do principal de serviço, então o **Fluxo 2** será o método a seguir.

## <a name="flow-2-abc-it-administrator-provides-the-key-to-the-coolapp-team"></a>Fluxo 2: *ABC* administrador de TI fornece a chave para o *CoolApp* equipe

Assim que o Administrador de TI da *ABC* criar o principal de serviço, conforme exemplificado na **Figura 1**, a *ABC* irá fornecer as informações à equipa da *CoolApp*. Em seguida, a equipa da *CoolApp* irá incorporar essas informações na aplicação da *CoolApp* para serem utilizadas pelo inquilino da *ABC*.
