---
title: "Migrar a partir do portal clássico do Azure - AIP"
description: "Tarefas de administração de uma rapidamente no portal do Azure que utilizou para fazer no portal clássico do Azure"
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/20/2018
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 57a1073c-02e0-441b-bf49-c6b72fdba24f
ms.reviewer: demizets
ms.suite: ems
ms.openlocfilehash: 25604d8537aedb4421b460850ce34723c8047964
ms.sourcegitcommit: 67750454f8fa86d12772a0075a1d01a69f167bcb
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/23/2018
---
# <a name="tasks-that-you-used-to-do-with-the-azure-classic-portal"></a>Tarefas que utilizou para fazer com o portal clássico do Azure

>*Aplica-se a: Azure Information Protection, Office 365*

Utilizado para o portal clássico do Azure para gerir o serviço Azure Rights Management e precisarem de alguns ajudar a transição para o portal do Azure?

Portal clássico do Azure extinto **08 de Janeiro de 2018**. Após esta data, não será capaz de gerir o serviço Azure Rights Management e os modelos personalizados no portal clássico. Se tentar aceder ao portal clássico, verá uma ligação que leva-o para o novo portal do Azure.

Para mais informações sobre a extinção do portal clássica, consulte o anúncio de mensagem de blogue: [Marching no futuro da experiência de administração do Azure AD: extinguir o portal clássico do Azure](https://cloudblogs.microsoft.com/enterprisemobility/2017/09/18/marching-into-the-future-of-the-azure-ad-admin-experience-retiring-the-azure-classic-portal/). Para a extensão temporária para a data de retirada original, consulte [atualizações de extinção de experiência do portal clássica do Azure AD e a migração de políticas de acesso condicional](https://cloudblogs.microsoft.com/enterprisemobility/2017/11/29/update-on-retirement-of-azure-ad-classic-portal-experience-and-migration-of-conditional-access-policies/).

## <a name="how-to-do-your-familiar-admin-tasks"></a>Como fazer as tarefas administrativas familiar

Utilize as seguintes informações para ajudá-lo rapidamente transição para o portal atual.

No entanto, os clientes que tem uma subscrição para o Office 365 US Government (nuvem de Comunidade Government) atualmente não é possível utilizar o portal do Azure em, em vez disso, tem de utilizar [PowerShell](configure-templates-with-powershell.md) para gerir os seus modelos.


|Portal clássico do Azure|Como efetuar esta tarefa no portal do Azure
|-----------|--------------------|
|As definições de configuração de acesso pela primeira vez|1. [Inicie sessão no portal do Azure](configure-policy.md#signing-in-to-the-azure-portal).<br /><br />2. No hub menu, clique em **crie um recurso**e, em seguida, o **MARKETPLACE** lista, selecione **segurança + identidade**.<br /><br />3. No **segurança + identidade** painel, do **aplicações em destaque** lista, selecione **Azure Information Protection**. Em seguida, no **Azure Information Protection** painel, clique em **criar**.<br /><br />Esta ação cria o **Azure Information Protection** painel para que a próxima vez que iniciar sessão no portal, pode selecionar o serviço do hub **todos os serviços** lista.
|Criar um novo modelo|Criar uma etiqueta que se aplica a proteção e utilizar **definir permissões** para definir as permissões, a expiração e acesso offline. <br /><br />Nos bastidores, esta configuração cria um novo modelo personalizado que possam ser acedido por serviços e aplicações que se integram com modelos do Rights Management.<br /><br />Para obter mais informações, consulte [para criar um novo modelo](configure-policy-templates.md#to-create-a-new-template).
|Edite propriedades do modelo: <br /><br />-Modelo nome e descrição<br /><br />-Direitos de utilização, a expiração de conteúdo e definições de acesso offline|Se ainda não o tiver feito deste modo, [converter o modelo para uma etiqueta](configure-policy-templates.md#to-convert-templates-to-labels), e, em seguida, efetue o seguinte<br /><br />1. Alterar o nome de etiqueta e descrição<br /><br />2. Altere as definições de proteção na etiqueta para atualizar as permissões, a expiração e as definições de acesso offline.<br /><br />Para obter mais informações, consulte [para configurar uma etiqueta para a proteção Rights Management](configure-policy-protection.md#to-configure-a-label-for-rights-management-protection).
|Arquivar um modelo|Defina o estado da etiqueta **desativado**.
|Criar um modelo de âmbito|Criar uma política no âmbito e criar uma etiqueta neste âmbito que se aplica proteção. <br /><br />Para obter mais informações, consulte [como configurar a política do Azure Information Protection para utilizadores específicos através da utilização de políticas de âmbito](configure-policy-scope.md).
|Copiar um modelo|Não é possível copiar um modelo no portal do Azure. Se quiser duas etiquetas ter as mesmas definições de proteção, tem de definir as permissões em cada etiqueta. <br /><br />Para obter mais informações, consulte [para configurar uma etiqueta para a proteção Rights Management](configure-policy-protection.md#to-configure-a-label-for-rights-management-protection).
|Eliminar um modelo|Eliminar modelos pode resultar em dados inacessíveis, pelo que o portal do Azure não suporta esta ação. No entanto, pode eliminar a etiqueta e, em seguida, utilizar o PowerShell [Remove-AadrmTemplate](/powershell/module/aadrm/remove-aadrmtemplate) cmdlet para remover o modelo. <br /><br />Para obter mais informações, consulte [como eliminar ou reordenar uma etiqueta para o Azure Information Protection](configure-policy-delete-reorder.md).
|Suporte de vários idiomas|Do **GERIR** selecção de menu, selecione **idiomas** para exportar os campos personalizáveis, que incluem o nome do modelo e a descrição. Traduzir as cadeias e, em seguida, importe estes cadeias para o portal. <br /><br />Para obter mais informações, consulte [como configurar as etiquetas e modelos para idiomas diferentes no Azure Information Protection](configure-policy-languages.md).
|Os relatórios de gestão de direitos|Utilizar o PowerShell [Get-AadrmUsageLog](/powershell/module/aadrm/Get-AadrmUsageLog) cmdlet para transferir os registos de utilização para o serviço Azure Rights Management. Em seguida, pode utilizar estes dados para criar relatórios personalizados. <br /><br />Para obter mais informações, consulte [Registar e analisar a utilização do serviço Azure Rights Management](log-analyze-usage.md).<br /><br />Sugestão: Procure anúncios no [blogue Enterprise Mobility and Security](https://cloudblogs.microsoft.com/enterprisemobility/?product=azure-information-protection) para uma solução de relatórios nova e centralizada para o Azure Information Protection.
|Ativar e desativar o serviço Rights Management|Do **GERIR** opções de menu, selecionadas **definições RMS** ou **ativação da proteção**. Esta opção está no processo de ser mudado.<br /><br />Para obter mais informações, consulte [como ativar o Azure Rights Management a partir do portal do Azure](activate-azure.md).

Antes de editar os modelos ou convertê-las em etiquetas no portal do Azure, consulte [considerações para modelos no portal do Azure](configure-policy-templates.md#considerations-for-templates-in-the-azure-portal).


## <a name="what-else-has-changed"></a>Que outros problemas foi alterada

Nova funcionalidade no portal do Azure:

- Pode editar o [modelos predefinidos](configure-policy-templates.md#default-templates) que são criadas automaticamente para a sua organização.

- Pode converter modelos etiquetas, para que gerir um único objeto em vez de gerir um modelo e etiqueta de forma independente. Para obter instruções, consulte [converter modelos etiquetas](configure-policy-templates.md#to-convert-templates-to-labels).

- Suporte para outras funções de administrador: enquanto tiver de iniciar sessão no portal clássico do Azure como um Administrador Global para configurar o Azure Rights Management, pode iniciar sessão portal do Azure para configurar o Azure Information Protection utilizando uma conta que tenha o funções administrativas a seguir: Administrador Global, o administrador de segurança ou o administrador de proteção de informações. Para obter mais informações sobre cada uma destas funções, consulte o [funções disponíveis](/azure/active-directory/active-directory-assign-admin-roles-azure-portal#available-roles) secção de documentação do Azure Active Directory.

Os cmdlets do PowerShell para criar e gerir modelos e para ativar ou desativar o serviço, permanecem suportados sem alterações.

## <a name="see-also"></a>Consulte também
Para obter mais informações, consulte [configurar e gerir modelos de política do Azure Information Protection](../deploy-use/configure-policy-templates.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
