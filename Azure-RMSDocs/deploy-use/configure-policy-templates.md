---
title: "Configurar e gerir modelos na política do Azure Information Protection"
description: "Atualmente em pré-visualização, já pode configurar e gerir modelos de gestão de direitos da política do Azure Information Protection."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 05/30/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 8301aabb-047d-4892-935c-7574f6af8813
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: 1f41aad2d132e087e9122b2683be4b45185527de
ms.sourcegitcommit: 04eb4990e2bf0004684221592cb93df35e6acebe
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/30/2017
---
<a id="configuring-and-managing-templates-in-the-azure-information-protection-policy" class="xliff"></a>

# Configurar e gerir modelos na política do Azure Information Protection

>*Aplica-se a: Azure Information Protection*

>[!NOTE]
>Esta funcionalidade está atualmente em pré-visualização e está sujeita a alterações frequentes.
>
>Antes de testar esta capacidade de pré-visualização com os modelos personalizados que criou no portal clássico do Azure, considere se tem uma cópia de segurança recente dos modelos. Pode fazer uma cópia de segurança dos seus modelos personalizados com o cmdlet do PowerShell [Export-AadrmTemplate](/powershell/module/aadrm/export-aadrmtemplate) e, se necessário, utilize o [Import-AadrmTemplate](/powershell/module/aadrm/import-aadrmtemplate) para os restaurar.
>
>Devido às diferenças na implementação, não recomendamos que gira os mesmos modelos do portal clássico do Azure e o portal do Azure.


Os modelos de gestão de direitos estão agora integrados com a política do Azure Information Protection. 

**Quando tem uma subscrição que inclui a classificação, a etiquetagem e a proteção (Azure Information Protection P1 ou P2):**

- Os modelos de gestão de direitos para o seu inquilino são apresentados na nova secção **Modelos** depois das etiquetas. Pode converter estes modelos em etiquetas ou pode continuar a geri-los como modelos separados e ligá-los ao configurar a proteção das etiquetas. 

**Quando tem uma subscrição que inclui apenas proteção (uma subscrição do Office 365 que inclui o serviço Azure Rights Management):**

- Os modelos de gestão de direitos do seu inquilino são apresentados como etiquetas e, atualmente, as definições de configuração que são específicas para classificação e etiquetagem também estão disponíveis. 


<a id="considerations-for-templates-in-the-azure-portal" class="xliff"></a>

## Considerações para modelos no portal do Azure

Antes de editar estes modelos ou convertê-los em etiquetas no portal do Azure, esteja ciente das seguintes alterações na implementação de gestão de modelos no portal clássico do Azure. Algumas limitações devem ser tratadas durante a pré-visualização:

- Depois de editar ou converter um modelo e guardar a política do Azure Information Protection, as seguintes alterações são feitas nos [direitos de utilização](configure-usage-rights.md) originais. Se for preciso, pode adicionar ou remover direitos de utilização individuais através do PowerShell com os cmdlets [New-AadrmRightsDefinition](/powershell/module/aadrm/set-aadrmtemplateproperty) e [Set-AadrmTemplateProperty](/powershell/module/aadrm/new-aadrmrightsdefinition).
    
    - **Guardar como, Exportar** (nome comum) é removido. No portal do Azure, não pode especificar manualmente este direito de utilização, mas este está incluído no direito de utilização do Controlo Total, que pode adicionar se for apropriado.
    
    - **Permitir Macros** (nome comum) é adicionado automaticamente. Este direito de utilização é preciso para a barra do Azure Information Protection nas aplicações do Office.
    
- Atualmente, os modelos predefinidos são apresentados, mas não podem ser editados ou convertidos. 

- Não pode copiar ou eliminar um modelo. Para remover um modelo, utilize o cmdlet do PowerShell [Remove-AadrmTemplate](/powershell/module/aadrm/remove-aadrmtemplate). 

- Atualmente, os modelos que foram configurados para idiomas com o portal clássico do Azure ou o PowerShell não apresentam esses idiomas para o nome e para as descrições, mas são mantidos.

- As definições **Publicado** e **Arquivado** são apresentadas como **Ativado**: **Ligado** e **Ativado**: **Desligado** respetivamente no painel **Etiqueta**.

- Os modelos departamentais (modelos que estão configurados para um âmbito) são apresentados na política Global. Atualmente, se editar e guardar um modelo departamental, este remove a configuração do âmbito. O equivalente de um modelo com âmbito na política do Azure Information Protection é uma [política com âmbito](configure-policy-scope.md). Se converter o modelo numa etiqueta, pode selecionar um âmbito existente.
    
    Além disso, atualmente não pode definir a definição de compatibilidade aplicacional para um modelo departamental. Se for necessário, pode definir esta opção através do PowerShell com o cmdlet [Set-AadrmTemplateProperty](/powershell/module/aadrm/set-aadrmtemplateproperty).

- O utilizador não cria um novo modelo a partir do contentor **Modelos**; em vez disso, cria uma etiqueta com a definição **Proteger** e configura os direitos de utilização e as definições a partir do painel **Proteção**. Para obter todas as instruções, veja [Criar um novo modelo](#to-create-a-new-template).

<a id="to-configure-the-templates-in-the-azure-information-protection-policy" class="xliff"></a>

## Para configurar os modelos na política do Azure Information Protection

1. Numa nova janela de browser, inicie sessão no [portal do Azure](https://portal.azure.com) como administrador de segurança ou administrador global.

2. Navegue para o painel **Azure Information Protection**: por exemplo, no menu do hub, clique em **Mais serviços** e comece a escrever **Information Protection** na caixa Filtro. Na lista de resultados, selecione **Azure Information Protection**. 

2. Se o modelo que pretende configurar se aplicar a todos os utilizadores, selecione **Global** no painel **Azure Information Protection**. Contudo, se o modelo que pretende configurar estiver numa [política de âmbito](configure-policy-scope.md) para que seja aplicado apenas a utilizadores selecionados, então selecione essa política de âmbito.

3. No painel de política, encontre o modelo que pretende configurar:
    
    - Quando tem uma subscrição que inclui a classificação, a etiquetagem e a proteção: expanda **Modelos** depois das suas etiquetas.
    
    - Quando tem uma subscrição que inclui apenas proteção: os modelos são apresentados como etiquetas.

4. Selecione o modelo e, no painel **Etiqueta**, pode alterar o nome do modelo e a descrição, se necessário, ao editar o **Nome da etiqueta** e a **Descrição**. Em seguida, selecione **Proteção**, que tem um valor de **Azure RMS**, para abrir o painel **Proteção**.

5. No painel **Proteção**, pode alterar as permissões, a expiração de conteúdo e as definições de acesso offline. Para obter mais informações, sobre a configuração das definições de proteção, veja [Como configurar uma etiqueta para a proteção do Rights Management](configure-policy-protection.md)
    
    Clique em **OK** para manter as suas alterações e, no painel **Etiqueta**, clique em **Guardar**.

6. Para disponibilizar as alterações às aplicações e serviços dos utilizadores, no painel **Azure Information Protection**, clique em **Publicar**.

<a id="to-convert-templates-to-labels" class="xliff"></a>

## Converter modelos em etiquetas

Quando tem uma subscrição que inclui a classificação, a etiquetagem e a proteção, pode converter um modelo numa etiqueta. Quando o faz, o modelo original é mantido mas, no portal do Azure, é apresentado agora como incluído numa nova etiqueta.

Por exemplo, se converter uma etiqueta denominada **Marketing** que concede direitos de utilização ao grupo de marketing, no portal do Azure é agora apresentada como uma etiqueta denominada **Marketing** que tem as mesmas definições de proteção. Se alterar as definições de proteção nesta etiqueta criada recentemente, está a alterá-las no modelo e qualquer utilizador ou serviço que utilize este modelo irá obter as novas definições de proteção com a próxima atualização do modelo. 

Não existe nenhum requisito para converter todos os modelos em etiquetas, mas, quando o fizer, as definições de proteção são totalmente integradas com a funcionalidade completa de etiquetas para que não precise de manter as definições separadamente.

Para converter um modelo numa etiqueta, clique com o botão direito no rato no modelo e selecione **Converter em etiqueta**. Em alternativa, utilize o menu de contexto para selecionar esta opção.

Ao converter um modelo numa etiqueta:

- O nome do modelo é convertido num novo nome de etiqueta e a descrição do modelo é convertida na descrição da etiqueta. 

- Se o estado do modelo for publicado, esta definição é mapeada para **Ativado**: **Ligado** na etiqueta, que é agora apresentada como esta etiqueta para os utilizadores quando voltar a publicar a política do Azure Information Protection. Se o estado do modelo for arquivado, esta definição é mapeada para **Ativado**: **Desligado** para a etiqueta e não é apresentada como uma etiqueta disponível aos utilizadores.

- As definições de proteção são mantidas e pode editá-las se for necessário, além de adicionar outras definições de etiqueta como marcadores visuais e condições.

- O modelo original deixará de ser apresentado em **Modelos** e, para o editar no portal do Azure, edita agora a etiqueta que foi criada. O modelo permanece disponível para o serviço Azure Rights Management e ainda pode ser gerido com os [comandos do PowerShell](administer-powershell.md).  

<a id="to-create-a-new-template" class="xliff"></a>

## Criar um novo modelo

Ao criar um novo modelo com a definição de proteção do **Azure RMS**, nos bastidores, esta ação cria um novo modelo personalizado que pode ser acedido por serviços e aplicações que se integram nos modelos do Rights Management.

1. Se o novo modelo que pretende criar se aplicar a todos os utilizadores, no painel **Política: Global**, clique em **Adicionar uma nova etiqueta**.
    
     Se a nova etiqueta que pretende criar for um modelo departamental, para ser aplicada apenas a utilizadores selecionados, selecione ou crie primeiro uma política de âmbito no painel inicial do **Azure Information Protection**.

2. No painel **Etiqueta**, mantenha a predefinição de **Ativado**: **Ligado** para publicar este novo modelo, ou altere esta definição para **Desligado** para criar o modelo como arquivado. Em seguida, insira um nome de etiqueta e descrição para o nome do modelo e a descrição.

3. Para **Defina permissões para documentos e e-mails que contenham esta etiqueta**, selecione **Proteger** e, em seguida, selecione **Proteção**:
    
     ![Configurar a proteção para uma etiqueta do Azure Information Protection](../media/info-protect-protection-bar.png)

4. No painel **Proteção**, pode alterar as permissões, a expiração de conteúdo e as definições de acesso offline. Para obter mais informações sobre a configuração destas definições de proteção, veja [Como configurar uma etiqueta para a proteção do Rights Management](configure-policy-protection.md)
    
    Clique em **OK** para manter as suas alterações e, no painel **Etiqueta**, clique em **Guardar**.

5. Para disponibilizar estes modelos às aplicações e serviços dos utilizadores, no painel **Azure Information Protection**, clique em **Publicar**.


<a id="next-steps" class="xliff"></a>

## Próximos passos

Como em todas as alterações à política do Azure Information Protection, pode demorar até 15 minutos para que um computador que executa o cliente do Azure Information Protection conclua a transferência destes modelos. Para obter mais informações sobre como os computadores e os serviços transferem e atualizam modelos, veja [Atualizar modelos para utilizadores e serviços](refresh-templates.md).

Para mais informações sobre como configurar a política do Azure Information Protection, utilize as ligações na secção [Configurar política da organização](configure-policy.md#configuring-your-organizations-policy).  

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
