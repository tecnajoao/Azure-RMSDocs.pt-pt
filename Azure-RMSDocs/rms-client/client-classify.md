---
title: Classificar ficheiros e e-mails utilizando o Azure Information Protection
description: Instruções como classificar os documentos e e-mails.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 11/20/2017
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: d65c7690-fab7-4823-845c-8c73903e9c79
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: 0d3abf33ada7c639c1e7b0bad67c36636a9a0951
ms.sourcegitcommit: dbbfadc72f4005f81c9f28c515119bc3098201ce
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/28/2018
---
# <a name="user-guide-classify-a-file-or-email-by-using-azure-information-protection"></a>Guia do utilizador: Classificar um ficheiro ou e-mail utilizando o Azure Information Protection

>*Aplica-se a: serviços de gestão de direitos do Active Directory [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 com SP1*

> [!NOTE]
> Utilize estas instruções para ajudá-lo classificar (mas não proteger) seus documentos e e-mails. Se precisar de também proteger os seus documentos e e-mails, consulte o [classificar e proteger instruções](client-classify-protect.md). Se não tem a certeza de que conjunto de instruções para utilizar, consulte o seu administrador ou suporte técnico.

A forma mais fácil para classificar os documentos e e-mails é quando estiver a criar ou editá-los a partir de dentro das aplicações de ambiente de trabalho do Office: **Word**, **Excel**, **PowerPoint**,  **Outlook**. 

No entanto, também pode classificar ficheiros utilizando **Explorador de ficheiros**. Este método suporta tipos de ficheiro adicionais e é uma forma conveniente para classificar vários ficheiros de uma só vez. 

## <a name="using-office-apps-to-classify-your-documents-and-emails"></a>Utilizar aplicações do Office para classificar os documentos e e-mails

Utilize a barra do Azure Information Protection e selecione uma das etiquetas que tenha sido configurada para si. 

Por exemplo, a imagem seguinte mostra que o documento ainda não foi etiquetado porque a **Sensibilidade** indica **Não definido**. Para definir uma etiqueta, tais como "Geral", clique em **geral**. Se não estiver certo sobre que etiqueta aplicar ao e-mail ou documento atual, utilize as descrições de etiquetas para saber mais sobre cada etiqueta e quando a aplicar. 

![Exemplo de barra do Azure Information Protection](../media/info-protect-bar-not-set-callout.png)

Se uma etiqueta já estiver aplicada ao documento e pretender alterá-la, poderá selecionar uma diferente. Se as etiquetas não forem apresentadas na barra, clique primeiro no ícone **Editar Etiqueta**, junto ao valor da etiqueta atual.

> [!TIP]
> Também pode selecionar etiquetas do **proteger** no botão de **ficheiro** separador.

Além de selecionar etiquetas manualmente, as etiquetas também podem ser aplicadas das seguintes formas:

- O administrador configurou uma etiqueta predefinida, que pode manter ou alterar.

- O administrador configurou pedidos recomendados para selecionar uma etiqueta específica quando são detetados dados confidenciais. Pode aceitar a recomendação (e a etiqueta é aplicada) ou rejeitá-la (não é aplicada a etiqueta recomendada).

### <a name="exceptions-for-the-azure-information-protection-bar"></a>Exceções para a barra do Azure Information Protection 

##### <a name="dont-see-this-information-protection-bar-in-your-office-apps"></a>Não vê esta barra do Information Protection nas suas aplicações do Office?

- Poderá não ter o cliente Azure Information Protection [instalado](install-client-app.md).

- Ter o cliente instalado, mas o administrador configurou uma definição de que não apresenta a barra. Em vez disso, selecione as etiquetas do **proteger** no botão de **ficheiro** separador a partir do friso Office. 

##### <a name="is-the-label-that-you-expect-to-see-not-displayed-on-the-bar"></a>A etiqueta que pretende ver não é apresentada na barra? 

- Se o administrador tiver configurado recentemente uma nova etiqueta para si, experimente fechar todas as instâncias da sua aplicação do Office e voltar a abrir-la. Esta ação verifica se as suas etiquetas sofreram alguma alteração.

- A etiqueta pode estar numa política de âmbito que não inclui a sua conta. Contacte o suporte técnico ou o administrador.


## <a name="using-file-explorer-to-classify-files"></a>Utilizar o Explorador de ficheiros para classificar ficheiros

Quando utilizar o Explorador de ficheiros, rapidamente pode classificar um ficheiro único, vários ficheiros ou uma pasta. 

Quando seleciona uma pasta, todos os ficheiros nessa pasta e eventuais subpastas tem são selecionadas automaticamente para a classificação que definir. No entanto, os novos ficheiros que criar nessa pasta ou nas subpastas não são automaticamente classificados.

Quando utilizar o Explorador de ficheiros para classificar os ficheiros, se um ou mais das etiquetas aparecem desativadas, os ficheiros que selecionou não suportam a classificação sem também protegendo-os.

O Guia do administrador contém uma lista completa dos tipos de ficheiros que suportam a classificação sem proteção: [tipos suportados apenas para classificação de ficheiros](client-admin-guide-file-types.md#file-types-supported-for-classification-only).

### <a name="to-classify-a-file-by-using-file-explorer"></a>Para classificar um ficheiro ao utilizar o Explorador de ficheiros

1. No Explorador de Ficheiros, selecione o ficheiro, vários ficheiros ou uma pasta. Clique com o botão direito do rato e selecione **Classificar e proteger**. Por exemplo:
    
    ![No Explorador de Ficheiros, clique com o botão direito do rato em Classificar e proteger ao utilizar o Azure Information Protection](../media/right-click-classify-protect-folder.png)

2. No **classificar e proteger - Azure Information Protection** caixa de diálogo, utilize as etiquetas como seriam feito numa aplicação do Office, que define a classificação, conforme definido pelo seu administrador. 
    
    Se nenhuma das etiquetas pode ser seleccionada (aparecem desativadas): O ficheiro selecionado não suporta a classificação. Por exemplo:
    
    ![Não há etiquetas disponíveis na caixa de diálogo Classificar e proteger – Azure Information Protection**](../media/info-protect-dialog-labels-dimmed.png)

3. Se tiver selecionado um ficheiro que não suporta a classificação, clique em **fechar**. Não é possível classificar este ficheiro sem também a protegê-lo.
    
    Se tiver selecionado uma etiqueta, clique em **aplicar** e aguarde que o **trabalho concluído** mensagem para ver os resultados. Em seguida, clique em **Fechar**.

Se mudar de ideias sobre a etiqueta que escolheu, basta repetir este processo e escolha outra etiqueta.

A classificação que especificou permanece com o ficheiro, mesmo que o ficheiro de e-mail ou guarde-o para outra localização. 
## <a name="other-instructions"></a>Outras instruções
Pode obter mais instruções sobre os procedimentos no guia do utilizador do Azure Information Protection:

- [O que pretende fazer?](client-user-guide.md#what-do-you-want-to-do)

## <a name="additional-information-for-administrators"></a>Informações adicionais para administradores    
Consulte [configurar a política do Azure Information Protection](../deploy-use/configure-policy.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
