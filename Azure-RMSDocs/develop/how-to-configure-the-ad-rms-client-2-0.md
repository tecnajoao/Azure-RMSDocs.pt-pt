---
# required metadata

title: Configurar o cliente | Azure RMS
description: Instruções sobre como configurar o Cliente dos Serviços de Gestão de Direitos do Active Directory 2.1.
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 74C342BF-0F79-486D-AED7-C53230DE5FA7
# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---
** Este conteúdo do SDK não está atualizado. Durante um curto período de tempo, pode encontrar a [versão atual](https://msdn.microsoft.com/library/windows/desktop/hh535290(v=vs.85).aspx) da documentação no MSDN. **
# Configurar o cliente

Este tópico contém instruções sobre como configurar o Cliente dos Serviços de Gestão de Direitos do Active Directory 2.1.

**Importante** se testar a aplicação executando-a no ambiente do ISV do RMS de 1 só caixa, não é necessário configurar o Cliente de AD RMS 2.1. Para obter mais informações, consulte [Testar aplicações com capacidade para direitos](running-your-first-application.md).

 

### Pré-requisitos

-   Tem de ter o Cliente de AD RMS 2.1 instalado no computador no qual irá testar a aplicação.

    -   Se testar a aplicação no seu computador de desenvolvimento, deve ter previamente instalado o SDK Rights Management Services 2.1. O Cliente de AD RMS 2.1 terá sido instalado silenciosamente.

        Para obter informações sobre como instalar o SDK RMS 2.1, consulte [Instalar o SDK](create-your-first-rights-aware-application.md).

    -   Se testar a aplicação num computador diferente do seu computador de desenvolvimento, pode instalar o Cliente de AD RMS 2.1 nesse computador a partir da [página de transferência do Cliente de AD RMS 2.1](http://www.microsoft.com/en-us/download/details.aspx?id=38396).
        **Nota** Se a sua aplicação utiliza o Modo de API do Servidor (**IPC\_API\_MODE\_SERVER**), não é necessário utilizar um manifesto de aplicação. Pode testar a aplicação relativamente a um servidor RMS de produção e não é necessário obter uma licença de produção quando mudar para um ambiente de produção. Para obter mais informações sobre as aplicações do modo de servidor, consulte [Tipos de aplicação](application-types.md).

         

-   Tem de ter um servidor RMS instalado e configurado para trabalhar no ambiente de pré-produção. Para obter mais informações, consulte [Instalar e Configurar o Servidor](how-to-install-and-configure-an-rms-server.md).

Instruções

### Passo 1: como configurar o Cliente do RMS 2.1 para a hierarquia de certificados de pré-produção

Os passos seguintes descrevem como instalar o tempo de execução do programador, configurar o cliente para utilizar a hierarquia de certificados (de pré-produção) ISV e configurar a deteção de serviços no cliente.

1.  Copie o tempo de execução do programador, Ipcsecproc\_isv.dll, de %MSIPCSDKDIR%\\bin\\x86 (para versões de 32 bits do Windows) ou %MSIPCSDKDIR\\bin\\x64 (para versões de 64 bits do Windows) para C:\\Programas\\Active Directory Rights Management Services Client 2.1.

    **Importante** Se estiver a executar uma aplicação de 32 bits numa versão de 64 bits do Windows, terá de copiar Ipcsecproc\_isv.dll de %MSIPCSDKDIR%\\bin\\x86 para C:\\Programas(x86)\\Active Directory Rights Management Services Client 2.1.

     

2.  Configurar o Cliente de AD RMS 2.1 para utilizar a hierarquia de certificados (de pré-produção) ISV ao definir o valor da chave do Registo **Hierarquia** para 1.

    ```
    HKEY_LOCAL_MACHINE
       SOFTWARE
          Microsoft
             MSIPC
                Hierarchy DWORD = 00000001
                Data type
                DWORD
    ```

    **Nota** não ter o valor **Hierarquia** presente no registo é funcionalmente o mesmo que ter o respetivo valor definido como 0 (zero), o que significa que o SDK RMS 2.1 irá funcionar no modo de produção. Para mais informações sobre chaves e cadeias de certificado, consulte [Compreender as cadeias de certificados](understanding-certificate-chains.md).

    **Importante**  
    Se estiver a executar uma aplicação de 32 bits numa versão de 64 bits do Windows, tem de definir o valor **Hierarquia** na seguinte localização da chave:

    ```
    HKEY_LOCAL_MACHINE
        SOFTWARE
           Wow6432Node
              Microsoft
                MSIPC
    ```
     

3.  Configure a deteção do lado do servidor ou do lado do cliente para permitir que o Cliente de AD RMS 2.1 detete e estabeleça a comunicação com o seu servidor RMS de pré-produção.

    -   Na deteção do lado do servidor, um administrador regista um ponto de ligação de serviço (SCP) para o cluster de raiz RMS de pré-produção com o Active Directory e o cliente consulta o Active Directory para detetar o SCP e estabelecer uma ligação com o servidor.
    -   Na deteção do lado do cliente, pode configurar definições de Deteção de Serviços do RMS no registo no computador onde está a executar o Cliente de AD RMS 2.1. Estas definições apontam o Cliente de AD RMS 2.1 para o servidor RMS a utilizar. Quando estiverem presentes, a deteção do lado do servidor não é efetuada.

    Para configurar a deteção do lado do cliente, pode definir as seguintes chaves de registo para que apontem para o servidor RMS de pré-produção. Para obter informações sobre como configurar a deteção do lado do serviço, consulte as [Notas de Implementação do Cliente do RMS 2.0](https://TechNet.Microsoft.Com/en-us/library/jj159267(WS.10).aspx).

|Chave|Valor|
|---|-----|
|`HKEY_LOCAL_MACHINE\`<br>`SOFTWARE\`<br>`Microsoft\`<br>`MSIPC\`<br>`ServiceLocation\`<br>`EnterpriseCertification`|(Predefinido):<br><br> [**http**&#124;**https**]**://** *RMSClusterName* **/_wmcs/Certification**|
|`HKEY_LOCAL_MACHINE\`<br>`SOFTWARE\`<br>`Microsoft\`<br>`MSIPC\`<br>`ServiceLocation\`<br>`EnterprisePublishing`|(Predefinido):<br><br> [**http**&#124;**https**]**://** *RMSClusterName* **/_wmcs/Licensing**|


**Nota** por predefinição, estas chaves não existem no registo e têm de ser criadas.
     
**Importante**  
    Se estiver a executar uma aplicação de 32 bits numa versão de 64 bits do Windows, tem de definir estas chaves na seguinte localização da chave:


    HKEY_LOCAL_MACHINE
        SOFTWARE
           Wow6432Node
              Microsoft
                MSIPC
    

### Observações

As orientações neste tópico não são abrangentes. Para obter informações detalhadas sobre como configurar o Cliente de AD RMS 2.1, consulte as [Notas de Implementação do Cliente do RMS 2.0](https://TechNet.Microsoft.Com/en-us/library/jj159267(WS.10).aspx).

## Tópicos relacionados


* [Como utilizar](how-to-use-msipc.md)
* [Notas de Implementação do Cliente do RMS 2.0](https://TechNet.Microsoft.Com/en-us/library/jj159267(WS.10).aspx)
* [Instalar o SDK](create-your-first-rights-aware-application.md)
* [Instalar e configurar o servidor](how-to-install-and-configure-an-rms-server.md)
* [Testar as suas aplicações com capacidade para direitos](running-your-first-application.md)
* [Compreender as cadeias de certificados](understanding-certificate-chains.md)
 

 


<!--HONumber=Jun16_HO1-->


