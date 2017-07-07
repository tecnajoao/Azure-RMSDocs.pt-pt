---
title: "Desenvolver a aplicação – AIP"
description: "Documentação de orientação sobre uma aplicação de consola básica a implementar proteção de documentos com o AIP"
keywords: 
author: bruceperlerms
ms.author: bruceper
manager: mbaldwin
ms.date: 03/13/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 396A2C19-3A00-4E9A-9088-198A48B15289
audience: developer
ms.reviewer: kartikk
ms.suite: ems
ms.openlocfilehash: c4334bad5a7ca6650c087425e4794c348b73501b
ms.sourcegitcommit: 04eb4990e2bf0004684221592cb93df35e6acebe
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/30/2017
---
# <a name="developing-your-application"></a>Desenvolver a sua aplicação

Neste exemplo, vai criar uma aplicação de consola simples que interage com o serviço do Azure Information Protection (AIP).  Este irá considerar o caminho de um documento a proteger como uma entrada e, em seguida, vai protegê-lo com uma política ad hoc ou um modelo do Azure. A aplicação irá aplicar as políticas corretas, de acordo com as entradas, e criar um documento de informações protegido. O código de exemplo que irá utilizar é a [aplicação de teste de IP do Azure](https://github.com/Azure-Samples/Azure-Information-Protection-Samples/tree/master/AzureIP_Test) e encontra-se no Github.

## <a name="sample-app-prerequisites"></a>Pré-requisitos da aplicação de exemplo
- **Sistema Operativo**: Windows 10, Windows 8, Windows 7, Windows Server 2008, Windows Server 2008 R2 ou Windows Server 2012
- **Linguagem de Programação**: C# (.NET Framework 3.0 e superior)
- **Ambiente de desenvolvimento**: Visual Studio 2015 (e posterior)

## <a name="setting-up-your-azure-configuration"></a>Definir a Configuração do Azure

A configuração do Azure para esta aplicação requer que crie um ID de Inquilino, uma Chave Simétrica e um ID Principal da Aplicação.

### <a name="azure-ad-tenant-configuration"></a>Configuração do Inquilino do Azure AD

Para configurar o ambiente do Azure AD para o Azure Information Protection, siga as orientações em [Ativar o Azure Rights Management](https://docs.microsoft.com/en-us/information-protection/deploy-use/activate-service).

Após a ativação do serviço, precisará de componentes do PowerShell para os passos seguintes. Veja [Administrar o serviço Azure Rights Management através do Windows PowerShell](https://docs.microsoft.com/en-us/information-protection/deploy-use/administer-powershell) para os obter.

### <a name="getting-your-tenant-id"></a>Obter o ID de Inquilino

- Enquanto administrador, abra o PowerShell.
- Importe o módulo do RMS: `Import-Module AADRM`
- Ligue-se ao serviço com as credenciais de utilizador atribuídas: `Connect-AadrmService –Verbose`
- Confirme que o RMS está ativado: `Enable-AADRM`
- Obtenha o ID do Inquilino ao executar: `Get-AadrmConfiguration`

>Registe o valor de BPOSId (ID do inquilino). Irá precisar dele nos próximos passos.

*Saída de exemplo*
![resultado do cmdlet](../media/develop/output-of-Get-AadrmConfiguration.png)

- Encerre o serviço: `Disconnect-AadrmService`

### <a name="create-a-service-principal"></a>Criar um Principal de serviço
Siga estes passos para criar um Principal de Serviço:
> Um principal de serviço corresponde às credenciais configuradas globalmente para o controlo de acesso, que permite a autenticação de um serviço com o Microsoft Azure AD e protege as informações com o Microsoft Azure AD Rights Management

- Enquanto administrador, execute o PowerShell
- Importe o módulo do Microsoft Azure AD com:`Import-Module MSOnline`
- Ligue-se ao serviço online com as credenciais de utilizador atribuídas: `Connect-MsolService`
- Crie um novo principal de serviço ao executar:`New-MsolServicePrincipal`
- Forneça um nome para o seu principal de serviço
> Registe a chave simétrica e o ID principal da aplicação para utilização futura.

*Saída de exemplo*
![resultado do cmdlet](../media/develop/output-of-NewMsolServicePrincipal.png)

- Adicione o seu ID principal da aplicação, a chave simétrica e o ID do inquilino ao ficheiro App.config da aplicação.

*Ficheiro App.config de exemplo*
![resultado do cmdlet](../media/develop/example-App.config-file.png)

- O *ClientID* e *RedirectUri* estarão disponíveis quando registar a aplicação no Azure. Para obter mais informações sobre como registar a sua aplicação no Azure e para adquirir um *ClientID* e *RedirectUri*, veja [Configurar o Azure RMS para a autenticação ADAL](adal-auth.md).


## <a name="design-summary"></a>Resumo da estrutura
O diagrama seguinte descreve uma arquitetura e o fluxo de processo da aplicação que está a criar (passos descritos abaixo).
![resumo da estrutura](../media/develop/design-summary.png)

1. As entradas do utilizador:
  - O caminho do ficheiro a ser protegido
  - Seleciona um modelo ou cria uma política ad hoc
2. A aplicação solicita a autenticação com AIP.
3. O AIP confirma a autenticação
4. A aplicação solicita modelos do AIP.
5. O AIP devolve modelos predefinidos.
6. A aplicação localiza o ficheiro especificado com a localização fornecida.
7. A aplicação aplica a política de proteção do AIP ao ficheiro.

## <a name="how-the-code-works"></a>Como funciona o código

No exemplo, Teste de IP do Azure, a solução começa com o ficheiro Iprotect.cs. Esta é uma aplicação da consola C# e, como com qualquer outra aplicação com suporte AIP, começa por carregar o *MSIPC.dll*, conforme mostrado no método `main()`.

    //Loads MSIPC.dll
    SafeNativeMethods.IpcInitialize();
    SafeNativeMethods.IpcSetAPIMode(APIMode.Server);

Carregue os parâmetros necessários para ligar ao Azure

    //Loads credentials for the service principal from App.Config
    SymmetricKeyCredential symmetricKeyCred = new SymmetricKeyCredential();
    symmetricKeyCred.AppPrincipalId = ConfigurationManager.AppSettings["AppPrincipalId"];
    symmetricKeyCred.Base64Key = ConfigurationManager.AppSettings["Base64Key"];
    symmetricKeyCred.BposTenantId = ConfigurationManager.AppSettings["BposTenantId"];

Ao fornecer o caminho do ficheiro na aplicação da consola, a aplicação verifica se o documento já está encriptado. O método pertence à classe **SafeFileApiNativeMethods**.

    var checkEncryptionStatus = SafeFileApiNativeMethods.IpcfIsFileEncrypted(filePath);

Se o documento não estiver encriptado, este realiza a encriptação do mesmo com a seleção fornecida na linha de comandos.

    if (!checkEncryptionStatus.ToString().ToLower().Contains(alreadyEncrypted))
    {
      if (method == EncryptionMethod1)
      {
        //Encrypt a file via AIP template
        ProtectWithTemplate(symmetricKeyCred, filePath);

      }
      else if (method == EncryptionMethod2)
      {
        //Encrypt a file using ad-hoc policy
        ProtectWithAdHocPolicy(symmetricKeyCred, filePath);
      }

A opção proteger com modelo obtém a lista de modelos do servidor e fornece ao utilizador a opção a selecionar.
>Se não tiver modificado os modelos, terá os modelos predefinidos do AIP

     public static void ProtectWithTemplate(SymmetricKeyCredential symmetricKeyCredential, string filePath)
     {
       // Gets the available templates for this tenant             
       Collection<TemplateInfo> templates = SafeNativeMethods.IpcGetTemplateList(null, false, true,
           false, true, null, null, symmetricKeyCredential);

       //Requests tenant template to use for encryption
       Console.WriteLine("Please select the template you would like to use to encrypt the file.");

       //Outputs templates available for selection
       int counter = 0;
       for (int i = 0; i < templates.Count; i++)
       {
         counter++;
         Console.WriteLine(counter + ". " + templates.ElementAt(i).Name + "\n" +
             templates.ElementAt(i).Description);
       }

       //Parses template selection
       string input = Console.ReadLine();
       int templateSelection;
       bool parseResult = Int32.TryParse(input, out templateSelection);

       //Returns error if no template selection is entered
       if (parseResult)
       {
         //Ensures template value entered is valid
         if (0 < templateSelection && templateSelection <= counter)
         {
           templateSelection -= templateSelection;

           // Encrypts the file using the selected template             
           TemplateInfo selectedTemplateInfo = templates.ElementAt(templateSelection);

           string encryptedFilePath = SafeFileApiNativeMethods.IpcfEncryptFile(filePath,
               selectedTemplateInfo.TemplateId,
               SafeFileApiNativeMethods.EncryptFlags.IPCF_EF_FLAG_KEY_NO_PERSIST, true, false, true, null,
               symmetricKeyCredential);
          }
        }
      }

Se selecionar a política ad hoc, o utilizador da aplicação terá de disponibilizar os e-mails das pessoas que terão direitos. Nesta secção, a licença é criada com o método **IpcCreateLicenseFromScratch()** e a nova política no modelo é aplicada.

    if (issuerDisplayName.Trim() != "")
    {
      // Gets the available issuers of rights policy templates.              
      // The available issuers is a list of RMS servers that this user has already contacted.
      try
      {
        Collection<TemplateIssuer> templateIssuers = SafeNativeMethods.IpcGetTemplateIssuerList(
                                                        null,
                                                        true,
                                                        false,
                                                        false, true, null, symmetricKeyCredential);

        // Creates the policy and associates the chosen user rights with it             
        SafeInformationProtectionLicenseHandle handle = SafeNativeMethods.IpcCreateLicenseFromScratch(
                                                            templateIssuers.ElementAt(0));
        SafeNativeMethods.IpcSetLicenseOwner(handle, owner);
        SafeNativeMethods.IpcSetLicenseUserRightsList(handle, userRights);
        SafeNativeMethods.IpcSetLicenseDescriptor(handle, new TemplateInfo(null, CultureInfo.CurrentCulture,
                                                                policyName,
                                                                policyDescription,
                                                                issuerDisplayName,
                                                                false));

        //Encrypts the file using the ad hoc policy             
        string encryptedFilePath = SafeFileApiNativeMethods.IpcfEncryptFile(
                                       filePath,
                                       handle,
                                       SafeFileApiNativeMethods.EncryptFlags.IPCF_EF_FLAG_KEY_NO_PERSIST,
                                       true,
                                       false,
                                       true,
                                       null,
                                       symmetricKeyCredential);
       }
    }

## <a name="user-interaction-example"></a>Exemplo de interação do utilizador

Depois de ter tudo compilado e em execução, os resultados da aplicação devem ter o seguinte aspeto:

1.É-lhe pedido para selecionar um método de encriptação.
![resultado da aplicação – passo 1](../media/develop/app-output-1.png)

2. É-lhe solicitado para indicar o caminho do ficheiro a ser protegido.
![resultado da aplicação – passo 2](../media/develop/app-output-2.png)

3. É-lhe pedido para introduzir o e-mail de um proprietário de licença (este proprietário tem de ter privilégios de Administrador Global no Inquilino do Azure AD).
![resultado da aplicação – passo 3](../media/develop/app-output-3.png)

4. Introduza os endereços de e-mail dos utilizadores que terão direitos de acesso ao ficheiro (os e-mails devem ser separados por espaços).
![resultado da aplicação – passo 4](../media/develop/app-output-4.png)

5. Seleciona a partir de uma lista de direitos a atribuir aos utilizadores autorizados.
![resultado da aplicação – passo 5](../media/develop/app-output-5.png)

6. Por último, introduza alguns metadados da política: nome da política, descrição e nome a apresentar do emissor (Inquilino do Azure AD) ![resultado da aplicação – passo 6](../media/develop/app-output-6.png)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]