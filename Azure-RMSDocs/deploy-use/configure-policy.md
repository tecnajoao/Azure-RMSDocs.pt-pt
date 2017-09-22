---
title: "Configurar a política do Azure Information Protection"
description: "Para configurar a classificação, a etiquetagem e a proteção, tem de configurar a política do Azure Information Protection."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 08/07/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: ba0e8119-886c-4830-bd26-f98fb14b2933
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: 4c656ed4e7fdb7945b6ccf466a1138cdb68a2189
ms.sourcegitcommit: f7ef0f040ae4af4bf1283ebcb0750b65b6939313
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-the-azure-information-protection-policy"></a>Configurar a política do Azure Information Protection

>*Aplica-se a: Azure Information Protection*

Para configurar a classificação, a etiquetagem e a proteção, tem de configurar a política do Azure Information Protection. Esta política é, em seguida, transferida para computadores que têm instalado o [cliente do Azure Information Protection](https://www.microsoft.com/en-us/download/details.aspx?id=53018).

## <a name="subscription-support"></a>Suporte da subscrição

O Azure Information Protection suporta diferentes níveis de subscrições:

- Azure Information Protection P2: suporte para todas as funcionalidades de classificação, etiquetagem e proteção.

- Azure Information Protection P1: suporte para a maioria das funcionalidades de classificação, etiquetagem e proteção, mas não para classificação automática ou HYOK.

- Office 365 que inclui o serviço Azure Rights Management: suporte para proteção, mas não para classificação e etiquetagem.

As opções que necessitam de uma subscrição do Azure Information Protection P2 são identificadas no portal.

Se a sua organização tem uma combinação de subscrições, é da responsabilidade do cliente, certifique-se de que os utilizadores não a utilizar funcionalidades que a conta não está licenciada para utilizar. O Azure Information Protection does de cliente não licenças verificação e de imposição. Quando configurar as opções que nem todos os utilizadores possuem uma licença para, utilize confinada políticas ou de uma definição de registo para se certificar de que a sua organização permanece em conformidade com as suas licenças:

- **Quando a sua organização tem uma combinação de licenças do Azure Information Protection P1 e Azure Information Protection P2**: para utilizadores que tenham um P2 de licença, criar e utilizar um ou mais [âmbito políticas](configure-policy-scope.md) quando configurar as opções que requerem uma licença do Azure Information Protection P2. Certifique-se de que a política global não contém opções que requerem uma licença do Azure Information Protection P2.

- **Quando a sua organização tem uma subscrição do Azure Information Protection, alguns utilizadores tem apenas uma licença para o Office 365 que inclui o serviço Azure Rights Management, mas**: para os utilizadores que não possuem uma licença para o Azure Information Protection, Edite o registo nos respetivos computadores para não transferir política do Azure Information Protection. Para obter instruções, consulte o guia de administração para a personalização seguinte: [impor proteção-modo só de quando a sua organização tiver uma mistura de licenças](../rms-client/client-admin-guide-customizations.md#enforce-protection-only-mode-when-your-organization-has-a-mix-of-licenses).

Para obter mais informações sobre as subscrições, veja [De que subscrição preciso para o Azure Information Protection e que funcionalidades estão incluídas?](../get-started/faqs.md#what-subscription-do-i-need-for-azure-information-protection-and-what-features-are-included)


## <a name="how-to-configure-the-azure-information-protection-policy"></a>Como configurar a política do Azure Information Protection

1. Numa nova janela de browser, inicie sessão no [portal do Azure](https://portal.azure.com) como administrador de segurança ou administrador global.

2. Navegue para o painel **Azure Information Protection**: por exemplo, no menu do hub, clique em **Mais serviços** e comece a escrever **Information Protection** na caixa Filtro. Na lista de resultados, selecione **Azure Information Protection**. 
    
    Na primeira vez que se ligar ao serviço, o **Azure Information Protection - início rápido** automaticamente é aberto o painel. Para configurar a política que todos os utilizadores obtêm, do **políticas** selecção de menu, selecione **política Global** para abrir o **Azure Information Protection - política Global** painel. Este painel é aberto automaticamente para ligações subsequentes ao serviço, para ver e editar a política global que todos os utilizadores obtêm. 
    
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
