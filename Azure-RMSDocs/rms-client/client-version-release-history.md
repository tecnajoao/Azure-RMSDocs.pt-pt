---
title: Histórico de versões de cliente do Azure Information Protection - versão e política de suporte
description: Veja o que há de novo ou alterado numa versão do cliente do Azure Information Protection para Windows e compreender a política de ciclo de vida de suporte.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 11/14/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 6ebd0ca3-1864-4b3d-bb3e-a168eee5eb1d
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: d4b9419ee12dfef0db29604dc7a396eedd7225fc
ms.sourcegitcommit: a547dee247e4961e8f7c1f08e39b03dff710a74c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/14/2018
ms.locfileid: "51628076"
---
# <a name="azure-information-protection-client-version-release-history-and-support-policy"></a>Cliente do Azure Information Protection: política de histórico e suporte de lançamento de versão

>*Aplica-se a: serviços de gestão de direitos do Active Directory [do Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 com SP1, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2*

A equipa do Azure Information Protection atualiza regularmente o cliente do Azure Information Protection com correções e novas funcionalidades. 

Pode baixar a mais recente versão de lançamento de disponibilidade geral e a versão de pré-visualização atual (se disponível) partir do [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=53018). A versão de disponibilidade geral também está incluída no catálogo Microsoft Update (categoria: **do Azure Information Protection**), para que pode atualizar o cliente com o WSUS ou do Configuration Manager ou outra implementação de software mecanismos de utilizam o Microsoft Update.

Para obter mais informações, consulte [Upgrading e manter o cliente do Azure Information Protection](client-admin-guide.md#upgrading-and-maintaining-the-azure-information-protection-client).

### <a name="servicing-information-and-timelines"></a>Informações e as linhas do tempo de manutenção

Cada versão de disponibilidade geral (GA) do cliente do Azure Information Protection é suportado para até seis meses após o lançamento da versão GA subsequente. Versões não suportadas do cliente não estão incluídas nesta página. Correções e novas funcionalidades sempre são aplicadas para a versão de DG mais recente e não serão aplicadas a versões mais antigas do GA.

As versões de pré-visualização não devem ser implementadas para os utilizadores finais em redes de produção. Em alternativa, utilize a versão de pré-visualização mais recente para ver e experimentar novas funcionalidades ou correções disponíveis na versão de DG. Versões de pré-visualização que não estão atualmente não são suportadas.

### <a name="release-history"></a>Histórico de versões

Utilize as seguintes informações para ver o que há de novo ou alterado para uma versão suportada do cliente do Azure Information Protection para Windows. A versão mais atual aparece em primeiro na lista. 

> [!NOTE]
> Pequenas correções não são listadas para que se ocorrer um problema com o cliente do Azure Information Protection, recomendamos que verifique se ser corrigido com o lançamento de DG mais recente. Se o problema persistir, verifique a versão de pré-visualização atual.
>  
> Para obter suporte técnico, consulte a [opções de suporte e recursos da Comunidade](../information-support.md#support-options-and-community-resources) informações. Também o incentivamos a interagir com a equipa do Azure Information Protection, no [site Yammer](https://www.yammer.com/askipteam/).

## <a name="versions-later-than-137190"></a>Versões mais tarde do que 1.37.19.0

Se tiver uma versão 1 do cliente posterior 1.37.19.0, é uma versão de pré-visualização para fins de teste e avaliação. 

> [!TIP]
> Interessado na avaliação do Azure Information Protection unified cliente etiquetagem porque as etiquetas são publicadas a partir do Centro de conformidade e segurança do Office 365? Ver [do Azure Information Protection unified cliente etiquetagem: informações de lançamento de versão](unifiedlabelingclient-version-release-history.md).

**Lançado**: 20/09/2018

**Novas funcionalidades:**

- Suporte para [central reporting](../reports-aip.md) para a funcionalidade de análise do Azure Information Protection anunciada na Microsoft Ignite.

**Adicionais:**

Apenas para esta versão de pré-visualização, específica para a deteção de impressão:

- Instale o scanner, seguindo estes passos:
    
    1. Instale a versão de DG (1.37.19.0) atual do cliente.
    2. Instalar e configurar a deteção de impressão.
    3. Inicie o scanner.
    4. Atualize o cliente do Azure Information Protection para esta versão de pré-visualização.
    5. Inicie o scanner.

- Problema conhecido com a análise de grandes conjuntos de dados:
    
    Com esta versão de pré-visualização, aumente gradualmente o número de ficheiros analisados e monitorizar o progresso. Se o estado do leitor de relatórios que está a ser executado, mas não obter analisados novos ficheiros, reduza o número de ficheiros analisados e reiniciar o scanner. 

Se precisar de instruções para instalar, configurar e iniciar o scanner, consulte [Implantando o scanner do Azure Information Protection para classificar e proteger ficheiros automaticamente](../deploy-aip-scanner.md).

## <a name="version-137190"></a>Versão 1.37.19.0

**Lançado**: 17/09/2018

Esta versão inclui a versão 1.0.3592.627 do cliente RMS MSIPC.

**Novas funcionalidades**: 

- Suporte para a norma ISO para a encriptação de PDF, ao configurar uma nova [configuração de cliente avançado](client-admin-guide-customizations.md#protect-pdf-files-by-using-the-iso-standard-for-pdf-encryption). Quando esta opção estiver configurada, documentos PDF que protege reter a respetiva extensão de nome de ficheiro. pdf (em vez de alterar para. ppdf) e podem ser abertos por leitores PDF que suportam esta norma ISO. Atualmente, deve instruir os utilizadores para abrir estas PDFs protegidos manualmente ao utilizar o Visualizador do Azure Information Protection. Para ajudar os usuários a fazer isso, quando abrir um destes PDFs protegidos, verão uma página com ícones para selecionar para seu sistema operativo.

- Suporte para novos tipos de informações confidenciais para o ajudar a classificar documentos que contenham informações pessoais. [Mais informações](../configure-policy-classification.md#sensitive-information-types-that-require-a-minimum-version-of-the-client) 

- As etiquetas que aplicam a proteção agora apresentadas nas aplicações do Office 2016 (versão mínima 1805, build 9330.2078) quando o utilizador tem atribuída uma licença do Azure Rights Management (também conhecido como Azure Information Protection para o Office 365).

- Suporte de etiquetagem **Strict documento de XML aberto** formato em arquivos do Word, Excel e PowerPoint. Para obter mais informações sobre os formatos XML abertos, consulte a postagem no blog Office [novas opções de formato de ficheiro do novo Office](https://www.microsoft.com/en-us/microsoft-365/blog/2012/08/13/new-file-format-options-in-the-new-office/). 

- Suporte para ficheiros que foram protegidos pelo Secure Islands quando os ficheiros que não documentos PDF e do Office. Por exemplo, texto e imagem os ficheiros protegidos. Em alternativa, a extensão de nome de ficheiro de ficheiros que tenham um. pfile. Este suporte permite novos cenários, como o scanner do Azure Information Protection poder inspecionar esses arquivos de informações confidenciais e relabeling-las automaticamente para o Azure Information Protection. [Mais informações](client-admin-guide-customizations.md#support-for-files-protected-by-secure-islands)

- Novas definições de cliente avançadas para remover os cabeçalhos e rodapés que foram aplicadas a documentos por outras soluções de etiquetas. [Mais informações](client-admin-guide-customizations.md#remove-headers-and-footers-from-other-labeling-solutions)

- Para o scanner do Azure Information Protection:

    - Novo cmdlet, [AIPScanner atualização](/powershell/module/azureinformationprotection/Update-AIPScanner): necessário para executar uma vez após a atualização da versão anterior de GA (1.29.5.0) ou anterior.
    
    - Novo cmdlet, [Get-AIPScannerStatus](/powershell/module/azureinformationprotection/Get-AIPScannerStatus): obtém o estado atual do serviço para a deteção de impressão.  
    
    - Novo cmdlet, [início AIPScan](/powershell/module/azureinformationprotection/Start-AIPScan): instrui o scanner para iniciar um ciclo de análise de quando a agenda está definida para manual de tempo.
    
    - SharePoint Server 2010 é suportada para os clientes que tenham [suporte para esta versão do SharePoint estendido](https://support.microsoft.com/lifecycle/search?alpha=SharePoint%20Server%202010).
    
- Suporte para a nova **do Azure Information Protection – nós (pré-visualização)** painel no portal do Azure, o que lhe permite gerir scanners de um local central. Informações da sua implementados scanners que ter conectividade para o Azure são atualizadas a cada cinco minutos. A partir deste painel, pode iniciar o scanner para uma única análise, reanalisar todos os ficheiros, verificar o estado de um scanner e ver a taxa de digitalização.

**Correções**

- Para o scanner do Azure Information Protection:
    
    - Para documentos protegidos em bibliotecas do SharePoint, que o *DefaultOwner* parâmetro não for utilizado para o repositório de dados, o valor de Editor do SharePoint agora é utilizado como o valor predefinido em vez do valor de autor.
    
    - Os relatórios de scanner incluem "Última modificação por" para documentos do Office.
    
    - Agora pode proteger todos os tipos de ficheiro ao utilizar o `*` universais ao editar o registro, conforme descrito no [editar o registo para o scanner](../deploy-aip-scanner.md#editing-the-registry-for-the-scanner) secção.

- Ver mensagens de e-mail ao utilizar os ícones de seta próximo Item e o Item anterior na barra de ferramentas de acesso rápido mostra a etiqueta correta de cada e-mail.

- Permissões personalizadas suporta endereços de e-mail do destinatário que contêm um apóstrofe.

- O ambiente de computador será inicializado com sucesso (arranque) quando esta ação é iniciada, abrindo um documento protegido que é armazenado no SharePoint Online.

- Ao utilizar o cliente para o botão direito do rato no Explorador de ficheiros, o PowerShell ou o scanner, etiquetagem está bloqueada para ficheiros em localizações de WebDav porque se trata de um cenário não suportado.

- O ícone Eliminar etiqueta não apresenta nas aplicações de cliente (Word, Excel, PowerPoint e Outlook) ao configurar o [definição de política](../configure-policy-settings.md) dos **todos os documentos e e-mails devem ter uma etiqueta**.

**Alterações adicionais**:

- Para [Set-AIPScannerConfiguration](/powershell/module/azureinformationprotection/Set-AIPScannerConfiguration):
    
    - Os valores para o *agenda* parâmetro já não são **OneTime**, **contínua**, e **Never**, mas agora **Manual** e **sempre**.
        
    - O *tipo* parâmetro é removido, pelo que também é removido da saída quando executa [Get-AIPScannerConfiguration](/powershell/module/azureinformationprotection/Get-AIPScannerConfiguration). Por predefinição, os ficheiros apenas novos ou modificados são inspecionados após a primeira análise ciclo. Se definiu anteriormente a *tipo* parâmetro para **completo** para executar a reanálise todos os ficheiros, agora, execute [AIPScan início](/powershell/module/azureinformationprotection/Start-AIPScan) com o *repor* parâmetro. A deteção de impressão também tem de ser configurada para um agendamento manual, o que requer o *agenda* parâmetro para ser definido como **Manual** com [conjunto AIPScannerConfiguration](/powershell/module/azureinformationprotection/Set-AIPScannerConfiguration).
    
- A lista de exclusão predefinida para o cliente e o scanner agora inclui arquivos. zip, rar e msg. O scanner também exclui os arquivos. rtf. [Mais informações](client-admin-guide-file-types.md#file-types-that-are-excluded-from-classification-and-protection)

- A versão de política é alterada para 1.4. Identificar o número de versão é necessária para [configurar computadores desligados](client-admin-guide-customizations.md#support-for-disconnected-computers).

- O **enviar comentários** ligação na **ajuda e Feedback** caixa de diálogo é removida. Temporariamente foi substituída pela **comunicar um problema**, mas esta ligação apresenta agora apenas versões de pré-visualização. Por predefinição, esta opção envia um e-mail à Microsoft, mas pode alterar este endereço de e-mail para uma cadeia de caracteres HTTP que especificar. Por exemplo, uma página da web personalizada para os utilizadores comuniquem problemas, ou um endereço de e-mail que vai para o suporte técnico. Para modificar este endereço, utilize um [definição de cliente avançado](client-admin-guide-customizations.md#modify-the-email-address-for-the-report-an-issue-link).

## <a name="version-12950"></a>Versão 1.29.5.0 

**Lançado**: 06/26/2018

Esta versão inclui a versão 1.0.3403.1224 do cliente RMS MSIPC.

**Correções**:

- Para versões do Outlook 16.0.9324.1000 e posterior (clique-e-use), a barra do Azure Information Protection suporta as opções de exibição de monitor mais recente que anteriormente, poderão resultar na barra de exibição de fora da aplicação do Outlook.

- Marcas visuais que configurou [por tipo de aplicação do Office](../configure-policy-markings.md#setting-different-visual-markings-for-word-excel-powerpoint-and-outlook) agora substitua um cabeçalho ou rodapé que estava anteriormente aplicada por uma etiqueta do Azure Information Protection.

- Quando um ficheiro do Excel já tem o nome e a etiqueta aplicar marcações visuais, uma nova folha também tem agora marcas visuais a etiqueta aplicadas.

- Quando utiliza o definição de cliente avançado [Etiquetar um documento do Office usando uma propriedade personalizada existente](client-admin-guide-customizations.md#label-an-office-document-by-using-an-existing-custom-property), a etiquetagem automática não substitui a etiquetagem manual.

## <a name="version-127480"></a>Versão 1.27.48.0

**Lançado**: 05/30/2018

Esta versão inclui a versão 1.0.3403.1224 do cliente RMS MSIPC.

**Novas funcionalidades**: 

- Para o scanner do Azure Information Protection:
    
    - Pode especificar uma lista de tipos de ficheiros para incluir ou excluir da análise. Para especificar esta lista, utilize [Set-AIPScannerScannedFileTypes](/powershell/module/azureinformationprotection/Set-AIPScannerScannedFileTypes). Depois de especificar a lista de tipos de ficheiro, pode adicionar um novo tipo de ficheiro à lista utilizando [Add-AIPScannerScannedFileTypes](/powershell/module/azureinformationprotection/Add-AIPScannerScannedFileTypes)e remover um tipo de ficheiro da lista com [Remove-AIPScannerScannedFileTypes](/powershell/module/azureinformationprotection/Remove-AIPScannerScannedFileTypes).
    
    - Pode Etiquetar ficheiros sem inspecionar os conteúdos através da aplicação de uma etiqueta predefinida. Utilize o [AIPScannerRepository conjunto](/powershell/module/azureinformationprotection/Set-AIPScannerRepository) cmdlet e defina o *MatchPolicy* parâmetro **desativar**. 
    
    - Pode detetar ficheiros com tipos de informações confidenciais sem configurar etiquetas para classificação automática. utilizar o [Set-AIPScannerConfiguration](/powershell/module/azureinformationprotection/Set-AIPScannerConfiguration) cmdlet e defina o *DiscoverInformationTypes* parâmetro **todos os**
    
    - Por predefinição, apenas os tipos de documentos do Office estão protegidos. Outros tipos de ficheiro podem ser protegidos ao defini-los no registo. Para obter instruções, consulte [configuração da API de ficheiros](../develop/file-api-configuration.md) de orientação para programadores.
    
    - Por predefinição, o scanner é agora executada com um nível baixo de integridade para uma maior segurança no caso de executar a deteção de impressão com uma conta que tem direitos privilegiado. Quando a conta de serviço que executa a deteção de impressão tem apenas os direitos documentados no [pré-requisitos do scanner](../deploy-aip-scanner.md#prerequisites-for-the-azure-information-protection-scanner), nível baixo de integridade não é necessário e não é recomendado porque ele afeta negativamente o desempenho. Pode utilizar um definição para desativar o nível de baixa integridade de cliente avançado. [Mais informações](client-admin-guide-customizations.md#disable-the-low-integrity-level-for-the-scanner) 
    
- Para [Get-AIPFileStatus](/powershell/module/azureinformationprotection/Get-AIPFileStatus), a saída inclui agora o proprietário do Rights Management e o emissor do Rights Management e a data em que o conteúdo que foi protegido.
 
**Alterações adicionais**:

- Para o scanner do Azure Information Protection: 
    
    - Se tiver instalado uma versão anterior do scanner, volte a executar o comando de instalação com o scanner [Install-AIPScanner](/powershell/module/azureinformationprotection/Install-AIPScanner) depois de ter atualizado o cliente do Azure Information Protection. As definições de configuração para o scanner e repositórios serão mantidas. Reinstalar o scanner concede o scanner permissões de eliminação de conta de serviço da base de dados do scanner, que será necessária para relatórios.    
    
    - O *ScanMode* parâmetro partir [AIPScannerConfiguration conjunto](/powershell/module/azureinformationprotection/Set-AIPScannerConfiguration) foi mudado para **impor**, com valores off e, no.
    
    - Para usar uma etiqueta predefinida, já não precisa de configurar uma etiqueta predefinida como uma definição de política. Em vez disso, basta especifica esta etiqueta predefinida com a configuração do repositório. 

- Removido "Parabéns!" Bem-vindo de página e a página "O que há de novo no Azure Information Protection", que é apresentado para a primeira utilização nas aplicações do Office.

## <a name="version-12660"></a>Versão 1.26.6.0

**Lançado**: 04/17/2018

Esta versão inclui a versão 1.0.3403.1224 do cliente RMS MSIPC.

**Novas funcionalidades**:

- O scanner do Azure Information Protection: módulo do PowerShell o que está incluído com o cliente tem novos cmdlets para instalar e configurar a deteção de impressão para que pode detetar, classificar e proteger ficheiros em seus arquivos de dados no local. Para obter instruções, consulte [Implantando o scanner do Azure Information Protection para classificar e proteger ficheiros automaticamente](../deploy-aip-scanner.md). 
- Agora pode definir diferentes marcas visuais para Word, Excel, PowerPoint e Outlook com uma declaração de variável "If.App" na cadeia de texto e identifique o tipo de aplicação. [Mais information]configure-policy-markings.md#setting-different-visual-markings-for-word-excel-powerpoint-and-outlook)

- Suporte para o [definição de política](../configure-policy-settings.md), **apresentar a barra de Information Protection nas aplicações do Office**. Quando esta definição estiver desativada, os utilizadores selecionarem etiquetas a partir da **Protect** botão na faixa de opções.

- Um nova definição de cliente avançado (ainda em pré-visualização) para ativar a classificação para executar continuamente em segundo plano. Quando esta definição estiver ativada, para aplicações do Office, classificação automática e recomendada é executada continuamente em segundo plano, em vez de executar quando os documentos são guardados. Com esta alteração no comportamento, agora pode aplicar classificação automática e recomendada para documentos armazenados no SharePoint Online. [Mais informações](client-admin-guide-customizations.md#turn-on-classification-to-run-continuously-in-the-background)

- Um nova definição de cliente avançado, de modo que o Outlook não se aplica a etiqueta predefinida que é configurada na política do Azure Information Protection. Em vez disso, o Outlook pode aplicar uma etiqueta predefinida diferente, ou nenhuma etiqueta. [Mais informações](client-admin-guide-customizations.md#set-a-different-default-label-for-outlook) 

- Para aplicações do Office, ao especificar permissões personalizadas, pode agora navegar e selecionar utilizadores a partir de um ícone de livro de endereços. Esta opção traz paridade para a experiência do usuário quando especifica permissões personalizadas utilizando o Explorador de ficheiros.

- Suporte para um método de autenticação completamente não interativa, para contas de serviço que utilize o PowerShell e que não é possível conceder a **iniciar sessão localmente** certo. Este método de autenticação, tem de utilizar a nova *Token* parâmetro com [Set-AIPAuthentication](/powershell/module/azureinformationprotection/Set-AIPAuthentication), e executar um script do PowerShell como uma tarefa. [Mais informações](client-admin-guide-powershell.md#specify-and-use-the-token-parameter-for-set-aipauthentication)

- Novo parâmetro, *IntegratedAuth* para [Set-RMSServerAuthentication](/powershell/module/azureinformationprotection/set-rmsserverauthentication). Este parâmetro suporta o modo de servidor para AD RMS, que é necessária para o AD RMS suportar a FCI do Windows Server.


**Correções**:

Correções para a estabilidade e para cenários específicos que incluem:

- Para versões do Office 16.0.8628.2010 e posterior (clique-e-use), a barra do Azure Information Protection suporta as opções de exibição de monitor mais recente que anteriormente, poderão resultar na barra de aplicativos fora do Office a apresentar.

- Quando dois organização ao utilizar o Azure Information Protection partilhar etiquetados de documentos e e-mails, suas próprias etiquetas são retidas e não são substituídas por etiquetas da outra organização.

- Para o Excel:
        
    - Suporte para alterar os temas do Office ou os temas do Windows, que anteriormente causado o Excel para não exibir todos os dados depois do tema foi alterado.
        
    - Suporte para as células que contenham cross-references, que anteriormente causado Corrupção de texto na célula.
    
    - Suporte para digitação japonês, chinês ou coreano caracteres, que anteriormente fechado uma janela para que não foi possível selecionar estes carateres.
    
    - Suporte para comentários, que anteriormente fechado o comentário enquanto ela foi escrita.

- Para o PowerPoint: Suporte para coautoria, que anteriormente pode provocar a perda de dados.

- Agora podem ser inspecionados ficheiros que tenham uma extensão de nome de ficheiro. XML para a classificação recomendada ou automática.

- O Visualizador pode agora abrir baseado em texto ficheiros protegidos (. ptxt e. pxml) mais de 20 MB. 
- Impedi que de Outlook quando são utilizados lembretes do Outlook.

- Arranque de for concluída com êxito no Office de 64 bits, para que possa proteger documentos e e-mails.

- Pode agora configurar uma etiqueta para permissões definidas pelo utilizador para o Word, Excel, PowerPoint e o Explorador de ficheiros e também utilizar a definição para ocultar as opções de permissões personalizadas de cliente avançado. [Mais informações](client-admin-guide-customizations.md#make-the-custom-permissions-options-available-or-unavailable-to-users) 

- Reverter para o tipo de letra Calibri se marcadores visuais na política do Azure Information Protection estão configurados para um nome de fonte que não está instalado no cliente.

- Evitar falhas de sistema do Office, depois do cliente do Azure Information Protection é atualizado.

- Para aplicações do Office, melhore o consumo de memória e desempenho.

- Quando configura uma etiqueta para permissões definidas pelo utilizador e a proteção do HYOK (AD RMS), a proteção usa incorretamente já não é o serviço Azure Rights Management.

- Para uma experiência de gestão mais consistente, subetiquetas deixa de herdar marcas visuais e as definições de proteção da sua etiqueta principal.

**Alterações adicionais**:

- Para [registo de utilização do cliente](client-admin-guide-files-and-logging.md#usage-logging-for-the-azure-information-protection-client ): 102 de ID de evento e ID 103 são substituídos por evento 101 de ID.

## <a name="next-steps"></a>Passos Seguintes

Para obter mais informações sobre como instalar e utilizar o cliente: 

- Para os utilizadores: [Transferir e instalar o cliente](install-client-app.md)

- Para os administradores: [Guia do administrador do cliente do Azure Information Protection](client-admin-guide.md)


