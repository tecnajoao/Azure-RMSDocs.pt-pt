---
title: "Configurar políticas de âmbito para o Azure Information Protection"
description: "Para configurar definições e etiquetas diferentes para utilizadores específicos, deve configurar uma política de âmbito para o Azure Information Protection."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 05/23/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 4b134785-0353-4109-8fa7-096d1caa2242
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: d3138cd16e1bd86d63243feea30d23db9aa45bdb
ms.sourcegitcommit: 04eb4990e2bf0004684221592cb93df35e6acebe
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/30/2017
---
# <a name="how-to-configure-the-azure-information-protection-policy-for-specific-users-by-using-scoped-policies"></a>Como configurar a política do Azure Information Protection para utilizadores específicos com políticas de âmbito

>*Aplica-se a: Azure Information Protection*

Quando a política do Azure Information Protection é transferida para computadores com o [cliente do Azure Information Protection](https://www.microsoft.com/en-us/download/details.aspx?id=53018) instalado, todos os utilizadores recebem as definições e as etiquetas da política predefinida ou as alterações que configurou para a política global. Se quiser complementá-las para utilizadores específicos, ao ter definições e etiquetas diferentes, terá de criar uma **política de âmbito** configurada para esses utilizadores.

Todos os utilizadores recebem a política global, a qual contém o título da barra e a descrição, as definições e as etiquetas globais do Information Protection. Se tiver configurado políticas de âmbito para utilizadores específicos, estes recebem definições e etiquetas adicionais. 

As políticas de âmbito, tal como as etiquetas, são ordenadas no portal do Azure. Se um utilizador estiver configurado para vários âmbitos, será calculada uma política eficaz para esse utilizador antes de ser transferida. De acordo com a ordem das políticas, a última definição de política é aplicada. O utilizador vê as etiquetas da política global e, simultaneamente, etiquetas adicionais das políticas de âmbito às quais pertence. 

Como uma política de âmbito herda sempre as etiquetas e as definições da política global, as etiquetas da política global são apresentadas quando cria ou edita uma política de âmbito. No entanto, não pode editar as etiquetas da política global quando edita uma política de âmbito. Pode, porém, adicionar subetiquetas para estas etiquetas herdadas.

Por exemplo, se tiver uma etiqueta com o nome **Confidencial** na política global, todos os utilizadores veem esta etiqueta. Não a pode remover ou reordenar com uma política de âmbito. Contudo, poderá querer criar uma política de âmbito para o departamento de Marketing que adiciona uma nova subetiqueta a Confidencial, para que estes utilizadores vejam **Confidencial\Promoções**. Também pode criar outra política de âmbito para o departamento de Vendas que adiciona uma nova subetiqueta a Confidencial, para que estes utilizadores vejam **Confidencial\Parceiros**. Cada subetiqueta pode ser, então, configurada para diferentes definições e esta fica visível apenas para os utilizadores nos respetivos departamentos.


Para configurar uma política de âmbito para o Azure Information Protection:

1. Numa nova janela de browser, inicie sessão no [portal do Azure](https://portal.azure.com) como administrador de segurança ou administrador global.

2. Navegue para o painel **Azure Information Protection**: por exemplo, no menu do hub, clique em **Mais serviços** e comece a escrever **Information Protection** na caixa Filtro. Na lista de resultados, selecione **Azure Information Protection**. 

    No painel inicial do **Azure Information Protection**, selecione **Adicionar uma nova política**. Em seguida, verá o segundo painel utilizado para apresentar a atualização da política global, para que possa agora configurar a sua nova política de âmbito.

3. Especifique um nome e uma descrição da política que apenas os administradores veem no portal do Azure. O nome do inquilino deve ser exclusivo. Em seguida, clique em **Especificar que utilizadores/grupos recebem esta política** e, nos painéis subsequentes, pode pesquisar e selecionar os utilizadores e grupos para esta política. As etiquetas e as definições que configurou nesta política de âmbito serão aplicadas apenas a esses utilizadores.

4. Agora, crie novas etiquetas ou configure as definições da política de âmbito. A política global é aplicada sempre em primeiro lugar, desta forma, pode complementar a política global com novas etiquetas e pode substituir as definições globais. Por exemplo, a política global poderá não ter uma etiqueta predefinida especificada e pode configurar uma etiqueta predefinida diferente em políticas de âmbito diferentes para departamentos específicos.

    Se precisar de ajuda a configurar as etiquetas ou as definições, utilize as ligações na secção [Configurar a política da sua organização](configure-policy.md#configuring-your-organizations-policy).

5. Tal como na edição da política global, quando realiza alterações num painel do Azure Information Protection, clique em **Guardar** para guardar as alterações ou clique em **Eliminar** para reverter para as últimas definições guardadas. 

6. Quando terminar de realizar as alterações pretendidas para esta política de âmbito, no painel inicial do **Azure Information Protection**, confirme que esta política de âmbito está na ordem que pretende aplicar. Isto é importante quando tiver selecionado o mesmo utilizador para várias políticas de âmbito. Em seguida, clique em **Publicar**. 

O cliente do Azure Information Protection verifica a existência de alterações sempre que uma das aplicações do Office suportadas é iniciada ou o Explorador de Ficheiros é aberto. O cliente transfere as alterações feitas à política global ou às políticas de âmbito que se aplicam a esse utilizador.

> [!TIP]
> Depois de guardar a política de âmbito, pode utilizar o **Editor de Políticas Cruzadas** no painel inicial do **Azure Information Protection** para ver e reconfigurar todas as etiquetas da sua política do Azure Information Protection. Este método proporciona uma forma fácil de comparar etiquetas de múltiplas políticas (a sua política global e de todas as políticas de âmbito). No entanto, este editor não permite adicionar e reorganizar etiquetas ou ver e configurar as definições de política.

## <a name="next-steps"></a>Próximos passos

Para obter um exemplo de como personalizar a política predefinida e ver o comportamento resultante de uma aplicação do Office, experimente o [Tutorial de início rápido do Azure Information Protection](../get-started/infoprotect-quick-start-tutorial.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
