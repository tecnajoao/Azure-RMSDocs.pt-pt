---
title: Configurar e gerir modelos do Azure Information Protection
description: "Configurar e gerir modelos de gestão de direitos do portal do Azure."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 09/12/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 8301aabb-047d-4892-935c-7574f6af8813
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: 1094c0a711b3691b8186baafc06d1fb72daf5613
ms.sourcegitcommit: 94a9b6714c555b95f6064088e77ed94f08224a15
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/13/2017
---
# <a name="configuring-and-managing-templates-for-azure-information-protection"></a>Configurar e gerir modelos do Azure Information Protection

>*Aplica-se a: Azure Information Protection*

>[!NOTE]
>Esta funcionalidade substitui configurar modelos personalizados no portal clássico do Azure.
>
>Apesar de ainda pode criar e gerir modelos no portal clássico do Azure, não recomendamos que gerir os mesmos modelos a partir do portal clássico do Azure e o portal do Azure. A implementação para a configuração de modelos nestes portais diferentes foi alterada, para que configurar o mesmo modelo no portais diferentes pode resultar numa configuração instável.


Modelos de gestão de direitos agora estão integrados com a política do Azure Information Protection. 

**Quando tem uma subscrição que inclui a classificação, a etiquetagem e a proteção (Azure Information Protection P1 ou P2):**

- Modelos de gestão de direitos que não estão integrados com as etiquetas para o seu inquilino são apresentados no **modelos** secção após as etiquetas a **Azure Information Protection - política Global** painel. Pode converter estes modelos das etiquetas, ou pode ligar aos mesmos quando configurar a proteção para as etiquetas. 

**Quando tem uma subscrição que inclui apenas proteção (uma subscrição do Office 365 que inclui o serviço Azure Rights Management):**

- Modelos de gestão de direitos para o seu inquilino são apresentados no **Azure Information Protection - política Global** painel, no **modelos** secção. Não são apresentadas etiquetas. Consulte também as definições de configuração que são específicas para classificação e etiquetagem, mas estas não tem qualquer efeito nos seus modelos ou não pode ser configurados. 

## <a name="default-templates"></a>Modelos predefinidos

Quando obtiver a sua subscrição do Azure Information Protection ou uma subscrição do Office 365 que inclui o serviço Azure Rights Management, dois modelos predefinidos são criados automaticamente para o seu inquilino que restringem o acesso aos utilizadores autorizados na sua organização. Quando são criados estes dois modelos, estes têm as seguintes restrições: 

- Permissões Ler ou Modificar para o conteúdo protegido
    
    - **Permissões específicas**: ver conteúdo, guarde o ficheiro, editar conteúdo, ver direitos atribuídos, permitir Macros, reencaminhar, responder, responder a todos

- Visualização só de leitura dos conteúdos protegidos
    
    - **Permissão específica**: ver conteúdo

Além disso, os modelos são configurados para permitir acesso offline durante sete dias e não dispõe de uma data de expiração.

>[!NOTE]
> Pode alterar estas definições e os nomes e descrições dos modelos predefinidos. Esta capacidade não foi possível com o portal clássico do Azure e continua sem suporte para o PowerShell.

Estes modelos predefinidos tornam mais fácil para si e a outras pessoas, imediatamente começar a proteger os dados confidenciais da sua organização. Estes modelos podem ser utilizados com etiquetas do Azure Information Protection, ou por si mesmos com [aplicações e serviços](../understand-explore/applications-support.md) que pode utilizar modelos de Rights Management.

Também pode criar os seus modelos personalizados. Embora provavelmente necessite de apenas alguns modelos, pode ter um máximo de 500 modelos personalizados guardados no Azure.

### <a name="default-template-names"></a>Nomes de modelo predefinido

Se tiver adquirido recentemente uma subscrição do Azure Information Protection, os modelos predefinidos são criados com os nomes seguintes:

- **Confidencial \ todos os funcionários** para ler ou modificar permissões para o conteúdo protegido.

- **Altamente confidenciais \ todos os funcionários** para visualização só de leitura para o conteúdo protegido.

Se tiver adquirido a subscrição do Azure Information Protection algum tempo há ou se não tiver uma subscrição do Azure Information Protection, mas tiver uma subscrição do Office 365 que inclua o Azure Rights Management, os modelos predefinidos são criados com o nomes seguintes:

- **\<nome da organização > – confidencial** para ler ou modificar permissões para o conteúdo protegido.

- **\<nome da organização >-apenas visualização confidencial**, para uma visualização só de leitura para o conteúdo protegido. 

Pode mudar o nome (e reconfigurar) estes modelos predefinidos, ao utilizar o portal do Azure.

>[!NOTE]
>Se não vir os modelos predefinidos no **Azure Information Protection - política Global** painel, estes são convertidos para as etiquetas ou ligados a uma etiqueta. Ainda existem como modelos, mas no portal do Azure, pode vê-los como parte de uma configuração de etiqueta, que inclui proteção Azure RMS. Pode confirmar sempre que modelos tem o inquilino, executando o [Get-AadrmTemplate](/powershell/module/aadrm/get-aadrmtemplate) do [módulo AADRM PowerShell](administer-powershell.md).
>
>Pode converter manualmente modelos, conforme explicado na secção posterior, [converter modelos etiquetas](#to-convert-templates-to-labels)e, em seguida, renomeie-os se pretender. Ou serão convertidos automaticamente para si se a política de Azure Information Protection predefinida criada recentemente e o serviço Azure Rights Management para o seu inquilino foi ativado nessa altura.

Modelos são arquivados apresentam como indisponíveis no **Azure Information Protection - política Global** painel. Não não possível selecionar estes modelos para etiquetas, mas pode ser convertidos para etiquetas.

## <a name="considerations-for-templates-in-the-azure-portal"></a>Considerações para modelos no portal do Azure

Antes de editar estes modelos ou convertê-las em etiquetas, certifique-se de que está ciente das seguintes alterações e considerações. Devido a alterações de implementação, a lista seguinte é especialmente importante se anteriormente a gerido modelos no portal clássico do Azure.

- Depois de editar ou converter um modelo e guardar a política do Azure Information Protection, as seguintes alterações são feitas nos [direitos de utilização](configure-usage-rights.md) originais. Se for preciso, pode adicionar ou remover direitos de utilização individuais através do PowerShell com os cmdlets [New-AadrmRightsDefinition](/powershell/module/aadrm/set-aadrmtemplateproperty) e [Set-AadrmTemplateProperty](/powershell/module/aadrm/new-aadrmrightsdefinition).
    
    - **Guardar como, Exportar** (nome comum) é removido. No portal do Azure, não pode especificar manualmente este direito de utilização, mas este está incluído no direito de utilização do Controlo Total, que pode adicionar se for apropriado.
    
    - **Permitir Macros** (nome comum) é adicionado automaticamente. Este direito de utilização é preciso para a barra do Azure Information Protection nas aplicações do Office.
    

- As definições **Publicado** e **Arquivado** são apresentadas como **Ativado**: **Ligado** e **Ativado**: **Desligado** respetivamente no painel **Etiqueta**. Para modelos que pretende manter, mas não é visível para utilizadores ou serviços, colocá-los **ativado**: **desativar**.

- Não é possível copiar ou eliminar um modelo no portal do Azure. Quando o modelo é convertido para uma etiqueta, pode configurar a etiqueta para deixar de utilizar o modelo selecionando **não configurado** para o **definir as permissões para documentos e e-mails que contêm esta etiqueta** opção. Em alternativa, pode eliminar a etiqueta. Em ambos os cenários no entanto, o modelo não é eliminado e permanece num Estado arquivado.
    
    Agora pode eliminar o modelo utilizando o PowerShell [Remove-AadrmTemplate](/powershell/module/aadrm/remove-aadrmtemplate) cmdlet. Também pode utilizar este cmdlet do PowerShell para modelos que não são convertidos em etiquetas. No entanto, se eliminar um modelo que foi utilizado para proteger conteúdo, esse conteúdo já não pode ser aberto. Elimine modelos apenas se tiver a certeza de que não foram utilizadas para proteger documentos ou e-mails na produção. Como precaução, poderá considerar conferir primeiro exportar o modelo como um back cópias de segurança, utilizando o [Export-AadrmTemplate](/powershell/module/aadrm/export-aadrmtemplate) cmdlet. 

- Os modelos departamentais (modelos que estão configurados para um âmbito) são apresentados na política Global. Atualmente, se editar e guardar um modelo departamental, este remove a configuração do âmbito. O equivalente de um modelo com âmbito na política do Azure Information Protection é uma [política com âmbito](configure-policy-scope.md). Se converter o modelo numa etiqueta, pode selecionar um âmbito existente.
    
    Além disso, atualmente não pode definir a definição de compatibilidade aplicacional para um modelo departamental. Se for necessário, pode definir esta opção através do PowerShell com o cmdlet [Set-AadrmTemplateProperty](/powershell/module/aadrm/set-aadrmtemplateproperty).

- Quando converter ou ligar um modelo para uma etiqueta, já não pode ser utilizada por outras etiquetas. Além disso, este modelo já não apresenta na **modelos** ou **modelos proteção** secção. Esta secção está no processo de ser mudado.

- Não crie um novo modelo do **modelos** ou **modelos proteção** secção. Em vez disso, crie uma etiqueta que tem o **proteger** definir e configurar os direitos de utilização e as definições do **proteção** painel. Para obter todas as instruções, veja [Criar um novo modelo](#to-create-a-new-template).

## <a name="to-configure-the-templates-in-the-azure-information-protection-policy"></a>Para configurar os modelos na política do Azure Information Protection

1. Se ainda não o tiver feito, abra uma nova janela do browser e inicie sessão para o [portal do Azure](https://portal.azure.com) como um administrador de segurança ou um administrador global. Em seguida, navegue para o painel **Azure Information Protection**. 
    
    Por exemplo, no menu do hub, clique em **Mais serviços** e comece a escrever **Information** na caixa Filtrar. Selecione **Azure Information Protection**.

2. Se o modelo que pretende configurar para todos os utilizadores, permaneça o **Azure Information Protection - política Global** painel.
    
    Se o modelo que pretende configurar está a ser um [âmbito política](configure-policy-scope.md) para que o se aplica apenas a utilizadores selecionados do **políticas** selecção de menu, selecione **âmbito políticas**. Em seguida, selecione a política de âmbito do **políticas do Azure Information Protection - âmbito** painel.

3. Do **Azure Information Protection - política Global** painel, ou o **política:\<nome >** painel, localize o modelo que pretende configurar:
    
    - Quando tiver uma subscrição que inclui a classificação, etiquetagem e proteção: expanda **modelos** ou **modelos proteção** após as etiquetas.
    
    - Quando tem uma subscrição que inclui apenas proteção: os modelos são apresentados como etiquetas.

4. Selecione o modelo e, no painel **Etiqueta**, pode alterar o nome do modelo e a descrição, se necessário, ao editar o **Nome da etiqueta** e a **Descrição**. Em seguida, selecione **proteção** que tem um valor de **Azure RMS** ou **Azure (chave de nuvem)**, para abrir o **proteção** painel.

5. No painel **Proteção**, pode alterar as permissões, a expiração de conteúdo e as definições de acesso offline. Para obter mais informações, sobre a configuração das definições de proteção, veja [Como configurar uma etiqueta para a proteção do Rights Management](configure-policy-protection.md)
    
    Clique em **OK** para manter as suas alterações e, no painel **Etiqueta**, clique em **Guardar**.

6. Para disponibilizar as alterações aos utilizadores aplicações e serviços no iniciais **Azure Information Protection** painel, clique em **publicar**.

> [!NOTE]
> Também pode editar um modelo utilizando o **Editar modelo** botão no **proteção** painel se tiver configurado uma etiqueta para utilizar um modelo predefinido. Desde que não existem outra etiqueta também utiliza o modelo selecionado, este botão converte o modelo de uma etiqueta e leva-o para o passo 5. Para obter mais informações sobre o que acontece quando os modelos são convertidos em etiquetas, consulte a secção seguinte.

## <a name="to-convert-templates-to-labels"></a>Converter modelos em etiquetas

Quando tem uma subscrição que inclui a classificação, a etiquetagem e a proteção, pode converter um modelo numa etiqueta. Quando o faz, o modelo original é mantido mas, no portal do Azure, é apresentado agora como incluído numa nova etiqueta.

Por exemplo, se converter uma etiqueta denominada **Marketing** que concede direitos de utilização ao grupo de marketing, no portal do Azure é agora apresentada como uma etiqueta denominada **Marketing** que tem as mesmas definições de proteção. Se alterar as definições de proteção nesta etiqueta criada recentemente, está a alterá-las no modelo e qualquer utilizador ou serviço que utilize este modelo irá obter as novas definições de proteção com a próxima atualização do modelo. 

Não existe nenhum requisito para converter todos os modelos em etiquetas, mas, quando o fizer, as definições de proteção são totalmente integradas com a funcionalidade completa de etiquetas para que não precise de manter as definições separadamente.

Para converter um modelo numa etiqueta, clique com o botão direito no rato no modelo e selecione **Converter em etiqueta**. Em alternativa, utilize o menu de contexto para selecionar esta opção. 

Também pode converter um modelo de uma etiqueta ao configurar uma etiqueta para a proteção e um modelo predefinido, utilizando o **Editar modelo** botão. 

Ao converter um modelo numa etiqueta:

- O nome do modelo é convertido num novo nome de etiqueta e a descrição do modelo é convertida na descrição da etiqueta. 

- Se o estado do modelo for publicado, esta definição é mapeada para **Ativado**: **Ligado** na etiqueta, que é agora apresentada como esta etiqueta para os utilizadores quando voltar a publicar a política do Azure Information Protection. Se o estado do modelo for arquivado, esta definição é mapeada para **Ativado**: **Desligado** para a etiqueta e não é apresentada como uma etiqueta disponível aos utilizadores.

- As definições de proteção são mantidas e pode editá-las se for necessário, além de adicionar outras definições de etiqueta como marcadores visuais e condições.

- O modelo original já não é apresentado em **modelos** ou **modelos proteção** e não pode ser selecionado como um modelo predefinido ao configurar a proteção para uma etiqueta. Para editar este modelo no portal do Azure, agora tem de editar a etiqueta que foi criada quando converter o modelo. O modelo permanece disponível para o serviço Azure Rights Management e ainda pode ser gerido com os [comandos do PowerShell](administer-powershell.md).  

## <a name="to-create-a-new-template"></a>Criar um novo modelo

Quando cria uma nova etiqueta com a definição de proteção da **Azure RMS** ou **Azure (chave de nuvem)**, nos bastidores, esta ação cria um novo modelo personalizado que possam ser acedido por aplicações e serviços que Integre com modelos do Rights Management.

1. Se o novo modelo for para todos os utilizadores, permaneça o **Azure Information Protection - política Global** painel.
    
     Se o novo modelo será um modelo departamental, de modo a que se aplica apenas a utilizadores selecionados do **políticas** selecção de menu, selecione **âmbito políticas**. Em seguida, crie ou selecione o [âmbito política](configure-policy-scope.md) do **políticas do Azure Information Protection - âmbito** painel.

2. Do **Azure Information Protection - política Global** painel, ou o **política:\<nome >** painel, clique em **adicionar uma nova etiqueta**.

3. No painel **Etiqueta**, mantenha a predefinição de **Ativado**: **Ligado** para publicar este novo modelo, ou altere esta definição para **Desligado** para criar o modelo como arquivado. Em seguida, insira um nome de etiqueta e descrição para o nome do modelo e a descrição.

4. Para **Defina permissões para documentos e e-mails que contenham esta etiqueta**, selecione **Proteger** e, em seguida, selecione **Proteção**:
    
     ![Configurar a proteção para uma etiqueta do Azure Information Protection](../media/info-protect-protection-bar-configured.png)

5. No painel **Proteção**, pode alterar as permissões, a expiração de conteúdo e as definições de acesso offline. Para obter mais informações sobre a configuração destas definições de proteção, veja [Como configurar uma etiqueta para a proteção do Rights Management](configure-policy-protection.md)
    
    Clique em **OK** para manter as suas alterações e, no painel **Etiqueta**, clique em **Guardar**.

6. Para que estes modelos disponíveis para aplicações de utilizador e serviços no iniciais **Azure Information Protection** painel, clique em **publicar**.


## <a name="next-steps"></a>Próximos passos

Como em todas as alterações à política do Azure Information Protection, pode demorar até 15 minutos para que um computador que executa o cliente do Azure Information Protection conclua a transferência destes modelos. Para obter mais informações sobre como os computadores e os serviços transferem e atualizam modelos, veja [Atualizar modelos para utilizadores e serviços](refresh-templates.md).

Tudo o que pode configurar no portal do Azure para criar e gerir os seus modelos, pode fazer com o PowerShell. Além disso, o PowerShell fornece mais opções que não estão disponíveis no portal. Para obter mais informações, consulte [referência do PowerShell para modelos de proteção](configure-templates-with-powershell.md). 

Para mais informações sobre como configurar a política do Azure Information Protection, utilize as ligações na secção [Configurar política da organização](configure-policy.md#configuring-your-organizations-policy).  

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
