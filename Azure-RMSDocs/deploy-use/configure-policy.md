---
title: "Configurar a política do Azure Information Protection"
description: "Para configurar a classificação, a etiquetagem e a proteção, tem de configurar a política do Azure Information Protection."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 04/25/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: ba0e8119-886c-4830-bd26-f98fb14b2933
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: 8b6bd6e44fb39c3787e2fe63577c7e7fd9948025
ms.sourcegitcommit: d814d2876cf56e8fff0b107a5e3ec6df2aeda9ae
translationtype: HT
---
# <a name="configuring-azure-information-protection-policy"></a>Configurar a política do Azure Information Protection

>*Aplica-se a: Azure Information Protection*

Para configurar a classificação, a etiquetagem e a proteção, tem de configurar a política do Azure Information Protection. Esta política é, em seguida, transferida para computadores que têm instalado o [cliente do Azure Information Protection](https://www.microsoft.com/en-us/download/details.aspx?id=53018).

Para configurar a política do Azure Information Protection:

1. Numa nova janela de browser, inicie sessão no [portal do Azure](https://portal.azure.com) como administrador de segurança ou administrador global.

2. Navegue para o painel **Azure Information Protection**: por exemplo, no menu do hub, clique em **Mais serviços** e comece a escrever **Information Protection** na caixa Filtro. Na lista de resultados, selecione **Azure Information Protection**. 

    Quando o painel **Azure Information Protection** é carregado, é apresentado automaticamente o painel **Política: Global**, onde pode ver e editar a política global que todos os utilizadores têm. Contudo, opcionalmente, também pode adicionar e editar as políticas de âmbito. As políticas do Azure Information Protection contêm os elementos seguintes que pode configurar:

    - Etiquetas que permitem tanto a si como aos utilizadores classificar documentos e e-mails.

    - Título e descrição para a barra Information Protection que os utilizadores veem nas aplicações do Office.

    - A opção para impor a classificação quando os utilizadores guardam documentos e enviam e-mails.

    - A opção para definir uma etiqueta predefinida como ponto de partida para classificar documentos e e-mails.

    - A opção para solicitar aos utilizadores que indiquem um motivo quando estes selecionam uma etiqueta que tem um nível de sensibilidade inferior ao original.

    - A opção para etiquetar automaticamente uma mensagem de e-mail com base nos respetivos anexos.

    - A opção para fornecer uma ligação de ajuda personalizada para os utilizadores.

O Azure Information Protection tem uma [política predefinida](configure-policy-default.md) que contém cinco etiquetas principais. Estas etiquetas podem ser utilizadas com o intervalo de dados completo que uma organização normalmente cria e armazena, desde a classificação mais baixa de dados pessoais à classificação mais elevada de dados altamente confidenciais. Pode utilizar as etiquetas predefinidas sem alterações ou pode personalizá-las, eliminá-las ou criar novas etiquetas.

Quando efetuar alterações num painel do Azure Information Protection, clique em **Guardar** para guardar as alterações ou clique em **Eliminar** para reverter para as últimas definições guardadas. 

Quando terminar de efetuar as alterações que pretende, clique em **Publicar**. 

O cliente do Azure Information Protection verifica se existem alterações sempre que uma das aplicações do Office suportada é iniciada e transfere as alterações como política do Azure Information Protection mais recente. Acionadores adicionais que atualizam a política do cliente:

- Clique com o botão direito do rato para classificar e proteger um ficheiro ou uma pasta.

- Execução dos cmdlets do PowerShell para etiquetagem e proteção (Get-AIPFileStatus e Set-AIPFileLabel).

- A cada 24 horas.


## <a name="configuring-your-organizations-policy"></a>Configurar a política da organização

Utilize as seguintes informações para ajudar a configurar a política do Azure Information Protection:

- [Política do Information Protection predefinida](configure-policy-default.md)

- [Como configurar as definições de política](configure-policy-settings.md)

- [Como criar uma nova etiqueta](configure-policy-new-label.md)

- [Como eliminar ou reordenar uma etiqueta](configure-policy-delete-reorder.md)

- [Como alterar ou personalizar uma etiqueta existente](configure-policy-change-label.md)

- [Como configurar uma etiqueta para proteção](configure-policy-protection.md)

- [Como configurar uma etiqueta para aplicar marcações visuais](configure-policy-markings.md)

- [Como configurar condições para as classificações automática e recomendada](configure-policy-classification.md)

- [Como configurar a política para utilizadores específicos com políticas de âmbito](configure-policy-scope.md)

## <a name="next-steps"></a>Próximos passos

Para obter um exemplo de como personalizar a política predefinida e ver o comportamento resultante de uma aplicação do Office, experimente o [Tutorial de início rápido do Azure Information Protection](../get-started/infoprotect-quick-start-tutorial.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
