---
title: Tipos de ficheiro suportados pelo Azure Information Protection
description: Detalhes técnicos sobre tipos de ficheiro suportados, extensões de nome de ficheiro e níveis de proteção para administradores responsáveis pelo cliente do Azure Information Protection para Windows.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 07/23/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: ''
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 90dac73ce15382b4be58e5eb191e44167bdee56f
ms.sourcegitcommit: 1f5a5cb650be2b4c302ad4b7a0b109246da3eb80
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/27/2018
ms.locfileid: "39295445"
---
# <a name="admin-guide-file-types-supported-by-the-azure-information-protection-client"></a>Guia do administrador: Tipos de ficheiro suportados pelo cliente do Azure Information Protection

>*Aplica-se a: serviços de gestão de direitos do Active Directory [do Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 com SP1, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2*

O cliente do Azure Information Protection pode aplicar o seguinte aos documentos e aos e-mails:

- Apenas classificação

- Classificação e proteção

- Apenas proteção

Utilize as seguintes informações para verificar que tipos de ficheiro, o cliente do Azure Information Protection suporta, compreender os diferentes níveis de proteção e como alterar o nível de proteção predefinido e para identificar quais arquivos estão automaticamente excluídos ( ignorado) da classificação e proteção.

## <a name="file-types-supported-for-classification-only"></a>Tipos de ficheiro suportados apenas para classificação

Os seguintes tipos de ficheiro podem ser classificados, mesmo quando não estão protegidos.

- **Formato Adobe Portable Document Format**: .pdf

- **Microsoft Project**: .mpp, .mpt

- **Microsoft Publisher**: .pub

- **Microsoft XPS**: .xps .oxps

- **Imagens**:. jpg,. jpe,. JPEG, .jif, jfif, .jfi. PNG, .TIF,. tiff

- **Design Review 2013 da Autodesk**: .dwfx

- **Adobe Photoshop**: .psd

- **Digital Negative**: .dng

- **Microsoft Office**: tipos de ficheiro na seguinte tabela.
    
    Os formatos de ficheiro suportados para estes tipos de ficheiro são os 97-2003 formatos de arquivo e formatos XML abertos do Office para os seguintes programas do Office: Word, Excel e PowerPoint. 
    
    |Tipo de ficheiro do Office|Tipo de ficheiro do Office|
    |----------------------------------|----------------------------------|
    |.doc<br /><br />.docm<br /><br />.docx<br /><br />.dot<br /><br />.dotm<br /><br />.dotx<br /><br />.potm<br /><br />.potx<br /><br />.pps<br /><br />.ppsm<br /><br />.ppsx<br /><br />.ppt<br /><br />.pptm<br /><br />.pptx<br /><br />.vdw<br /><br />.vsd|.vsdm<br /><br /> .vsdx<br /><br />ser<br /><br />. vssm<br /><br />. vst<br /><br />.vstm<br /><br />.vssx<br /><br />.vstx<br /><br />.xls<br /><br />.xlsb<br /><br />.xlt<br /><br />.xlsm<br /><br />.xlsx<br /><br />.xltm<br /><br />.xltx|

Tipos de ficheiro adicionais suportam a classificação quando também estão protegidos. Para estes tipos de ficheiros, consulte a [tipos de ficheiros suportados para classificação e proteção](#supported-file-types-for-classification-and-protection) secção.

Por exemplo, no atual [política predefinida](../deploy-use/configure-policy-default.md), o **geral** etiqueta aplica-se a classificação e não se aplica a proteção. Pode aplicar a **gerais** rótulo num arquivo chamado sales.pdf mas não foi possível aplicar esta etiqueta num arquivo chamado sales.txt. 

Também na política predefinida atual, o **confidencial \ todos os funcionários** aplica-se a classificação e proteção. Pode aplicar esta etiqueta num arquivo chamado sales.pdf e um ficheiro denominado sales.txt. Também pode aplicar proteção apenas a estes ficheiros, sem classificação.

## <a name="file-types-supported-for-protection"></a>Tipos de ficheiro suportados para proteção

O cliente do Azure Information Protection suporta a proteção em dois níveis diferentes, conforme descrito na tabela seguinte.

|Tipo de proteção|Nativa|Genérico|
|----------------------|----------|-----------|
|Descrição|Para texto, imagem, ficheiros do Microsoft Office (Word, Excel, PowerPoint), ficheiros .pdf e outros tipos de ficheiro de aplicação que suportam o serviço Rights Management, a proteção nativa fornece um elevado nível de proteção que inclui encriptação e imposição dos direitos (permissões).|Para todas as outras aplicações e tipos de ficheiro, a proteção genérica fornece um nível de segurança que inclui encapsulamento de ficheiro com o tipo de ficheiro .pfile e autenticação para verificar se um utilizador tem autorização para abrir o ficheiro.|
|Protection|A proteção de ficheiros é imposta das seguintes formas:<br /><br />- Antes da composição do conteúdo protegido, os utilizadores que recebem o ficheiro por e-mail ou aos quais é dado acesso ao mesmo através de permissões de ficheiro ou de partilha têm de se autenticar com êxito.<br /><br />-Além disso, direitos de utilização e a política que foram definidos pelo proprietário do conteúdo, quando os ficheiros foram protegidos são aplicadas quando o conteúdo é composto no Visualizador do Azure Information Protection (para ficheiros de texto e imagem protegidos) ou a aplicação associada ( para todos os outros tipos de ficheiro suportados).|A proteção de ficheiros é imposta das seguintes formas:<br /><br />-Antes da composição do conteúdo protegido, a autenticação bem-sucedida deve ocorrer para as pessoas que estão autorizadas a abrir o ficheiro e dado acesso ao mesmo. Se a autorização falhar, o ficheiro não abre.<br /><br />- A política e os direitos de utilização definidos pelo proprietário do conteúdo são apresentados para informar os utilizadores autorizados acerca da política de utilização prevista.<br /><br />- Existe um registo de auditoria dos utilizadores autorizados que abrem e acedem aos ficheiros. No entanto, os direitos de utilização não são impostos.|
|Predefinição para tipos de ficheiro|Este é o nível de proteção predefinido para os seguintes tipos de ficheiro:<br /><br />- Ficheiros de texto e imagem<br /><br />- Ficheiros do Microsoft Office (Word, Excel, PowerPoint)<br /><br />- Formato Portable Document Dormat (.pdf)<br /><br />Para obter mais informações, consulte a secção seguinte, [Tipos de ficheiros suportados para a classificação e proteção](#supported-file-types-for-classification-and-protection).|Esta é a proteção predefinida para todos os outros tipos de ficheiro (tal como .vsdx, .rtf, entre outros) que não são suportados pela proteção nativa.|

Pode alterar o nível de proteção predefinido que o cliente do Azure Information Protection aplica. Pode alterar o nível predefinido de nativo para genérico, de genérico para nativo e até mesmo impedir que o cliente do Azure Information Protection aplique proteção. Para obter mais informações, consulte a secção [Alterar o nível de proteção predefinido dos ficheiros](#changing-the-default-protection-level-of-files) neste artigo.

Esta proteção de dados pode ser aplicada automaticamente quando um utilizador seleciona uma etiqueta que um administrador tenha configurado ou, em alternativa, os utilizadores podem especificar as suas próprias definições de proteção personalizadas ao utilizar [níveis de permissão](../deploy-use/configure-usage-rights.md#rights-included-in-permissions-levels). 

### <a name="file-sizes-supported-for-protection"></a>Tamanhos de ficheiro suportados para proteção

Há tamanhos de ficheiro máximos que o cliente do Azure Information Protection suporta para proteção.

- **Para ficheiros do Office:**
    
    |Aplicação do Office|Tamanho máximo do ficheiro suportado|
    |--------------------------------|-------------------------------------|
    |Word 2007 (suportado apenas pelo AD RMS)<br /><br />Word 2010<br /><br />Word 2013<br /><br />Word 2016|32 bits: 512 MB<br /><br />64 bits: 512 MB
    |Excel 2007 (suportado apenas pelo AD RMS)<br /><br />Excel 2010<br /><br />Excel 2013<br /><br />Excel 2016|32 bits: 2 GB<br /><br />64 bits: limitado apenas pela memória e espaço disponível no disco|
    |PowerPoint 2007 (suportado apenas pelo AD RMS)<br /><br />PowerPoint 2010<br /><br />PowerPoint 2013<br /><br />PowerPoint 2016|32 bits: limitado apenas pela memória e espaço disponível no disco<br /><br />64 bits: limitado apenas pela memória e espaço disponível no disco

- **Para todos os outros ficheiros**: 
    
    - Para proteger a outros tipos de arquivo e abrir estes tipos de ficheiro no Visualizador do Azure Information Protection: O tamanho máximo é limitado apenas pela memória e espaço em disco disponível.
    
    - Para desproteger ficheiros ao utilizar o [Unprotect-RMSFile](/powershell/module/azureinformationprotection/unprotect-rmsfile) cmdlet: O tamanho de ficheiro máximo suportado para arquivos. pst é 5 GB. Outros tipos de ficheiros estão limitados apenas pela memória e espaço em disco disponível.

### <a name="supported-file-types-for-classification-and-protection"></a>Tipos de ficheiros suportados para a classificação e proteção

A seguinte tabela lista um subconjunto de tipos de ficheiro que suportam a proteção nativa pelo cliente do Azure Information Protection e que também podem ser classificados. 

Estes tipos de ficheiro são identificados separadamente, uma vez que, quando são protegidos nativamente, a extensão de nome de ficheiro original é alterada e estes ficheiros passam a ser só de leitura. Tenha em atenção que, quando os ficheiros são protegidos genericamente, a extensão de nome de ficheiro original é sempre alterada para .pfile.

> [!WARNING]
> Se tiver firewalls, web proxies ou software de segurança que inspecionem e tomem medidas de acordo com as extensões de nome de ficheiro, poderá ter de reconfigurar esses dispositivos de rede e software para suportar estas novas extensões de nome de ficheiro.

|Extensão de nome de ficheiro original|Extensão de nome de ficheiro protegido|
|--------------------------------|-------------------------------------|
|.txt|.ptxt|
|.xml|.pxml|
|.jpg|.pjpg|
|.jpeg|.pjpeg|
|.pdf|.ppdf|
|.png|.ppng|
|.tif|.ptif|
|.tiff|.ptiff|
|.bmp|.pbmp|
|.gif|.pgif|
|.jpe|.pjpe|
|.jfif|.pjfif|
|.jt|.pjt|


A seguinte tabela apresenta os tipos de ficheiros restantes que suportam a proteção nativa pelo cliente do Azure Information Protection e que também podem ser classificados. Irá reconhecê-los como tipos de ficheiro das aplicações do Microsoft Office. Os formatos de ficheiro suportados para estes tipos de ficheiro são os 97-2003 formatos de arquivo e formatos XML abertos do Office para os seguintes programas do Office: Word, Excel e PowerPoint.

Nestes ficheiros, a extensão de nome de ficheiro permanece igual depois de o ficheiro ser protegido pelo serviço Rights Management.

|Tipos de ficheiro suportados pelo Office|Tipos de ficheiro suportados pelo Office|
|----------------------------------|----------------------------------|
|.doc<br /><br />.docm<br /><br />.docx<br /><br />.dot<br /><br />.dotm<br /><br />.dotx<br /><br />.potm<br /><br />.potx<br /><br />.pps<br /><br />.ppsm<br /><br />.ppsx<br /><br />.ppt<br /><br />.pptm<br /><br />.pptx<br /><br />.vsdm|.vsdx<br /><br />. vssm<br /><br />.vssx<br /><br />.vstm<br /><br />.vstx<br /><br />.xla<br /><br />.xlam<br /><br />.xls<br /><br />.xlsb<br /><br />.xlt<br /><br />.xlsm<br /><br />.xlsx<br /><br />.xltm<br /><br />.xltx<br /><br />.xps|

### <a name="changing-the-default-protection-level-of-files"></a>Alterar o nível de proteção predefinido dos ficheiros
Pode alterar a forma como o cliente do Azure Information Protection protege os ficheiros ao editar o registo. Por exemplo, pode forçar os ficheiros que suportam a proteção nativa a serem protegidos genericamente pelo cliente do Azure Information Protection.

Seguem-se alguns motivos pelos quais poderá pretender fazê-lo:

- Para garantir que todos os utilizadores podem abrir o ficheiro se não tiverem uma aplicação que suporte a proteção nativa.

- Para acomodar os sistemas de segurança que tomam medidas em relação aos ficheiros com base na sua extensão de nome de ficheiro e que podem ser reconfigurados para acomodar a extensão de nome de ficheiro .pfile, mas não podem ser reconfigurados para acomodar várias extensões de nome de ficheiro para a proteção nativa.

Da mesma forma, pode forçar o cliente do Azure Information Protection a aplicar proteção nativa aos ficheiros aos quais seria aplicada proteção genérica por predefinição. Esta ação pode ser apropriada se tiver uma aplicação que suporte as APIs do RMS. Por exemplo, uma aplicação de linha de negócios escrita por programadores internos ou uma aplicação comprada a um fabricante de software independente (ISV).

Pode também forçar o cliente do Azure Information Protection a bloquear a proteção dos ficheiros (ou seja, não aplicar proteção nativa nem proteção genérica). Por exemplo, esta ação poderá ser necessária se tiver uma automatizada de aplicativos ou serviço que deve ser capaz de abrir um ficheiro específico para processar os respetivos conteúdos. Quando bloqueia a proteção de um tipo de ficheiro, os utilizadores não podem utilizar o cliente do Azure Information Protection para proteger um ficheiro desse tipo. Quando o tentam fazer, é apresentada uma mensagem que indica que o administrador impediu a proteção e têm de cancelar a ação para proteger o ficheiro.

Para configurar o cliente do Azure Information Protection para aplicar uma proteção genérica a todos os ficheiros que, por predefinição, teriam uma proteção nativa aplicada, realize as seguintes edições de registo. Tenha em atenção que, se a chave FileProtection não existir, terá de a criar manualmente.

1. Crie uma nova chave com o nome * para o seguinte caminho de registo, que indica ficheiros com qualquer extensão de nome de ficheiro:
    
    - Para a versão de 32 bits do Windows: **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\FileProtection**
    
    - Para a versão de 64 bits do Windows: **HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\MSIPC\FileProtection**

2. Na chave recentemente adicionada (por exemplo, HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\FileProtection\\\*), crie um novo valor de cadeia (REG_SZ) com o nome **Encryption** com o valor de dados **Pfile**.

    Esta definição faz com que o cliente do Azure Information Protection aplique proteção genérica.

Estas duas definições fazem com que o cliente do Azure Information Protection aplique proteção genérica a todos os ficheiros que tenham uma extensão de nome de ficheiro. Se for este o seu objetivo, não é necessário efetuar mais configurações. No entanto, pode definir exceções para tipos de ficheiro específicos, de modo a que estes continuem a ser protegidos nativamente. Para tal, tem de efetuar três edições de registo adicionais para cada tipo de ficheiro:

1. Para **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\FileProtection** (Windows de 32 bits) ou **HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\MSIPC\FileProtection** (Windows de 64 bits): adicione uma nova chave que inclua o nome da extensão de nome de ficheiro (sem o ponto final antes).

    Por exemplo, para os ficheiros que tenham uma extensão de nome de ficheiro .docx, crie uma chave denominada **DOCX**.

2. Na chave do tipo de ficheiro recém-adicionada (por exemplo, **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\FileProtection\DOCX**), crie um novo Valor DWORD com o nome **AllowPFILEEncryption** com um valor de **0**.

3. Na chave do tipo de ficheiro recém-adicionada (por exemplo, **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\FileProtection\DOCX**), crie um novo Valor de Cadeia com o nome **Encriptação** com o valor **Nativo**.

Como resultado destas definições, todos os ficheiros são protegidos genericamente, exceto os ficheiros que tenham uma extensão de nome de ficheiro. docx. Estes ficheiros são protegidos nativamente pelo cliente do Azure Information Protection.

Repita estes três passos para os outros tipos de ficheiro que pretenda definir como exceções, uma vez que suportam a proteção nativa e não pretende que sejam protegidos genericamente pelo cliente do Azure Information Protection.

Pode efetuar edições de registo semelhantes para outros cenários ao alterar o valor da cadeia **Encriptação** que suporta os seguintes valores:

- **Pfile**: proteção genérica

- **Nativo**: proteção nativa

- **Desativado**: bloquear proteção

Para obter mais informações, consulte [configuração da API de ficheiros](../develop/file-api-configuration.md) de orientação para programadores. Nesta documentação para programadores, a proteção genérica é referida como "PFile". 

## <a name="file-types-that-are-excluded-from-classification-and-protection"></a>Tipos de ficheiro que são excluídos da classificação e proteção

Para ajudar a impedir que os utilizadores alterem os ficheiros que são críticos para operações informáticas, alguns tipos de ficheiro e pastas são automaticamente excluídos da proteção e da classificação. Se os utilizadores tentarem classificar ou proteger estes ficheiros ao utilizar o cliente do Azure Information Protection, verão uma mensagem que foram excluídos.

- **Tipos de ficheiro excluídos**: .lnk, .exe, .com, .cmd, .bat, .dll, .ini, .pst, .sca, .drm, .sys, .cpl, .inf, .drv, .dat, .tmp, .msp, .msi, .pdb, .jar

- **Pastas excluídas**: 
    - Windows
    - Programas (\Programas e \Programas (x86))
    - \ProgramData 
    - \AppData (para todos os utilizadores)

### <a name="file-types-that-are-excluded-from-classification-and-protection-by-the-azure-information-protection-scanner"></a>Tipos de ficheiro que são excluídos da classificação e proteção, o scanner do Azure Information Protection

Por predefinição, o scanner também exclui os mesmos tipos de ficheiro que o cliente do Azure Information Protection. No entanto, pode alterar este comportamento para a deteção de impressão, utilizando os cmdlets do PowerShell seguintes:

- [Conjunto AIPScannerScannedFileTypes](/powershell/module/azureinformationprotection/Set-AIPScannerScannedFileTypes)

- [AIPScannerScannedFileTypes adicionar](/powershell/module/azureinformationprotection/Add-AIPScannerScannedFileTypes)

- [Remove-AIPScannerScannedFileTypes](/powershell/module/azureinformationprotection/Remove-AIPScannerScannedFileTypes)

Por predefinição, o scanner protege apenas os tipos de ficheiro do Office. Para alterar este comportamento para a deteção de impressão, editar o registo e especificar os tipos de ficheiro adicionais que pretende proteger. Para obter instruções, consulte [configuração da API de ficheiros](../develop/file-api-configuration.md) de orientação para programadores.

### <a name="files-that-cannot-be-protected-by-default"></a>Ficheiros que não podem ser protegidos por predefinição

Qualquer ficheiro protegido por palavra-passe não pode ser protegido nativamente pelo cliente do Azure Information Protection, a menos que o ficheiro está atualmente aberto no aplicativo que se aplica a proteção. É normalmente visualizado ficheiros PDF que são protegidos por palavra-passe, mas outros aplicativos, como aplicações do Office, também oferecem essa funcionalidade.

Além disso, o cliente do Azure Information Protection para Windows pode ver os seguintes arquivos, mas não é possível nativamente proteger ou desproteger ficheiros PDF em qualquer um dos seguintes circunstâncias:

- Um ficheiro PDF que é baseada em formulários.

- Um ficheiro PDF protegido que tem uma extensão de nome de ficheiro. pdf. 
    
    O cliente do Azure Information Protection pode proteger um ficheiro PDF não protegido e pode desproteger e voltar a proteger um ficheiro PDF protegido quando tem uma extensão de nome de ficheiro. ppdf.

Como solução para proteger estes ficheiros, poderia genericamente protegê-los ao seguir as instruções no [alterar o nível de proteção predefinido dos ficheiros](#changing-the-default-protection-level-of-files) secção. No entanto, esse método altera o nível de proteção para todos os ficheiros que tenham uma extensão de nome de ficheiro. pdf, no nível do computador. Não é possível definir a proteção genérica para apenas os ficheiros que cumpram os critérios listados.

Se proteger estes ficheiros é importante, pode copiá-los temporariamente para outro computador para genericamente protegê-los e, em seguida, copiá-los volta novamente.

### <a name="limitations-for-container-files-such-as-zip-files"></a>Limitações para ficheiros de contentor, como arquivos. zip

Ficheiros de contentor são ficheiros que incluem outros arquivos, com um exemplo típico que está a ser arquivos. zip que contêm arquivos compactados. Outros exemplos incluem rar, .7z, e. msg.

Pode classificar e proteger estes ficheiros de contentor, mas a classificação e proteção não se aplica a cada arquivo dentro do contentor.

Se tiver um arquivo de contêiner que inclui ficheiros classificados e protegidos, tem primeiro de extrair os ficheiros para alterar suas configurações de classificação ou de proteção. No entanto, pode remover a proteção para todos os ficheiros nos ficheiros de contentor suportadas utilizando o [Unprotect-RMSFile](/powershell/module/azureinformationprotection/unprotect-rmsfile) cmdlet.

## <a name="next-steps"></a>Passos Seguintes
Agora que identificou os tipos de ficheiro suportados pelo cliente do Azure Information Protection, consulte os seguintes recursos para obter informações adicionais que poderá precisar para suportar este cliente:

- [Personalizações](client-admin-guide-customizations.md)

- [Ficheiros de cliente e registo de utilização](client-admin-guide-files-and-logging.md)

- [Controlo de documentos](client-admin-guide-document-tracking.md)

- [Comandos do PowerShell](client-admin-guide-powershell.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
