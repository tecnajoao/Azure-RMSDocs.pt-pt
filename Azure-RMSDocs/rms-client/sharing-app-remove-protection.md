---
title: "Remover a proteção com a aplicação de partilha RMS – AIP"
description: "Instruções para remover a proteção de um ficheiro (ou seja, desproteger um ficheiro) protegido anteriormente com a aplicação de partilha RMS."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: da95b938-eaad-4c83-a21e-ff1d4872aae4
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 2131f40b51f34de7637c242909f10952b1fa7d9f
ms.openlocfilehash: 370b19894efb53604c798b38be02dda3f8804b8b
ms.lasthandoff: 02/24/2017


---

# <a name="remove-protection-from-a-file-by-using-the-rights-management-sharing-application"></a>Remover a proteção de um ficheiro com a aplicação de partilha Rights Management

>*Aplica-se a: Serviços de Gestão de Direitos do Active Directory, Azure Information Protection, Windows 10, Windows 7 com SP1, Windows 8 e Windows 8.1*

Para remover a proteção de um ficheiro (ou seja, desproteger um ficheiro) protegido anteriormente ao utilizar a aplicação de partilha RMS, utilize a opção **Remover Proteção** do Explorador de Ficheiros.

> [!IMPORTANT]
> Tem de ser um proprietário do ficheiro para remover a proteção.

## <a name="to-remove-protection-from-a-file"></a>Para remover a proteção de um ficheiro

1.  No Explorador de Ficheiros, clique com o botão direito do rato no ficheiro (por exemplo, Amostra.ptxt), selecione **Proteger com RMS**, clique em **Proteger no local** e, em seguida, clique em **Remover Proteção**:

    ![Opção de menu Remover proteção da aplicação de partilha RMS](../media/ADRMS_MSRMSApp_RemoveProtection.png)

    Poderão ser-lhe pedidas as credenciais.

Nota: se não vir estas opções de proteção, é provável que a aplicação de partilha RMS não esteja instalada no seu computador, que a versão mais recente não esteja instalada ou que seja necessário reiniciar o computador para concluir a instalação. Para obter mais informações sobre como instalar a aplicação de partilha, consulte [Transferir e instalar a aplicação de partilha Rights Management](install-sharing-app.md).

O ficheiro protegido original é eliminado (por exemplo, Amostra.ptxt) e substituído por um ficheiro que tem o mesmo nome, mas com a extensão de nome de ficheiro não protegido (por exemplo, Amostra.txt).

## <a name="examples-and-other-instructions"></a>Exemplos e outras instruções
Para obter exemplos de como pode utilizar a aplicação de partilha Rights Management e instruções sobre como proceder, veja as secções seguintes do guia do utilizador da aplicação de partilha Rights Management:

-   [Exemplos de utilização da aplicação de partilha RMS](sharing-app-user-guide.md#examples-for-using-the-rms-sharing-application)

-   [O que pretende fazer?](sharing-app-user-guide.md#what-do-you-want-to-do)

## <a name="see-also"></a>Consulte Também
[Guia do utilizador da aplicação de partilha Rights Management](sharing-app-user-guide.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
