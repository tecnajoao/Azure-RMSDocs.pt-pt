---
title: Configurar políticas de âmbito para o Azure Information Protection
description: Para configurar definições e etiquetas diferentes para utilizadores específicos, deve configurar uma política de âmbito para o Azure Information Protection.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 04/30/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 4b134785-0353-4109-8fa7-096d1caa2242
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: b11db1634896782afe0fe8caaabb316f4b0b6ff5
ms.sourcegitcommit: 44ff610dec678604c449d42cc0b0863ca8224009
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/31/2018
ms.locfileid: "39370922"
---
# <a name="how-to-configure-the-azure-information-protection-policy-for-specific-users-by-using-scoped-policies"></a>Como configurar a política do Azure Information Protection para utilizadores específicos com políticas de âmbito

>*Aplica-se a: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

Quando a política do Azure Information Protection é transferida para computadores com o [cliente do Azure Information Protection](https://www.microsoft.com/en-us/download/details.aspx?id=53018) instalado, todos os utilizadores recebem as definições e as etiquetas da política predefinida ou as alterações que configurou para a política global. Se quiser complementá-las para utilizadores específicos, ao ter definições e etiquetas diferentes, terá de criar uma **política de âmbito** configurada para esses utilizadores.

Para aplicações que suportam o cliente do Azure Information Protection, todos os utilizadores recebem a política global, que contém o título da barra de Information Protection e dica de ferramenta, as definições globais e as etiquetas globais. Se tiver configurado políticas de âmbito para utilizadores específicos, estes recebem definições e etiquetas adicionais. 

Tenha em atenção que, além das aplicações de ambiente de trabalho de Office que suportam o cliente do Azure Information Protection, as etiquetas também são suportadas com o PowerShell e o scanner do Azure Information Protection. Isso significa que pode criar e configurar políticas de âmbito para contas com comandos do PowerShell ou a deteção de impressão. 

As políticas de âmbito, tal como as etiquetas, são ordenadas no portal do Azure. Se um utilizador estiver configurado para vários âmbitos, será calculada uma política eficaz para esse utilizador antes de ser transferida. De acordo com a ordem das políticas, a última definição de política é aplicada. O utilizador vê as etiquetas da política global e, simultaneamente, etiquetas adicionais das políticas de âmbito às quais pertence.

Como uma política de âmbito herda sempre as etiquetas e as definições da política global, as etiquetas da política global são apresentadas quando cria ou edita uma política de âmbito. No entanto, não pode editar as etiquetas da política global quando edita uma política de âmbito. No entanto, pode adicionar subetiquetas para estas etiquetas herdadas.

Por exemplo, se tiver uma etiqueta com o nome **Confidencial** na política global, todos os utilizadores veem esta etiqueta. Não é possível remover ou reordená-lo com uma política de âmbito. Mas pode desejar criar uma política de âmbito para o departamento de Marketing que adiciona uma nova subetiqueta a confidencial, para que estes utilizadores vejam **confidencial \ promoções**. Também criar outra política de âmbito para o departamento de vendas que adiciona uma nova subetiqueta a confidencial, para que estes utilizadores vejam **confidencial \ parceiros**. Cada subetiqueta pode ser configurada para diferentes definições e a subetiqueta está visível apenas para os utilizadores nos respetivos departamentos.

Para configurar uma política de âmbito para o Azure Information Protection:

1. Se ainda não o tiver feito, abra uma nova janela do browser e [inicie sessão no portal do Azure](configure-policy.md#signing-in-to-the-azure-portal). Em seguida, navegue para o painel **Azure Information Protection**.

    Por exemplo, no hub menu, clique em **todos os serviços** e comece a escrever **informações** na caixa Filtro. Selecione **Azure Information Protection**.

2. Do **classificações** > **políticas** opção de menu: no **do Azure Information Protection - políticas** painel, selecione **adicionar um novo política**. Em seguida, consulte a **política** painel que apresenta a política global existente, onde pode agora configurar seu novo, a política de âmbito.

3. Especifique um nome e uma descrição da política que apenas os administradores veem no portal do Azure. O nome do inquilino deve ser exclusivo. Em seguida, selecione **especificar quais os utilizadores/grupos recebem esta política**, e nos painéis subsequentes, pode procurar e selecione os utilizadores e grupos para esta política. As etiquetas e as definições que configurou nesta política de âmbito serão aplicadas apenas a esses utilizadores.
    
    Por motivos de desempenho, é a associação de grupo para políticas de âmbito [em cache](../plan-design/prepare.md#group-membership-caching-by-azure-information-protection).

4. Agora, adicionar novas etiquetas ou configure as definições de política de âmbito. A política global é aplicada sempre em primeiro lugar, desta forma, pode complementar a política global com novas etiquetas e pode substituir as definições globais. Por exemplo, a política global poderá não ter uma etiqueta predefinida especificada e pode configurar uma etiqueta predefinida diferente em políticas de âmbito diferentes para departamentos específicos.

    Se precisar de ajuda a configurar as etiquetas ou as definições, utilize as ligações na secção [Configurar a política da sua organização](configure-policy.md#configuring-your-organizations-policy).

6. Tal como na edição da política global, quando realiza alterações num painel do Azure Information Protection, clique em **Guardar** para guardar as alterações ou clique em **Eliminar** para reverter para as últimas definições guardadas. 

7. Quando terminar de realizar as alterações pretendidas para esta política de âmbito, no inicial **do Azure Information Protection - políticas** painel, certifique-se de que esta política de âmbito está na ordem em que pretende aplicar. Isto é importante quando tiver selecionado o mesmo utilizador para várias políticas de âmbito. Para alterar a ordem, selecione o menu de contexto (**...** ) e selecione **mover para cima** ou **mover para baixo**. 

O cliente do Azure Information Protection verifica a existência de alterações sempre que uma das aplicações do Office suportadas é iniciada ou o Explorador de Ficheiros é aberto. O cliente transfere as alterações feitas à política global ou às políticas de âmbito que se aplicam a esse utilizador.

## <a name="next-steps"></a>Passos Seguintes

Para obter um exemplo de como personalizar a política predefinida e ver o comportamento resultante de uma aplicação do Office, experimente o [Tutorial de início rápido do Azure Information Protection](../get-started/infoprotect-quick-start-tutorial.md).

