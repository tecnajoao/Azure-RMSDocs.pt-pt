---
# required metadata

title: Testar a aplicação com capacidade para direitos | Azure RMS
description: Descreve os passos necessários para testar a aplicação com capacidade para direitos do SDK RMS 2.1.
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 834B7242-31D3-4275-A892-CFE95A61E29E
# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Testar a aplicação com capacidade para direitos

Este tópico descreve os passos necessários para testar a aplicação com capacidade para direitos SDK Rights Management Services 2.1.

Para publicar e consumir conteúdo protegido, a aplicação Rights Management Services (RMS) utiliza vários tipos diferentes de certificados e licenças, sendo que cada um é composto por uma cadeia de certificados que reconduz a uma autoridade de certificação da Microsoft. A Microsoft fornece as seguintes hierarquias:

-   A hierarquia de Pré-produção pode ser utilizada para desenvolver e testar aplicações.
-   A hierarquia de Produção tem de ser utilizada por aplicações publicadas

Recomendamos que utilize a hierarquia de Pré-produção quando desenvolver uma aplicação. Ao fazê-lo, pode trabalhar sem assinar um Contrato de Licença de Produção com a Microsoft.

> [!IMPORTANT]
> Recomenda-se que teste primeiro a aplicação SDK RMS 2.1 com o ambiente de pré-produção do RMS num Servidor RMS. Em seguida, se pretender que o cliente tenha a capacidade de utilizar a aplicação com o Serviço Azure RMS, passe para o teste nesse ambiente. Para obter mais informações, consulte [Permitir que a aplicação do serviço funcione com o RMS baseado na nuvem](how-to-use-file-api-with-aadrm-cloud.md).

 

### Pré-requisitos

-   Uma configuração de ambiente de desenvolvimento do SDK RMS 2.1. Para obter mais informações, consulte [Configurar o ambiente de desenvolvimento de pré-produção](how-to-set-up-the-pre-production-development-environment.md).
-   Para obter um exemplo de uma aplicação, consulte [IPCHelloWorld – uma aplicação de exemplo](how-to-build-your-first-application.md).

Instruções

### Passo 1:

Crie uma aplicação com capacidade para direitos. Consulte a secção de Pré-requisitos acima para ver opções.

### Passo 2: gerar um manifesto de aplicação utilizando a cadeia de certificados de pré-produção

Tem de gerar um manifesto para a sua aplicação antes de a executar.

**Nota** Se a sua aplicação utiliza o Modo de API do Servidor (**IPC\_API\_MODE\_SERVER**), não é necessário utilizar um manifesto de aplicação. Pode testar a aplicação relativamente a um servidor AD RMS de produção e não é necessário obter uma licença de produção quando mudar para um ambiente de produção. Para obter mais informações sobre as aplicações do modo de servidor, consulte [Tipos de aplicação](application-types.md).

 

Este processo também é conhecido como assinar a aplicação. É possível gerar o manifesto através de uma cadeia de certificados de produção ou da cadeia de certificados de pré-produção que é instalada com o SDK. Recomendamos que utilize a cadeia de certificados de pré-produção durante o desenvolvimento.

Para mais informações sobre chaves e cadeias de certificado, consulte [Compreender as cadeias de certificados](understanding-certificate-chains.md).

Para obter informações sobre como assinar uma aplicação com uma cadeia de certificados de produção, consulte [Mudar para o ambiente de produção](switching-to-the-production-environment.md).

Para gerar o manifesto de aplicação utilizando a cadeia de certificados de pré-produção, execute estes passos no seu computador de desenvolvimento:

1.  Copie os seguintes ficheiros dos respetivos diretórios de instalação para a mesma pasta que a aplicação.

    %MSIPCSdkDir%\\Tools\\Genmanifest.exe

    %MSIPCSdkDir%\\bin\\Isvtier5appsigningprivkey.dat

    %MSIPCSdkDir%\\bin\\Isvtier5appsigningpubkey.dat

    %MSIPCSdkDir%\\bin\\Isvtier5appsignsdk\_client.xml

    %MSIPCSdkDir%\\bin\\YourAppName.isv.mcf

2.  Na pasta de aplicação, mude o nome do ficheiro de configuração do manifesto ONomeDaSuaAplicação.isv.mcf para o nome da sua aplicação com a extensão de nome de ficheiro .mcf acrescentada. Por exemplo, se a aplicação tiver o nome AMinhaAplicação.exe, mude o nome ONomeDaSuaAplicação.isv.mcf para AMinhaAplicação.exe.mcf.

3.  Utilize um editor de texto para adicionar a sua aplicação ao ficheiro de configuração do manifesto. Para o fazer, substitua o texto do marcador de posição &lt;ONomeDaSuaAplicação&gt;.exe na lista de módulos no ficheiro .mcf pelo nome da sua aplicação; por exemplo, AMinhaAplicação.exe.

    O processo de assinatura irá gerar um erro se o ficheiro .mcf for utilizado sem modificação.

4.  Execute Genmanifest.exe para gerar o manifesto de aplicação. Esta ação também é conhecida como assinar a aplicação. O resultado desta operação deve ser um ficheiro .man. Por exemplo, se a aplicação tiver o nome AMinhaAplicação.exe e o ficheiro de configuração do manifesto tiver o nome AMinhaAplicação.exe.mcf, execute o seguinte comando:

    **genmanifest.exe -chain isvtier5appsignsdk\_client.xml MyApp.exe.mcf MyApp.exe.man**

### Passo 3: executar a aplicação

Pode executar a aplicação a partir de qualquer diretório, mas o manifesto de aplicação (AMinhaAplicação.exe.man) deve estar no mesmo diretório que o executável (AMinhaAplicação.exe).

-   **Utilizar o Ambiente de 1 Só Caixa do RMS**

    Se estiver a utilizar o ambiente de 1 só caixa do RMS para testar a sua aplicação, copie o executável da aplicação e o manifesto de aplicação para qualquer diretório no ambiente de 1 só caixa e, em seguida, execute a aplicação.

    Para obter mais informações sobre o ambiente de 1 só caixa do RMS, consulte [Configurar o ambiente de teste](how-to-set-up-your-test-environment.md).

-   **Utilizar uma configuração do Servidor de pré-produção**

    Se estiver a testar a aplicação num servidor RMS que esteja configurado para pré-produção, certifique-se de que configurou o Cliente dos Serviços de Gestão de Direitos do Active Directory 2.1 no computador onde a aplicação irá ser executada; por exemplo, no computador de desenvolvimento. Em seguida, certifique-se de que o executável da aplicação e o manifesto de aplicação estão localizados no mesmo diretório nesse computador e execute a aplicação.

    Para obter informações sobre como configurar o cliente no computador, consulte [Configurar o cliente](how-to-configure-the-ad-rms-client-2-0.md). Para obter informações sobre como instalar um servidor RMS, consulte [Instalar e configurar o servidor](how-to-install-and-configure-an-rms-server.md).

## Tópicos relacionados

* [Como utilizar](how-to-use-msipc.md)
* [Configurar o cliente](how-to-configure-the-ad-rms-client-2-0.md)
* [Instalar e configurar o servidor](how-to-install-and-configure-an-rms-server.md)
* [IPCHelloWorld – uma aplicação de exemplo](how-to-build-your-first-application.md)
* [Configurar o ambiente de desenvolvimento de pré-produção](how-to-set-up-the-pre-production-development-environment.md)
* [Mudar para o ambiente de produção](switching-to-the-production-environment.md)
* [Configurar o ambiente de teste](how-to-set-up-your-test-environment.md)
* [Compreender as cadeias de certificados](understanding-certificate-chains.md)
 

 





<!--HONumber=Apr16_HO4-->


