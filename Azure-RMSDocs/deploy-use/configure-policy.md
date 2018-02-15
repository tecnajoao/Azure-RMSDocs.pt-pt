---
title: "Configurar a política do Azure Information Protection"
description: "Para configurar a classificação, a etiquetagem e a proteção, tem de configurar a política do Azure Information Protection."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/13/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: ba0e8119-886c-4830-bd26-f98fb14b2933
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: 6b0556755597fe20755e7b798a24498a780b87b5
ms.sourcegitcommit: c157636577db2e2a2ba5df81eb985800cdb82054
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/14/2018
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

## <a name="signing-in-to-the-azure-portal"></a>Iniciar sessão no portal do Azure

Para iniciar sessão no portal do Azure, para configurar e gerir o Azure Information Protection:

- Utilize a seguinte hiperligação: https://portal.azure.com

- Utilizar uma conta que tenha um dos seguintes [funções de administrador](/azure/active-directory/active-directory-assign-admin-roles-azure-portal):
    
    - **Administrador de proteção de informações** (atualmente em pré-visualização)

    - **Administrador de segurança**

    - **Administrador global / administrador de empresa**


## <a name="to-access-the-azure-information-protection-blade-for-the-first-time"></a>Para aceder ao painel do Azure Information Protection pela primeira vez

1. Inicie sessão no portal do Azure.

2. No menu do hub, clique em **Novo** e, em seguida, na lista **MARKETPLACE**, selecione **Security + Identity**. 
    
3. No **segurança + identidade** painel, do **aplicações em destaque** lista, selecione **Azure Information Protection**. Em seguida, no **Azure Information Protection** painel, clique em **criar**.
    
    Esta ação cria o **Azure Information Protection** painel para o seu inquilino para que a próxima vez iniciar sessão no portal, pode selecionar o serviço do hub **mais serviços** lista. 
    
    > [!TIP] 
    > Selecione **Afixar ao dashboard** para criar um mosaico do **Azure Information Protection** no seu dashboard. Assim, não terá de procurar o serviço da próxima vez que iniciar sessão no portal.

4. Pode ver o **início rápido** página que abre automaticamente na primeira vez que o se ligar ao serviço. Procurar os recursos sugeridos ou utilizar as outras opções de menu. Para configurar as etiquetas que os utilizadores podem selecionar, utilize o procedimento seguinte.

Tempo junto de acesso a **Azure Information Protection** painel,-seleciona automaticamente o **políticas** > **política Global** opção para que possa Configure as etiquetas para todos os utilizadores. Poderá regressar ao **início rápido** página selecionando-à partir de **geral** menu.

## <a name="how-to-configure-the-azure-information-protection-policy"></a>Como configurar a política do Azure Information Protection

1. Certifique-se de que tem sessão iniciada portal do Azure, utilizando uma dessas funções administrativas: administrador de proteção de informações, o administrador de segurança ou o Administrador Global. Consulte o [anterior a secção](#signing-in-to-the-azure-portal) para obter mais informações sobre estas funções administrativas.

2. Se necessário, navegue para o **Azure Information Protection** painel: por exemplo, no hub menu, clique em **mais serviços** e comece a escrever **Information Protection** no Caixa de filtro. Na lista de resultados, selecione **Azure Information Protection**. 
    
    O **Azure Information Protection - política Global** painel abre-se automaticamente para que possa ver e editar a política global que obtêm todos os utilizadores. 
    
    A política do Azure Information Protection contém os elementos seguintes que pode configurar:
    
    - Etiquetas que permitem tanto a si como aos utilizadores classificar documentos e e-mails.
    
    - Título e descrição para a barra Information Protection que os utilizadores veem nas aplicações do Office.
    
    - A opção para impor a classificação quando os utilizadores guardam documentos e enviam e-mails.
    
    - A opção para definir uma etiqueta predefinida como ponto de partida para classificar documentos e e-mails.
    
    - A opção para solicitar aos utilizadores que indiquem um motivo quando estes selecionam uma etiqueta que tem um nível de sensibilidade inferior ao original.
    
    - A opção para etiquetar automaticamente uma mensagem de e-mail com base nos respetivos anexos.
    
    - A opção para fornecer uma ligação de ajuda personalizada para os utilizadores.

O Azure Information Protection tem uma [política predefinida](configure-policy-default.md) que contém cinco etiquetas principais. Dois destas etiquetas contenham sublabels para fornecer subcategorias, quando necessário. Quando uma etiqueta está configurada para sublabels, os utilizadores não é possível selecionar a etiqueta principal, mas tem de selecionar uma dos sublabels.

As etiquetas de Azure Information Protection podem ser utilizadas com o intervalo completo de dados que uma organização, normalmente, cria e armazena a classificação mais baixo de dados pessoais, para a classificação máxima de dados altamente confidenciais. 

Pode utilizar as etiquetas predefinidas sem alterações ou pode personalizá-las, eliminá-las ou criar novas etiquetas. Para obter mais informações, utilize as ligações na próxima secção, para o ajudar a encontrar as opções relevantes e como as configurar.

Pode criar qualquer número de etiquetas. No entanto, quando são iniciados obter demasiado elevado para os utilizadores vejam e selecione a etiqueta de direita de facilmente, crie políticas de âmbito para que os utilizadores veem apenas as etiquetas que são relevantes nos mesmos. Não há um limite superior para etiquetas que aplicar a proteção, o que é 500.

Quando efetuar alterações num painel do Azure Information Protection, clique em **Guardar** para guardar as alterações ou clique em **Eliminar** para reverter para as últimas definições guardadas.

Quando terminar de efetuar as alterações que pretende, clique em **Publicar**. 

O cliente do Azure Information Protection verifica se existem alterações sempre que uma das aplicações do Office suportada é iniciada e transfere as alterações como política do Azure Information Protection mais recente. Acionadores adicionais que atualizam a política do cliente:

- Clique com o botão direito do rato para classificar e proteger um ficheiro ou uma pasta.

- Execução dos [cmdlets do PowerShell](../rms-client/client-admin-guide-powershell.md) para etiquetagem e proteção (Get-AIPFileStatus, Set-AIPFileClassification e Set-AIPFileLabel).

- A cada 24 horas.

- Para o [Scanner de proteção de informações do Azure](deploy-aip-scanner.md): quando inicia o serviço de mensagens em fila e a cada hora.


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
