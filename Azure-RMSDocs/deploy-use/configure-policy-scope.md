---
title: "Configurar políticas de âmbito | Azure Information Protection"
description: "Para configurar definições e etiquetas diferentes para utilizadores específicos, deve configurar uma política de âmbito para o Azure Information Protection."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 4b134785-0353-4109-8fa7-096d1caa2242
ms.reviewer: eymanor
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 5d1a5e3b85d5450bcb2064a6c3b95e6ad802eea3
ms.openlocfilehash: 99d7a2a9580466492edc313329cada315a9966d6


---

# <a name="how-to-configure-the-azure-information-protection-policy-for-specific-users-by-using-scoped-policies"></a>Como configurar a política do Azure Information Protection para utilizadores específicos com políticas de âmbito

>*Aplica-se a: Azure Information Protection*

**[Esta funcionalidade está na pré-visualização e está sujeita a alterações.]**

Quando a política do Azure Information Protection é transferida para computadores com o [cliente do Azure Information Protection](https://www.microsoft.com/en-us/download/details.aspx?id=53018) instalado, todos os utilizadores recebem as definições e as etiquetas da política predefinida ou as alterações que configurou para a política global. Se pretender complementar estas para utilizadores específicos, ao ter definições e etiquetas diferentes, deve criar uma **política de âmbito** (atualmente na pré-visualização) configurada para esses utilizadores.

Todos os utilizadores recebem a política global, a qual contém o título da barra e a descrição, as definições e as etiquetas globais do Information Protection. Se tiver configurado políticas de âmbito para utilizadores específicos, estes recebem definições e etiquetas adicionais. 

As políticas de âmbito, tal como as etiquetas, são ordenadas no portal do Azure. Se um utilizador estiver configurado para vários âmbitos, será calculada uma política eficaz para esse utilizador antes de ser transferida. De acordo com a ordem das políticas, a última definição de política é aplicada. O utilizador vê as etiquetas da política global e, simultaneamente, etiquetas adicionais das políticas de âmbito às quais pertence. 

Como uma política de âmbito herda sempre as etiquetas e as definições da política global, as etiquetas da política global são apresentadas quando cria ou edita uma política de âmbito. No entanto, não pode editar as etiquetas da política global quando edita uma política de âmbito. Pode, porém, adicionar subetiquetas para estas etiquetas herdadas.

Por exemplo, se tiver uma etiqueta com o nome Confidencial na política global, todos os utilizadores veem esta etiqueta. Não a pode remover ou reordenar com uma política de âmbito. Contudo, poderá querer criar uma política de âmbito para o departamento de Marketing que adiciona uma nova subetiqueta a Confidencial, para que estes utilizadores vejam Confidencial\Promoções. Depois, pode criar outra política de âmbito para o departamento de Vendas que adiciona uma nova subetiqueta a Confidencial, para que estes utilizadores vejam Confidencial\Parceiros. Cada subetiqueta pode ser, então, configurada para diferentes definições e esta fica visível apenas para os utilizadores nos respetivos departamentos.


Para configurar uma política de âmbito para o Azure Information Protection:

1. Numa nova janela de browser, inicie sessão no [portal do Azure](https://portal.azure.com) como administrador global.

2. Navegue para o painel **Azure Information Protection**: por exemplo, no menu hub, clique em **Mais serviços** e comece a escrever **Information Protection** na caixa Filtro. Na lista de resultados, selecione **Azure Information Protection**. 

    No painel inicial do **Azure Information Protection**, selecione **Adicionar uma nova política (PRÉ-VISUALIZAÇÃO)**. Em seguida, verá o segundo painel utilizado para apresentar a atualização da política global, para que possa agora configurar a sua nova política de âmbito.

3. Especifique um nome e uma descrição da política que apenas os administradores veem no portal do Azure. O nome do inquilino deve ser exclusivo. Em seguida, clique em **Especificar que utilizadores/grupos recebem esta política** e, nos painéis subsequentes, pode pesquisar e selecionar os utilizadores e grupos para esta política. As etiquetas e as definições que configurou nesta política de âmbito serão aplicadas apenas a esses utilizadores. 

4. Agora, crie novas etiquetas ou configure as definições da política de âmbito. A política global é aplicada sempre em primeiro lugar, desta forma, pode complementar a política global com novas etiquetas e pode substituir as definições globais. Por exemplo, a política global poderá não ter uma etiqueta predefinida especificada e pode configurar uma etiqueta predefinida diferente em políticas de âmbito diferentes para departamentos específicos.

    Se precisar de ajuda a configurar as etiquetas ou as definições, utilize as ligações na secção [Configurar a política da sua organização](configure-policy.md#configuring-your-organizations-policy).

5. Tal como na edição da política global, quando realiza alterações num painel do Azure Information Protection, clique em **Guardar** para guardar as alterações ou clique em **Eliminar** para reverter para as últimas definições guardadas. 

6. Quando terminar de realizar as alterações pretendidas para esta política de âmbito, no painel inicial do **Azure Information Protection**, confirme que esta política de âmbito está na ordem que pretende aplicar. Isto é importante quando tiver selecionado o mesmo utilizador para várias políticas de âmbito. Em seguida, clique em **Publicar**. 

O cliente do Azure Information Protection verifica a existência de quaisquer alterações sempre que uma das aplicações do Office suportadas é iniciada. Este transfere as alterações realizadas na política global ou nas políticas de âmbito que se aplicam a esse utilizador.

## <a name="next-steps"></a>Passos seguintes

Para obter um exemplo de como personalizar a política predefinida e ver o comportamento resultante de uma aplicação do Office, experimente o [Tutorial de inicio rápido do Azure Information Protection](../get-started/infoprotect-quick-start-tutorial.md).




<!--HONumber=Dec16_HO1-->


