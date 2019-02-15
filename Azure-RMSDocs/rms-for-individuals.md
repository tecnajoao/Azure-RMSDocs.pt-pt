---
title: RMS para indivíduos e Azure Information Protection
description: Informações sobre o RMS para indivíduos, uma subscrição self-service gratuita para os utilizadores que foram enviados os ficheiros protegidos, mas estes utilizadores não podem ser autenticados porque o respetivo departamento de TI não gere uma conta para os mesmos no Azure.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 11/02/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 2efcb440-fefd-45e9-872b-f471573aadf2
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 947461f31c6c9d8ef8a97d07c78370153169af03
ms.sourcegitcommit: a78d4236cbeff743703c44b150e69c1625a2e9f4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/14/2019
ms.locfileid: "56252445"
---
# <a name="rms-for-individuals-and-azure-information-protection"></a>RMS para indivíduos e Azure Information Protection

>*Aplica-se a: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

RMS para indivíduos é uma subscrição self-service gratuita para usuários que precisam para abrir ficheiros que foram protegidos pelo Azure Information Protection. Se estes utilizadores não podem ser autenticados pelo Azure Active Directory, este serviço de inscrição gratuito pode criar uma conta no Azure Active Directory para um utilizador. Como resultado, estes utilizadores podem autenticar-se com o respetivo endereço de e-mail da empresa e, em seguida, leia os ficheiros protegidos em computadores ou dispositivos móveis.

RMS para indivíduos utiliza a inscrição self-service do Azure Active Directory. Se os utilizadores criaram contas para a sua organização ao utilizar esta subscrição, como um administrador para a sua organização, pode reclamar propriedade e [assuma o controle de suas contas](/azure/active-directory/users-groups-roles/domains-admin-takeover#external-admin-takeover). 


> [!NOTE]
> Esta subscrição gratuita é uma opção para ajudar a garantir que as pessoas autorizadas fora da sua organização podem sempre ler ficheiros que protege a sua organização. Outra opção consiste em documentos de e-mail através de [encriptação de mensagens do Office 365 com os novos recursos](https://support.office.com/article/7ff0c040-b25c-4378-9904-b1b50210d00e). Esta solução de correio eletrónico funciona para todos os endereços de e-mail em todos os dispositivos e é a forma recomendada para partilhar informações de maneira segura e ver documentos do Office num navegador com pessoas fora da sua organização.
> 
> Outra opção é usar contas Microsoft. No entanto, nem todos os aplicativos podem abrir conteúdo protegido, quando uma conta Microsoft é utilizada para autenticação. [Mais informações](secure-collaboration-documents.md#supported-scenarios-for-opening-protected-documents) 

Para se inscrever nesta conta gratuita, os utilizadores aceder a [página do Microsoft Azure Information Protection](https://aka.ms/rms-signup)e fornecer o respetivo endereço de e-mail de trabalho. Eles recebem um e-mail na resposta da Microsoft e, em seguida, eles podem concluir o processo de inscrição, introduzindo os detalhes para criar a conta. 

Quando a conta é criada, a última página apresenta ligações para transferir o cliente do Azure Information Protection ou visualizador para diferentes dispositivos, uma ligação para o guia de utilizador e uma ligação para a lista atual de aplicações que suportam nativamente a proteção do Rights Management. 

## <a name="to-sign-up-for-rms-for-individuals"></a>Para se inscrever no RMS para indivíduos

1. Num computador Windows ou Mac ou num dispositivo móvel, aceda à [página do Microsoft Azure Information Protection](https://aka.ms/rms-signup).

2. Escreva o endereço de e-mail que foi utilizado para proteger o documento que tem de abrir.

3. Clique em **Inscrever-se**.

    A Microsoft utiliza o seu endereço de e-mail para verificar se a sua organização já tem um [subscrição Premium do Azure Information Protection](https://www.microsoft.com/cloud-platform/azure-information-protection-pricing) ou um [subscrição do Office 365 que inclui proteção de dados ao utilizar o Azure Proteção de informações](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf). Se for encontrada qualquer uma destas subscrições, não precisa do RMS para indivíduos. Tem sessão iniciada imediatamente e a inscrição self-service para o RMS para indivíduos é cancelada. Se não for encontrada uma destas subscrições, continue para o passo seguinte.

4. Aguarde que uma mensagem de e-mail de confirmação seja enviada para o endereço que especificou. Esta será enviada pela Equipa do Office 365 (support@email.microsoftonline.com) com o assunto **Concluir a sua inscrição no Microsoft Azure Information Protection**.

5. Quando receber o e-mail, clique em **Sim, sou eu** para verificar o seu endereço de e-mail e concluir o processo de inscrição.

6. Verá a página **Mais uma coisa...**, onde pode fornecer os detalhes da sua conta. Escreva o seu nome próprio, o seu apelido, introduza e confirme uma palavra-passe à sua escolha e, em seguida, clique em **Iniciar**.

7. Quando a conta é criada, verá uma nova página Microsoft Azure Information Protection, onde pode transferir e instalar o cliente do Azure Information Protection ou clique nas [Guia do usuário](./rms-client/client-user-guide.md) ligação para instruções sobre como proceder para Windows computadores.

Agora sua conta é criada, se lhe for pedido para iniciar sessão ler ficheiros protegidos, introduza o mesmo endereço de e-mail e a palavra-passe que utilizou para criar a conta do RMS para indivíduos.

> [!IMPORTANT]
> Embora também agora pode proteger ficheiros com esta conta, não efetuar este procedimento até que a sua organização tem um [subscrição de avaliação ou paga](https://azure.microsoft.com/pricing/details/information-protection/) do Azure Information Protection. Se proteger ficheiros e e-mails ao utilizar esta subscrição gratuita e, em seguida, sua organização assume o controlo da sua conta, conteúdo anteriormente protegido pode tornar-se inacessível.


## <a name="next-steps"></a>Passos Seguintes
RMS para indivíduos é um exemplo de como utilizar a inscrição self-service, que é suportada pelo Azure Active Directory. Para obter mais informações sobre como isto funciona, consulte [o que é a inscrição Self-Service do Azure Active Directory?](/azure/active-directory/users-groups-roles/directory-self-service-signup) na documentação do Azure Active Directory.

