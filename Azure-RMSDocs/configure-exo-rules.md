---
title: Configurar regras de fluxo de correio Exchange Online para as etiquetas do Azure Information Protection
description: Instruções e exemplos para configurar regras de fluxo de correio Exchange Online para as etiquetas do Azure Information Protection.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 02/16/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: ba4e4a4d-5280-4e97-8f5c-303907db1bf5
ms.reviewer: shakella
ms.suite: ems
ms.openlocfilehash: 0a09c4c89ffd461cb0c922cb09ee0acd3ed033be
ms.sourcegitcommit: d8cadf325472e7fc8900905305d7f583a97506b0
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/19/2019
ms.locfileid: "57829007"
---
# <a name="configuring-exchange-online-mail-flow-rules-for-azure-information-protection-labels"></a>Configurar regras de fluxo de correio Exchange Online etiquetas do Azure Information Protection

>*Aplica-se a: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Utilize as seguintes informações para ajudar a configurar as regras de fluxo de correio no Exchange Online para utilizar etiquetas do Azure Information Protection e para aplicar proteção adicional para cenários específicos. Por exemplo:

- É da sua etiqueta predefinida **gerais**, que não se aplica proteção. Para e-mails com esta etiqueta que são enviados externamente, aplicam-se a ação de proteção não reencaminhar adicional.

- Se um anexo com um **confidencial \ parceiros** etiqueta é enviado por e-mail para pessoas fora da organização e o e-mail não está protegido, aplicam-se a ação de proteção adicional de só de encriptar.

As regras de fluxo de correio que aplicam a proteção como uma ação são ignoradas, se o e-mail já está protegido. Por exemplo, uma mensagem de e-mail que foi protegida por não reencaminhar não pode ser alterada por uma regra de fluxo de correio do Exchange para utilizar a opção de criptografar apenas.  

Pode expandir estes exemplos, bem como modificá-los. Por exemplo, adicione mais condições. Para obter mais informações sobre como configurar as regras de fluxo de correio, consulte [(regras de transporte) as regras de fluxo de correio no Exchange Online](https://technet.microsoft.com/library/jj919238(v=exchg.150).aspx) na documentação do Exchange Online.

Para obter mais informações sobre como configurar as regras de fluxo de correio para encriptar mensagens de e-mail, consulte [definem as regras de fluxo de correio para encriptar mensagens de e-mail do Office 365](https://support.office.com/article/define-mail-flow-rules-to-encrypt-email-messages-in-office-365-9b7daf19-d5f2-415b-bc43-a0f5f4a585e8) na documentação do Office. 

## <a name="prerequisite-know-your-label-guid"></a>Pré-requisito: Saber a sua etiqueta de GUID

Como uma etiqueta do Azure Information Protection é armazenada nos metadados, fluxo de emails de regras no Exchange Online pode ler estas informações para mensagens e anexos de documento do Office. As regras de fluxo de correio não suportam a inspecionar os metadados de documentos PDF.

Antes de configurar as regras de fluxo de correio para identificar mensagens e documentos que estão identificados, certifique-se de que sabe o GUID da etiqueta do Azure Information Protection que pretende utilizar. 

Para obter mais informações sobre os metadados armazenados por uma etiqueta e como identificar os GUIDs de etiqueta, consulte [Etiquetar informações armazenadas em e-mails e documentos](configure-policy.md#label-information-stored-in-emails-and-documents).

## <a name="example-configurations"></a>Configurações de exemplo

Para os exemplos seguintes, crie uma nova regra de fluxo de correio, utilize os seguintes passos:

1. Num navegador da web, com uma conta escolar ou profissional que foram concedida permissões de administrador global, inicie sessão no Office 365. 

2. Escolha o mosaico **Administrador**.

3. No Centro de administração do Microsoft 365, escolha **do Centro de administração** > **Exchange**.

4. No Centro de administração do Exchange: **fluxo de correio** > **regras** > **+** > **criar uma nova regra** . 

> [!TIP]
> Se tiver problemas com a interface de utilizador quando configurar as regras, tente um browser diferente, como o Internet Explorer.

Os exemplos de ter uma condição única que aplica a proteção quando uma mensagem de e-mail é enviada fora da organização. Para obter mais informações sobre outras condições que pode selecionar, consulte [condições de regra de fluxo e exceções (predicados) de correio no Exchange Online](https://technet.microsoft.com/library/jj919235(v=exchg.150).aspx).


### <a name="example-1-rule-that-applies-the-do-not-forward-option-to-emails-that-are-labeled-general-when-they-are-sent-outside-the-organization"></a>Exemplo 1: Regra aplica-se a opção não reencaminhar para e-mails que estão identificadas **gerais** quando são enviados fora da organização

Neste exemplo, o **gerais** etiqueta tiver um GUID de 0e421e6d-ea17-4fdb-8f01-93a3e71333b8. Substitua o seu próprio etiqueta ou sublabel GUID que pretende utilizar com esta regra. 

A política do Azure Information Protection, esta etiqueta foi configurada como a etiqueta predefinida para classificar e-mails como **gerais** e a etiqueta não se aplica a proteção. 

1. Na **Name**, escreva um nome para a regra, tal como `Apply Do Not Forward for General emails sent externally`.
 
2. Para **aplicar esta regra se**: Selecione **o destinatário está localizado**, selecione **fora da organização**e, em seguida, selecione **OK**.

3. Selecione **mais opções**e, em seguida, selecione **adicionar condição**.
 
4. Para **e**: Selecione **um cabeçalho de mensagem**e, em seguida, selecione **inclui qualquer um dessas palavras**:
     
    a. Selecione **introduzir texto**e introduza `msip_labels`.
     
    b. Selecione **introduza palavras**e introduza `MSIP_Label_0e421e6d-ea17-4fdb-8f01-93a3e71333b8_Enabled=True;`
    
    c. Selecione **+** e, em seguida, selecione **OK**.

5. Para **efetue o seguinte procedimento**: Selecione **modificar a segurança da mensagem** > **aplicar encriptação de mensagens do Office 365 e direitos de proteção** > **não reencaminhar**e, em seguida, Selecione **OK**.
    
    A configuração de regra deve agora ter um aspeto semelhante ao seguinte:  ![Regra de fluxo de correio Exchange Online e configurada para uma etiqueta do Azure Information Protection - example1](./media/aip-exo-rule-ex1.png)

7. Selecione **guardar** 

Para obter mais informações sobre a opção não reencaminhar, consulte [opção não reencaminhar para e-mails](configure-usage-rights.md#do-not-forward-option-for-emails).

### <a name="example-2-rule-that-applies-the-encrypt-only-option-to-emails-when-they-have-attachments-that-are-labeled-confidential--partners-and-these-emails-are-sent-outside-the-organization"></a>Exemplo 2: Regra aplica-se a opção de criptografar somente a mensagens de correio eletrónico quando têm anexos que estão identificados **confidencial \ parceiros** e estes e-mails são enviados fora da organização

Neste exemplo, o **confidencial \ parceiros** subetiqueta tem um GUID de 0e421e6d-ea17-4fdb-8f01-93a3e71333b8. Substitua o seu próprio etiqueta ou sublabel GUID que pretende utilizar com esta regra. 

Esta etiqueta é utilizada para classificar e proteger os documentos que utiliza para colaboração de parceiros.   

1. Na **Name**, escreva um nome para a regra, tal como `Apply Encrypt to emails sent externally if protected attachments`.
 
2. Para **aplicar esta regra se**: Selecione **o destinatário está localizado**, selecione **fora da organização**e, em seguida, selecione **OK**.

3. Selecione **mais opções**e, em seguida, selecione **adicionar condição**.
 
4. Para **e**: Selecione **qualquer anexo**e, em seguida, selecione **tem essas propriedades, incluindo qualquer uma dessas palavras**:
     
    a. Selecione **+**  >  **especificar uma propriedade personalizada anexo**.
  
    b. Para **propriedade**, introduza `MSIP_Label_0e421e6d-ea17-4fdb-8f01-93a3e71333b8_Enabled`.
    
    c. Para **valor**, introduza `True`
    
    d. Selecione **salvar**e, em seguida, selecione **OK**.

5. Para **efetue o seguinte procedimento**: Selecione **modificar a segurança da mensagem** > **aplicar encriptação de mensagens do Office 365 e direitos de proteção** > **Encrypt**e, em seguida, selecione **OK**.
    
    A configuração de regra deve agora ter um aspeto semelhante ao seguinte:  ![Regra de fluxo de correio Exchange Online e configurada para uma etiqueta do Azure Information Protection - example1](./media/aip-exo-rule-ex2.png)

6. Selecione **guardar** 

Para obter mais informações sobre a opção de criptografar, consulte [opção de criptografar apenas para e-mails](configure-usage-rights.md#encrypt-only-option-for-emails).


## <a name="next-steps"></a>Passos Seguintes

Para obter informações sobre como criar e configurar as etiquetas para utilizar com as regras de fluxo de correio Exchange Online, consulte [política de configuração do Azure Information Protection](configure-policy.md).

Além disso, para ajudar a classificar as mensagens de e-mail que contenham anexos, considere a utilização do Azure Information Protection seguintes [definição de política](configure-policy-settings.md): **Para mensagens de e-mail com anexos, aplique uma etiqueta que corresponda à classificação mais elevada desses anexos**.


