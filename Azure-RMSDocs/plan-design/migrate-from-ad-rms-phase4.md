---
title: "Migrar do AD RMS para o Azure Information Protection – Fase 4 | Azure Information Protection"
description: "Fase 4 da migração do AD RMS para o Azure Information Protection, abrangendo os passos 8 a 9 de Migrar do AD RMS para o Azure Information Protection."
author: cabailey
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: d51e7bdd-2e5c-4304-98cc-cf2e7858557d
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: d7e21c2bb07e82bc243e5ab01c0a21aa0fe274d1
ms.openlocfilehash: 78b61500cb1e596ae469ecad650ab3d5ee27566d


---

# Fase 4 da migração – tarefas pós-migração

>*Aplica-se a: Serviços de Gestão de Direitos do Active Directory, Azure Information Protection, Office 365*


Utilize as seguintes informações para a Fase 4 da migração do AD RMS para o Azure Information Protection. Estes procedimentos incluem os passos 8 a 9 do tópico [Migrar do AD RMS para o Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md).


## Passo 8. Desativar o AD RMS

Opcional: remova o Ponto de Ligação de Serviço (SCP) do Active Directory para impedir que os computadores detetem a sua infraestrutura do Rights Management no local. Isto é opcional devido ao redirecionamento que foi configurado no registo (por exemplo, ao executar o script de migração). Para remover o Ponto de Ligação de Serviço, utilize a ferramenta de Registo de SCP do AD do [Conjunto de Ferramentas de Administração dos Serviços de Gestão de Direitos](http://www.microsoft.com/download/details.aspx?id=1479).

Monitorize a atividade dos seus servidores do AD RMS, por exemplo, ao verificar os [pedidos no relatório de Estado de Funcionamento do Sistema](https://technet.microsoft.com/library/ee221012%28v=ws.10%29.aspx), a [tabela ServiceRequest](http://technet.microsoft.com/library/dd772686%28v=ws.10%29.aspx) ou a [auditoria de acesso de utilizador a conteúdo protegido](http://social.technet.microsoft.com/wiki/contents/articles/3440.ad-rms-frequently-asked-questions-faq.aspx). Quando tiver confirmado que os clientes RMS já não estão a comunicar com estes servidores e que os clientes estão a utilizar o Azure Information Protection com êxito, pode remover a função de servidor do AD RMS destes servidores. Se estiver a utilizar servidores dedicados, poderá preferir o passo cautelar de começar por encerrar os servidores durante um período de tempo para se certificar de que não existem problemas comunicados que exijam reiniciar estes servidores para assegurar a continuidade do serviço enquanto estiver a investigar por que razão os clientes não estão a utilizar o Azure Information Protection.

Após a desativação dos servidores AD RMS, pode aproveitar a oportunidade para rever os modelos no portal clássico do Azure e consolidá-los para que os utilizadores tenham menos por onde escolher, reconfigurá-los ou até adicionar novos modelos. É também uma boa altura para publicar os modelos predefinidos. Para mais informações, consulte [Configurar modelos personalizados para o Azure Rights Management](../deploy-use/configure-custom-templates.md).

## Passo 9. Recodificar a chave de inquilino do Azure Information Protection
Este passo é aplicável apenas se a topologia de chave de inquilino escolhida for gerida pela Microsoft e não pelo cliente (BYOK com o Cofre de Chaves do Azure).

Este passo é opcional, mas recomendado quando a chave de inquilino do Azure Information Protection for gerida pela Microsoft e tiver sido migrada a partir do AD RMS. A recodificação neste cenário ajuda a proteger a chave de inquilino do Azure Information Protection contra potenciais falhas de segurança na chave do AD RMS.

Quando recodificar a chave de inquilino do Azure Information Protection (também conhecido como “implementar a chave”), é criada uma nova chave e a chave original é arquivada. No entanto, uma vez que a mudança de uma chave para outra não é imediata, mas sim um processo de algumas semanas, não espere até suspeitar que existe uma falha na chave original e recodifique a chave de inquilino do Azure Information Protection assim que a migração for concluída.

Para recodificar a chave de inquilino do Azure Information Protection gerida pela Microsoft, [contacte o Suporte da Microsoft](../get-started/information-support.md#to-contact-microsoft-support) e abra um **incidente de suporte do Azure Information Protection com um pedido de recodificação da chave de inquilino do Azure Information Protection após a migração a partir do AD RMS**. Tem de provar que é um administrador do inquilino do Azure Information Protection e compreender que este processo demorará vários dias a ser confirmado. São aplicáveis encargos de suporte padrão; a recodificação da chave de inquilino não é um serviço de suporte gratuito.


## Passos seguintes

Para mais informações sobre a gestão da chave de inquilino do Azure Information Protection, consulte [Operações para a chave de inquilino do Azure Rights Management](../deploy-use/operations-tenant-key.md).

Agora que concluiu a migração, consulte o [plano de implementação](deployment-roadmap.md) para identificar quaisquer outras tarefas de implementação que tenha de efetuar.




<!--HONumber=Sep16_HO4-->


