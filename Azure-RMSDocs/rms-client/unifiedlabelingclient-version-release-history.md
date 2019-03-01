---
title: O Azure Information Protection unified cliente etiquetagem - informações de lançamento de versão
description: Ver as informações de versão para o Azure Information Protection unified etiquetagem cliente para Windows.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 02/28/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.reviewer: maayan
ms.suite: ems
ms.openlocfilehash: 699e2807c700b90b98bbc855dd8792aa607696f3
ms.sourcegitcommit: 8ba63c0f4cd7d2ad7614af4ea9cfe8aec7fac4c0
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/27/2019
ms.locfileid: "56956258"
---
# <a name="azure-information-protection-unified-labeling-client-version-release-information"></a>O Azure Information Protection unified cliente etiquetagem: Informações de lançamento de versão

>*Aplica-se a: Serviços de gestão de direitos do Active Directory [do Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 com SP1, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2*

> [!NOTE]
> Este cliente está em pré-visualização e está sujeitas a alterações. Ele utiliza o armazenamento de etiquetagem unificado e transfere a política com as etiquetas do Centro de conformidade e segurança do Office 365. [Mais informações](/Office365/SecurityCompliance/sensitivity-labels)

Pode baixar a versão de pré-visualização mais recente do Azure Information Protection unified etiquetagem cliente do [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=57440).

### <a name="release-information"></a>Informações de versão

Utilize as seguintes informações para ver o que é suportado para a versão de pré-visualização mais recente do cliente etiquetagem unificada do Azure Information Protection.

Este cliente instala um suplemento do Office para computadores Windows, uma extensão para o Explorador de ficheiros e um módulo do PowerShell. Este cliente tem o mesmo [pré-requisitos](../requirements.md) que o cliente do Azure Information Protection que transfere a política do Azure.

Para comparar recursos e funcionalidades com o cliente do Azure Information Protection, consulte [comparações de recursos para os clientes](use-client.md#feature-comparisons-for-the-clients).

## <a name="current-preview-version"></a>Versão de pré-visualização atual

**Lançado**: 02/25/2019

Esta versão de pré-visualização do Azure Information Protection unified etiquetagem cliente para o Windows suporta as seguintes funcionalidades: 

- Atualizar a partir do cliente do Azure Information Protection.

- Manual, automática e recomendada de etiquetagem: Uso **etiquetagem automática** partir do Centro de conformidade e segurança do Office 365, para configurar a etiquetagem automática e recomendada. Para obter mais informações, consulte [aplique uma etiqueta de sensibilidade para o conteúdo automaticamente](/Office365/SecurityCompliance/apply_sensitivity_label_automatically).

- Explorador de ficheiros, faça duplo clique ações para classificar e proteger ficheiros, remover a proteção e aplicar permissões personalizadas.

- Um Visualizador de texto protegido e arquivos de imagem protegido ficheiros PDF e os ficheiros que são protegidos genericamente.

- Comandos do PowerShell para fazer o seguinte:
    - [Definir ou remover uma etiqueta num documento](/powershell/module/azureinformationprotection/set-aipfilelabel)
    - [Etiqueta de um documento depois inspecionar o seu conteúdo](/powershell/module/azureinformationprotection/set-aipfileclassification)
    - [Ler as informações de etiqueta aplicadas a um documento](/powershell/module/azureinformationprotection/get-aipfilestatus)
    - [Autenticar para oferecer suporte a sessões do PowerShell autónomas](/powershell/module/azureinformationprotection/set-aipauthentication)

- Suporte para a utilização de relatórios central [analytics do Azure Information Protection](../reports-aip.md).

- As seguintes definições de política e a etiqueta:
    - Marcação Visual (cabeçalhos, rodapés e marcas d'água)
    - Padrão de etiquetagem
    - Etiquetas que aplicam-se não reencaminhar e apresentam apenas no Outlook
    - Pedidos de justificação se os utilizadores diminuir o nível de classificação ou remover uma etiqueta
    - Cores para as etiquetas

- Atualização de política a partir do Centro de conformidade e segurança do:
    - Sempre que inicia uma aplicação do Office e todas as 4 horas
    - Quando rato para classificar e proteger um ficheiro ou pasta
    - Quando executa os cmdlets do PowerShell para etiquetagem e proteção

- Uma caixa de diálogo Ajuda e feedback, que inclui repor definições e exportar registos.

### <a name="features-that-do-not-work-in-this-preview-version-or-are-not-available"></a>Funcionalidades não irão funcionar nesta versão de pré-visualização ou não estão disponíveis

Inclui:

- O scanner para o descobrir, Etiquetar e proteger ficheiros em arquivos de dados no local não está disponível.

- As etiquetas que são migradas do portal do Azure e configuradas para exibição de proteção do HYOK no cliente quando estes forem publicados, mas estas etiquetas não aplique proteção.

- O conjunto completo de cmdlets do módulo AzureInformationProtection não estão disponíveis, que inclui cmdlets que se ligam diretamente a um serviço de proteção. Por exemplo, Unprotect-RMSFile para desproteger ficheiros em massa.

Para mais informações, consulte a [tabelas comparativas](use-client.md#feature-comparisons-for-the-clients).

## <a name="instructions"></a>Instruções

1. Instale o cliente utilizando as instruções seguintes: [Guia de utilizador: Transferir e instalar o cliente do Azure Information Protection (pré-visualização)](install-unifiedlabelingclient-app.md) 

2. Utilize o cliente, tal como faria com o cliente do Azure Information Protection, com as seguintes exceções de aplicações do Office:
    - O botão da faixa de opções do Office é designado **sensibilidade** vez **proteger**.
    - Os administradores não é possível apresentar a barra do Information Protection por predefinição, mas os utilizadores podem exibi-lo selecionando **Mostrar barra** partir a **sensibilidade** botão. 
    - Permissões personalizadas não estão disponíveis
    - Controlar e revogar não está disponível
    
    Para obter instruções de utilizador:
    
    - [Classificar um ficheiro ou e-mail](client-classify.md) 
    
    - [Classificar e proteger um ficheiro ou e-mail](client-classify-protect.md)

3. Partilhe a sua experiência: 
    
    - Para fornecer comentários ou fazer perguntas sobre este cliente de pré-visualização, utilize o [site do Yammer do Azure Information Protection](https://www.yammer.com/AskIPTeam).
