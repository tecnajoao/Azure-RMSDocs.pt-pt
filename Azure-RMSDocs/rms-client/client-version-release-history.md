---
title: Histórico de versões de cliente de proteção de informações do Azure - versão e política de suporte
description: Ver o que é nova ou alterada uma versão do cliente Azure Information Protection para o Windows e compreender a política de ciclo de vida de suporte.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 03/19/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 6ebd0ca3-1864-4b3d-bb3e-a168eee5eb1d
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: ff9d6a4ce66deed8add68d7b1efc889ee9448f53
ms.sourcegitcommit: 5866509c17872e274720d3014fe218ed95e86ee3
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/06/2018
---
# <a name="azure-information-protection-client-version-release-history-and-support-policy"></a>Cliente do Azure Information Protection: política de suporte e histórico da versão versão

>*Aplica-se a: serviços de gestão de direitos do Active Directory [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 com SP1, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2*

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

A versão de pré-visualização atual é **1.21.203.0** e tem as seguintes alterações desde a versão GA atual do cliente.

Esta versão inclui o MSIPC versão 1.0.3403.1224 do cliente RMS.

**Novas funcionalidades**:

- O scanner do Azure Information Protection: módulo do PowerShell a que está incluído com o cliente tem novos cmdlets para instalar e Configurar scanner para que possam detetar, classificar e proteger ficheiros no seu arquivos de dados no local. Para obter instruções, consulte [implementar a análise do Azure Information Protection para classificar e proteger ficheiros automaticamente](../deploy-use/deploy-aip-scanner.md). 

- Para aplicações do Office, a classificação automática e recomendada é executada continuamente em segundo plano, em vez de executar quando os documentos são guardados. Com esta alteração no comportamento, agora pode aplicar a classificação automática e recomendada para os documentos que estão armazenados no SharePoint Online. [Mais informações](../deploy-use/configure-policy-classification.md#how-automatic-or-recommended-labels-are-applied) 

- Agora pode definir diferentes marcas visuais para o Word, Excel, PowerPoint e Outlook utilizando uma instrução de variável "If.App" na cadeia de texto e identifique o tipo de aplicação. [Mais informações](../deploy-use/configure-policy-markings.md#setting-different-visual-markings-for-word-excel-powerpoint-and-outlook)

- Suporte para o [definição de política](../deploy-use/configure-policy-settings.md), **apresentar a barra do Information Protection em aplicações do Office**. Quando esta definição estiver desativada, os utilizadores selecionar etiquetas do **proteger** botão no Friso.

- Uma nova avançado definição de cliente, de modo que Outlook não se aplica a etiqueta predefinida que está configurada na política do Azure Information Protection. Em vez disso, o Outlook pode aplicar uma etiqueta predefinida diferente ou sem etiqueta. [Mais informações](client-admin-guide-customizations.md#set-a-different-default-label-for-outlook) 

- Para aplicações do Office, ao especificar permissões personalizadas, pode procurar e selecione os utilizadores a partir de um ícone de livro de endereços. Esta opção coloca paridade à experiência de utilizador quando especificar permissões personalizadas, utilizando o Explorador de ficheiros.

- Suporte para um método de autenticação completamente não interativa, para contas de serviço que utilize o PowerShell e que não é possível conceder a **iniciar sessão localmente** à direita. Este método de autenticação requer que utilize a nova *Token* parâmetro com [conjunto AIPAuthentication](/powershell/module/azureinformationprotection/Set-AIPAuthentication), e executar um script do PowerShell como uma tarefa. [Mais informações](../rms-client/client-admin-guide-powershell.md#specify-and-use-the-token-parameter-for-set-aipauthentication)

- Novo parâmetro, *IntegratedAuth* para [Set-RMSServerAuthentication](/powershell/module/azureinformationprotection/set-rmsserverauthentication). Este parâmetro suporta o modo de servidor para AD RMS, que é necessário para o AD RMS suportar a FCI do Windows Server.


**Correções**:

Correções para estabilidade e para cenários específicos que incluem:

- Para versões do Office 16.0.8628.2010 e posterior (clique para execução), a barra do Azure Information Protection suporta as opções de visualização mais recentes do monitor que anteriormente poderão resultar na barra de apresentar fora das aplicações do Office.

- Quando dois organização através do Azure Information Protection partilhar identificados documentos e e-mails, as suas próprias etiquetas são mantidas e não são substituídas por etiquetas de outra organização.

- Suporte para células no Excel que contêm cross-references, que anteriormente provocou a existência de danos no texto nessa célula.

- Suporte para a alteração de temas do Office ou temas do Windows, que anteriormente provocou o Excel para não apresentar todos os dados depois do tema foi alterado.

- Agora podem ser inspecionados os ficheiros que tenham uma extensão de nome de ficheiro. XML para a classificação recomendada ou automática.

- O Visualizador pode agora abrir baseado em texto ficheiros protegidos (. ptxt e. pxml) com mais de 20 MB. 

- Evitar pendente Outlook quando são utilizados lembretes Outlook.

- O arranque de configuração é concluída com êxito no Office 64 bits, para que possam proteger documentos e e-mails.

- Pode agora configurar uma etiqueta para permissões definidas pelo utilizador para Word, Excel, PowerPoint e Explorador de ficheiros e também utilizar a definição para ocultar as opções de permissões personalizadas de cliente avançado. [Mais informações](client-admin-guide-customizations.md#make-the-custom-permissions-options-available-or-unavailable-to-users) 

- Reverter para o tipo de letra Calibri se marcas visuais na política do Azure Information Protection estão configurados para um nome de tipo de letra que não está instalado no cliente.

- Impedir que as falhas do Office depois do cliente Azure Information Protection é atualizado.

- Para aplicações do Office, melhore o consumo de memória e desempenho.

- Quando configurar uma etiqueta de utilizador definido permissões e a proteção de HYOK (AD RMS), a proteção já não utiliza incorretamente o serviço Azure Rights Management.

- Para uma experiência mais consistente de gestão, sublabels deixa de herdar marcações visuais e as definições de proteção da respetiva etiqueta principal.


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

## <a name="next-steps"></a>Próximos passos

Para obter mais informações sobre como instalar e utilizar o cliente: 

- Para os utilizadores: [Transferir e instalar o cliente](install-client-app.md)

- Para os administradores: [Guia do administrador do cliente do Azure Information Protection](client-admin-guide.md)


[!INCLUDE[Commenting house rules](../includes/houserules.md)]
