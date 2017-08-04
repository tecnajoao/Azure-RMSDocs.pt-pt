---
title: "Configurar a política do Azure Information Protection"
description: "Para configurar a classificação, a etiquetagem e a proteção, tem de configurar a política do Azure Information Protection."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 07/31/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: ba0e8119-886c-4830-bd26-f98fb14b2933
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: 88843833b87eb054f534a7c85e6a7c2e52797e9b
ms.sourcegitcommit: 55a71f83947e7b178930aaa85a8716e993ffc063
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/31/2017
---
# <a name="configuring-azure-information-protection-policy"></a>Configurar a política do Azure Information Protection

>*Aplica-se a: Azure Information Protection*

Para configurar a classificação, a etiquetagem e a proteção, tem de configurar a política do Azure Information Protection. Esta política é, em seguida, transferida para computadores que têm instalado o [cliente do Azure Information Protection](https://www.microsoft.com/en-us/download/details.aspx?id=53018).

## <a name="subscription-support"></a>Suporte da subscrição

A política do Azure Information Protection suporta diferentes níveis de subscrições:

- Azure Information Protection P2: suporte para todas as funcionalidades de classificação, etiquetagem e proteção.

- Azure Information Protection P1: suporte para a maioria das funcionalidades de classificação, etiquetagem e proteção, mas não para classificação automática ou HYOK.

- Office 365 que inclui o serviço Azure Rights Management: suporte para proteção, mas não para classificação e etiquetagem.

As opções que exigem uma subscrição do Azure Information Protection P2 estão agora identificadas no portal.

Se tiver uma mistura de subscrições para os utilizadores do seu inquilino, é da sua responsabilidade assegurar-se de que a política do Azure Information Protection que os utilizadores transferem não contém opções de configuração para as quais a respetiva conta não tem licença de utilização. Ao configurar opções para as quais nem todos os utilizadores têm uma licença, utilize políticas de âmbito, para que os utilizadores que não estão configurados utilizem as funcionalidades para os quais têm uma licença.

Para obter mais informações sobre as subscrições, veja [De que subscrição preciso para o Azure Information Protection e que funcionalidades estão incluídas?](../get-started/faqs.md#what-subscription-do-i-need-for-azure-information-protection-and-what-features-are-included)

Para obter mais informações sobre como configurar políticas de âmbito, veja [Como configurar a política para utilizadores específicos com políticas de âmbito](configure-policy-scope.md).

## <a name="how-to-configure-the-azure-information-protection-policy"></a>Como configurar a política do Azure Information Protection

1. Numa nova janela de browser, inicie sessão no [portal do Azure](https://portal.azure.com) como administrador de segurança ou administrador global.

2. Navegue para o painel **Azure Information Protection**: por exemplo, no menu do hub, clique em **Mais serviços** e comece a escrever **Information Protection** na caixa Filtro. Na lista de resultados, selecione **Azure Information Protection**. 
    
    Ao ligar ao serviço pela primeira vez, a página **Início rápido** abre-se automaticamente. Para configurar a política que todos os utilizadores obtêm, clique em **Política global** para abrir o painel **Política: Global**. Este painel é aberto automaticamente para ligações subsequentes ao serviço, para ver e editar a política global que todos os utilizadores obtêm. 
    
    A política do Azure Information Protection contém os elementos seguintes que pode configurar:
    
    - Etiquetas que permitem tanto a si como aos utilizadores classificar documentos e e-mails.
    
    - Título e descrição para a barra Information Protection que os utilizadores veem nas aplicações do Office.
    
    - A opção para impor a classificação quando os utilizadores guardam documentos e enviam e-mails.
    
    - A opção para definir uma etiqueta predefinida como ponto de partida para classificar documentos e e-mails.
    
    - A opção para solicitar aos utilizadores que indiquem um motivo quando estes selecionam uma etiqueta que tem um nível de sensibilidade inferior ao original.
    
    - A opção para etiquetar automaticamente uma mensagem de e-mail com base nos respetivos anexos.
    
    - A opção para fornecer uma ligação de ajuda personalizada para os utilizadores.

O Azure Information Protection tem uma [política predefinida](configure-policy-default.md) que contém cinco etiquetas principais. Estas etiquetas podem ser utilizadas com o intervalo de dados completo que uma organização normalmente cria e armazena, desde a classificação mais baixa de dados pessoais à classificação mais elevada de dados altamente confidenciais. 

Pode utilizar as etiquetas predefinidas sem alterações ou pode personalizá-las, eliminá-las ou criar novas etiquetas. Para obter mais informações, utilize as ligações na próxima secção, para o ajudar a encontrar as opções relevantes e como as configurar. 

Quando efetuar alterações num painel do Azure Information Protection, clique em **Guardar** para guardar as alterações ou clique em **Eliminar** para reverter para as últimas definições guardadas. 

Quando terminar de efetuar as alterações que pretende, clique em **Publicar**. 

O cliente do Azure Information Protection verifica se existem alterações sempre que uma das aplicações do Office suportada é iniciada e transfere as alterações como política do Azure Information Protection mais recente. Acionadores adicionais que atualizam a política do cliente:

- Clique com o botão direito do rato para classificar e proteger um ficheiro ou uma pasta.

- Execução dos [cmdlets do PowerShell](../rms-client/client-admin-guide-powershell.md) para etiquetagem e proteção (Get-AIPFileStatus, Set-AIPFileClassification e Set-AIPFileLabel).

- A cada 24 horas.

>[!NOTE]
>Quando o cliente transferir a política, poderá ter de aguardar alguns minutos até que fique totalmente operacional. O tempo em questão varia devido a fatores como o tamanho e a complexidade da configuração da política e a conectividade de rede. Se a ação resultante das suas etiquetas não corresponder às suas alterações mais recentes, aguarde 15 minutos e tente novamente.

### <a name="configuring-your-organizations-policy"></a>Configurar a política da organização

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

- [Como configurar e gerir modelos](configure-policy-templates.md)

- [Como configurar etiquetas para diferentes idiomas](configure-policy-languages.md)

## <a name="next-steps"></a>Próximos passos

Para obter um exemplo de como personalizar a política predefinida e ver o comportamento resultante de uma aplicação do Office, experimente o [Tutorial de início rápido do Azure Information Protection](../get-started/infoprotect-quick-start-tutorial.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
