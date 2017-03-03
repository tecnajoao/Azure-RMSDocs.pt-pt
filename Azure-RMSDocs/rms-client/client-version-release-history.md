---
title: "Cliente do Azure Information Protection&colon; histórico de lançamento de versões"
description: "Veja as novidades ou alterações ao lançamento do cliente do Azure Information Protection para Windows."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 03/01/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 6ebd0ca3-1864-4b3d-bb3e-a168eee5eb1d
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 343ac5f79902379e45efcb6979a115ba4c00d1c5
ms.openlocfilehash: 503cb76825d0092e8562d39281b1d702edaf6438
ms.lasthandoff: 03/02/2017


---

# <a name="azure-information-protection-client-version-release-history"></a>Cliente do Azure Information Protection: histórico de lançamento de versões

>*Aplica-se a: Azure Information Protection*

A equipa do Azure Information Protection atualiza regularmente o cliente do Azure Information Protection com correções e novas funcionalidades. O cliente está incluído no Catálogo do Microsoft Update (categoria: **Azure Information Protection**), além de poder transferir sempre a versão mais recente no [Centro de Transferências da Microsoft](https://www.microsoft.com/en-us/download/details.aspx?id=53018).

Utilize as seguintes informações para ver o que há de novo ou o que foi alterado num lançamento. A versão mais atual aparece em primeiro na lista. As versões anteriores à Disponibilidade Geral não se encontram listadas.

> [!NOTE]
> As pequenas correções não se encontram listadas, pelo que se encontrar um problema com o cliente do Azure Information Protection, primeiro deve verificar se é ou não um problema com a versão mais recente.
>  
> Se o problema continuar, veja as informações em [Opções de suporte e recursos da comunidade](../get-started/information-support.md#support-options-and-community-resources). Também o incentivamos a interagir com a equipa do Azure Information Protection, no [site Yammer](https://www.yammer.com/askipteam/).

## <a name="version-131552"></a>Versão 1.3.155.2

**Lançada**: 08/02/2017

**Novos requisitos**:

Microsoft .NET Framework

- Esta versão do Azure Information Protection requer a versão mínima do Microsoft .NET Framework 4.6.2. Se esta versão estiver em falta, o instalador tentará transferi-la e instalá-la. Poderá ser preciso reiniciar o computador depois de concluída a instalação do cliente do Azure Information Protection.

- Se o Visualizador do Azure Information Protection for instalado à parte, precisará da versão mínima do Microsoft .NET Framework 4.5.2 e, se esta estiver em falta, o instalador não a transfere nem a instala.

**Novas funcionalidades**:

- Um cliente novo e unificado que combina as funcionalidades da aplicação de partilha Rights Management para Windows com o cliente do Azure Information Protection. Inclui:
    
    - Integração com o Explorador de Ficheiros do Windows (clique com o botão direito do rato) para aplicar as etiquetas e a proteção. Suporta formatos de ficheiro adicionais e a seleção múltipla de ficheiros.
    - Um visualizador para documentos protegidos (inclui o PDF protegido para SharePoint).
    - Cmdlets do PowerShell para obter e definir etiquetas para os ficheiros que estão armazenados localmente ou em partilhas de rede. Estes cmdlets são instalados com os cmdlets anteriormente enviados com a Ferramenta de Proteção RMS (módulo RMSProtection).
    - Registos da utilização do cliente que registam as informações como a etiqueta que foi aplicada, como e por quem.

Esta versão do cliente é a [Versão de Disponibilidade Geral](https://blogs.technet.microsoft.com/enterprisemobility/2017/02/08/azure-information-protection-december-update-moves-to-general-availability/) do cliente de pré-visualização que foi anunciada pela primeira vez em dezembro de 2016. Para obter mais informações acerca desta versão do cliente, veja os guias seguintes:

- [Guia do administrador de clientes do Azure Information Protection](client-admin-guide.md)

- [Guia do utilizador do Azure Information Protection](client-user-guide.md)


## <a name="version-1240"></a>Versão 1.2.4.0

**Lançada**: 27/10/2016

**Correções**:

- A instalação do cliente é concluída quando o serviço Windows Update for desativado.

- No Office 2016, quando guarda um documento e a etiqueta aplicada é configurada para um cabeçalho ou rodapé, o cursor não se desloca para o cabeçalho ou rodapé.

- A classificação automática funciona no Word para texto em caixas de texto agregadas.

**Nova funcionalidade**:

- Os testes de diagnóstico e a opção de reposição que um utilizador pode executar a partir da aplicação do Office quando o cliente do Azure Information Protection está instalado: no separador **Base**, no grupo **Proteção**, clique em **Proteger** e em **Ajuda e comentários** e, em seguida, clique em **Executar diagnósticos**. 

    Para obter mais informações acerca desta opção, veja a secção [Para verificar a instalação, o estado da ligação ou enviar comentários](client-admin-guide.md#additional-checks-to-verify-installation-connection-status-or-send-feedback) na documentação de instalação do cliente.

## <a name="version-11230"></a>Versão 1.1.23.0

**Lançada**: 01/10/2016

Disponibilidade Geral.

## <a name="next-steps"></a>Passos seguintes

Para obter mais informações sobre como instalar o cliente:

- Para os utilizadores: [Transferir e instalar o cliente](install-client-app.md)

- Para os administradores: [Guia do administrador do cliente do Azure Information Protection](client-admin-guide.md)


[!INCLUDE[Commenting house rules](../includes/houserules.md)]
