---
# required metadata

title: Assinar a aplicação para produção | Azure RMS
description: Este tópico descreve o processo de assinatura da aplicação para o modo de produção.
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 09BA148C-7D1E-43C8-92EA-24BBB6EFDB19
# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Assinar a aplicação para produção

Este tópico descreve o processo de assinatura da aplicação para o modo de produção.

## Assinar a aplicação com capacidade para direitos

Estes passos partem do princípio de que já assinou a aplicação para uma hierarquia de pré-produção. Se ainda não o fez, siga o processo descrito em [Testar a aplicação com capacidade para direitos](running-your-first-application.md).

Quando receber o certificado de produção da Microsoft, terá os seguintes ficheiros:

-   YourPrivateKey.dat
-   YourPublicKey.dat
-   ProductionCertificate.xml

Coloque-os no mesmo diretório com o *GenManifest.exe* e o binário da aplicação (.exe).

-   O processo abaixo descreve os passos para criar um novo ficheiro MCF com certificado de produção:

    -   Crie um novo diretório e coloque ficheiros nesse novo diretório. Utilize o Notepad.exe para criar um ficheiro MCF para a sua aplicação. O ficheiro deverá possuir o seguinte conteúdo.

        ``` syntax
        AUTO-GUID
        .\\YourPrivateKey.dat
        modulelist
        req     .\\<yourappname>.exe
        POLICYLIST
        INCLUSION
        PUBLICKEY .\\YourPublicKey.dat
        EXCLUSION
        ```

    -   Execute o seguinte comando para assinar a aplicação:

        **genmanifest.exe -chain ProductionCertificate.xml** *NomeAplic***.mcf** *NomeAplic***.exe.man**

        Se Genmanifest tiver sido bem-sucedido, verá apenas o seguinte texto:

        Se Genmanifest tiver falhado, verá uma mensagem de erro.

    -   O ficheiro *NomeAplic*. exe.man deve sempre ser colocado no mesmo diretório que *NomeAplic*.exe.

## Tópicos relacionados

* [Como utilizar](how-to-use-msipc.md)
* [Testar a aplicação com capacidade para direitos](running-your-first-application.md)
 

 





<!--HONumber=Apr16_HO4-->


