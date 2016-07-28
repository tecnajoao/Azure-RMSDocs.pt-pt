---
title: "Tutorial de início rápido do Azure Information Protection | Azure Rights Management"
description: "Um tutorial de apresentação para experimentar rapidamente o Microsoft Azure Information Protection na sua organização com apenas 4 passos que devem demorar menos de 15 minutos."
author: cabailey
manager: mbaldwin
ms.date: 07/16/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 1260b9e5-dba1-41de-84fd-609076587842
translationtype: Human Translation
ms.sourcegitcommit: cac95dec84f99d2e6caa3458dc8284defe2324bc
ms.openlocfilehash: 7dc988365c1fa86827d1a7edc33c0a2eb6180f0e


---

# Tutorial de início rápido do Azure Information Protection 

*Aplica-se a: pré-visualização do Azure Information Protection*

Utilize este tutorial para experimentar rapidamente o Microsoft Azure Information Protection na sua organização com apenas 4 passos que devem demorar menos de 15 minutos. Como opção, irá ativar o serviço Azure Rights Management, observar e modificar a política do Azure Information Protection predefinida, instalar o Azure Information Protection e, em seguida, utilizar um documento do Word para ver a classificação, as etiquetas e a proteção em ação.

Este tutorial destina-se a administradores de TI e consultores, para os ajudar a avaliar o Azure Information Protection como uma solução de proteção de informações empresariais para uma organização. Num ambiente de produção, as instruções para ativar o serviço, configurar a política de Information Protection e instalar o cliente para os utilizadores teriam de ser feitas por um administrador. As instruções para etiquetar o documento teriam de ser feitas por utilizadores finais. Ambos os conjuntos de instruções estão incluídos neste tutorial para demonstrar o cenário de ponto a ponto de classificação, etiquetagem e proteção dos dados da sua organização. 

Se tiver algum problema quando concluir este tutorial, utilizando a versão de pré-visualização do Azure Information Protection ou pretende ver o que se tem sido dito sobre esta aplicação, vá para o [site Yammer do Azure Information Protection](https://www.yammer.com/askipteam/#/threads/inGroup?type=in_group&feedId=8652489&view=all).

## Pré-requisitos 
Para concluir este tutorial, terá de ter o seguinte:

- Qualquer subscrição que inclua a Azure Rights Management, irá dar-lhe acesso à versão de pré-visualização do Azure Information Protection. O Azure Information Protection está disponível em todas as regiões que suportam a Azure Rights Management. Para obter mais informações sobre as subscrições e ligações disponíveis para as versões de avaliação gratuitas, veja [Requisitos do Azure RMS: subscrições na nuvem que suportam o Azure RMS](../get-started/requirements-subscriptions.md).

- Uma subscrição do Azure, para que possa aceder ao portal do Azure, para configurar a política do Azure Information Protection. Se ainda não tem uma subscrição do Azure para a sua organização, pode obter uma inscrevendo-se numa versão de avaliação gratuita: aceda à [página Introdução ao Azure](https://account.windowsazure.com/organization) e siga as instruções.

  > [!TIP] 
  > Se precisar de obter uma ou ambas as subscrições, faça o seguinte com antecedência porque este processo pode, por vezes, demorar algum tempo a concluir.

- Uma conta de administrador global para iniciar sessão no centro de administração do Office 365 ou no portal clássico do Azure se necessitar de ativar o serviço Rights Management. Esta conta também tem de ter um endereço de e-mail e um serviço de e-mail a funcionar (por exemplo, Exchange Online ou Exchange Server).

- Um computador que execute o Windows (no mínimo, o Windows 7 com o Service Pack 1) e que tenha instalado o Office 2016, Office 2013 com o Service Pack 1 ou o Office 2010. 

- Se tiver o Active Directory Rights Management Services (AD RMS) implementado na sua organização: o computador tem de ser um computador de grupo de trabalho que não tenha utilizado anteriormente AD RMS. Isto é necessário se quiser proteger documentos e assegura que o computador transfere modelos apenas a partir do Azure Rights Management. Um computador não pode ligar ao AD RMS e ao Azure RMS ao mesmo tempo. Se estiver interessado em informações sobre migração, veja [Migrar do AD RMS para o Azure Rights Management](../plan-design/migrate-from-ad-rms-to-azure-rms.md).   

Vamos começar.

>[!div class="step-by-step"]
[&#187; Passo 1](infoprotect-tutorial-step1.md)





<!--HONumber=Jul16_HO3-->


