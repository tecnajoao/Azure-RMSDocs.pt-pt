---
title: Descrição geral técnica da aplicação de partilha RMS – AIP
description: Informações técnicas para administradores em redes empresariais cuja responsabilidade é implementar a aplicação de partilha RMS para Windows.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 06/02/2017
ms.topic: article
ms.service: information-protection
ms.assetid: f7b13fa4-4f8e-489a-ba46-713d7a79f901
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 4a04af78d1327fa9810325d799336c98f12b5163
ms.sourcegitcommit: 7ba9850e5bb07b14741bb90ebbe98f1ebe057b10
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/23/2018
ms.locfileid: "42804494"
---
# <a name="technical-overview-and-protection-details-for-the-microsoft-rights-management-sharing-application"></a>Descrição geral técnica e detalhes de proteção da aplicação de partilha Microsoft Rights Management

>*Aplica-se a: serviços de gestão de direitos do Active Directory [do Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 7 com SP1, Windows 8, Windows 8.1*


A aplicação de partilha Microsoft Rights Management é uma aplicação transferível e opcional para o Microsoft Windows e outras plataformas que fornece o seguinte:

-   Proteção de um único ficheiro ou proteção em volume de vários ficheiros, bem como de todos os ficheiros numa pasta selecionada.

-   Suporte integral para proteção de qualquer tipo de ficheiro e um visualizador incorporado para tipos de ficheiro de texto e imagem utilizados frequentemente.

-   Proteção genérica para ficheiros que não suportam a proteção RMS.

-   Interoperabilidade completa com ficheiros protegidos através da Gestão de Direitos de Informação (IRM) do Office.

-   Interoperabilidade completa com ficheiros PDF protegidos através da Infraestrutura de Classificação de Ficheiros (FCI) e ferramentas de criação de PDFs suportadas.

A aplicação de partilha Microsoft Rights Management utiliza o [runtime do Cliente de AD RMS 2.1](http://www.microsoft.com/download/details.aspx?id=38396). Ao utilizar a funcionalidade do AD RMS 2.1, a aplicação de partilha Microsoft Rights Management proporciona aos utilizadores finais uma experiência de proteção e consumo simples.

Com a versão de outubro de 2013 do RMS, pode proteger documentos nativamente com o Office 2010 e enviá-los para pessoas noutra empresa, que, depois, podem aceder aos mesmos através do serviço Azure Rights Management do Azure Information Protection. Além disso, com esta versão, se utilizar o AD RMS no Modo Criptográfico 2, pode utilizar o RMS para indivíduos e consumir conteúdos de pessoas noutra empresa que utilize o serviço Azure Rights Management. Para mais informações sobre o Modo Criptográfico 2, consulte [Modos Criptográficos do AD RMS](http://technet.microsoft.com/library/hh867439%28v=ws.10%29.aspx).

Para obter mais informações sobre a implementação, consulte [Implementação automática da aplicação de partilha Microsoft Rights Management](sharing-app-admin-guide.md#automatic-deployment-for-the-microsoft-rights-management-sharing-application)

## <a name="levels-of-protection--native-and-generic"></a>Níveis de proteção – nativa e genérica
A aplicação de partilha Microsoft Rights Management suporta proteção a dois níveis diferentes, conforme descrito na tabela seguinte.

|Tipo de proteção|Nativa|Genérico|
|----------------------|----------|-----------|
|Descrição|Para texto, imagem, ficheiros do Microsoft Office (Word, Excel, PowerPoint), ficheiros .pdf e outros tipos de ficheiro de aplicação que suportam o serviço Rights Management, a proteção nativa fornece um elevado nível de proteção que inclui encriptação e imposição dos direitos (permissões).|Para todas as outras aplicações e tipos de ficheiro, a proteção genérica fornece um nível de segurança que inclui encapsulamento de ficheiro com o tipo de ficheiro .pfile e autenticação para verificar se um utilizador tem autorização para abrir o ficheiro.|
|Protection|Os ficheiros são totalmente encriptados e a proteção é imposta das seguintes formas:<br /><br />- Antes da composição do conteúdo protegido, os utilizadores que recebem o ficheiro por e-mail ou aos quais é dado acesso ao mesmo através de permissões de ficheiro ou de partilha têm de se autenticar com êxito.<br /><br />- Além disso, a política e os direitos de utilização definidos pelo proprietário do conteúdo durante a proteção dos ficheiros são impostos na totalidade quando o conteúdo é composto no Visualizador de IP (para os ficheiros de texto e imagem protegidos) ou na aplicação associada (para todos os outros tipos de ficheiro suportados).|A proteção de ficheiros é imposta das seguintes formas:<br /><br />- Antes da composição do conteúdo protegido, os utilizadores com autorização para abrir o ficheiro e aos quais é dado acesso ao mesmo têm de se autenticar com êxito. Se a autorização falhar, o ficheiro não abre.<br /><br />- A política e os direitos de utilização definidos pelo proprietário do conteúdo são apresentados para informar os utilizadores autorizados acerca da política de utilização prevista.<br /><br />- Existe um registo de auditoria dos utilizadores autorizados que abrem e acedem aos ficheiros. No entanto, não são impostos direitos de utilização por aplicações sem suporte.|
|Predefinição para tipos de ficheiro|Este é o nível de proteção predefinido para os seguintes tipos de ficheiro:<br /><br />- Ficheiros de texto e imagem<br /><br />- Ficheiros do Microsoft Office (Word, Excel, PowerPoint)<br /><br />- Formato Portable Document Dormat (.pdf)<br /><br />Para mais informações, consulte a secção seguinte [Tipos de ficheiro suportados e extensões de nome de ficheiro](#supported-file-types-and-file-name-extensions).|Esta é a proteção predefinida para todos os outros tipos de ficheiro (tal como .vsdx, .rtf e etc.) que não são suportados pela proteção completa.|
Pode alterar o nível de proteção predefinido aplicado pela aplicação de partilha RMS. Pode alterar o nível predefinido de nativa para genérica, de genérica para nativa e até mesmo impedir que a aplicação de partilha RMS aplique proteção. Para obter mais informações, consulte a secção [Alterar o nível de proteção predefinido dos ficheiros](#changing-the-default-protection-level-of-files) neste artigo.

## <a name="supported-file-types-and-file-name-extensions"></a>Tipos de ficheiro suportados e extensões de nome de ficheiro
A tabela seguinte apresenta uma lista dos tipos de ficheiro que são suportados nativamente pela aplicação de partilha Microsoft Rights Management. Para estes tipos de ficheiro, a extensão de nome de ficheiro original é alterada quando a proteção nativa é aplicada e esses ficheiros passam a ser só de leitura.

Além disso, quando a aplicação de partilha RMS protege nativamente um ficheiro do Word, Excel ou PowerPoint que os utilizadores protegem através da partilha, esta ação cria automaticamente um segundo ficheiro que é uma cópia do original com o mesmo nome de ficheiro, mas com uma extensão de nome de ficheiro **.ppdf**¹. Esta versão do ficheiro garante que os destinatários que instalem a aplicação de partilha RMS podem abrir sempre o ficheiro ao qual foi aplicada proteção nativa.

Para os ficheiros que são protegidos genericamente, a extensão de nome de ficheiro original é sempre alterada para .pfile.

> [!WARNING]
> Se tiver firewalls, proxies Web ou software de segurança que inspecionem e tomem medidas de acordo com as extensões de nome de ficheiro, poderá ter de os reconfigurar para suportar estas novas extensões de nome de ficheiro.

|Extensão de nome de ficheiro original|Extensão de nome de ficheiro protegido pelo RMS|
|--------------------------------|-------------------------------------|
|.txt|.ptxt|
|.xml|.pxml|
|.jpg|.pjpg|
|.jpeg|.pjeg|
|.pdf|.ppdf|
|.png|.ppng|
|.tif|.ptif|
|.tiff|.ptiff|
|.bmp|.pbmp|
|.gif|.pgif|
|.jpe|.pjpe|
|.jfif|.pjfif|
|.jt|.pjt|
¹ Composição de PDF com tecnologia da Foxit. Copyright © 2003–2014 por Foxit Corporation.

A tabela seguinte apresenta uma lista dos tipos de ficheiro que a aplicação de partilha Microsoft Rights Management suporta nativamente no Microsoft Office 2016, Office 2013 e Office 2010. Nestes ficheiros, a extensão de nome de ficheiro permanece igual depois de o ficheiro ser protegido pelo serviço Rights Management.

|Tipos de ficheiro suportados pelo Office|Tipos de ficheiro suportados pelo Office|
|----------------------------------|----------------------------------|
|.doc<br /><br />.docm<br /><br />.docx<br /><br />.dot<br /><br />.dotm<br /><br />.dotx<br /><br />.potm<br /><br />.potx<br /><br />.pps<br /><br />.ppsm<br /><br />.ppsx<br /><br />.ppt<br /><br />.pptm|.pptx<br /><br />.thmx<br /><br />.xla<br /><br />.xlam<br /><br />.xls<br /><br />.xlsb<br /><br />.xlt<br /><br />.xlsm<br /><br />.xlsx<br /><br />.xltm<br /><br />.xltx<br /><br />.xps|

### <a name="changing-the-default-protection-level-of-files"></a>Alterar o nível de proteção predefinido dos ficheiros
Pode alterar a forma como a aplicação de partilha RMS protege os ficheiros ao editar o registo. Por exemplo, pode forçar os ficheiros que suportam a proteção nativa a serem protegidos genericamente pela aplicação de partilha RMS.

Seguem-se alguns motivos pelos quais poderá pretender fazê-lo:

-   Para garantir que todos os utilizadores podem abrir o ficheiro nos seus dispositivos móveis.

-   Para garantir que todos os utilizadores podem abrir o ficheiro se não tiverem uma aplicação que suporte a proteção nativa.

-   Para acomodar os sistemas de segurança que tomam medidas em relação aos ficheiros com base na sua extensão de nome de ficheiro e que podem ser reconfigurados para acomodar a extensão de nome de ficheiro .pfile, mas não podem ser reconfigurados para acomodar várias extensões de nome de ficheiro para a proteção nativa.

Da mesma forma, pode forçar a aplicação de partilha RMS a aplicar proteção nativa aos ficheiros aos quais seria aplicada proteção genérica por predefinição. Este procedimento poderá ser apropriado se tiver uma aplicação que suporta as APIs de RMS, por exemplo, uma aplicação de linha de negócio criada por programadores internos ou uma aplicação comprada a um fabricante independente de software (ISV).

Pode também forçar a aplicação de partilha RMS a bloquear a proteção dos ficheiros (ou seja, não aplicar proteção nativa nem proteção genérica). Por exemplo, tal poderá ser necessário se tiver uma aplicação ou um serviço automatizado que tem de conseguir abrir um ficheiro específico para processar os respetivos conteúdos. Quando bloqueia a proteção de um tipo de ficheiro, os utilizadores não podem utilizar a aplicação de partilha RMS para proteger um ficheiro desse tipo. Quando o tentam fazer, é apresentada uma mensagem que indica que o administrador impediu a proteção e têm de cancelar a ação para proteger o ficheiro.

Para configurar a aplicação de partilha RMS para aplicar uma proteção genérica a todos os ficheiros que, por predefinição, teriam uma proteção nativa aplicada, efetue as seguintes edições de registo. Tenha em atenção que, se as chaves RmsSharingApp ou FileProtection não existirem, tem de as criar manualmente.

1.  **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\RmsSharingApp\FileProtection**: crie uma nova chave com o nome *.

    Esta definição indica ficheiros com qualquer extensão de nome de ficheiro.

2.  Na chave recém-adicionada HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\RmsSharingApp\FileProtection\\\*, crie um novo valor de cadeia (REG_SZ) com o nome **Encriptação** com o valor de dados **Pfile**.

    Esta definição faz com que a aplicação de partilha RMS aplique proteção genérica.

Estas duas definições fazem com que a aplicação de partilha RMS aplique proteção genérica a todos os ficheiros que tenham uma extensão de nome de ficheiro. Se for este o seu objetivo, não é necessário efetuar mais configurações. No entanto, pode definir exceções para tipos de ficheiro específicos, de modo a que estes continuem a ser protegidos nativamente. Para tal, tem de efetuar três edições de registo adicionais para cada tipo de ficheiro:

1.  **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\RmsSharingApp\FileProtection**: adicione uma nova chave com o nome da extensão de nome de ficheiro (sem o ponto final precedente).

    Por exemplo, para os ficheiros que tenham uma extensão de nome de ficheiro .docx, crie uma chave denominada **DOCX**.

2.  Na chave do tipo de ficheiro recém-adicionada (por exemplo, **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\RmsSharingApp\FileProtection\DOCX**), crie um novo Valor DWORD com o nome **AllowPFILEEncryption** com um valor de **0**.

3.  Na chave do tipo de ficheiro recém-adicionada (por exemplo, **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\RmsSharingApp\FileProtection\DOCX**), crie um novo valor de cadeia com o nome **Encriptação** com o valor **Nativo**.

Como resultado destas definições, todos os ficheiros são protegidos genericamente, exceto os ficheiros que tenham uma extensão de nome de ficheiro .docx, que são protegidos nativamente pela aplicação de partilha RMS.

Repita estes três passos para os outros tipos de ficheiro que pretenda definir como exceções, uma vez que suportam a proteção nativa e não pretende que sejam protegidos genericamente pela aplicação de partilha RMS.

Pode efetuar edições de registo semelhantes para outros cenários ao alterar o valor da cadeia **Encriptação** que suporta os seguintes valores:

-   **Pfile**: proteção genérica

-   **Nativo**: proteção nativa

-   **Desativado**: bloquear proteção

## <a name="see-also"></a>Consulte Também
[Guia do utilizador da aplicação de partilha Rights Management](sharing-app-user-guide.md)

