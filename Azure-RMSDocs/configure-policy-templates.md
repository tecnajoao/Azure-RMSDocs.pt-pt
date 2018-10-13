---
title: Configurar e gerir modelos do Azure Information Protection
description: Configurar e gerir modelos de gestão de direitos do portal do Azure.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 08/20/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 8301aabb-047d-4892-935c-7574f6af8813
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: 71444804ab21dfbe09e0cf13ab1b75425f7a84d0
ms.sourcegitcommit: 1e6394044d646278ae582c7713cac8ffb9bf4c1e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49169860"
---
# <a name="configuring-and-managing-templates-for-azure-information-protection"></a>Configurar e gerir modelos do Azure Information Protection

>*Aplica-se a: [do Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Modelos de proteção, também conhecido como modelos do Rights Management, são um agrupamento de definições de proteção definidos pelo administrador do Azure Information Protection. Estas definições incluem a escolhida [direitos de utilização](configure-usage-rights.md) para os utilizadores autorizados e controlos de acesso para a expiração e acesso offline. Estes modelos são integrados com a política do Azure Information Protection: 

**Quando tem uma subscrição que inclui a classificação, a etiquetagem e a proteção (Azure Information Protection P1 ou P2):**

- Os modelos que não estão integrados com as etiquetas para o seu inquilino são apresentados no **modelos de proteção** secção depois das suas etiquetas no **do Azure Information Protection – etiquetas** painel. Para navegar para este painel, selecione o **classificações** > **etiquetas** opção de menu. Pode converter estes modelos em etiquetas ou pode ligá-los ao configurar a proteção das suas etiquetas. 

**Quando tem uma subscrição que inclui apenas proteção (uma subscrição do Office 365 que inclui o serviço Azure Rights Management):**

- Modelos para o seu inquilino são apresentados no **modelos de proteção** secção sobre o **do Azure Information Protection – etiquetas** painel. Para navegar para este painel, selecione o **classificações** > **etiquetas** opção de menu. Não são apresentadas etiquetas. Também pode ver as definições de configuração que são específicas para classificação e etiquetagem, mas estas definições não têm efeito nos seus modelos ou não podem ser configuradas. 

>[!NOTE]
>Em alguns aplicativos e serviços, poderá ver [não reencaminhar](configure-usage-rights.md#do-not-forward-option-for-emails) e [só Encrypt](configure-usage-rights.md#encrypt-only-option-for-emails) (ou **Encrypt**) exibida como um modelo. Essas não são modelos que pode editar ou eliminar, mas as opções que são fornecidos por predefinição com o serviço do Exchange.

## <a name="default-templates"></a>Modelos predefinidos

Quando obtiver a sua subscrição do Azure Information Protection ou uma subscrição do Office 365 que inclui o serviço Azure Rights Management, os dois modelos predefinidos são criados automaticamente para o seu inquilino. Estes modelos restringem o acesso a utilizadores autorizados na sua organização. Quando estes modelos são criados, eles têm as permissões que estão listadas as [configurar direitos de utilização do Azure Rights Management](configure-usage-rights.md#rights-included-in-the-default-templates) documentação.

Além disso, os modelos são configurados para permitir o acesso offline durante sete dias e não têm uma data de expiração.

>[!NOTE]
> Pode alterar estas definições e os nomes e descrições dos modelos predefinidos. Esta capacidade não era possível com o portal clássico do Azure e continua sem suporte para o PowerShell.

Estes modelos predefinidos tornam mais fácil para e a outras pessoas, começar imediatamente a proteger os dados confidenciais da sua organização. Estes modelos podem ser utilizados com o Azure Information Protection etiquetas ou por conta própria com [aplicativos e serviços](applications-support.md) que pode utilizar modelos do Rights Management.

Também pode criar seus próprios modelos personalizados. Embora provavelmente necessite de apenas alguns modelos, pode ter um máximo de 500 modelos personalizados guardados no Azure.


### <a name="default-template-names"></a>Nomes de modelo padrão

Se obteve recentemente a sua subscrição, os modelos predefinidos são criados com os seguintes nomes:

- **Confidencial \ todos os funcionários** que concede ler e modificar as permissões para o conteúdo protegido.

- **Altamente confidencial \ todos os funcionários** que concede permissão só de leitura para o conteúdo protegido.

Se tiver adquirido sua assinatura há algum tempo, os modelos predefinidos são criados com os seguintes nomes:

- **\<nome da organização > – confidencial** que concede ler e modificar as permissões para o conteúdo protegido.

- **\<nome da organização >-apenas visualização confidencial** que concede permissão só de leitura para o conteúdo protegido. 

Pode mudar o nome (e reconfigurar) estes modelos predefinidos ao utilizar o portal do Azure.

>[!NOTE]
>Se não vir os modelos padrão no **do Azure Information Protection – etiquetas** painel, eles são convertidos em etiquetas ou ligados a uma etiqueta. Eles ainda existem como modelos, mas no portal do Azure, vê-los como parte de uma configuração de etiqueta, que inclui definições de proteção para uma chave de cloud. Pode confirmar sempre que modelos o inquilino tem, ao executar o [Get-AadrmTemplate](/powershell/module/aadrm/get-aadrmtemplate) da [módulo do PowerShell do AADRM](administer-powershell.md).
>
>Pode converter manualmente a modelos, conforme explicado na seção posterior, [para converter modelos em etiquetas](#to-convert-templates-to-labels)e, em seguida, renomeá-los, se desejar. Ou eles são convertidos automaticamente para se sua política do Azure Information Protection predefinida criada recentemente e o serviço Azure Rights Management para o seu inquilino tiver sido ativado nesse momento.

Os modelos que são arquivados são apresentados como não disponível na **do Azure Information Protection – etiquetas** painel. Estes modelos não podem ser selecionados para etiquetas, mas pode ser convertidos em etiquetas.

## <a name="considerations-for-templates-in-the-azure-portal"></a>Considerações para modelos no portal do Azure

Antes de editar estes modelos ou convertê-los em etiquetas, certifique-se de que está ciente das seguintes alterações e considerações. Devido a alterações na implementação, a lista seguinte é especialmente importante se anteriormente gerida modelos no portal clássico do Azure.

- Depois de editar ou converter um modelo e guardar a política do Azure Information Protection, as seguintes alterações são feitas nos [direitos de utilização](configure-usage-rights.md) originais. Se for necessário, pode adicionar ou remover direitos de utilização individuais através do portal do Azure. Em alternativa, utilizar o PowerShell com o [New-AadrmRightsDefinition](/powershell/module/aadrm/set-aadrmtemplateproperty) e [Set-AadrmTemplateProperty](/powershell/module/aadrm/set-aadrmtemplateproperty) cmdlets.
    
    - **Permitir Macros** (nome comum) é adicionado automaticamente. Este direito de utilização é preciso para a barra do Azure Information Protection nas aplicações do Office.

- As definições **Publicado** e **Arquivado** são apresentadas como **Ativado**: **Ligado** e **Ativado**: **Desligado** respetivamente no painel **Etiqueta**. Em modelos que pretende manter, mas não ser visível para utilizadores ou serviços, esses modelos, defina como **Enabled**: **desativar**.

- Não é possível copiar ou eliminar um modelo no portal do Azure. Quando o modelo é convertido para uma etiqueta, pode configurar a etiqueta de deixar de utilizar o modelo selecionando **não configurado** para o **definir permissões para documentos e e-mails que contenham esta etiqueta** opção. Em alternativa, pode eliminar a etiqueta. Em ambos os cenários, no entanto, o modelo não é eliminado e permanece num Estado de funcionamento arquivado.
    
    Agora pode eliminar o modelo através do PowerShell [Remove-AadrmTemplate](/powershell/module/aadrm/remove-aadrmtemplate) cmdlet. Também pode utilizar este cmdlet do PowerShell para modelos que não são convertidos em etiquetas. No entanto, se eliminar um modelo que foi utilizado para proteger conteúdo, esse conteúdo já não pode ser aberto. Elimine modelos apenas se tiver a certeza de que não foram utilizados para proteger documentos ou e-mails na produção. Como precaução, talvez queira considerar primeiro exportar o modelo de cópia de segurança, ao utilizar o [Export-AadrmTemplate](/powershell/module/aadrm/export-aadrmtemplate) cmdlet. 

- Atualmente, se editar e guardar um modelo departamental, este remove a configuração do âmbito. O equivalente de um modelo com âmbito na política do Azure Information Protection é uma [política com âmbito](configure-policy-scope.md). Se converter o modelo numa etiqueta, pode selecionar um âmbito existente.
    
    Além disso, não é possível definir a definição de compatibilidade de aplicativo para um modelo departamental com o portal do Azure. Se necessário, pode definir esta definição de compatibilidade de aplicativos com o [Set-AadrmTemplateProperty](/powershell/module/aadrm/set-aadrmtemplateproperty) cmdlet e os *EnableInLegacyApps* parâmetro.

- Ao converter ou ao ligar um modelo numa etiqueta, já não pode ser utilizada por outras etiquetas. Além disso, este modelo já não é apresentado no **modelos de proteção** secção. 

- Não criar um novo modelo a partir da **modelos de proteção** secção. Em vez disso, crie uma etiqueta com o **proteger** definir e configurar os direitos de utilização e as definições a partir do **proteção** painel. Para obter todas as instruções, veja [Criar um novo modelo](#to-create-a-new-template).

## <a name="to-configure-the-templates-in-the-azure-information-protection-policy"></a>Para configurar os modelos na política do Azure Information Protection

1. Se ainda não o tiver feito, abra uma nova janela do browser e [inicie sessão no portal do Azure](configure-policy.md#signing-in-to-the-azure-portal). Em seguida, navegue para o **do Azure Information Protection – etiquetas** painel.
    
    Por exemplo, no hub menu, clique em **todos os serviços** e comece a escrever **informações** na caixa Filtro. Selecione **Azure Information Protection**.

2. Do **classificações** > **etiquetas** opção de menu: no **do Azure Information Protection – etiquetas** painel, expanda **proteção modelos**e, em seguida, localize o modelo que pretende configurar.
    
3. Selecione o modelo e, no **rótulo** painel, pode alterar o nome do modelo e a descrição, se necessário, ao editar o **nome a apresentar etiqueta** e **Descrição**. Em seguida, selecione **proteção** que tem um valor de **(chave da cloud) do Azure**, para abrir o **proteção** painel.

4. No painel **Proteção**, pode alterar as permissões, a expiração de conteúdo e as definições de acesso offline. Para obter mais informações, sobre a configuração das definições de proteção, veja [Como configurar uma etiqueta para a proteção do Rights Management](configure-policy-protection.md)
    
    Clique em **OK** para manter as suas alterações e, no painel **Etiqueta**, clique em **Guardar**.
    
> [!NOTE]
> Também pode editar um modelo ao utilizar o **Editar modelo** botão a **proteção** painel se tiver configurado uma etiqueta para utilizar um modelo predefinido. Desde que não existem outra etiqueta também utiliza o modelo selecionado, este botão converte o modelo numa etiqueta e leva-o para o passo 5. Para obter mais informações sobre o que acontece quando modelos são convertidos em etiquetas, consulte a secção seguinte.

## <a name="to-convert-templates-to-labels"></a>Converter modelos em etiquetas

Quando tem uma subscrição que inclui a classificação, a etiquetagem e a proteção, pode converter um modelo numa etiqueta. Quando converte um modelo, o modelo original é mantido mas, no portal do Azure, é apresentado agora como incluído numa nova etiqueta.

Por exemplo, se converter uma etiqueta denominada **Marketing** que concede direitos de utilização ao grupo de marketing, no portal do Azure é agora apresentada como uma etiqueta denominada **Marketing** que tem as mesmas definições de proteção. Se alterar as definições de proteção nesta etiqueta criada recentemente, está a alterá-las no modelo e qualquer utilizador ou serviço que utilize este modelo irá obter as novas definições de proteção com a próxima atualização do modelo. 

Não existe nenhum requisito para converter todos os modelos em etiquetas, mas, quando o fizer, as definições de proteção são totalmente integradas com a funcionalidade completa de etiquetas para que não precise de manter as definições separadamente.

Para converter um modelo numa etiqueta, clique com o botão direito no rato no modelo e selecione **Converter em etiqueta**. Em alternativa, utilize o menu de contexto para selecionar esta opção. 

Também pode converter um modelo a para uma etiqueta ao configurar uma etiqueta para proteção e um modelo predefinido, utilizando o **Editar modelo** botão. 

Ao converter um modelo numa etiqueta:

- O nome do modelo é convertido num novo nome de etiqueta e a descrição do modelo é convertida na descrição da etiqueta. 

- Se o estado do modelo for publicado, esta definição é mapeada para **Ativado**: **Ligado** na etiqueta, que é agora apresentada como esta etiqueta para os utilizadores quando voltar a publicar a política do Azure Information Protection. Se o estado do modelo foi arquivado, esta definição é mapeada para **Enabled**: **desativar** para a etiqueta e não é apresentada como uma etiqueta disponível aos utilizadores.

- As definições de proteção são mantidas e pode editá-las se for necessário, além de adicionar outras definições de etiqueta como marcadores visuais e condições.

- O modelo original deixa de ser apresentado em **modelos de proteção** e não pode ser selecionada como um modelo predefinido ao configurar a proteção para uma etiqueta. Para editar este modelo no portal do Azure, agora tem de editar a etiqueta que foi criada quando converter o modelo. O modelo permanece disponível para o serviço Azure Rights Management e ainda pode ser gerido com os [comandos do PowerShell](administer-powershell.md).  

## <a name="to-create-a-new-template"></a>Criar um novo modelo

Quando cria uma nova etiqueta com a definição de proteção do **Azure (chave da cloud)**, nos bastidores, esta ação cria um novo modelo personalizado que pode ser acedido por serviços e aplicações que se integram com o Rights Management modelos.

1. Do **classificações** > **etiquetas** opção de menu: no **do Azure Information Protection – etiquetas** painel, selecione **adicionar uma nova etiqueta** .

2. Na **etiqueta** painel, mantenha a predefinição **ativado**: **no**, em seguida, introduza um nome de etiqueta e descrição para o nome do modelo e a descrição.

3. Para **Defina permissões para documentos e e-mails que contenham esta etiqueta**, selecione **Proteger** e, em seguida, selecione **Proteção**:
    
     ![Configurar a proteção para uma etiqueta do Azure Information Protection](./media/info-protect-protection-bar-configured.png)

4. No painel **Proteção**, pode alterar as permissões, a expiração de conteúdo e as definições de acesso offline. Para obter mais informações sobre a configuração destas definições de proteção, veja [Como configurar uma etiqueta para a proteção do Rights Management](configure-policy-protection.md)
    
    Clique em **OK** para manter as suas alterações e, no painel **Etiqueta**, clique em **Guardar**.
    
    Sobre o **do Azure Information Protection – etiquetas** painel, verá agora sua nova etiqueta apresentada com o **PROTEÇÃO** coluna para indicar que ele contém as definições de proteção. Estas definições de proteção apresentam como modelos para aplicações e serviços que suportam o serviço Azure Rights Management.
    
    Embora a etiqueta é ativada, por predefinição, o modelo for arquivado. Para que as aplicações e serviços podem utilizar o modelo para proteger documentos e e-mails, conclua a etapa final para publicar o modelo.

5. Do **classificações** > **políticas** menu opção, selecione a política que contém as novas definições de proteção. Em seguida, selecione **adicionar ou remover etiquetas**. Partir do **política: Adicionar ou remover as etiquetas** painel, selecione a etiqueta criada recentemente que contém as definições de proteção, selecione **OK**e, em seguida, selecione **guardar**.

## <a name="next-steps"></a>Passos Seguintes

Pode demorar até 15 minutos para um computador a executar o cliente do Azure Information Protection para obter estas definições alteradas. Para obter mais informações sobre como os computadores e os serviços transferem e atualizam modelos, veja [Atualizar modelos para utilizadores e serviços](refresh-templates.md).

Tudo o que pode configurar no portal do Azure para criar e gerir os seus modelos, pode fazer com o PowerShell. Além disso, o PowerShell fornece mais opções que não estão disponíveis no portal. Para obter mais informações, consulte [referência do PowerShell para modelos de proteção](configure-templates-with-powershell.md). 

Para mais informações sobre como configurar a política do Azure Information Protection, utilize as ligações na secção [Configurar política da organização](configure-policy.md#configuring-your-organizations-policy).  

