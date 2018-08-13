---
title: Configurar a política do Azure Information Protection
description: Para configurar a classificação, a etiquetagem e a proteção, tem de configurar a política do Azure Information Protection.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 08/02/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: ba0e8119-886c-4830-bd26-f98fb14b2933
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: 5bb41669d8f2d4abed72094d33c6136380ed8020
ms.sourcegitcommit: 5fdf013fe05b65517b56245e1807875d80be6e70
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/03/2018
ms.locfileid: "39491306"
---
# <a name="configuring-the-azure-information-protection-policy"></a>Configurar a política do Azure Information Protection

>*Aplica-se a: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

Para configurar a classificação, a etiquetagem e a proteção, tem de configurar a política do Azure Information Protection. Esta política é, em seguida, transferida para computadores que têm instalado o [cliente do Azure Information Protection](https://www.microsoft.com/en-us/download/details.aspx?id=53018).

A política contém etiquetas e as definições:

- As etiquetas aplicam-se um valor de classificação a documentos e e-mails e, opcionalmente, podem proteger este conteúdo. O cliente do Azure Information Protection apresenta estas etiquetas para os seus utilizadores nas aplicações do Office, e quando os utilizadores com o botão direito no Explorador de ficheiros. Estas etiquetas também podem ser aplicadas através da utilização do PowerShell e o scanner do Azure Information Protection.

- As definições de alterar o comportamento padrão do cliente do Azure Information Protection. Por exemplo, pode selecionar uma etiqueta predefinida, se todos os documentos e e-mails devem ter uma etiqueta e se a barra do Azure Information Protection é apresentada nas aplicações do Office.

## <a name="subscription-support"></a>Suporte da subscrição

O Azure Information Protection suporta diferentes níveis de assinaturas:

- Azure Information Protection P2: suporte para todas as funcionalidades de classificação, etiquetagem e proteção.

- Azure Information Protection P1: suporte para a maioria das funcionalidades de classificação, etiquetagem e proteção, mas não para classificação automática ou HYOK.

- Office 365 que inclui o serviço Azure Rights Management: suporte para proteção, mas não para classificação e etiquetagem.

As opções que requerem uma subscrição do Azure Information Protection P2 estão identificadas no portal.

Se sua organização tiver uma mistura de subscrições, é sua responsabilidade certificar-se de que os utilizadores não utilizar funcionalidades que a conta não está licenciada para utilizar. O cliente do Azure Information Protection não fazer para licenciar a verificação e de imposição. Quando configurar as opções que nem todos os utilizadores tenham uma licença para, a utilização no âmbito políticas ou de uma definição de registo para se certificar de que a sua organização se mantém em conformidade com as suas licenças:

- **Quando a sua organização tiver uma mistura de licenças do Azure Information Protection P1 e P2 do Azure Information Protection**: para utilizadores que têm uma P2 licenciar, criar e utilizar um ou mais [políticas de âmbito](configure-policy-scope.md) ao configurar opções que requerem uma licença do Azure Information Protection P2. Certifique-se de que a política global não contém opções que requerem uma licença do Azure Information Protection P2.

- **Quando a sua organização tem uma subscrição do Azure Information Protection, alguns utilizadores têm apenas uma licença para o Office 365 que inclui o serviço Azure Rights Management, mas**: para os utilizadores que não tem uma licença do Azure Information Protection, Edite o registo em seus computadores para que eles não transferir política do Azure Information Protection. Para obter instruções, consulte o Guia do administrador para a personalização do seguinte: [impor modo apenas de proteção quando a sua organização tiver uma mistura de licenças](./rms-client/client-admin-guide-customizations.md#enforce-protection-only-mode-when-your-organization-has-a-mix-of-licenses).

Para obter mais informações sobre as subscrições, veja [De que subscrição preciso para o Azure Information Protection e que funcionalidades estão incluídas?](faqs.md#what-subscription-do-i-need-for-azure-information-protection-and-what-features-are-included)

## <a name="signing-in-to-the-azure-portal"></a>O início de sessão no portal do Azure

Para iniciar sessão no portal do Azure, configurar e gerir o Azure Information Protection:

- Utilize a seguinte hiperligação: https://portal.azure.com

- Utilizar uma conta que tenha um dos seguintes [funções de administrador](/azure/active-directory/active-directory-assign-admin-roles-azure-portal):
    
    - **Administrador do Information Protection**

    - **Administrador de segurança**

    - **Administrador global / administrador de empresa**


## <a name="to-access-the-azure-information-protection-blade-for-the-first-time"></a>Para aceder ao painel de proteção de informações do Azure pela primeira vez

1. Inicie sessão no portal do Azure.

2. No hub menu, selecione **criar um recurso**e, em seguida, a partir da caixa de pesquisa para o Marketplace, escreva **do Azure Information Protection**. 
    
3. Na lista de resultados, selecione **do Azure Information Protection**. Sobre o **do Azure Information Protection** painel, clique em **criar**.
    
    > [!TIP] 
    > Opcionalmente, selecione **afixar ao dashboard** para criar um **do Azure Information Protection** mosaico no dashboard, para que não terá de procurar para o serviço da próxima vez que iniciar sessão no portal.
    
    Clique em **criar** novamente.

4. Verá o **guia de introdução** página que abre automaticamente na primeira vez que ligar ao serviço. Procurar os recursos sugeridos ou utilizar as outras opções de menu. Para configurar as etiquetas que os utilizadores podem selecionar, utilize o procedimento seguinte.

Acesso de tempo junto a **do Azure Information Protection** painel, ele seleciona automaticamente o **etiquetas** opção para que possa ver e configurar etiquetas para todos os utilizadores. Pode regressar à **início rápido** página selecionando-o a partir do **geral** menu.

## <a name="how-to-configure-the-azure-information-protection-policy"></a>Como configurar a política do Azure Information Protection

1. Certifique-se de que tem sessão iniciada portal do Azure ao utilizar uma destas funções administrativas: Administrador Global, administrador de segurança ou administrador do Information Protection. Consulte a [secção anterior](#signing-in-to-the-azure-portal) para obter mais informações sobre estas funções administrativas.

2. Se necessário, navegue para o **do Azure Information Protection** painel: por exemplo, no hub menu, clique em **todos os serviços** e comece a escrever **proteção de informações** no Caixa de filtro. Na lista de resultados, selecione **Azure Information Protection**. 
    
    O **do Azure Information Protection – etiquetas** painel abre automaticamente para que possa ver e editar as etiquetas disponíveis. As etiquetas podem ser disponibilizadas para todos os utilizadores, os utilizadores selecionados ou não existem utilizadores adicionando ou removendo-los a partir de uma política.

3. Para ver e editar as políticas, selecione **políticas** entre as opções de menu. Para ver e editar a política que obtém todos os utilizadores, selecione o **Global** política. Para criar uma política personalizada para utilizadores selecionados, selecione **adicionar uma nova política**.
    

### <a name="overview-of-the-policy"></a>Descrição geral da política

Uma política do Azure Information Protection contém os elementos seguintes que pode configurar:
    
- As etiquetas são incluídas que permitem que os administradores e utilizadores classificar (e, opcionalmente, proteger) documentos e e-mails.

- Título e descrição para a barra Information Protection que os utilizadores veem nas aplicações do Office.

- A opção para definir uma etiqueta predefinida como ponto de partida para classificar documentos e e-mails.

- A opção para impor a classificação quando os utilizadores guardam documentos e enviam e-mails.

- A opção para solicitar aos utilizadores que indiquem um motivo quando estes selecionam uma etiqueta que tem um nível de sensibilidade inferior ao original.

- A opção para etiquetar automaticamente uma mensagem de e-mail com base nos respetivos anexos.

- A opção de controlar se a barra do Information Protection é apresentada em aplicativos do Office.

- A opção para controlar se o botão não reencaminhar é apresentado no Outlook.

- A opção para permitir aos utilizadores especificar suas próprias permissões para documentos.

- A opção para fornecer uma ligação de ajuda personalizada para os utilizadores.

O Azure Information Protection tem uma [política predefinida](configure-policy-default.md) que contém cinco etiquetas principais. Duas destas etiquetas contenham subetiquetas para fornecer subcategorias, quando necessário. Quando uma etiqueta está configurada para subetiquetas, os utilizadores não é possível selecionar a etiqueta principal, mas tem de selecionar uma das subetiquetas.

As etiquetas do Azure Information Protection podem ser utilizadas com o intervalo completo de dados que uma organização normalmente cria e armazena, desde a classificação mais baixa de dados pessoais, à classificação mais elevada de dados altamente confidenciais. 

Pode utilizar as etiquetas predefinidas sem alterações ou pode personalizá-las, eliminá-las ou criar novas etiquetas. Para obter mais informações, utilize as ligações na próxima secção, para o ajudar a encontrar as opções relevantes e como as configurar.

Pode criar qualquer número de etiquetas. No entanto, durante o arranque obter demasiado elevado para os utilizadores vejam e selecione a etiqueta de direito de facilmente, crie políticas de âmbito, para que os utilizadores veem apenas as etiquetas que são relevantes para eles. Existe um limite superior para as etiquetas que aplicam a proteção, o que é 500.

Quando efetuar alterações num painel do Azure Information Protection, clique em **Guardar** para guardar as alterações ou clique em **Eliminar** para reverter para as últimas definições guardadas. Quando guardar as alterações de uma política ou tornar a alterar as alterações para etiquetas que são adicionadas às políticas, essas alterações são automaticamente publicadas. Não existe nenhum separado opção de publicar.

O cliente do Azure Information Protection verifica se existem alterações sempre que uma das aplicações do Office suportada é iniciada e transfere as alterações como política do Azure Information Protection mais recente. Acionadores adicionais que atualizam a política do cliente:

- Clique com o botão direito do rato para classificar e proteger um ficheiro ou uma pasta.

- Execução dos [cmdlets do PowerShell](./rms-client/client-admin-guide-powershell.md) para etiquetagem e proteção (Get-AIPFileStatus, Set-AIPFileClassification e Set-AIPFileLabel).

- A cada 24 horas.

- Para o [do Azure Information Protection Scanner](deploy-aip-scanner.md): quando o serviço é iniciado (se a política é mais antiga do que uma hora) de mensagens em fila e a cada hora durante a operação.


>[!NOTE]
>Quando o cliente transferir a política, poderá ter de aguardar alguns minutos até que fique totalmente operacional. O tempo em questão varia devido a fatores como o tamanho e a complexidade da configuração da política e a conectividade de rede. Se a ação resultante das suas etiquetas não corresponder às suas alterações mais recentes, aguarde 15 minutos e tente novamente.

### <a name="configuring-your-organizations-policy"></a>Configurar a política da organização

Utilize as seguintes informações para ajudar a configurar a política do Azure Information Protection:

- [Política do Information Protection predefinida](configure-policy-default.md)

- [Como configurar as definições de política](configure-policy-settings.md)

- [Como criar uma nova etiqueta](configure-policy-new-label.md)

- [Como adicionar ou remover uma etiqueta](configure-policy-add-remove-label.md)
 
- [Como eliminar ou reordenar uma etiqueta](configure-policy-delete-reorder.md)

- [Como alterar ou personalizar uma etiqueta existente](configure-policy-change-label.md)

- [Como configurar uma etiqueta para proteção](configure-policy-protection.md)

- [Como configurar uma etiqueta para aplicar marcações visuais](configure-policy-markings.md)

- [Como configurar condições para as classificações automática e recomendada](configure-policy-classification.md)

- [Como configurar a política para utilizadores específicos com políticas de âmbito](configure-policy-scope.md)

- [Como configurar e gerir modelos](configure-policy-templates.md)

- [Como configurar etiquetas para diferentes idiomas](configure-policy-languages.md)

## <a name="next-steps"></a>Passos Seguintes

Para obter um exemplo de como personalizar a política predefinida e ver o comportamento resultante de uma aplicação do Office, experimente o [Tutorial de início rápido do Azure Information Protection](infoprotect-quick-start-tutorial.md).
