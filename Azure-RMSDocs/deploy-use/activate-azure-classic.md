---
# required metadata

title: Como ativar o Azure Rights Management a partir do portal clássico do Azure | Azure RMS
description:
keywords:
author: cabailey
manager: mbaldwin
ms.date: 05/05/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 9b0a0227-88ce-44b8-ba3f-31eeaab27ff7

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: esaggese
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Como ativar o Azure Rights Management a partir do portal clássico do Azure

*Aplica-se a: Azure Rights Management*


Utilize estas instruções se tiver acesso ao portal do Azure. Por exemplo, tem uma subscrição do Enterprise Mobility Suite.

> [!TIP]
> Veja um vídeo de 2 minutos: [Como ativar o Azure RMS](https://channel9.msdn.com/series/pit-stop-enterprise-mobility-suite/activate-azure-rms)

1.  Depois de se ter inscrito para a sua conta do Azure, [inicie sessão no portal clássico do Azure](http://go.microsoft.com/fwlink/p/?LinkID=275081).

2.  No painel esquerdo, clique em **ACTIVE DIRECTORY**.

3.  Na página **active directory**, clique em **RIGHTS MANAGEMENT**..

4.  Selecione o diretório a gerir para o [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)], clique em **ATIVAR** e confirme a ação.

---

   Nota: se vir um erro de ativação, poderá ser porque a versão de produtos ou plano de serviço não inclui o [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)].

   Utilize as informações em [Subscrições na nuvem que suportam o Azure RMS](../get-started/requirements-subscriptions.md) para confirmar o suporte do RMS. Para obter ajuda com este problema, envie uma mensagem de e-mail para [askipteam](mailto:askipteam?subject=I%20cannot%20activate%20RMS).

---


O **ESTADO DO RIGHTS MANAGEMENT** deverá agora apresentar **Ativo** e a opção **ATIVAR** é substituída por **DESATIVAR**.

## Valores e descrições do estado do Rights Management no portal clássico do Azure
Para além do estado **Ativo**, que indica que o serviço Rights Management está ativado e pronto a ser utilizado, também poderá ver **Inativo**, **Indisponível** ou **Não Autorizado**.

|Valor do estado|Descrição|
|----------------|---------------|
|**Ativo**|[!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] está ativado e pronto a utilizar.|
|**Inativo**|[!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] está desativado e tem de ser ativado para a sua organização poder proteger ficheiros.|
|**Indisponível**|O serviço [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] está inativo. Tente novamente mais tarde.|
|**Não Autorizado**|Não tem permissões para ver o estado do serviço [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)]. Por exemplo, a sua conta está bloqueada ou não é o administrador global do inquilino selecionado.|

## Passos seguintes
Voltar a [Ativar o Azure Rights Management](activate-service.md).

<!--HONumber=May16_HO1-->

