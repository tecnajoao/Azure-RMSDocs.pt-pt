---
title: RMS para indivíduos e Azure Information Protection
description: Informações sobre o RMS para indivíduos, uma subscrição gratuita personalizada para os utilizadores que foram enviados ficheiros protegidos, mas estes utilizadores não podem ser autenticados porque o respetivo departamento de TI não gere uma conta para os mesmos no Azure.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 03/19/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 2efcb440-fefd-45e9-872b-f471573aadf2
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: df2d97fd8abdf7c2f210d857287d3590838222db
ms.sourcegitcommit: affda7572064edaf9e3b63d88f4a18d0d6932b13
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/16/2018
---
# <a name="rms-for-individuals-and-azure-information-protection"></a>RMS para indivíduos e Azure Information Protection

>*Aplica-se a: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

RMS para indivíduos é uma subscrição gratuita personalizada para utilizadores que necessitam para abrir ficheiros que foram protegidos pelo Azure Information Protection. Se estes utilizadores não podem ser autenticados pelo Azure Active Directory, este serviço de inscrição gratuito pode criar uma conta no Azure Active Directory para um utilizador. Como resultado, estes utilizadores podem autenticar-se utilizando o respetivo endereço de e-mail da empresa e, em seguida, ler os ficheiros protegidos em dispositivos móveis ou computadores.

RMS para indivíduos utiliza a inscrição self-service do Azure Active Directory. Se os utilizadores criou contas para a sua organização ao utilizar esta subscrição, como um administrador para a sua organização, pode reclamar a propriedade e [assumir o controlo das respetivas contas](/active-directory/domains-admin-takeover#external-admin-takeover). 


> [!NOTE]
> Esta subscrição gratuita é uma opção para ajudar a garantir que as pessoas autorizadas fora da sua organização podem sempre ler ficheiros que protege a sua organização. Outra opção consiste em documentos de e-mail utilizando [encriptação de mensagens do Office 365 com as novas capacidades](https://support.office.com/article/7ff0c040-b25c-4378-9904-b1b50210d00e). Esta solução de correio eletrónico funciona para todos os endereços de e-mail em todos os dispositivos e é a forma recomendada de forma segura partilhar informações e ver documentos do Office por e-mail com pessoas fora da sua organização. 

Para se inscrever nesta conta gratuita, os utilizadores aceder ao [página do Microsoft Azure Information Protection](https://aka.ms/rms-signup)e forneça o respetivo endereço de e-mail de trabalho. Recebem uma mensagem de e-mail em resposta da Microsoft e, em seguida, podem concluir o processo de inscrição, introduzindo os detalhes para criar a conta. 

Quando a conta é criada, a página final apresenta ligações para transferir o cliente Azure Information Protection ou visualizador para diferentes dispositivos, uma ligação para o Guia do utilizador e uma ligação para uma lista atualizada das aplicações que suportam nativamente o proteção Rights Management. 

## <a name="to-sign-up-for-rms-for-individuals"></a>Para se inscrever no RMS para indivíduos

1. Num computador Windows ou Mac ou num dispositivo móvel, aceda à [página do Microsoft Azure Information Protection](https://aka.ms/rms-signup).

2. Escreva o endereço de e-mail que foi utilizado para proteger o documento que é necessário abrir.

3. Clique em **Inscrever-se**.

    A Microsoft utiliza o seu endereço de e-mail para verificar se a sua organização já tem um [subscrição do Azure Premium de proteção de informações (https://www.microsoft.com/cloud-platform/azure-information-protection-pricing) ou um [subscrição do Office 365 que inclui proteção de dados através da utilização de informações do Azure Proteção](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf). Se não for encontrada qualquer uma destas subscrições, não precisa do RMS para indivíduos. Tem sessão iniciada imediatamente e a inscrição self-service para o RMS para indivíduos é cancelada. Se um destas subscrições não for encontrado, continue para o passo seguinte.

4. Aguarde que uma mensagem de e-mail de confirmação seja enviada para o endereço que especificou. Esta será enviada pela Equipa do Office 365 (support@email.microsoftonline.com) com o assunto **Concluir a sua inscrição no Microsoft Azure Information Protection**.

5. Quando receber o e-mail, clique em **Sim, que é-me** para verificar se o seu endereço de e-mail e concluir o processo de inscrição.

6. Verá a página **Mais uma coisa...**, onde pode fornecer os detalhes da sua conta. Escreva o seu nome próprio, o seu apelido, introduza e confirme uma palavra-passe à sua escolha e, em seguida, clique em **Iniciar**.

7. Quando é criada a sua conta, verá uma nova página do Microsoft Azure Information Protection onde pode transferir e instalar o cliente Azure Information Protection ou clique em de [Guia do utilizador](../rms-client/client-user-guide.md) ligação para instruções sobre como proceder para computadores Windows.

Agora a conta é criada, se lhe for pedida a sessão para ler ficheiros protegidos, introduza o mesmo endereço de e-mail e a palavra-passe que utilizou para criar a conta para o RMS para indivíduos.

> [!IMPORTANT]
> Embora também agora pode proteger ficheiros com esta conta, não fazê-lo até a sua organização tem um [subscrição de avaliação ou paga](https://azure.microsoft.com/pricing/details/information-protection/) para o Azure Information Protection. Se se proteger ficheiros e e-mails com esta subscrição gratuita e, em seguida, a sua organização demora controlo da sua conta, conteúdo anteriormente protegido pode ficar inacessível.


## <a name="next-steps"></a>Próximos passos
RMS para indivíduos é um exemplo de utilização da inscrição self-service que é suportada pelo Azure Active Directory. Para obter mais informações sobre como isto funciona, consulte [O que é a Inscrição Self-Service para o Azure?](/active-directory/active-directory-self-service-signup) na documentação do Azure Active Directory.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
