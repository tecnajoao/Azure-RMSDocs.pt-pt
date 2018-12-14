---
title: Leitores de PDF protegidos para o Microsoft Information Protection
description: Saiba mais sobre documentos PDF que estão identificados para classificação e proteção e, como visualizá-los.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 12/12/2018
ms.topic: article
ms.service: information-protection
ms.assetid: aab59e02-930b-4a17-8442-2d5d081fe1a6
ms.reviewer: kartikka
ms.suite: ems
ms.openlocfilehash: fc1a6c136d0b44671cbae0e6eb15202364e356d4
ms.sourcegitcommit: b2414cc00d50ccefe10f8c3719eb3f6c1e78fc65
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/11/2018
ms.locfileid: "53246127"
---
# <a name="supported-pdf-readers-for-microsoft-information-protection"></a>Leitores de PDF suportados para o Microsoft Information Protection

Utilize as seguintes informações para saber mais sobre documentos PDF que estão identificados para classificação e proteção e como visualizar esses documentos.

Uma colaboração entre a Microsoft e a Adobe traz até uma experiência mais consistente e simplificada para documentos PDF que foram classificados e, opcionalmente, protegidos. Esta colaboração fornece suporte para integração nativa do Adobe Acrobat com as soluções do Microsoft Information Protection, tal como [do Azure Information Protection](../what-is-information-protection.md). 

Esta integração nativa tem as seguintes vantagens:

- Pode exibir documentos PDF que foram protegidos porque contêm informações confidenciais.

- Pode ver o valor de classificação para a etiqueta da sua organização que foi aplicada ao documento.

- Suporte para a norma ISO para a encriptação de PDF.
    
    A menos que esta capacidade tem sido [desativada por um administrador](client-admin-guide-customizations.md#dont-protect-pdf-files-by-using-the-iso-standard-for-pdf-encryption), este formato de ficheiro PDF protegido agora está ativado por predefinição, a versão mais recente do cliente do Azure Information Protection.

Para obter mais informações, consulte a seguinte mensagem de blogue: [A partir de Outubro, a utilizar o Adobe Acrobat Reader para PDFs protegidos pelo Microsoft Information Protection](https://techcommunity.microsoft.com/t5/Azure-Information-Protection/Starting-October-use-Adobe-Acrobat-Reader-for-PDFs-protected-by/ba-p/262738)

## <a name="supported-pdf-readers"></a>Leitores PDF suportados

Os leitores PDF seguintes podem abrir ficheiros PDF protegidos que sigam o padrão para a encriptação de PDF do ISO:

|Sistema operativo|Os leitores suportados e ligação de transferência|
|----------------|-----------------------------------|
|Windows 10 e versões anteriores<br />por meio do Windows 7 Service Pack 1|Adobe Acrobat Reader (preferencial):<br />-1. Leia o [Adobe geral termos de utilização](https://www.adobe.com/legal/terms.html) <br />-2. Instalar o Adobe Reader do [site da Adobe](https://www.adobe.com/)<br />-3. Instalar o [Plug-in do Adobe](https://go.microsoft.com/fwlink/?linkid=2050049)<br />-4. Se lhe for solicitado, peça ao seu administrador para [autorizar o plug-in](https://techcommunity.microsoft.com/t5/Azure-Information-Protection/General-Availability-of-Adobe-Acrobat-Reader-integration-with/ba-p/298396) <br /><br /> Visualizador do Azure Information Protection: [Transferência](https://go.microsoft.com/fwlink/?linkid=838993)<br /><br />Foxit Reader: [Transferência](https://www.foxitsoftware.com/pdf-reader/)|
|Android|Azure Information Protection app: [Transferência](https://go.microsoft.com/fwlink/?LinkId=325340)|
|iOS|Azure Information Protection app: [Transferência](https://go.microsoft.com/fwlink/?LinkId=325338)|

### <a name="support-for-previous-formats"></a>Suporte para formatos anteriores

Os leitores PDF no suporte de tabela seguinte protegidas documentos PDF que tenham uma extensão de nome de ficheiro. ppdf e formatos mais antigos que tenham uma extensão de nome de ficheiro. pdf.

Atualmente, SharePoint Online e SharePoint no local utilizam um formato mais antigo para documentos PDF em bibliotecas protegidas por IRM.


|Sistema operativo|Leitores suportados|
|----------------|-----------------------------------|
|Windows 10 e versões anteriores<br />por meio do Windows 7 Service Pack 1|Visualizador do Azure Information Protection<br /><br />Gaaiho Doc<br /><br />Cliente PDF do ambiente de trabalho GigaTrust para Adobe<br /><br />Foxit Reader<br /><br />Leitor de PDF do nitro<br /><br />Aplicação de partilha RMS|
|Android|Azure Information Protection app<br /><br />Foxit MobilePDF com o RMS<br /><br />GigaTrust App for Android|
|iOS|Azure Information Protection app<br /><br />Foxit MobilePDF com o RMS<br /><br />TITUS Docs|
