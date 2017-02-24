---
title: "Migrar do AD RMS para o Azure Information Protection – Fase 4 | Azure Information Protection"
description: "Fase 4 da migração do AD RMS para o Azure Information Protection, abrangendo os passos 8 a 9 de Migrar do AD RMS para o Azure Information Protection."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/08/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: d51e7bdd-2e5c-4304-98cc-cf2e7858557d
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: e45bbfe0fc2b064d987016cac8af8c4f57d465c9
ms.openlocfilehash: e10b271872935b7903a3e1bcfe2e8287e693c613


---

# <a name="migration-phase-4---post-migration-tasks"></a>Fase 4 da migração – tarefas pós-migração

>*Aplica-se a: Serviços de Gestão de Direitos do Active Directory, Azure Information Protection, Office 365*


Utilize as seguintes informações para a Fase 4 da migração do AD RMS para o Azure Information Protection. Estes procedimentos incluem os passos 8 a 9 do tópico [Migrar do AD RMS para o Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md).


## <a name="step-8-decommission-ad-rms"></a>Passo 8. Desativar o AD RMS

Remova o Ponto de Ligação de Serviço (SCP) do Active Directory para impedir que os computadores detetem a sua infraestrutura da Gestão de Direitos no local. Isto é opcional para os clientes existentes que migraram devido ao redirecionamento que foi configurado no registo (por exemplo, ao executar o script de migração). No entanto, remover o SCP impede que novos clientes e potenciais serviços e ferramentas relacionados com o RMS localizem o SCP quando a migração estiver concluída e que todas as ligações sejam ligadas ao serviço do Azure Rights Management. 

Para remover o SCP, garanta que tem sessão iniciada como administrador da empresa do domínio e, em seguida, utilize o seguinte procedimento:

1. Na consola Serviços de Gestão de Direitos do Active Directory, clique com o botão direito do rato no cluster do AD RMS e, em seguida, clique em **Propriedades**.

2. Clique no separador **SCP**.

3. Selecione a caixa de verificação **Alterar SCP**.

4. Selecione **Remover SCP atual** e, em seguida, clique em **OK**.

Monitorize a atividade dos seus servidores do AD RMS, por exemplo, ao verificar os [pedidos no relatório de Estado de Funcionamento do Sistema](https://technet.microsoft.com/library/ee221012%28v=ws.10%29.aspx), a [tabela ServiceRequest](http://technet.microsoft.com/library/dd772686%28v=ws.10%29.aspx) ou a [auditoria de acesso de utilizador a conteúdo protegido](http://social.technet.microsoft.com/wiki/contents/articles/3440.ad-rms-frequently-asked-questions-faq.aspx). Quando tiver confirmado que os clientes RMS já não estão a comunicar com estes servidores e que os clientes estão a utilizar o Azure Information Protection com êxito, pode remover a função de servidor do AD RMS destes servidores. Se estiver a utilizar servidores dedicados, poderá preferir o passo cautelar de começar por encerrar os servidores durante um período de tempo para se certificar de que não existem problemas comunicados que exijam reiniciar estes servidores para assegurar a continuidade do serviço enquanto estiver a investigar por que razão os clientes não estão a utilizar o Azure Information Protection.

Após a desativação dos servidores AD RMS, pode aproveitar a oportunidade para rever os modelos no portal clássico do Azure e consolidá-los para que os utilizadores tenham menos por onde escolher, reconfigurá-los ou até adicionar novos modelos. É também uma boa altura para publicar os modelos predefinidos. Para mais informações, consulte [Configurar modelos personalizados para o serviço Azure Rights Management](../deploy-use/configure-custom-templates.md).

## <a name="step-9-re-key-your-azure-information-protection-tenant-key"></a>Passo 9. Recodificar a chave de inquilino do Azure Information Protection
Este passo é aplicável apenas se a topologia de chave de inquilino escolhida for gerida pela Microsoft e não pelo cliente (BYOK com o Cofre de Chaves do Azure).

Este passo é opcional, mas recomendado quando a chave de inquilino do Azure Information Protection for gerida pela Microsoft e tiver sido migrada a partir do AD RMS. A recodificação neste cenário ajuda a proteger a chave de inquilino do Azure Information Protection contra potenciais falhas de segurança na chave do AD RMS.

Quando recodificar a chave de inquilino do Azure Information Protection (também conhecido como "implementar a chave"), é criada uma nova chave e a chave original é arquivada. No entanto, uma vez que a mudança de uma chave para outra não é imediata, mas sim um processo de algumas semanas, não espere até suspeitar que existe uma falha na chave original e recodifique a chave de inquilino do Azure Information Protection assim que a migração for concluída.

Para recodificar a chave de inquilino do Azure Information Protection gerida pela Microsoft, [contacte o Suporte da Microsoft](../get-started/information-support.md#to-contact-microsoft-support) e abra um **incidente de suporte do Azure Information Protection com um pedido de recodificação da chave de inquilino do Azure Information Protection após a migração a partir do AD RMS**. Tem de provar que é um administrador do inquilino do Azure Information Protection e compreender que este processo demorará vários dias a ser confirmado. São aplicáveis encargos de suporte padrão; a recodificação da chave de inquilino não é um serviço de suporte gratuito.


## <a name="next-steps"></a>Passos seguintes

Para mais informações sobre a gestão da chave de inquilino do Azure Information Protection, consulte [Operações para a chave de inquilino do Azure Rights Management](../deploy-use/operations-tenant-key.md).

Agora que concluiu a migração, consulte o [plano de implementação](deployment-roadmap.md) para identificar quaisquer outras tarefas de implementação que tenha de efetuar.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]



<!--HONumber=Feb17_HO2-->


