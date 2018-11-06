---
title: Leitores de PDF protegidos para o Microsoft Information Protection
description: ''
keywords: ''
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 10/13/2018
ms.topic: article
ms.prod: azure
ms.service: information-protection
ms.assetid: aab59e02-930b-4a17-8442-2d5d081fe1a6
ms.reviewer: kartikka
ms.suite: ems
ms.openlocfilehash: ab3d141394a9a042a8a3e15e35d1daffab20ad98
ms.sourcegitcommit: 1e6394044d646278ae582c7713cac8ffb9bf4c1e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49170351"
---
# <a name="supported-pdf-readers-for-microsoft-information-protection"></a>Leitores de PDF suportados para o Microsoft Information Protection

Utilize as seguintes informações para saber mais sobre documentos PDF que estão identificados para classificação e proteção e como visualizar esses documentos.

Uma colaboração entre a Microsoft e a Adobe traz até uma experiência mais consistente e simplificada para documentos PDF que foram classificados e, opcionalmente, protegidos. Esta colaboração fornece suporte para integração nativa do Adobe Acrobat com as soluções do Microsoft Information Protection, tal como [do Azure Information Protection](../what-is-information-protection.md). 

Esta integração nativa tem as seguintes vantagens:

- Pode exibir documentos PDF que foram protegidos porque contêm informações confidenciais.

- Pode ver o valor de classificação para a etiqueta da sua organização que foi aplicada ao documento.

- Suporte para a norma ISO para a encriptação de PDF.
    
    Este formato de ficheiro PDF protegido tem de ser [ativada por um administrador](client-admin-guide-customizations.md#protect-pdf-files-by-using-the-iso-standard-for-pdf-encryption). Quando esta configuração é feita, a extensão de nome de ficheiro permanece como. pdf e não é alterado para. ppdf.

Para obter mais informações, consulte a seguinte mensagem de blogue: [Outubro inicial, utilize o Adobe Acrobat Reader para PDFs protegidos pelo Microsoft Information Protection](https://techcommunity.microsoft.com/t5/Azure-Information-Protection/Starting-October-use-Adobe-Acrobat-Reader-for-PDFs-protected-by/ba-p/262738)

## <a name="supported-pdf-readers"></a>Leitores PDF suportados

Os leitores PDF seguintes podem abrir ficheiros PDF protegidos que sigam o padrão para a encriptação de PDF do ISO:

|Sistema operativo|Os leitores suportados e ligação de transferência|
|----------------|-----------------------------------|
|Windows 10 e versões anteriores<br />por meio do Windows 7 Service Pack 1|Adobe Acrobat Reader (preferencial):<br />-  [Leia os termos do Adobe gerais de utilização](https://www.adobe.com/legal/terms.html) <br />- [Transferir a pré-visualização](https://ardownload2.adobe.com/pub/adobe/reader/win/AcrobatDC/misc/MIP_Preview/1900820120/Adobe_MIP_Preview_1900820120.zip) <br /><br /> Visualizador do Azure Information Protection: [transferir](https://go.microsoft.com/fwlink/?linkid=838993)<br /><br />Foxit Reader: [transferir](https://www.foxitsoftware.com/pdf-reader/)|
|Android|Azure Information Protection app: [transferir](https://go.microsoft.com/fwlink/?LinkId=325340)|
|iOS|Azure Information Protection app: [transferir](https://go.microsoft.com/fwlink/?LinkId=325338)|

### <a name="support-for-previous-formats"></a>Suporte para formatos anteriores

Os leitores PDF no suporte de tabela seguinte de documentos PDF que tenham um. ppdf nome extensionand mais antigos formatos de arquivo que tenham uma extensão de nome de ficheiro. pdf protegidos.

Atualmente, SharePoint Online e SharePoint no local utilizam um formato mais antigo para documentos PDF em bibliotecas protegidas por IRM.


|Sistema operativo|Leitores suportados|
|----------------|-----------------------------------|
|Windows 10 e versões anteriores<br />por meio do Windows 7 Service Pack 1|Visualizador do Azure Information Protection<br /><br />Gaaiho Doc<br /><br />GigaTrust Desktop PDF Client for Adobe<br /><br />Foxit Reader<br /><br />Nitro PDF Reader<br /><br />Aplicação de partilha RMS|
|Android|Azure Information Protection app<br /><br />Foxit MobilePDF com o RMS<br /><br />GigaTrust App for Android|
|iOS|Azure Information Protection app<br /><br />Foxit MobilePDF com o RMS<br /><br />TITUS Docs|