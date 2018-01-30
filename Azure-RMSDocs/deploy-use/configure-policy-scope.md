---
title: "Configurar políticas de âmbito para o Azure Information Protection"
description: "Para configurar definições e etiquetas diferentes para utilizadores específicos, deve configurar uma política de âmbito para o Azure Information Protection."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 01/29/2018
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 4b134785-0353-4109-8fa7-096d1caa2242
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: c7aa1c3aa18a246457c00a5a61c6004e55f76b4b
ms.sourcegitcommit: 972acdb468ac32a28e3e24c90694aff4b75206fc
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/29/2018
---
# <a name="how-to-configure-the-azure-information-protection-policy-for-specific-users-by-using-scoped-policies"></a>Como configurar a política do Azure Information Protection para utilizadores específicos com políticas de âmbito

>*Aplica-se a: Azure Information Protection*

Quando a política do Azure Information Protection é transferida para computadores com o [cliente do Azure Information Protection](https://www.microsoft.com/en-us/download/details.aspx?id=53018) instalado, todos os utilizadores recebem as definições e as etiquetas da política predefinida ou as alterações que configurou para a política global. Se quiser complementá-las para utilizadores específicos, ao ter definições e etiquetas diferentes, terá de criar uma **política de âmbito** configurada para esses utilizadores.

Todos os utilizadores recebem a política global, a qual contém o título da barra e a descrição, as definições e as etiquetas globais do Information Protection. Se tiver configurado políticas de âmbito para utilizadores específicos, estes recebem definições e etiquetas adicionais. 

As políticas de âmbito, tal como as etiquetas, são ordenadas no portal do Azure. Se um utilizador estiver configurado para vários âmbitos, será calculada uma política eficaz para esse utilizador antes de ser transferida. De acordo com a ordem das políticas, a última definição de política é aplicada. O utilizador vê as etiquetas da política global e, simultaneamente, etiquetas adicionais das políticas de âmbito às quais pertence. 

Como uma política de âmbito herda sempre as etiquetas e as definições da política global, as etiquetas da política global são apresentadas quando cria ou edita uma política de âmbito. No entanto, não pode editar as etiquetas da política global quando edita uma política de âmbito. No entanto, pode adicionar sublabels para estas etiquetas herdadas.

Por exemplo, se tiver uma etiqueta com o nome **Confidencial** na política global, todos os utilizadores veem esta etiqueta. Não a pode remover ou reordenar com uma política de âmbito. Mas pode querer criar uma política com âmbito definido para o departamento de Marketing que adiciona um novo sublabel a confidencial, para que estes utilizadores vejam **confidencial \ promoções**. Também criar outra política no âmbito para o departamento de vendas que adiciona um novo sublabel a confidencial, para que estes utilizadores vejam **confidencial \ parceiros**. Cada sublabel, em seguida, pode ser configurado para diferentes definições e o sublabel está visível apenas para os utilizadores os respetivos departamentos.

Para configurar uma política de âmbito para o Azure Information Protection:

1. Se ainda não o tiver feito, abra uma nova janela do browser e inicie sessão para o [portal do Azure](https://portal.azure.com) como um administrador de segurança ou um administrador global. Em seguida, navegue para o painel **Azure Information Protection**. 

    Por exemplo, no menu do hub, clique em **Mais serviços** e comece a escrever **Information** na caixa Filtrar. Selecione **Azure Information Protection**.

2. Do **políticas** selecção de menu, selecione **âmbito políticas**.

3. No **Azure Information Protection - políticas de âmbito** painel, selecione **adicionar uma nova política**. Em seguida, consulte o **política** painel que mostra a política global existente, onde agora, pode configurar a nova, âmbito política.

4. Especifique um nome e uma descrição da política que apenas os administradores veem no portal do Azure. O nome do inquilino deve ser exclusivo. Em seguida, selecione **especifique quais os utilizadores/grupos obter esta política**, e os painéis subsequentes, pode procurar e selecione os utilizadores e grupos para esta política. As etiquetas e as definições que configurou nesta política de âmbito serão aplicadas apenas a esses utilizadores.
    
    Por motivos de desempenho, a associação a grupos para políticas de âmbito é [em cache](../plan-design/prepare.md#group-membership-caching-by-azure-information-protection).

5. Agora, crie novas etiquetas ou configure as definições da política de âmbito. A política global é aplicada sempre em primeiro lugar, desta forma, pode complementar a política global com novas etiquetas e pode substituir as definições globais. Por exemplo, a política global poderá não ter uma etiqueta predefinida especificada e pode configurar uma etiqueta predefinida diferente em políticas de âmbito diferentes para departamentos específicos.

    Se precisar de ajuda a configurar as etiquetas ou as definições, utilize as ligações na secção [Configurar a política da sua organização](configure-policy.md#configuring-your-organizations-policy).

6. Tal como na edição da política global, quando realiza alterações num painel do Azure Information Protection, clique em **Guardar** para guardar as alterações ou clique em **Eliminar** para reverter para as últimas definições guardadas. 

7. Quando terminar de efetuar as alterações que pretende para este âmbito de política, no iniciais **Azure Information Protection - políticas de âmbito** painel, certifique-se de que esta política âmbito na ordem que pretende que o se aplicadas. Isto é importante quando tiver selecionado o mesmo utilizador para várias políticas de âmbito. Para alterar a ordem, selecione o menu de contexto (**...** ) e selecione **mover para cima** ou **mover para baixo**. 

8. Para implementar as suas alterações, clique em **publicar**. 

O cliente do Azure Information Protection verifica a existência de alterações sempre que uma das aplicações do Office suportadas é iniciada ou o Explorador de Ficheiros é aberto. O cliente transfere as alterações feitas à política global ou às políticas de âmbito que se aplicam a esse utilizador.

> [!TIP]
> Depois de guardar a política de âmbito, do **políticas** secção, pode utilizar o **tudo - entre a vista de política** opção de visualizar e reconfigurar todas as etiquetas da sua política do Azure Information Protection. Este método proporciona uma forma fácil para comparar as etiquetas de política global e âmbito de todas as políticas. 

## <a name="next-steps"></a>Próximos passos

Para obter um exemplo de como personalizar a política predefinida e ver o comportamento resultante de uma aplicação do Office, experimente o [Tutorial de início rápido do Azure Information Protection](../get-started/infoprotect-quick-start-tutorial.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
