---
title: "Compreender as restrições de utilização | Azure RMS"
description: "Todas as aplicações com suporte RMS têm de impor restrições de utilização."
keywords: 
author: bruceperlerms
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: E388B16C-ECDA-4696-A040-D457D3C96766
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: cb33a6c784a9b7efca0780771e764b984b51fedd
ms.openlocfilehash: 3141c4131d83e043e987546900d433e43ee4c946


---

# Compreender as restrições de utilização

Todas as aplicações com suporte RMS têm de impor restrições de utilização. Uma restrição de utilização é uma condição que resulta quando um utilizador tenta executar uma ação (por exemplo, imprimir um documento), mas a política do RMS desse documento não lhes concede a permissão ou o direito de executar essa ação (por exemplo, o direito de IMPRIMIR).

As permissões de um utilizador num documento podem ser consultadas ao utilizar a função [IpcAccessCheck](https://msdn.microsoft.com/library/hh535253.aspx).

## Compreender as restrições de utilização

-   Familiarizar-se com os direitos padrão do RMS

    Para ver o conjunto completo de direitos do RMS que a sua aplicação pode impor, consulte [Referência das restrições de utilização](usage-restriction-reference.md).

    Tenha em atenção que é possível criar direitos definidos para a aplicação específicos da sua situação e que vão para além dos direitos padrão do RMS.

-   Identificar pontos de imposição de restrições de utilização

    Um *ponto de imposição de restrição de utilização* é um local no fluxo de controlo da sua aplicação onde precisa de impor uma restrição de utilização. O tópico [Referência das restrições de utilização](usage-restriction-reference.md) fornece vários exemplos de pontos de imposição comuns.

    Avalie a sua própria aplicação para determinar os pontos de imposição de restrições de utilização a aplicar.

    A sua aplicação pode não necessitar de todos os pontos de imposição descritos na [Referência das restrições de utilização](usage-restriction-reference.md). Por exemplo, se a sua aplicação não permitir que os utilizadores imprimam conteúdo, não é necessário verificar o direito **IPC\_GENERIC\_PRINT**.

-   Atualizar o código para executar uma verificação de acesso em cada ponto de imposição

    Para obter orientações acerca de como impor direitos específicos, consulte [Referência das restrições de utilização](usage-restriction-reference.md).

## Tópicos relacionados

* [IpcAccessCheck](https://msdn.microsoft.com/library/hh535253.aspx)
* [Referência das restrições de utilização](usage-restriction-reference.md)
 

 



<!--HONumber=Oct16_HO3-->


