---
title: Classificar e proteger um ficheiro ou e-mail com o Azure Information Protection | Azure Information Protection
description: "Instruções sobre como classificar e proteger os seus documentos e e-mails."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 75268245-6f14-4218-b904-202f63fb3ce6
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: e6d4cc50259b9d9bb73a75c648f9e6915562accf
ms.openlocfilehash: e1d61fbe1d74a4a57d9a1fdf518aeb0242d0f7ad


---

# <a name="classify-and-protect-a-file-or-email-by-using-azure-information-protection"></a>Classificar e proteger um ficheiro ou e-mail com o Azure Information Protection

>*Aplica-se a: Serviços de Gestão de Direitos do Active Directory, Azure Information Protection, Windows 10, Windows 8.1, Windows 8 e Windows 7 com SP1*

**[Esta versão do cliente está em pré-visualização e está sujeita a alterações.]**

A forma mais fácil de classificar e proteger os seus documentos e e-mails é durante a criação ou edição nas aplicações de ambiente de trabalho do Office: **Word**, **Excel**, **PowerPoint** e **Outlook**. 

No entanto, também pode classificar e proteger ficheiros com o **Explorador de Ficheiros**, que suporta outros tipos de ficheiros e é uma forma conveniente de classificar e proteger vários ficheiros ao mesmo tempo.

## <a name="using-office-apps-to-classify-and-protect-your-documents-and-emails"></a>Utilizar aplicações do Office para classificar e proteger os seus documentos e e-mails

Utilize a barra do Azure Information Protection e selecione uma das etiquetas que tenha sido configurada para si. Por exemplo:

![Exemplo de barra do Azure Information Protection](../media/info-protect-bar-not-set-callout.png)


## <a name="using-file-explorer-to-classify-and-protect-files"></a>Utilizar o Explorador de Ficheiros para classificar e proteger ficheiros

Quando utiliza o Explorador de Ficheiros, pode rapidamente classificar e proteger um ficheiro único, vários ficheiros ou uma pasta. 

Quando seleciona uma pasta, todos os ficheiros nessa pasta e eventuais subpastas são automaticamente selecionados para as opções de proteção e classificação que definiu. No entanto, os novos ficheiros que criar nessa pasta ou subpastas não são configurados automaticamente com essas opções.

Quando utiliza o Explorador de Ficheiros para classificar e proteger os seus ficheiros, poderá notar que as etiquetas não estão sempre disponíveis. Tal acontece quando os ficheiros que selecionou não suportam classificação. No caso desses ficheiros, poderá selecionar uma etiqueta apenas se o administrador tiver configurado a etiqueta para aplicar proteção. Em alternativa, pode especificar as suas próprias definições de proteção. 

Para obter uma lista dos tipos de ficheiros suportados no Explorador de Ficheiros, veja a secção [Tipos de ficheiros suportados para classificação e proteção](#file-types-supported-for-classification-and-protection) nesta página.


### <a name="to-classify-and-protect-a-file-by-using-file-explorer"></a>Para classificar e proteger ficheiros com o Explorador de Ficheiros

1.  No Explorador de Ficheiros, selecione o ficheiro, vários ficheiros ou uma pasta. Clique com o botão direito do rato e selecione **Classificar e proteger (pré-visualização)**. 

2. Na caixa de diálogo **Classificar e proteger – Azure Information Protection**, utilize as etiquetas como faria numa aplicação do Office, o que define a classificação e a proteção, conforme definido pelo seu administrador. Se não puder selecionar uma etiqueta (se estiver indisponível), o ficheiro selecionado não suportará a classificação, mas poderá protegê-lo.

3. Para proteger o ficheiro, escolha entre as definições de proteção que o administrador definiu para a etiqueta selecionada (**Automático, com base na etiqueta de classificação selecionada**) ou especifique as suas próprias definições (**Substituir com permissões personalizadas**).
    
    A opção de substituição não utiliza quaisquer definições de proteção que o administrador poderá ter definido para a etiqueta escolhida. Em vez disso, pode especificar as suas próprias definições de proteção. 

4. Se tiver selecionado a opção de substituição, especifique o seguinte:

    - **Selecionar permissões**: selecione o nível de acesso que pretende que as pessoas tenham quando protege o ficheiro ou ficheiros selecionados.
    
    - **Selecionar utilizadores**: especifique as pessoas que devem ter as permissões que selecionou para o seu ficheiro ou ficheiros. Pode utilizar o livro de endereços para pesquisar e selecionar as pessoas e os grupos na sua organização. Para pessoas noutra organização, tem de especificar o endereço de e-mail completo. Verifique que utiliza um endereço de e-mail profissional, uma vez que os endereços de e-mail pessoais não são atualmente suportados.
        
    - **Expirar acesso**: selecione esta opção apenas para ficheiros sensíveis ao tempo para que as pessoas que especificou não consigam abrir o ficheiro ou ficheiros selecionados após uma data especificada. Ainda poderá abrir o ficheiro original, mas, após a meia-noite (o seu fuso horário atual), no dia que selecionou, as pessoas especificadas não poderão abrir o ficheiro.

5. Clique em **Aplicar** e, em seguida, em **Fechar**.

O ficheiro ou ficheiros selecionados estão agora classificados e protegidos, de acordo com as suas seleções. Em alguns casos (quando a adição de proteção altera a extensão de nome de ficheiro), o ficheiro original no Explorador de Ficheiros é substituído por um novo ficheiro que tem o ícone de cadeado do Azure Information Protection. Por exemplo:

![Ficheiro protegido com o ícone de cadeado do Azure Information Protection](../media/Pfile.png)

Se mudar de ideias sobre a classificação e proteção, ou precisar de modificar as definições posteriormente, repita simplesmente este processo com as suas novas definições.

A classificação e proteção que especificou permanecem com o ficheiro, mesmo que o envie por e-mail ou o guarde noutra localização. Se tiver protegido o ficheiro, pode controlar a forma como as pessoas estão a utilizá-lo e, se necessário, revogar o acesso ao mesmo. Para obter mais informações, veja [Controlar e revogar os documentos protegidos quando utiliza o Azure Information Protection](client-track-revoke.md). 

#### <a name="file-types-supported-for-classification-and-protection"></a>Tipos de ficheiros suportados para classificação e proteção

Os seguintes tipos de ficheiros suportam apenas a classificação. Outros tipos de ficheiros suportam a classificação quando também estão protegidos.

- **Microsoft Visio**: vsdx, .vsdm, .vssx, .vssm, .vsd, .vdw, .vst

- **Microsoft Project**: .mpp, .mpt

- **Microsoft Publisher**: .pub

- **Microsoft Office 97, Office 2010, Office 2003**: .xls, .xlt, .doc, .dot, .ppt, .pps, .pot

- **Microsoft XPS**: .xps .oxps

- **Imagens**: .jpg, .jpe, .jpeg, .jif, .jfif, .jfi.png, .tif, .tiff

- **SolidWorks**: .sldprt, .slddrw, .sldasm

- **Design Review 2013 da Autodesk**: .dwfx

- **Adobe Photoshop**: .psd

- **Digital Negative**: .dng


A proteção com o serviço Rights Management é suportada para os tipos de ficheiros documentados na [configuração da API de Ficheiros](../develop/file-api-configuration.md). Esta proteção pode ser aplicada automaticamente ao selecionar uma etiqueta que o seu administrador tenha configurado ou pode especificar as suas próprias definições de proteção com [níveis de permissão](../deploy-use/configure-usage-rights.md#rights-included-in-permissions-levels). 


## <a name="other-instructions"></a>Outras instruções
Para obter instruções sobre os procedimentos, veja as secções seguintes do guia do utilizador do Azure Information Protection:

-   [O que pretende fazer?](client-user-guide.md#what-do-you-want-to-do)




<!--HONumber=Dec16_HO1-->


