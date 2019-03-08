---
title: Configuração da API de Ficheiros | Azure RMS
description: O comportamento da API de Ficheiros pode ser configurado através de definições no registo.
keywords: ''
author: msmbaldwin
ms.author: mbaldwin
manager: barbkess
ms.date: 10/11/2017
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 930878C2-D2B4-45F1-885F-64927CEBAC1D
audience: developer
ms.reviewer: kartikk
ms.suite: ems
ms.openlocfilehash: d1181dfe1c495a334aaebd567df5db7e14649e25
ms.sourcegitcommit: 471b3683367d93f0673c1cf276a15f83572aa80e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/05/2019
ms.locfileid: "57331006"
---
# <a name="file-api-configuration"></a>Configuração da API de Ficheiros


O comportamento da API de Ficheiros pode ser configurado através de definições no registo.

A API de Ficheiros fornece dois tipos de proteção: a proteção nativa e a proteção PFile.

-   **Proteção nativa** – o ficheiro é protegido para um formato do AD RMS baseado no respetivo tipo de MIME (extensão de nome de ficheiro).
-   **Proteção PFile** – o ficheiro é protegido para o formato de Ficheiro Protegido (PFile) do AD RMS.

Para obter mais informações sobre formatos de ficheiro suportados, consulte **detalhes de suporte do arquivo de API de ficheiro** neste artigo.

## <a name="keykey-value-types-and-descriptions"></a>Tipos e descrições de Chaves/Valores de Chave

As secções seguintes descrevem as chaves e os valores de chave que controlam a encriptação.

### `HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\FileProtection`

**Tipo de**: Chave

**Descrição**: Contém configuração geral para a API de ficheiros.

### `HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\FileProtection\<EXT>`

**Tipo de**: Chave

**Descrição**: Especifica as informações de configuração de uma extensão de ficheiro específicos; Por exemplo, TXT, JPG e assim por diante.

- O caráter universal, ' *', é permitido. No entanto, uma definição para uma extensão específica tem prioridade sobre a definição de caráter universal. O caráter universal não afeta as definições de ficheiros do Microsoft Office. Estas devem ser explicitamente desativadas por tipo de ficheiro.
- Para especificar os ficheiros que não tenham uma extensão, utilize '.'
- Não especifique o '.' quando especificar a chave para uma extensão de ficheiro específicos; de carateres Por exemplo, utilizar `HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\FileProtection\TXT` para especificar as definições de ficheiros. txt. (Não utilize `HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\FileProtection\.TXT`).

Para especificar o comportamento de proteção, defina o **Encryption** valor na chave. Se o valor de **Encriptação** não for definido, é aplicado o comportamento predefinido para o tipo de ficheiro.


### `HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\FileProtection\<EXT>\Encryption*`

**Tipo de**: REG_SZ

**Descrição**: Contém um de três valores:

- **Off**: Encriptação está desativada.

> [!Note]
> Esta definição não tem efeito na desencriptação. Qualquer ficheiro encriptado, seja ele encriptado com a proteção nativa ou Pfile, pode ser desencriptado, desde que o utilizador tenha o direito **EXTRAIR**.

- **Nativo**:  Encriptação nativa é utilizada. Para ficheiros do Office, o ficheiro encriptado terá a mesma extensão que o ficheiro original. Por exemplo, um ficheiro com a extensão de ficheiro .docx será encriptado para um ficheiro com uma extensão .docx. Para outros ficheiros que podem ter a proteção nativa aplicada, o ficheiro será encriptado para um ficheiro com uma extensão no formato p*zzz*, em que *zzz* é a extensão do ficheiro original. Por exemplo, os arquivos. txt serão encriptados para um ficheiro com extensão. ptxt. Segue uma lista de extensões de ficheiro que podem ter a proteção nativa aplicada.

- **Pfile**: Encriptação PFile é utilizada. O ficheiro encriptado terá .pfile anexado à extensão original. Por exemplo, depois da encriptação, um ficheiro .txt terá uma extensão .txt.pfile.


> [!Note]
> Esta definição não tem efeito em formatos de ficheiros do Office. Por exemplo, se o valor `HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\FileProtection\DOCX\Encryption` estiver definido para &quot;Pfile”, os ficheiros .docx ainda serão encriptados com a proteção nativa e o ficheiro encriptado continuará a ter uma extensão de ficheiro .docx.

A definição de qualquer outro valor ou nenhum valor resulta no comportamento predefinido.

## <a name="default-behavior-for-different-file-formats"></a>Comportamento predefinido para formatos de ficheiro diferentes

-   **Ficheiros do Office** A encriptação nativa está ativada.
-   **Ficheiros txt, xml, jpg, jpeg, pdf, png, tiff, bmp, gif, giff, jpe, jfif, jif** A encriptação nativa está ativada (xxx torna-se pxxx)
-   **Todos os outros ficheiros** A encriptação ativada é a de ficheiro protegido (.pfile) (xxx torna-se xxx.pfile)

Se a encriptação for tentada num tipo de ficheiro que está bloqueado, ocorre um erro [IPCERROR\_FILE\_ENCRYPT\_BLOCKED](https://msdn.microsoft.com/library/hh535248.aspx).

### <a name="file-api---file-support-details"></a>API de Ficheiros – Detalhes de Suporte de Ficheiros

É possível adicionar suporte nativo para qualquer tipo de ficheiro (extensão). Por exemplo, para qualquer extensão &lt;ext&gt; (não Ooffice), \*.p&lt;ext&gt; será utilizado se a configuração de administração para essa extensão for "NATIVO".

**Ficheiros do Office**

-   Extensões de ficheiros: doc, dot, xla, xls, xlt, pps, ppt, docm, docx, dotm, dotx, xlam, xlsb, xlsm, xlsx, xltm, xltx, xps, potm, potx, ppsx, ppsm, pptm, pptx, thmx, vsdx, vsdm, vssx, vssm, vstx e vstm. 
-   Tipo de proteção = Nativa (predefinição): exemplo.docx está encriptado para exemplo.docx
-   Tipo de proteção = Pfile: Para ficheiros do Office, tem o mesmo efeito que nativa.
-   Desativado: Desativa a encriptação.

**Ficheiros PDF**

-   Tipo de proteção = Nativa: exemplo.pdf é encriptado e é-lhe atribuído o nome exemplo.ppdf
-   Tipo de proteção = Pfile: exemplo.pdf é encriptado e é-lhe atribuído o nome exemplo.pdf.pfile.
-   Desativado: Desativa a encriptação.

**Todos os outros formatos de ficheiros**

-   Tipo de proteção = Pfile: exemplo.*zzz* é encriptado e é-lhe atribuído o nome exemplo.*zzz*.pfile; em que *zzz* é a extensão de ficheiro original.
-   Desativado: Desativa a encriptação.

### <a name="examples"></a>Exemplos

As definições seguintes ativam a encriptação PFile para ficheiros txt. Os ficheiros do Office terão a proteção nativa aplicada (por predefinição), os ficheiros txt terão a proteção PFile aplicada e todos os outros ficheiros terão a proteção bloqueada (por predefinição).

```
HKEY_LOCAL_MACHINE
   Software
      Microsoft
         MSIPC
            FileProtection
               txt
                  Encryption = Pfile
```

As definições seguintes ativam a encriptação PFile para todos os ficheiros não Office, exceto os txt. Os ficheiros do Office terão a proteção nativa aplicada (por predefinição), os ficheiros txt terão a proteção bloqueada e todos os outros ficheiros terão a proteção PFile aplicada.

```
HKEY_LOCAL_MACHINE
   Software
      Microsoft
         MSIPC
            FileProtection
               *
                  Encryption = Pfile
               txt
                  Encryption = Off
```

As definições seguintes desativam a encriptação nativa para ficheiros docx. Os ficheiros do Office, exceto os ficheiros docx, terão a proteção nativa aplicada (por predefinição) e todos os outros ficheiros terão a proteção bloqueada (por predefinição).

```
HKEY_LOCAL_MACHINE
   Software
      Microsoft
         MSIPC
            FileProtection
               docx
                  Encryption = Off
```

## <a name="related-articles"></a>Artigos relacionados

- [Notas do programador](developer-notes.md)
- [IPCERROR\_FILE\_ENCRYPT\_BLOCKED](https://msdn.microsoft.com/library/hh535248.aspx)
