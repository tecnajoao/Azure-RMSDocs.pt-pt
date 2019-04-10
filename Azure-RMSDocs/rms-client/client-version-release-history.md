---
title: Histórico de versões de cliente do Azure Information Protection - versão e política de suporte
description: Veja o que há de novo ou alterado numa versão do cliente do Azure Information Protection para Windows e compreender a política de ciclo de vida de suporte.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 04/08/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 52b72d7d05b405e0d4972dd4c4c1edfee3d9fe3b
ms.sourcegitcommit: ce2078712d111f102a72b3a8697121f1390bdf07
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/08/2019
ms.locfileid: "59289507"
---
# <a name="azure-information-protection-client-version-release-history-and-support-policy"></a>Cliente do Azure Information Protection: Política de histórico e suporte de lançamento de versão

>*Aplica-se a: Serviços de gestão de direitos do Active Directory [do Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 com SP1, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2*

A equipa do Azure Information Protection atualiza regularmente o cliente do Azure Information Protection com correções e novas funcionalidades. 

Pode baixar a mais recente versão de lançamento de disponibilidade geral e a versão de pré-visualização atual (se disponível) partir do [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=53018). Após um curto atraso, normalmente, duas semanas, a versão mais recente da disponibilidade geral também está incluída no catálogo Microsoft Update (categoria: **Azure Information Protection**). Essa inclusão no catálogo significa que pode atualizar o cliente com o WSUS ou do Configuration Manager ou de outros mecanismos de implantação de software que utilizam o Microsoft Update.

Para obter mais informações, consulte [Upgrading e manter o cliente do Azure Information Protection](client-admin-guide.md#upgrading-and-maintaining-the-azure-information-protection-client).

### <a name="servicing-information-and-timelines"></a>Informações e as linhas do tempo de manutenção

Cada versão de disponibilidade geral (GA) do cliente do Azure Information Protection é suportado para até seis meses após o lançamento da versão GA subsequente. A documentação não inclui informações sobre as versões não suportadas do cliente. Correções e novas funcionalidades sempre são aplicadas para a versão de DG mais recente e não serão aplicadas a versões mais antigas do GA.

As versões de pré-visualização não devem ser implementadas para os utilizadores finais em redes de produção. Em alternativa, utilize a versão de pré-visualização mais recente para ver e experimentar novas funcionalidades ou correções disponíveis na versão de DG. Versões de pré-visualização que não estão atualmente não são suportadas.

### <a name="release-history"></a>Histórico de versões

Utilize as seguintes informações para ver o que há de novo ou alterado para uma versão suportada do cliente do Azure Information Protection para Windows. A versão mais atual aparece em primeiro na lista. 

> [!NOTE]
> Pequenas correções não são listadas para que se ocorrer um problema com o cliente do Azure Information Protection, recomendamos que verifique se ser corrigido com o lançamento de DG mais recente. Se o problema persistir, verifique a versão de pré-visualização atual.
>  
> Para obter suporte técnico, consulte a [opções de suporte e recursos da Comunidade](../information-support.md#support-options-and-community-resources) informações. Também o incentivamos a interagir com a equipa do Azure Information Protection, no [site Yammer](https://www.yammer.com/askipteam/).

## <a name="versions-later-than-141510"></a>Versões mais tarde do que 1.41.51.0

Se tiver uma versão 1 do cliente posterior 1.41.51.0, é uma versão de pré-visualização para fins de teste e avaliação.  

> [!TIP]
> Interessado na avaliação do Azure Information Protection unified cliente etiquetagem porque as etiquetas são publicadas a partir da segurança do Office 365 & o Centro de conformidade, o Centro de segurança do Microsoft 365 ou o Centro de conformidade do Microsoft 365? Consulte [do Azure Information Protection unified cliente etiquetagem: Informações de lançamento de versão](unifiedlabelingclient-version-release-history.md).

**Lançado**: 03/05/2019

Esta versão inclui a versão 1.0.3592.627 do cliente RMS MSIPC.

**Novas funcionalidades:**

- O scanner do Azure Information Protection está agora configurado no portal do Azure, em vez de através do PowerShell:
    
    - Se estiver a atualizar a partir de uma versão de disponibilidade geral do scanner, o processo de atualização é diferente das versões anteriores, por isso, certifique-se de que leia [atualizar o scanner do Azure Information Protection](client-admin-guide.md#upgrading-the-azure-information-protection-scanner).
    
    - Se estiver instalando o scanner pela primeira vez, em vez atualizar, veja [implantar a versão de pré-visualização do scanner do Azure Information Protection para classificar e proteger ficheiros automaticamente](../deploy-aip-scanner-preview.md).

- Se Etiquetar e proteger ficheiros ao utilizar o [Set-AIPFileLabel](/powershell/azureinformationprotection/vlatest/set-aipfilelabel) cmdlet, pode utilizar os *EnableTracking* parâmetro para registrar o arquivo com o site de controlo de documentos. [Mais informações](client-admin-guide-document-tracking.md#using-powershell-to-register-labeled-documents-with-the-document-tracking-site)

- O scanner do Azure Information Protection suporta agora várias bases de dados de configuração na mesma instância do SQL server quando especifica um nome de perfil.

- Suporte para os seguintes tipos de informações confidenciais que ajudam a identificar as credenciais em documentos e e-mails:
    - Cadeia de ligação do Azure Service Bus
    - Cadeia de ligação do IoT do Azure
    - Conta de armazenamento do Azure
    - Cadeia de ligação de base de dados IAAS do Azure e a cadeia de ligação de SQL do Azure
    - Cadeia de ligação de Cache de Redis do Azure
    - Azure SAS
    - Cadeia de ligação do SQL Server
    - Chave de autenticação do Azure DocumentDB
    - A definição de palavra-passe de publicação do Azure
    - Chave de conta de armazenamento do Azure (genérico)

- Novas definições de cliente avançado que implementam as mensagens pop-up no Outlook que pode avisar, justificar ou bloco de e-mails enviados. [Mais informações](client-admin-guide-customizations.md#implement-pop-up-messages-in-outlook-that-warn-justify-or-block-emails-being-sent)

- Nova definição de cliente avançado que é aplicável apenas ao configurar a política de configuração para não exibir permissões personalizadas: Quando existe um ficheiro que está protegido com permissões personalizadas, exiba a opção de permissões personalizadas no Explorador de ficheiros para os utilizadores podem ver e alterá-los (se tiverem permissões para alterar as definições de proteção). [Mais informações](client-admin-guide-customizations.md#for-files-protected-with-custom-permissions-always-display-custom-permissions-to-users-in-file-explorer)

- Duas novas definições avançadas de cliente para a análise do Azure Information Protection, para os seguintes cenários:
    
    - Evitar o envio de corresponde ao tipo de informações para um subconjunto de utilizadores quando tiver selecionado a caixa de verificação no portal do Azure para recolher as correspondências de conteúdo. [Mais informações](client-admin-guide-customizations.md#disable-sending-information-type-matches-for-a-subset-of-users)
    - Para o relatório de deteção, apresenta se os ficheiros contêm informações confidenciais. [Mais informações](client-admin-guide-customizations.md#enable-azure-information-protection-analytics-to-discover-sensitive-information-in-documents)

**Correções**:

- Marcas visuais novos consistentemente são aplicadas quando um utilizador adiciona duas novas secções para um documento do Word e, em seguida, relabels o documento.

- O cliente do Azure Information Protection remove corretamente proteção a partir de um documento PDF que foi protegido pela aplicação de partilha Rights Management.

- Nomes de ficheiros e caminhos não apresentar pontos de interrogação (**?**) em vez de não-ASCII no analytics do Azure Information Protection quando a Localidade do sistema de operativo envio está em inglês.

- Subetiquetas sejam aplicadas corretamente ao PowerShell e o scanner quando a etiqueta principal está configurada para permissões definidas pelo utilizador.

- O cliente do Azure Information Protection exiba corretamente as etiquetas que foram aplicadas pelo [clientes que suportam a etiquetagem unificada](../configure-policy-migrate-labels.md#clients-and-services-that-support-unified-labeling).

- Documentos aberto corretamente no Office sem uma mensagem de recuperação após a proteção foi removida pelo Explorador de ficheiros e com o botão direito, PowerShell e a deteção de impressão.

- Quando utiliza a definição para definir de cliente avançado uma [etiqueta predefinida para o Outlook](client-admin-guide-customizations.md#set-a-different-default-label-for-outlook), pode aplicar uma etiqueta de principal com subetiquetas quando todos os esses subetiquetas estão desativadas para o utilizador.

- Quando utiliza a [definição de política](../configure-policy-settings.md) **para mensagens de e-mail com anexos, aplique uma etiqueta que corresponda à classificação mais elevada desses anexos** e a etiqueta com a classificação mais alta é configurado para permissões definidas pelo utilizador, o resultado anteriormente era que a etiqueta foi aplicada à mensagem de e-mail, mas não era a proteção. Agora:
    - Quando a etiqueta definida pelo utilizador permissões incluem Outlook (não reencaminhar): Aplica essa etiqueta e a proteção não reencaminhar para o e-mail.
    - Quando a etiqueta definida pelo utilizador permissões são apenas para o Word, Excel, PowerPoint e o Explorador de ficheiros: Não se aplicam a etiqueta e não são aplicáveis a toda a proteção para o e-mail.

**Alterações adicionais:**

- Já não são suportados os seguintes tipos de informações confidenciais para as etiquetas que configurou para a classificação recomendada ou automática:
    - Número de telefone da UE
    - Coordenadas do GPS da UE

- Porque o scanner de proteções de informações do Azure está configurado no portal do Azure, os seguintes cmdlets foram preteridos e não pode ser utilizados para configurar repositórios de dados ou a lista de tipos de ficheiros:
    - Add-AIPScannerRepository
    - Add-AIPScannerScannedFileTypes
    - Get-AIPScannerRepository
    - Remove-AIPScannerRepository
    - Remove-AIPScannerScannedFileTypes
    - Set-AIPScannerRepository
    - Set-AIPScannerScannedFileTypes

- Um novo cmdlet do PowerShell, [Import-AIPScannerConfiguration](/powershell/module/azureinformationprotection/Import-AIPScannerConfiguration), para cenários onde o scanner do Azure Information Protection não é possível transferir a configuração do portal do Azure.

- O scanner do Azure Information Protection já não exclui os arquivos. zip por predefinição. Para inspecionar e etiquetar os ficheiros. zip, consulte a [inspecionar os ficheiros. zip](client-admin-guide-file-types.md#to-inspect-zip-files) secção do Guia do administrador.

- O [definição de política](../configure-policy-settings.md) **os utilizadores têm de fornecer justificação para definir uma etiqueta de classificação inferior, remover uma etiqueta ou remover a proteção** já não se aplica ao scanner. O scanner executa estas ações quando é configurada a definição **Relabel arquivos** ao **no** no perfil de scanner.

## <a name="version-141510"></a>Versão 1.41.51.0

**Lançado**: 11/27/2018

Esta versão inclui a versão 1.0.3592.627 do cliente RMS MSIPC.

**Novas funcionalidades:**

- Agora, o cliente do Azure Information Protection, por predefinição, protege os ficheiros PDF, utilizando a norma ISO para a encriptação de PDF. Anteriormente, era necessário ativar esse suporte com um definição de cliente avançado.
    
    Se pretender que o cliente para reverter para proteger ficheiros PDF com uma extensão de nome de ficheiro. ppdf, utilizar o mesmo [definição de cliente avançado](client-admin-guide-customizations.md#dont-protect-pdf-files-by-using-the-iso-standard-for-pdf-encryption), mas especifique **falso**.

- Suporte para [central reporting](../reports-aip.md) para a funcionalidade de análise do Azure Information Protection anunciada na Microsoft Ignite.

- O Excel agora também suporta [marcação visual](../configure-policy-markings.md)s com cores diferentes.

- Para implementações de S/MIME existentes, um novo a definição de cliente para configurar uma etiqueta para aplicar automaticamente a proteção de S/MIME no Outlook avançada. [Mais informações](client-admin-guide-customizations.md#configure-a-label-to-apply-smime-protection-in-outlook)

- Uma nova definição avançada de cliente, como uma alternativa ao editar o registo para impedir pedidos de início de sessão para o serviço Azure Information Protection para [desligado computadores](client-admin-guide-customizations.md#support-for-disconnected-computers).

- Um nova definição de cliente avançado [suportam a ordem das subetiquetas](client-admin-guide-customizations.md#enable-order-support-for-sublabels-on-attachments) quando utiliza a seguinte definição de política:
    - **Para mensagens de e-mail com anexos, aplique uma etiqueta que corresponda à classificação mais elevada desses anexos**

**Correções**:

- O cliente do Azure Information Protection já não exclui extensões de nome de ficheiro. zip, rar e msg para o Explorador de ficheiros (contexto) e comandos do PowerShell. No entanto, estas extensões de nome de ficheiro permanecem excluídos por predefinição para a deteção de impressão. 

- O cliente do Azure Information Protection pode desproteger vários ficheiros (seleção múltipla e uma pasta que contém os ficheiros protegidos) quando utiliza o Explorador de ficheiros, clique com botão direito.

- Para o Excel:
    
    - Marcas visuais são aplicadas agora se guardar a folha de cálculo durante a edição de uma célula.
    
    - Excel 2010: Quando uma folha de cálculo é protegida com o Coautor [nível de permissão](../configure-usage-rights.md#rights-included-in-permissions-levels), o **eliminar etiqueta** botão agora está disponível quando o ficheiro com o botão direito e escolher **classificar e proteger**.

- As definições de cliente avançado poderão [remover os cabeçalhos e rodapés de outras soluções de etiquetas](client-admin-guide-customizations.md#remove-headers-and-footers-from-other-labeling-solutions) agora oferece suporte a esquemas personalizados.

**Alterações adicionais:**

- Quando agenda o scanner é definida como **sempre**, agora existe um atraso de 30 segundos entre verificações.

- O scanner já não altera o proprietário do Rights Management para os ficheiros que ele etiquetas quando o ficheiro já está protegido.

## <a name="version-137190"></a>Versão 1.37.19.0

**Lançado**: 09/17/2018

Esta versão inclui a versão 1.0.3592.627 do cliente RMS MSIPC.

**Novas funcionalidades**: 

- Suporte para a norma ISO para a encriptação de PDF, ao configurar uma nova [configuração de cliente avançado](client-admin-guide-customizations.md#dont-protect-pdf-files-by-using-the-iso-standard-for-pdf-encryption). Quando esta opção está definida como **True**, documentos PDF que protege reter a respetiva extensão de nome de ficheiro. pdf (em vez de alterar para. ppdf) e podem ser abertos por leitores PDF que suportam esta norma ISO. Atualmente, deve instruir os utilizadores para abrir estas PDFs protegidos manualmente ao utilizar o Visualizador do Azure Information Protection. Para ajudar os usuários a fazer isso, quando abrir um destes PDFs protegidos, verão uma página com ícones para selecionar para seu sistema operativo.

- Suporte para novos tipos de informações confidenciais para o ajudar a classificar documentos que contenham informações pessoais. [Mais informações](../configure-policy-classification.md#sensitive-information-types-that-require-a-minimum-version-of-the-client) 

- As etiquetas que aplicam-se agora a proteção apresentadas nas aplicações do Office 365, do Office 365 empresas ou do Microsoft 365 empresas quando o utilizador tem atribuída uma licença do Azure Rights Management (também conhecido como Azure Information Protection para o Office 365).

- Suporte de etiquetagem **Strict documento de XML aberto** formato em arquivos do Word, Excel e PowerPoint. Para obter mais informações sobre os formatos XML abertos, consulte a postagem no blog Office [novas opções de formato de ficheiro do novo Office](https://www.microsoft.com/en-us/microsoft-365/blog/2012/08/13/new-file-format-options-in-the-new-office/). 

- Suporte para ficheiros que foram protegidos pelo Secure Islands quando os ficheiros que não documentos PDF e do Office. Por exemplo, texto e imagem os ficheiros protegidos. Em alternativa, a extensão de nome de ficheiro de ficheiros que tenham um. pfile. Este suporte permite novos cenários, como o scanner do Azure Information Protection poder inspecionar esses arquivos de informações confidenciais e relabeling-las automaticamente para o Azure Information Protection. [Mais informações](client-admin-guide-customizations.md#support-for-files-protected-by-secure-islands)

- Novas definições de cliente avançadas para remover os cabeçalhos e rodapés que foram aplicadas a documentos por outras soluções de etiquetas. [Mais informações](client-admin-guide-customizations.md#remove-headers-and-footers-from-other-labeling-solutions)

- Para o scanner do Azure Information Protection:

    - Novo cmdlet, [AIPScanner atualização](/powershell/module/azureinformationprotection/Update-AIPScanner): Necessário para executar uma vez após a atualização da versão anterior de GA (1.29.5.0) ou anterior.
    
    - Novo cmdlet, [Get-AIPScannerStatus](/powershell/module/azureinformationprotection/Get-AIPScannerStatus): Obtém o estado atual do serviço para a deteção de impressão.  
    
    - Novo cmdlet, [Start-AIPScan](/powershell/module/azureinformationprotection/Start-AIPScan): Instrui o scanner para iniciar um ciclo de análise de quando a agenda está definida para manual de tempo.
    
    - Documentos PDF estão agora protegidos por predefinição, quando utiliza a norma ISO para a encriptação de PDF.
    
    - SharePoint Server 2010 é suportada para os clientes que tenham [suporte para esta versão do SharePoint estendido](https://support.microsoft.com/lifecycle/search?alpha=SharePoint%20Server%202010).
    
- Suporte para a nova **do Azure Information Protection – nós (pré-visualização)** painel no portal do Azure, o que lhe permite gerir scanners de um local central. Informações da sua implementados scanners que ter conectividade para o Azure são atualizadas a cada cinco minutos. A partir deste painel, pode iniciar o scanner para uma única análise, reanalisar todos os ficheiros, verificar o estado de um scanner e ver a taxa de digitalização.

**Correções**

- Para o scanner do Azure Information Protection:
    
    - Para documentos protegidos em bibliotecas do SharePoint, que o *DefaultOwner* parâmetro não for utilizado para o repositório de dados, o valor de Editor do SharePoint agora é utilizado como o valor predefinido em vez do valor de autor.
    
    - Os relatórios de scanner incluem "Última modificação por" para documentos do Office.
    
    - Agora pode proteger todos os tipos de ficheiro ao utilizar o `*` universais ao editar o registro, conforme descrito no [editar o registo para o scanner](../deploy-aip-scanner.md#editing-the-registry-for-the-scanner) secção.

- Ver mensagens de e-mail ao utilizar os ícones de seta próximo Item e o Item anterior na barra de ferramentas de acesso rápido mostra a etiqueta correta de cada e-mail.

- Quando classifica e protege utilizando o Explorador de ficheiros, o PowerShell ou o scanner, os metadados de documento do Office não é removido ou criptografados.

- Permissões personalizadas suportam endereços de e-mail do destinatário que contêm um apóstrofe.

- O ambiente de computador será inicializado com sucesso (arranque) quando esta ação é iniciada, abrindo um documento protegido que é armazenado no SharePoint Online.

- Ao utilizar o cliente para o botão direito do rato no Explorador de ficheiros, o PowerShell ou o scanner, etiquetagem está bloqueada para ficheiros em localizações de WebDav porque se trata de um cenário não suportado.

- O ícone Eliminar etiqueta não apresenta nas aplicações de cliente (Word, Excel, PowerPoint e Outlook) ao configurar o [definição de política](../configure-policy-settings.md) dos **todos os documentos e e-mails devem ter uma etiqueta**.

**Alterações adicionais**:

- Para [Set-AIPScannerConfiguration](/powershell/module/azureinformationprotection/Set-AIPScannerConfiguration):
    
    - Os valores para o *agenda* parâmetro já não são **OneTime**, **contínua**, e **Never**, mas agora **Manual** e **sempre**.
        
    - O *tipo* parâmetro é removido, pelo que também é removido da saída quando executa [Get-AIPScannerConfiguration](/powershell/module/azureinformationprotection/Get-AIPScannerConfiguration). Por predefinição, os ficheiros apenas novos ou modificados são inspecionados após a primeira análise ciclo. Se definiu anteriormente a *tipo* parâmetro para **completo** para executar a reanálise todos os ficheiros, agora, execute [AIPScan início](/powershell/module/azureinformationprotection/Start-AIPScan) com o *repor* parâmetro. A deteção de impressão também tem de ser configurada para um agendamento manual, o que requer o *agenda* parâmetro para ser definido como **Manual** com [conjunto AIPScannerConfiguration](/powershell/module/azureinformationprotection/Set-AIPScannerConfiguration).
    
- A lista de exclusão predefinida para o cliente e o scanner agora inclui arquivos. zip, rar e msg. O scanner também exclui os arquivos. rtf. [Mais informações](client-admin-guide-file-types.md#file-types-that-are-excluded-from-classification-and-protection)

- A versão de política é alterada para 1.4. Identificar o número de versão é necessária para [configurar computadores desligados](client-admin-guide-customizations.md#support-for-disconnected-computers).

- O **enviar comentários** ligação na **ajuda e Feedback** caixa de diálogo é removida. Temporariamente foi substituída pela **comunicar um problema** que, por predefinição, enviado um e-mail à Microsoft. A partir de Dezembro de 2018 ou superior, o **comunicar um problema** opção não é apresentada por predefinição, mas podem ser adicionada com um [definição de cliente avançado](client-admin-guide-customizations.md#add-report-an-issue-for-users) onde pode especificar uma cadeia de caracteres HTTP para a ligação. Por exemplo, uma página da web personalizada para os utilizadores comuniquem problemas, ou um endereço de e-mail que vai para o suporte técnico. 


## <a name="next-steps"></a>Passos Seguintes

Para obter mais informações sobre como instalar e utilizar o cliente: 

- Para os utilizadores: [Transferir e instalar o cliente](install-client-app.md)

- Para administradores: [Guia do administrador de clientes do Azure Information Protection](client-admin-guide.md)
