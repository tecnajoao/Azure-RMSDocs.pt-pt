---
title: "Cliente do Azure Information Protection&colon; histórico de lançamento de versões"
description: "Veja as novidades ou alterações ao lançamento do cliente do Azure Information Protection para Windows."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 10/20/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 6ebd0ca3-1864-4b3d-bb3e-a168eee5eb1d
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: ec73c1e0c0c2d5ef959f15975b2a972086a3bcff
ms.sourcegitcommit: 91585427fe62956fd78d4e7897ec8abe55b3c11d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/02/2017
---
# <a name="azure-information-protection-client-version-release-history"></a>Cliente do Azure Information Protection: histórico de lançamento de versões

>*Aplica-se a: Azure Information Protection*

A equipa do Azure Information Protection atualiza regularmente o cliente do Azure Information Protection com correções e novas funcionalidades. O cliente está incluído no catálogo Microsoft Update (categoria: **Azure Information Protection**) e podem sempre transferir a versão mais recente disponibilidade geral (DG) e a versão de pré-visualização atual do [Centro de transferências da Microsoft](https://www.microsoft.com/en-us/download/details.aspx?id=53018). 

As versões de pré-visualização não devem ser implementadas para os utilizadores finais em redes de produção. Em vez disso, utilize as versões de pré-visualização para ver e experimentar as novas funcionalidades ou correções disponíveis na futura versão de DG. 

Utilize as seguintes informações para ver o que há de novo ou o que foi alterado num determinado lançamento de DG. A versão mais atual aparece em primeiro na lista. 

> [!NOTE]
> As pequenas correções não se encontram listadas, pelo que se encontrar um problema com o cliente do Azure Information Protection, primeiro deverá verificar se é ou não um problema com a versão de DG mais recente. Se for, verifique a versão de pré-visualização atual.
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

- As etiquetas são apresentadas a partir do **proteger** botão no friso Office, para além de apresentação na barra de Information Protection. 

- Proteção nativa para os seguintes tipos de ficheiro do Visio: .vsdm. vsdx, .vssm, .vssx, .vstm, .vstx

- Suporte para configurações de cliente avançado que configurar no portal do Azure. Estas configurações incluem o seguinte:
    
    - [Ocultar o botão não reencaminhar no Outlook](../rms-client/client-admin-guide-customizations.md#hide-the-do-not-forward-button-in-outlook)
    
    - [Fazer com que as opções de permissões personalizadas disponíveis aos utilizadores](../rms-client/client-admin-guide-customizations.md#make-the-custom-permissions-options-unavailable-to-users)
    
    - [Permanentemente ocultar a barra do Azure Information Protection](../rms-client/client-admin-guide-customizations.md#make-the-custom-permissions-options-unavailable-to-users)
    
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

- A etiqueta principal não é apresentada quando todas as etiquetas secundárias são configuradas para proteção e o cliente não tem uma edição do Office que suporta a proteção. 

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

## <a name="version-14210"></a>Versão 1.4.21.0

**Lançada**: 15/03/2017

**Alteração nos requisitos:**

A versão anterior introduziu o novo pré-requisito do Microsoft .NET Framework 4.6.2 para o cliente completo. Embora não seja recomendado, pode ignorar este pré-requisito com um parâmetro de instalação personalizada, **DowngradeDotNetRequirement**. Para obter mais informações, consulte [instalar o cliente Azure Information Protection para os utilizadores](client-admin-guide-install.md) do guia de administração.

**Novas funcionalidades**:

- A capacidade de definir permissões personalizadas a partir da aplicação do Office, que lhe permite definir a proteção apenas para si, para grupos externos ou para todos os utilizadores noutra organização. Para obter mais informações, veja [Definir permissões personalizadas para um documento](client-classify-protect.md#set-custom-permissions-for-a-document) no guia do utilizador.
    
- Os ficheiros PDF já suportam etiquetas que aplicam apenas a classificação.

- Para os ficheiros PDF, o visualizador já suporta as opções como pesquisa, zoom e rodar. Para utilizar estas opções, clique com o botão direito do rato no ficheiro quando for apresentado no visualizador.

**Correções**:

- Suporte para unidades mapeadas para classificar e proteger ficheiros.

- Suporte para ficheiros grandes (maiores do que 250 MB) no Visualizador de cliente do Azure Information Protection. 

- Quando o HYOK estiver configurado, o Outlook pode aplicar etiquetas que estão configuradas para utilizar modelos do Azure Rights Management ou modelos do AD RMS.

## <a name="version-131552"></a>Versão 1.3.155.2

**Lançada**: 08/02/2017

**Novos requisitos**:

Microsoft .NET Framework

- Esta versão do Azure Information Protection requer a versão mínima do Microsoft .NET Framework 4.6.2. Se esta versão estiver em falta, o instalador tentará transferi-la e instalá-la. Poderá ser preciso reiniciar o computador depois de concluída a instalação do cliente do Azure Information Protection.

- Se o Visualizador do Azure Information Protection for instalado à parte, precisará da versão mínima do Microsoft .NET Framework 4.5.2 e, se esta estiver em falta, o instalador não a transfere nem a instala.

**Novas funcionalidades**:

- Um cliente novo e unificado que combina as funcionalidades da aplicação de partilha Rights Management para Windows com o cliente do Azure Information Protection. Inclui:
    
    - Integração com o Explorador de Ficheiros do Windows (clique com o botão direito do rato) para aplicar as etiquetas e a proteção. Suporta os formatos de ficheiro adicionais e a seleção de vários ficheiros.
    - Um visualizador para documentos protegidos (inclui o PDF protegido para SharePoint).
    - Cmdlets do PowerShell para obter e definir etiquetas para os ficheiros que estão armazenados localmente ou em partilhas de rede. Estes cmdlets são instalados com os cmdlets anteriormente enviados com a Ferramenta de Proteção RMS (módulo RMSProtection).
    - Registos da utilização do cliente que registam as informações como a etiqueta que foi aplicada, como e por quem.

Esta versão do cliente é a [Versão de Disponibilidade Geral](https://blogs.technet.microsoft.com/enterprisemobility/2017/02/08/azure-information-protection-december-update-moves-to-general-availability/) do cliente de pré-visualização que foi anunciada pela primeira vez em dezembro de 2016. Para obter mais informações acerca desta versão do cliente, veja os guias seguintes:

- [Guia do administrador de clientes do Azure Information Protection](client-admin-guide.md)

- [Guia do utilizador do Azure Information Protection](client-user-guide.md)


## <a name="version-1240"></a>Versão 1.2.4.0

**Lançada**: 27/10/2016

**Nova funcionalidade**:

- Os testes de diagnóstico e a opção de reposição que um utilizador pode executar a partir da aplicação do Office quando o cliente do Azure Information Protection está instalado: no separador **Base**, no grupo **Proteção**, clique em **Proteger** e em **Ajuda e comentários** e, em seguida, clique em **Executar diagnósticos**. 

    Para obter mais informações sobre esta opção, veja a secção [Verificações adicionais e resolução de problemas](client-admin-guide.md#installation-checks-and-troubleshooting) no guia do administrador.

**Correções**:

- A instalação do cliente é concluída quando o serviço Windows Update for desativado.

- No Office 2016, quando guarda um documento e a etiqueta aplicada é configurada para um cabeçalho ou rodapé, o cursor não se desloca para o cabeçalho ou rodapé.

- A classificação automática funciona no Word para texto em caixas de texto agregadas.


## <a name="version-11230"></a>Versão 1.1.23.0

**Lançada**: 01/10/2016

Disponibilidade Geral.

## <a name="next-steps"></a>Próximos passos

Para obter mais informações sobre como instalar e utilizar o cliente:

- Para os utilizadores: [Transferir e instalar o cliente](install-client-app.md)

- Para os administradores: [Guia do administrador do cliente do Azure Information Protection](client-admin-guide.md)


[!INCLUDE[Commenting house rules](../includes/houserules.md)]
