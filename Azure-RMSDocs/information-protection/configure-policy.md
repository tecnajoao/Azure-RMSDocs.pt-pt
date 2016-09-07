---
title: "Configurar política do Azure Information Protection | Azure RMS"
description: "Para configurar a classificação, a etiquetagem e a proteção, tem de configurar a política do Azure Information Protection."
author: cabailey
manager: mbaldwin
ms.date: 08/25/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: ba0e8119-886c-4830-bd26-f98fb14b2933
ms.reviewer: eymanor
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: da0145444a7d0abb6407ed2ccbb581d4dcdd10d6
ms.openlocfilehash: e5b8054b3b5cb38adf2f5ae1d2f4f399d98f6e23


---

# Configurar política do Azure Information Protection

>*Aplica-se a: pré-visualização do Azure Information Protection*

**[Estas informações são preliminares e estão sujeitas a alterações. ]**

Para configurar a classificação, a etiquetagem e a proteção, tem de configurar a política do Azure Information Protection. Esta política é, em seguida, transferida para computadores que têm instalado o [cliente Azure Information Protection](https://www.microsoft.com/en-us/download/details.aspx?id=53018).

Para configurar a política do Azure Information Protection durante o lançamento de pré-visualização do Azure Information Protection:

1. Inicie sessão no [portal do Azure](https://portal.azure.com).

2. Navegue para o painel **Azure Information Protection**: por exemplo, no menu do hub, clique em **Procurar** e comece a escrever **Information Protection** na caixa Filtro. Na lista de resultados, selecione **Azure Information Protection**. 

    Em seguida, irá ver o painel do **Azure Information Protection** onde pode configurar a política do Azure Information Protection, que contém os elementos seguintes:

    - Título e descrição para a barra Information Protection que os utilizadores veem nas aplicações do Office.

    - Etiquetas que permitem tanto a si como aos utilizadores classificar documentos e e-mails.

    - A opção para impor a classificação quando os utilizadores guardam documentos e enviam e-mails.

    - A opção para definir uma etiqueta predefinida como ponto de partida para classificar documentos e e-mails.

    - A opção para solicitar aos utilizadores que indiquem um motivo quando estes selecionam uma etiqueta que tem um nível de sensibilidade inferior ao original.


O Azure Information Protection vem com uma [política predefinida](configure-policy-default.md), que contém as etiquetas **Pessoal**, **Público**, **Interno**, **Confidencial** e **Secreto**. Pode utilizar as etiquetas predefinidas sem alterações ou pode personalizá-las, eliminá-las ou criar novas etiquetas.

Quando efetuar alterações num painel do Azure Information Protection, clique em **Guardar** para guardar as alterações ou clique em **Eliminar** para reverter para as últimas definições guardadas. 

Quando terminar de efetuar as alterações que pretende, clique em **Publicar**. 

O cliente Azure Information Protection verifica a existência de quaisquer alterações sempre que uma das aplicações do Office suportadas é iniciada e transfere as alterações como política do Azure Information Protection.

## Configurar a política da organização

Utilize as seguintes informações para ajudar a configurar a política do Azure Information Protection:

- [Política do Information Protection predefinida](configure-policy-default.md)

- [Como configurar as definições de política global](configure-policy-settings.md)

- [Como criar uma nova etiqueta](configure-policy-new-label.md)

- [Como eliminar ou reordenar uma etiqueta](configure-policy-delete-reorder.md)

- [Como alterar ou personalizar uma etiqueta existente](configure-policy-change-label.md)

- [Como configurar uma etiqueta para aplicar proteção](configure-policy-protection.md)

- [Como configurar uma etiqueta para aplicar marcações visuais](configure-policy-markings.md)

- [Como configurar condições para as classificações automática e recomendada](configure-policy-classification.md)

## Passos seguintes

Para obter um exemplo de como personalizar a política predefinida e ver o comportamento resultante de uma aplicação do Office, experimente o [Tutorial de inicio rápido do Azure Information Protection](infoprotect-quick-start-tutorial.md).




<!--HONumber=Aug16_HO4-->


