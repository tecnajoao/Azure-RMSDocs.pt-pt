---
title: "Ativar o Azure RMS com o portal do Azure clássico – AIP"
description: "Instruções de ativação para o serviço Azure Rights Management quando tem acesso ao portal do Azure. Por exemplo, tem uma subscrição para o Enterprise Mobility Suite ou a subscrição do Azure Information Protection Premium."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 04/07/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 9b0a0227-88ce-44b8-ba3f-31eeaab27ff7
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 7400cb489d3930ef1436bb3b08def5bf673c2bbf
ms.sourcegitcommit: 7b773ca5bf1abf30e527c34717ecb2dc96f88033
translationtype: HT
---
# <a name="how-to-activate-azure-rights-management-from-the-azure-classic-portal"></a>Como ativar o Azure Rights Management a partir do portal clássico do Azure

>*Aplica-se a: Azure Information Protection*


Utilize estas instruções se tiver acesso ao portal do Azure. Por exemplo, tem uma subscrição para o Enterprise Mobility Suite ou a subscrição do Azure Information Protection Premium.

> [!TIP]
> Veja um vídeo de 2 minutos: [Como ativar o Azure RMS](https://channel9.msdn.com/series/pit-stop-enterprise-mobility-suite/activate-azure-rms)

1.  Depois de se ter inscrito na a sua conta Azure, [inicie sessão no portal clássico do Azure](http://go.microsoft.com/fwlink/p/?LinkID=275081). Utilize uma conta de administrador global, tal como a conta que utilizou para obter a subscrição que inclui o Azure Rights Management.

2.  No painel esquerdo, clique em **ACTIVE DIRECTORY**.

3.  Na página **active directory**, clique em **RIGHTS MANAGEMENT**.

4.  Selecione o diretório a gerir para o [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)], clique em **ATIVAR** e confirme a ação.

    > [!NOTE]
    >Se vir um erro de ativação, poderá dever-se ao facto de o seu plano de serviços ou versão de produtos não incluir o serviço Azure Rights Management para o Azure Information Protection.
    >
    >Para ativar o serviço Azure Rights Management, precisa de ter um [plano Premium do Azure Information Protection](https://www.microsoft.com/cloud-platform/azure-information-protection-pricing) ou um [plano do Office 365 que inclua o Rights Management](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf). Para obter ajuda com este problema, envie uma mensagem de e-mail para [askipteam](mailto:askipteam?subject=I%20cannot%20activate%20RMS).


O **ESTADO DO RIGHTS MANAGEMENT** deverá agora apresentar **Ativo** e a opção **ATIVAR** é substituída por **DESATIVAR**.

## <a name="rights-management-status-values-and-descriptions-in-the-azure-classic-portal"></a>Valores e descrições do estado do Rights Management no portal clássico do Azure
Para além do estado **Ativo**, que indica que o serviço Rights Management está ativado e pronto a ser utilizado, também poderá ver **Inativo**, **Indisponível** ou **Não Autorizado**.

|Valor do estado|Descrição|
|----------------|---------------|
|**Ativo**|[!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] está ativado e pronto a utilizar.|
|**Inativo**|[!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] está desativado e tem de ser ativado para a sua organização poder proteger ficheiros.|
|**Indisponível**|O serviço [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] está inativo. Tente novamente mais tarde.|
|**Não Autorizado**|Não tem permissões para ver o estado do serviço [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)]. Por exemplo, a sua conta está bloqueada ou não é o administrador global do inquilino selecionado.|

## <a name="next-steps"></a>Passos seguintes
Volte a [Ativar o Azure Rights Management](activate-service.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]