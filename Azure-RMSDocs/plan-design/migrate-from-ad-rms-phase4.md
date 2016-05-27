---
# required metadata

title: Migrar do AD RMS para o Azure Rights Management – Fase 4 | Azure RMS
description:
keywords:
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: d51e7bdd-2e5c-4304-98cc-cf2e7858557d


# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: esaggese
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Fase 4 da migração – tarefas pós-migração

*Aplica-se a: Serviços de Gestão de Direitos do Active Directory, Azure Rights Management*


Utilize as seguintes informações para a Fase 4 da migração do AD RMS para o Azure Rights Management (Azure RMS). Estes procedimentos incluem os passos 8 a 9 da secção [Migrar do AD RMS para o Azure Rights Management](migrate-from-ad-rms-to-azure-rms.md).


## Passo 8. Desativar o AD RMS

Opcional: remova o Ponto de Ligação de Serviço (SCP) do Active Directory para impedir que os computadores detetem a sua infraestrutura do Rights Management no local. Isto é opcional devido ao redirecionamento que foi configurado no registo (por exemplo, ao executar o script de migração). Para remover o Ponto de Ligação de Serviço, utilize a ferramenta de Registo de SCP do AD do [Conjunto de Ferramentas de Administração dos Serviços de Gestão de Direitos](http://www.microsoft.com/download/details.aspx?id=1479).

Monitorize a atividade dos seus servidores AD RMS, por exemplo, ao verificar os [pedidos no relatório de Estado de Funcionamento do Sistema](https://technet.microsoft.com/library/ee221012%28v=ws.10%29.aspx), na [tabela ServiceRequest](http://technet.microsoft.com/library/dd772686%28v=ws.10%29.aspx) ou na [auditoria de acesso de utilizador a conteúdo protegido](http://social.technet.microsoft.com/wiki/contents/articles/3440.ad-rms-frequently-asked-questions-faq.aspx). Quando tiver confirmado que os clientes RMS já não estão a comunicar com estes servidores e que os clientes estão a utilizar o Azure RMS com êxito, pode remover a função de servidor do AD RMS destes servidores. Se estiver a utilizar servidores dedicados, poderá preferir o passo cautelar de começar por encerrar os servidores durante um período de tempo para se certificar de que não existem problemas comunicados que exijam reiniciar estes servidores para assegurar a continuidade do serviço enquanto estiver a investigar por que razão os clientes não estão a utilizar o Azure RMS.

Após a desativação dos servidores AD RMS, pode aproveitar a oportunidade para rever os modelos no portal clássico do Azure e consolidá-los para que os utilizadores tenham menos por onde escolher, reconfigurá-los ou até adicionar novos modelos. É também uma boa altura para publicar os modelos predefinidos. Para obter mais informações, consulte [Configurar modelos personalizados para o Azure Rights Management](../deploy-use/configure-custom-templates.md).

## Passo 9. Recodificar a chave de inquilino do Azure RMS
Este passo é obrigatório quando a migração estiver concluída se a sua implementação do AD RMS estava a utilizar o Modo Criptográfico 1 do RMS, pois o rechaveamento cria uma nova chave de inquilino que utiliza o Modo Criptográfico 2 do RMS. A utilização do Azure RMS com o Modo Criptográfico 1 é suportada apenas durante o processo de migração.

Este passo é opcional, mas recomendado, quando a migração estiver concluída, mesmo se estivesse a executar no Modo Criptográfico 2 do RMS, pois ajuda a proteger a sua chave de inquilino do Azure RMS contra potenciais falhas de segurança na chave do AD RMS. Quando efetuar o rechaveamento da chave de inquilino do Azure RMS (também conhecido como “implementar a chave”), é criada uma nova chave e a chave original é arquivada. No entanto, uma vez que mover de uma chave para outra não ocorre imediatamente mas ao longo de algumas semanas, não espere até suspeitar que existe uma falha na chave original e efetue o rechaveamento da chave de inquilino do RMS assim que a migração estiver concluída.

Para efetuar o rechaveamento da chave de inquilino do Azure RMS:

-   Se a chave de inquilino do RMS for gerida pela Microsoft: contacte o Suporte ao Cliente da Microsoft (CSS) e prove que é o administrador inquilino do RMS.

-   Se a chave inquilino do RMS for gerida por si (BYOK): repita o procedimento BYOK para gerar e criar uma nova chave através da Internet ou pessoalmente.

Para obter mais informações acerca da gestão da sua chave de inquilino do RMS, consulte [Operações para a chave de inquilino do Azure Rights Management](../deploy-use/operations-tenant-key.md).

## Passos seguintes

Agora que concluiu a migração, consulte o [plano de implementação](deployment-roadmap.md) para identificar quaisquer outras tarefas de implementação que tenha de efetuar.



<!--HONumber=Apr16_HO4-->


