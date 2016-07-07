---
title: "Tutorial de início rápido do Azure RMS – Passo 3 | Azure RMS"
description: "O terceiro passo de um tutorial para experimentar rapidamente o Microsoft Azure Rights Management na sua organização com apenas 5 passos que devem demorar menos de 15 minutos."
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: c604e749-8918-40e8-8148-6bd000cb2be2
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ed50d87138c428fadfd22cd5b3ef3c7f7e421848
ms.openlocfilehash: efe389db839f3f70e9cdb9138f6749e2bd2e029f


---


# Passo 3 do início rápido do Azure RMS: enviar por e-mail o documento que pretende proteger

*Aplica-se a: Azure Rights Management, Office 365*


Passar para: 
> [!div class="op_single_selector"]
- [Introdução](quick-start-tutorial.md)
- [Passo 1: ativar o Azure RMS](tutorial-step1.md)
- [Passo 2: instalar aplicação de partilha RMS](tutorial-step2.md)
- [Passo 3: enviar e-mail do documento confidencial](tutorial-step3.md)
- [Passo 4: o destinatário lê o documento](tutorial-step4.md)
- [Passo 5: controlar o documento](tutorial-step5.md)


Para este passo, comece por criar e guardar um documento através do Word que represente o documento que pretende proteger e atribua-lhe o nome **Confidential.docx**. Para este tutorial, é irrelevante o texto que de facto contém, mas é aconselhável que tenha algum texto para que possa mais facilmente confirmar que o destinatário autorizado o conseguiu ler. Por exemplo, pode introduzir: **Se conseguir ler isto no anexo de e-mail, significa que o remetente partilhou com êxito um ficheiro que foi protegido com o Azure RMS.**

Em seguida, está pronto para partilhar de forma segura este documento por e-mail.

![Passo 3 do tutorial de início rápido do Azure RMS](../media/AzRMS_Tutorial_3_Screenshots.png)

### Para partilhar de forma segura o seu documento por e-mail

1.  Ao utilizar o Outlook, crie uma nova mensagem e anexe o ficheiro que acabou de criar.

2.  Na caixa **Para**, escreva um ou mais endereços de e-mail profissionais. Certifique-se de que especifica um endereço de e-mail profissional, tal como **juliam@contoso.com** ou **p.barbosa@fabrikam.com**, porque atualmente o Azure Rights Management não suporta os endereços de e-mail pessoais que poderá utilizar em casa através do seu fornecedor de Internet. Não se preocupe se a pessoa a quem está a enviar também tem o Azure Rights Management ou não.

3.  Escreva um assunto, tal como **Documento confidencial**, em seguida, escreva uma mensagem curta no e-mail, tal como **Leia este documento confidencial e não o partilhe com outras pessoas.**

4.  Depois, no separador **Mensagem**, no grupo **RMS**, clique em **Partilhar Protegido** e, em seguida, clique em **Partilhar Protegido** novamente:

5.  Na caixa de diálogo **partilhar protegido**:

    1.  Selecione **Visualizador – Ver Apenas**.

        Isto significa que os nossos destinatários poderão visualizar o documento, mas não o poderão editar nem imprimir.

    2.  Selecione **Enviar-me um e-mail quando alguém tentar abrir estes documentos**.

        Receberá uma notificação por e-mail sempre que os destinatários tentam abrir o anexo e também se outra pessoa tentar abri-lo, por exemplo, o destinatário reencaminha a mensagem de e-mail para um colega de trabalho. Neste último cenário, verá que o acesso foi negado e, tendo em conta os detalhes do utilizador, pode decidir se envia uma cópia do documento a essa pessoa para que o possa abrir.

    3.  Selecione **Revogar instantaneamente o acesso a estes documentos**.

        Esta opção requer que os destinatários tenham ligação à Internet sempre que abrem o anexo, mas com a vantagem que se revogar o documento mais tarde, da próxima vez que o tentarem abrir, não será possível. Se não selecionar esta opção, os destinatários poderão conseguir abri-lo, mesmo sem uma ligação à Internet, mas com a desvantagem que se revogar o documento mais tarde, poderá haver um atraso na entrada em vigor da revogação.

    4.  Clique em **Enviar Agora**.

        O e-mail com anexo é enviado para os endereços de e-mail que especificou. Para além da mensagem de e-mail, os destinatários verão instruções sobre como ler o documento anexado protegido pelo Azure Rights Management.

Agora que enviou o documento protegido, pode pedir aos destinatários para o abrirem assim que o receberem. No entanto, não feche o Outlook, pois utilizá-lo-emos novamente no passo final para controlar o anexo.

|Se pretender mais informações|Informações adicionais|
|--------------------------------|--------------------------|
|Instruções completas e métodos alternativos para proteger ficheiros que partilha por e-mail|[Proteger um ficheiro que partilha por e-mail ao utilizar a aplicação de partilha Rights Management](../rms-client/sharing-app-protect-by-email.md)|
|Acerca das opções na caixa de diálogo **partilhar protegido**|[Opções da caixa de diálogo para a aplicação de partilha Rights Management](../rms-client/sharing-app-dialog-box.md)|


>[!div class="step-by-step"]
[« Passo 2](tutorial-step2.md)
[Passo 4 »](tutorial-step4.md)


<!--HONumber=Jun16_HO4-->


