---
# required metadata

title: Instalar e configurar o servidor | Azure RMS
description: Instale e configure e Servidor RMS para testar a sua aplicação com capacidade para direitos.
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 32C7F387-CF7E-4CE0-AFC9-4C63FE1E134A
# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Instalar e configurar o servidor

Este tópico inclui os passos para instalar e configurar o Servidor RMS para testar a sua aplicação com capacidade para direitos.

**Importante** Se testar a aplicação executando-a no ambiente do ISV do RMS de 1 só caixa, não é necessário instalar um Servidor RMS, uma vez que já há um instalado e configurado no ambiente de 1 só caixa.
Para obter mais informações sobre o ambiente do ISV do AD RMS de 1 só caixa, consulte [Configurar o ambiente de teste](how-to-set-up-your-test-environment.md).

 

## Instruções

### Passo 1: configurar o servidor RMS

Os seguintes passos descrevem a configuração do servidor RMS e incluem:

-   Configurar o registo
-   Instalar o servidor
-   Inscrever o servidor

1.  **Configurar o registo**

    Para especificar que está a utilizar a hierarquia de certificados de pré-produção, defina os seguintes valores do registo.

    **Nota** Se estiver a utilizar o Windows Server 2008 R2 ou Windows Server 2008, defina os valores do registo antes de instalar o serviço AD RMS.

    Se estiver a utilizar o AD RMS no Windows Server 2008 R2, tem de definir o seguinte valor **REG\_DWORD**. Altere este valor para 0 (zero) para mudar para a hierarquia de produção.

    **Computador**\\**HKEY\_LOCAL\_MACHINE**\\**Software**\\**Microsoft**\\**DRMS**\\**Hierarquia** = 0x00000001

    Se estiver a utilizar o AD RMS no Windows Server 2008 R2 e outro serviço AD RMS já estiver implementado no Active Directory como um serviço de pré-produção, adicione o seguinte valor da cadeia vazio ao registo.

    **Computador**\\**HKEY\_LOCAL\_MACHINE**\\**Software**\\**Microsoft**\\**DRMS**\\**GICURL** = ""

    Se estiver a utilizar o AD RMS no Windows Server 2008, tem de definir o seguinte valor **REG\_DWORD**. Altere este valor para 0 (zero) para mudar para a hierarquia de produção.

    **Computador**\\**HKEY\_LOCAL\_MACHINE**\\**Software**\\**Microsoft**\\**DRMS**\\**2.0**\\**Hierarquia** = 0x00000001

    Se estiver a utilizar o AD RMS no Windows Server 2008 e outro serviço AD RMS já estiver implementado no Active Directory como um serviço de pré-produção, adicione o seguinte valor da cadeia vazio ao registo.

    **Computador**\\**HKEY\_LOCAL\_MACHINE**\\**Software**\\**Microsoft**\\**DRMS**\\**2.0**\\**GICURL** = ""

2.  **Instalar o servidor**

    Os Serviços de Gestão de Direitos do Active Directory (AD RMS) são compostos por componentes de cliente e servidor separados. O componente de servidor é implementado como um conjunto de serviços Web que podem ser utilizados para administrar uma infraestrutura de RMS, emitir licenças para consumidores e publicadores de conteúdo e emitir certificados para computadores e utilizadores.

    A partir do Windows Server 2008, os componentes de cliente e servidor estão incluídos no sistema operativo. Pode transferir os componentes de servidor para sistemas operativos anteriores a partir da seguinte localização.

    -   [Servidor RMS v1.0 SP2](http://go.microsoft.com/fwlink/p/?linkid=73722)

    Para configurar o componente de servidor no Windows Server 2008, tem de instalar a função de AD RMS. No entanto, antes disso, tem de configurar o registo para especificar que irá utilizar a hierarquia de certificados de pré-produção em vez da hierarquia de Produção. Se, no entanto, estiver a desenvolver aplicações num sistema operativo do servidor anterior, configure o registo após a instalação do servidor RMS v1.0 SP2, mas antes do aprovisionamento do serviço RMS.

    Para obter mais informações, consulte o passo anterior – passo 1 "Configurar o registo".

3.  **Inscrever o servidor**

    Tem de inscrever um servidor dos Serviços de Gestão de Direitos (RMS) para o identificar na hierarquia de Pré-produção ou de Produção. O processo de inscrição deixa um certificado de licenciante para servidor no computador do servidor. Este certificado encadeia novamente para uma raiz de fidedignidade da Microsoft. O modo como inscreve o servidor depende da versão RMS que está a utilizar.

    -   **Autoinscrição**

        A partir do Windows Server 2008, é possível inscrever um servidor RMS na hierarquia adequada sem enviar informações à Microsoft. Ao instalar a função de RMS, um certificado de autoinscrição e a chave privada também são instalados. Estes são utilizados para criar automaticamente o certificado de licenciante para servidor. Nenhuma informação é trocada com a Microsoft.

    -   **Inscrição online**
Se estiver a utilizar o AD RMS v1.0 SP2, é possível registar o servidor online. A inscrição decorre em segundo plano durante o processo de aprovisionamento, mas tem de ter uma ligação à Internet e tem de especificar o valor do registo adequado para identificar em que hierarquia está a inscrever o servidor. Para se inscrever na hierarquia de Pré-produção, adicione o seguinte valor **REG\_SZ** e aprovisione o servidor. Para se inscrever na hierarquia de Produção, limpe este valor e aprovisione o servidor.

        Para obter mais informações, consulte o passo anterior – passo 1 "Configurar o registo".

        **HKEY\_LOCAL\_MACHINE**\\**Software**\\**Microsoft**\\**DRMS**\\**1.0**\\**UddiProvider** = 0e3d9bb8-b765-4a68-a329-51548685fed3

## Tópicos relacionados

* [Como utilizar](how-to-use-msipc.md)
 

 





<!--HONumber=Apr16_HO4-->


