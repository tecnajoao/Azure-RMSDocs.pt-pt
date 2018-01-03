---
title: "Cliente do Azure Information Protection&colon; política de suporte e histórico da versão versão"
description: "Ver o que é nova ou alterada uma versão do cliente Azure Information Protection para o Windows e compreender a política de ciclo de vida de suporte."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 12/22/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 6ebd0ca3-1864-4b3d-bb3e-a168eee5eb1d
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 20ee380a48fa8fb303a5c71f43df17b8740b0cb4
ms.sourcegitcommit: fc9a4487e2a0bc3481a814c7c308939868d52db9
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/21/2017
---
# <a name="azure-information-protection-client-version-release-history-and-support-policy"></a>Cliente do Azure Information Protection: política de suporte e histórico da versão versão

>*Aplica-se a: Azure Information Protection*

A equipa do Azure Information Protection atualiza regularmente o cliente do Azure Information Protection com correções e novas funcionalidades. 

Pode transferir a versão GA mais recente e a versão de pré-visualização atual do [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=53018). Estas versões também estão incluídas no catálogo Microsoft Update (categoria: **Azure Information Protection**), que pode implementar o cliente utilizando WSUS ou do Configuration Manager ou outros mecanismos de implementação de software que utilizam O Microsoft Update.

### <a name="servicing-information-and-timelines"></a>Informações e linhas cronológicas de manutenção

Cada versão de disponibilidade geral (DG) do cliente Azure Information Protection é suportada para até seis meses após o lançamento da versão GA subsequente. Versões não suportadas do cliente não estão incluídas nesta página. Correções e novas funcionalidades sempre são aplicadas para a última versão GA e não serão aplicadas a versões mais antigas do GA.

As versões de pré-visualização não devem ser implementadas para os utilizadores finais em redes de produção. Em alternativa, utilize a versão de pré-visualização mais recente para ver e experimentar novas funcionalidades ou correções que são provenientes na próxima versão GA. Versões de pré-visualização não são atuais não são suportadas.

### <a name="release-history"></a>Histórico de versões

Utilize as seguintes informações para ver o que é nova ou alterada para uma versão suportada do cliente Azure Information Protection para o Windows. A versão mais atual aparece em primeiro na lista. 

> [!NOTE]
> Correções secundárias não são listadas pelo se ocorrer um problema com o cliente Azure Information Protection, que recomendamos que verifique se é fixa com a versão GA mais recente. Se o problema continuar, verifique a versão de pré-visualização atual.
>  
> Para obter suporte técnico, consulte o [opções de suporte e recursos da Comunidade](../get-started/information-support.md#support-options-and-community-resources) informações. Também o incentivamos a interagir com a equipa do Azure Information Protection, no [site Yammer](https://www.yammer.com/askipteam/).

## <a name="versions-later-than-110560"></a>Versões posteriores 1.10.56.0

Se tiver uma versão do cliente que é posterior à 1.10.56.0, é uma versão de pré-visualização para fins de avaliação e teste. 

Para o que é nova ou alterada na versão de pré-visualização atual desde a última versão GA do cliente, consulte o **detalhes** secção no [página de transferência](https://www.microsoft.com/en-us/download/details.aspx?id=53018). 

## <a name="version-110560"></a>Versão 1.10.56.0

**Lançada**: 18/09/2017

Esta versão inclui o MSIPC versão 1.0.3219.0619 do cliente RMS.

**Novas funcionalidades**:

- Suporte para as condições de DLP do Office 365 novo que pode configurar para uma etiqueta. Para obter mais informações, consulte [configurar condições para uma etiqueta de Azure Information Protection](../deploy-use/configure-policy-classification.md).

- Suporte para as etiquetas que estão configurados para as ações definidas pelo utilizador. Para o Outlook, esta etiqueta aplica automaticamente a Outlook opção não reencaminhar. Para Word, Excel, PowerPoint e Explorador de ficheiros, esta etiqueta pede ao utilizador para especificar permissões personalizadas. Para obter mais informações, consulte [configurar uma etiqueta de Azure Information Protection para proteção](../deploy-use/configure-policy-protection.md).

- Etiquetas de suportem de vários idiomas. A partir de 30 de Agosto de 2017, o [política predefinida](../deploy-use/configure-policy-default.md) inclui suporte para vários idiomas que esta versão do cliente apresenta aos utilizadores. Para os utilizadores vejam as etiquetas na respetiva linguagem preferencial a partir de uma política predefinida antes desta data e para as etiquetas que configurar, consulte [como configurar as etiquetas para idiomas diferentes no Azure Information Protection](../deploy-use/configure-policy-languages.md).

- As etiquetas são apresentadas a partir do **proteger** botão no friso Office, para além de apresentação na barra de Information Protection. 

- Proteção nativa para os seguintes tipos de ficheiro do Visio: .vsdm. vsdx, .vssm, .vssx, .vstm, .vstx

- Suporte para configurações de cliente avançado que configurar no portal do Azure. Estas configurações incluem o seguinte:
    
    - [Ocultar ou mostrar o botão não reencaminhar no Outlook](../rms-client/client-admin-guide-customizations.md#hide-or-show-the-do-not-forward-button-in-outlook)
    
    - [Se as opções de permissões personalizadas disponível ou não está disponível para utilizadores](../rms-client/client-admin-guide-customizations.md#make-the-custom-permissions-options-available-or-unavailable-to-users)
    
    - [Permanentemente ocultar a barra do Azure Information Protection](../rms-client/client-admin-guide-customizations.md#permanently-hide-the-azure-information-protection-bar)
    
    - [Ativar a classificação recomendada no Outlook](../rms-client/client-admin-guide-customizations.md#enable-recommended-classification-in-outlook)

- Para o PowerShell, suporte para ficheiros de etiqueta forma não interativa utilizando os novos cmdlets do PowerShell, [conjunto AIPAuthentication](/powershell/module/azureinformationprotection/set-aipauthentication) e [limpar AIPAuthentication](/powershell/module/azureinformationprotection/clear-aipauthentication). Para obter mais informações como utilizar estes cmdlets, consulte o [PowerShell secção](../rms-client/client-admin-guide-powershell.md#how-to-label-files-non-interactively-for-azure-information-protection) do Guia do administrador.

- Para os cmdlets do PowerShell, [conjunto AIPFileLabel](/powershell/module/azureinformationprotection/set-aipfilelabel) e [conjunto AIPFileClassification](/powershell/module/azureinformationprotection/set-aipfileclassification), existem novos parâmetros: **proprietário** e **PreserveFileDetails** . Estes parâmetros permitem-lhe especificar um endereço de e-mail para a propriedade personalizada de proprietário e deixe a data inalterada para documentos que a etiqueta.

**Correções**:

Correções para estabilidade e para cenários específicos que incluem:

- Suporte para proteção genericamente ficheiros grandes, que anteriormente pode causar danos se com mais de 1 GB. Agora, o tamanho do ficheiro só está limitado pelo espaço de disco rígido disponível e memória disponível. Para obter mais informações sobre as limitações de tamanho de ficheiro, consulte [tamanhos suportados para proteção de ficheiros](client-admin-guide-file-types.md#file-sizes-supported-for-protection) do guia de administração.

- O Visualizador de cliente Azure Information Protection abre ficheiros protegidos de PDF (. ppdf) como só de vista.

- Suporte para etiquetagem e proteção de ficheiros armazenados no servidor do SharePoint.

- Marcas de água suportam agora várias linhas. Além disso, marcas visuais são agora aplicados a um documento de [guarde primeiro apenas](../deploy-use/configure-policy-markings.md#when-visual-markings-are-applied) em vez de sempre que um documento é guardado.

- O **executar diagnósticos** opção o **ajuda e comentários** caixa de diálogo é substituída pelo **repor definições**. O comportamento para esta ação foi alterado para incluir a assinatura de utilizador e eliminar a política do Azure Information Protection. Para obter mais informações, consulte [mais informações sobre a opção Repor definições](..\rms-client\client-admin-guide.md#more-information-about-the-reset-settings-option) do guia de administração.

- Suporte para a autenticação de proxy.

Correções para uma melhor experiência de utilizador, que incluem:

- Validação de e-mail quando os utilizadores especificarem permissões personalizadas. Além disso, vários endereços de e-mail agora podem ser especificados, premindo Enter.

- A etiqueta principal não é apresentada quando todos os respetivos sublabels estão configuradas para proteção e o cliente não tem uma edição do Office que suporta a proteção. 

## <a name="version-172100"></a>Versão 1.7.210.0

**Lançada**: 06/06/2017

Esta versão inclui a versão MSIPC 1.0.2217.1 do cliente RMS.

**Novas funcionalidades**:

- Novo cmdlet do PowerShell, [Set-AIPFileClassification](/powershell/module/azureinformationprotection/Set-AIPFileClassification). Ao executar este cmdlet, ele inspeciona os conteúdos do ficheiro e aplica automaticamente etiquetas em ficheiros sem etiqueta, de acordo com as condições que especificar na política do Azure Information Protection.

**Correções**:

- Todos os cmdlets de classificação e etiquetagem são agora suportados em computadores que não estão ligados à Internet, mas têm uma política do Azure Information Protection válida.

- Para obter consistência, um parâmetro de saída do cmdlet [Get-AIPFileStatus](/powershell/module/azureinformationprotection/get-aipfilestatus) é alterado de inglês britânico (**IsLabelled**) para inglês americano (**IsLabeled**). Se tiver scripts ou processos automatizados que procuram este parâmetro, atualize a ortografia desse parâmetro.

- As correções gerais para estabilidade são:

    - Para Outlook: correções para falhas de sistema, alto consumo de memória e problemas de exibição para menus.
    
    - Para Word, Excel e PowerPoint: correções de alta utilização da CPU, problemas de exibição ao guardar grandes ficheiros Excel ou a aplicação para de responder. 
    
    Também para estas aplicações, para melhorar o desempenho do Office 2016 com o SharePoint Online e o OneDrive para Empresas, a etiquetagem automática e recomendada é aplicada quando o ficheiro é fechado, em vez de quando o ficheiro é guardado (guarda automaticamente ou o utilizador opta por guardar). Da mesma forma, se a definição **todos os documentos e e-mails devem ter uma etiqueta** está ativada, os utilizadores não recebem pedidos para selecionar uma etiqueta até que o ficheiro for fechado. A exceção é para Word 2016 e Excel 2016 e o utilizador seleciona a opção **Guardar como**. Em seguida, esta ação aciona estes comportamentos de etiquetagem se forem configurados. 

## <a name="next-steps"></a>Próximos passos

Para obter mais informações sobre como instalar e utilizar o cliente: 

- Para os utilizadores: [Transferir e instalar o cliente](install-client-app.md)

- Para os administradores: [Guia do administrador do cliente do Azure Information Protection](client-admin-guide.md)


[!INCLUDE[Commenting house rules](../includes/houserules.md)]
