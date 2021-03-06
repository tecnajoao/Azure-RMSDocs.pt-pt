---
title: Migrar a partir do portal clássico do Azure – AIP
description: Tarefas de administração em breve no portal do Azure que utilizou para fazer no portal clássico do Azure
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 04/04/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 57a1073c-02e0-441b-bf49-c6b72fdba24f
ms.reviewer: demizets
ms.suite: ems
ms.openlocfilehash: 818d1f16d28a2d2b1b485aab9ddfdff5b9d814a9
ms.sourcegitcommit: 465709879998fcb78cd2a4efda559c43ed661dda
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/08/2019
ms.locfileid: "59233756"
---
# <a name="tasks-that-you-used-to-do-with-the-azure-classic-portal"></a>Tarefas que costumava realizar com o portal clássico do Azure

>*Aplica-se a: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Utilizado para portal clássico do Azure para gerir o serviço Azure Rights Management e precisam de algumas ajuda a transitar para o portal do Azure?

Portal clássico do Azure extinto **08 de Janeiro de 2018**. Após esta data, não será capaz de gerir o serviço Azure Rights Management e os modelos personalizados no portal clássico. Se tentar aceder ao portal clássico, verá um link que leva-o para o novo portal do Azure.

Para obter mais informações sobre a extinção do portal clássica, consulte a mensagem de anúncio do blogue: [Caminhando para o futuro da experiência de administrador do Azure AD: portal clássico do Azure a extinguir](https://cloudblogs.microsoft.com/enterprisemobility/2017/09/18/marching-into-the-future-of-the-azure-ad-admin-experience-retiring-the-azure-classic-portal/). Para a extensão temporária para a data de retirada original, consulte [atualização sobre a extinção da experiência do portal clássico do Azure AD e migração de políticas de acesso condicional](https://cloudblogs.microsoft.com/enterprisemobility/2017/11/29/update-on-retirement-of-azure-ad-classic-portal-experience-and-migration-of-conditional-access-policies/).

## <a name="how-to-do-your-familiar-admin-tasks"></a>Como fazer as tarefas administrativas familiares

Utilize as seguintes informações para ajudá-lo rapidamente a transição para o portal atual.

|Portal clássico do Azure|Como efetuar esta tarefa no portal do Azure
|-----------|--------------------|
|As definições de configuração de acesso pela primeira vez|1. [Inicie sessão no portal do Azure](configure-policy.md#signing-in-to-the-azure-portal).<br /><br />2. Siga as instruções para [para aceder ao painel de proteção de informações do Azure pela primeira vez](configure-policy.md#to-access-the-azure-information-protection-blade-for-the-first-time).
|Criar um novo modelo|Criar uma etiqueta que aplica a proteção e utilizar **definir permissões** para definir as permissões, a expiração e o acesso offline. <br /><br />Nos bastidores, esta configuração cria um novo modelo personalizado que pode ser acedido por serviços e aplicações que se integram nos modelos do Rights Management.<br /><br />Para obter mais informações, consulte [para criar um novo modelo](configure-policy-templates.md#to-create-a-new-template).
|Edite propriedades do modelo: <br /><br />-Modelo nome e descrição<br /><br />-Direitos de utilização, expiração de conteúdo e definições de acesso offline|Se ainda não fez isso, [converter o modelo numa etiqueta](configure-policy-templates.md#to-convert-templates-to-labels), e, em seguida, faça o seguinte<br /><br />1. Alterar o nome de etiqueta e descrição<br /><br />2. Altere as definições de proteção no rótulo para atualizar as permissões, a expiração e as definições de acesso offline.<br /><br />Para obter mais informações, consulte [para configurar uma etiqueta para as definições de proteção](configure-policy-protection.md#to-configure-a-label-for-protection-settings).
|Arquivar um modelo|Definir o estado de etiqueta como **desativado**.
|Criar um modelo com âmbito|Criar uma política de âmbito e criar uma etiqueta neste âmbito que se aplica a proteção. <br /><br />Para obter mais informações, consulte [como configurar a política do Azure Information Protection para utilizadores específicos com políticas de âmbito](configure-policy-scope.md).
|Copiar um modelo|Não é possível copiar um modelo no portal do Azure. Se quiser duas etiquetas para que as mesmas definições de proteção, tem de definir as permissões em cada etiqueta. <br /><br />Para obter mais informações, consulte [para configurar uma etiqueta para as definições de proteção](configure-policy-protection.md#to-configure-a-label-for-protection-settings).
|Eliminar um modelo|A eliminar modelos pode resultar em dados inacessíveis, para que o portal do Azure não suporta esta ação. No entanto, pode eliminar a etiqueta e, em seguida, utilizar o PowerShell [Remove-AadrmTemplate](/powershell/module/aadrm/remove-aadrmtemplate) cmdlet para remover o modelo. <br /><br />Para obter mais informações, consulte [como eliminar ou reordenar uma etiqueta do Azure Information Protection](configure-policy-delete-reorder.md).
|Suporte a vários idiomas|Do **Manage** seleção de menu, selecione **idiomas** para exportar os campos personalizáveis que incluem o nome do modelo e a descrição. Traduzir as cadeias de caracteres e, em seguida, importar essas cadeias de caracteres para o portal. <br /><br />Para obter mais informações, consulte [como configurar etiquetas e modelos para diferentes idiomas no Azure Information Protection](configure-policy-languages.md).
|Relatórios de web de gestão de direitos|[Centralizado de relatórios do Azure Information Protection](reports-aip.md) está agora em pré-visualização.<br /><br />Também pode utilizar o PowerShell [Get-AadrmUsageLog](/powershell/module/aadrm/Get-AadrmUsageLog) cmdlet para transferir os registos de utilização para o serviço Azure Rights Management. Em seguida, pode utilizar estes dados para criar relatórios personalizados. Para obter mais informações, consulte [Registar e analisar a utilização do serviço Azure Rights Management](log-analyze-usage.md).
|Ativar e desativar o serviço de Rights Management|Do **Manage** opções de menu, selecionadas **ativação de proteção**.<br /><br />Para obter mais informações, consulte [como ativar o Azure Rights Management a partir do portal do Azure](activate-azure.md).

Antes de edita os modelos ou convertê-los em etiquetas no portal do Azure, veja [considerações para modelos no portal do Azure](configure-policy-templates.md#considerations-for-templates-in-the-azure-portal).


## <a name="what-else-has-changed"></a>O que mais foi alterado

Nova funcionalidade no portal do Azure:

- Pode editar a [modelos predefinidos](configure-policy-templates.md#default-templates) que são criadas automaticamente para a sua organização.

- Pode converter modelos em etiquetas, para que gerir um único objeto em vez de gerir um modelo e identificar de forma independente. Para obter instruções, consulte [para converter modelos em etiquetas](configure-policy-templates.md#to-convert-templates-to-labels).

- Suporte para outras funções de administrador: Enquanto tiver de iniciar sessão no portal clássico do Azure como Administrador Global para configurar o Azure Rights Management, pode iniciar sessão no portal do Azure para configurar o Azure Information Protection com uma conta que tenha as seguintes funções administrativas: **Administrador global**, **administrador de segurança**, **administrador de conformidade**, ou **administrador do Information Protection**. Para obter mais informações sobre cada uma destas funções, consulte a [funções disponíveis](/azure/active-directory/active-directory-assign-admin-roles-azure-portal#available-roles) secção da documentação do Azure Active Directory.

Os cmdlets do PowerShell para criar e gerir modelos e para ativar ou desativar o serviço, ser suportados sem alterações.

## <a name="see-also"></a>Consulte também
Para obter mais informações, consulte [configurando e gerenciando modelos na política do Azure Information Protection](configure-policy-templates.md).

