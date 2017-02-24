---
title: "Exemplos de código de iOS/OS X | Azure RMS"
description: "Este tópico apresenta-lhe elementos de código importantes para a versão iOS/OS X do SDK RMS."
keywords: 
author: bruceperlerms
ms.author: bruceper
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 7E12EBF2-5A19-4A8D-AA99-531B09DA256A
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 7068e0529409eb783f16bc207a17be27cd5d82a8
ms.openlocfilehash: cd2436b20a489835aec650c2c5a19d0b0cc50eff


---

# <a name="iosos-x-code-examples"></a>Exemplos de código de iOS/OS X

Este tópico apresenta-lhe elementos de código importantes para a versão iOS/OS X do SDK RMS.

**Nota:** no código de exemplo e nas descrições que se seguem, utilizamos o termo MSIPC (Microsoft Information Protection and Control) para referenciar o processo de cliente.



## <a name="using-the-microsoft-rights-management-sdk-42---key-scenarios"></a>Utilizar o SDK Microsoft Rights Management 4.2 – cenários principais


Seguem-se exemplos de código do **Objetivo C** de uma aplicação de exemplo maior que representam cenários de desenvolvimento importantes para se orientar neste SDK. Estes demonstram a utilização do formato de Ficheiro Protegido da Microsoft referido como ficheiro protegido, a utilização de formatos de ficheiros protegidos personalizados e a utilização de controlos de IU personalizados.

### <a name="scenario-consume-an-rms-protected-file"></a>Cenário: consumir um ficheiro de RMS protegido


- **Passo 1**: criar um objeto [MSProtectedData](https://msdn.microsoft.com/library/dn758348.aspx)

 **Descrição**: instanciar um objeto [MSProtectedData](https://msdn.microsoft.com/library/dn758348.aspx) através do respetivo método de criação que implementa o serviço de autenticação com o [MSAuthenticationCallback](https://msdn.microsoft.com/library/dn758312.aspx) para obter um token ao transferir uma instância de **MSAuthenticationCallback**, como o parâmetro *authenticationCallback*, para a API de MSIPC. Consulte a chamada para [MSProtectedData protectedDataWithProtectedFile](https://msdn.microsoft.com/library/dn758351.aspx) na secção de código de exemplo seguinte.

        + (void)consumePtxtFile:(NSString *)path authenticationCallback:(id<MSAuthenticationCallback>)authenticationCallback
        {
            // userId can be provided as a hint for authentication
            [MSProtectedData protectedDataWithProtectedFile:path
                                                 userId:nil
                                 authenticationCallback:authenticationCallback
                                                options:Default
                                        completionBlock:^(MSProtectedData *data, NSError *error)
            {
                //Read the content from the ProtectedData, this will decrypt the data
                NSData *content = [data retrieveData];
            }];
        }

- **Passo 2**: configurar a autenticação com a Active Directory Authentication Library (ADAL).

  **Descrição**: neste passo, verá a ADAL utilizada para implementar um [MSAuthenticationCallback](https://msdn.microsoft.com/library/dn758312.aspx) com parâmetros de autenticação de exemplo. Para obter mais informações sobre a utilização da ADAL, consulte a Azure AD Authentication Library (ADAL).

      // AuthenticationCallback holds the necessary information to retrieve an access token.
      @interface MsipcAuthenticationCallback : NSObject<MSAuthenticationCallback>

      @end

      @implementation MsipcAuthenticationCallback

      - (void)accessTokenWithAuthenticationParameters:
             (MSAuthenticationParameters *)authenticationParameters
                                    completionBlock:
             (void(^)(NSString *accessToken, NSError *error))completionBlock
      {
          ADAuthenticationError *error;
          ADAuthenticationContext* context = [
              ADAuthenticationContext authenticationContextWithAuthority:authenticationParameters.authority
                                                                error:&error
          ];
          NSString *appClientId = @”com.microsoft.sampleapp”;
          NSURL *redirectURI = [NSURL URLWithString:@"local://authorize"];
          // Retrieve token using ADAL
          [context acquireTokenWithResource:authenticationParameters.resource
                                 clientId:appClientId
                              redirectUri:redirectURI
                                   userId:authenticationParameters.userId
                          completionBlock:^(ADAuthenticationResult *result) {
                              if (result.status != AD_SUCCEEDED)
                              {
                                  NSLog(@"Auth Failed");
                                  completionBlock(nil, result.error);
                              }
                              else
                              {
                                  completionBlock(result.accessToken, result.error);
                              }
                          }];
       }

-   **Passo 3**: verificar se o direito de Edição existe para este utilizador com estes conteúdos através do método [MSUserPolicy accessCheck](https://msdn.microsoft.com/library/dn790789.aspx) de um objeto [MSUserPolicy](https://msdn.microsoft.com/library/dn790796.aspx).

        - (void)accessCheckWithProtectedData:(MSProtectedData *)protectedData
        {
            //check if user has edit rights and apply enforcements
            if (!protectedData.userPolicy.accessCheck(EditableDocumentRights.Edit))
            {
                // enforce on the UI
                textEditor.focusableInTouchMode = NO;
                textEditor.focusable = NO;
                textEditor.enabled = NO;
            }
        }

### <a name="scenario-create-a-new-protected-file-using-a-template"></a>Cenário: criar um novo ficheiro protegido através de um modelo

Este cenário começa com a obtenção de uma lista de modelos, [MSTemplateDescriptor](https://msdn.microsoft.com/library/dn790785.aspx), ao selecionar o primeiro para criar uma política e, em seguida, ao criar e escrever no novo ficheiro protegido.

-   **Passo 1**: obter lista de modelos

        + (void)templateListUsageWithAuthenticationCallback:(id<MSAuthenticationCallback>)authenticationCallback
        {
            [MSTemplateDescriptor templateListWithUserId:@"user@domain.com"
                            authenticationCallback:authenticationCallback
                                   completionBlock:^(NSArray/*MSTemplateDescriptor*/ *templates, NSError *error)
                                   {
                                     // use templates array of MSTemplateDescriptor (Note: will be nil on error)
                                   }];
        }

-   **Passo 2**: criar um [MSUserPolicy](https://msdn.microsoft.com/library/dn790796.aspx) com o primeiro modelo na lista.

        + (void)userPolicyCreationFromTemplateWithAuthenticationCallback:(id<MSAuthenticationCallback>)authenticationCallback
        {
            [MSUserPolicy userPolicyWithTemplateDescriptor:[templates objectAtIndex:0]
                                            userId:@"user@domain.com"
                                     signedAppData:nil
                            authenticationCallback:authenticationCallback
                                           options:None
                                   completionBlock:^(MSUserPolicy *userPolicy, NSError *error)
            {
            // use userPolicy (Note: will be nil on error)
            }];
        }

-   **Passo 3**: criar um [MSMutableProtectedData](https://msdn.microsoft.com/library/dn758325.aspx) e escrever os conteúdos no mesmo.

        + (void)createPtxtWithUserPolicy:(MSUserPolicy *)userPolicy contentToProtect:(NSData *)contentToProtect
        {
            // create an MSMutableProtectedData to write content
            [contentToProtect protectedDataInFile:filePath
                        originalFileExtension:kDefaultTextFileExtension
                               withUserPolicy:userPolicy
                              completionBlock:^(MSMutableProtectedData *data, NSError *error)
            {
             // use data (Note: will be nil on error)
            }];
        }

### <a name="scenario-open-a-custom-protected-file"></a>Cenário: abrir um ficheiro protegido personalizado


-   **Passo 1**: criar um [MSUserPolicy](https://msdn.microsoft.com/library/dn790796.aspx) a partir de um *serializedContentPolicy*.

        + (void)userPolicyWith:(NSData *)protectedData
        authenticationCallback:(id<MSAuthenticationCallback>)authenticationCallback
        {
            // Read header information from protectedData and extract the  PL
            /*-------------------------------------------
            | PL length | PL | ContetSizeLength |
            -------------------------------------------*/
            NSUInteger serializedPolicySize;
            NSMutableData *serializedPolicy;
            [protectedData getBytes:&serializedPolicySize length:sizeof(serializedPolicySize)];
            [protectedData getBytes:[serializedPolicy mutableBytes] length:serializedPolicySize];

            // Get the user policy , this is an async method as it hits the REST service
            // for content key and usage restrictions
            // userId provided as a hint for authentication
            [MSUserPolicy userPolicyWithSerializedPolicy:serializedPolicy
                                              userId:@"user@domain.com"
                              authenticationCallback:authenticationCallback
                                             options:Default
                                     completionBlock:^(MSUserPolicy *userPolicy,
                                                       NSError *error)
            {

            }];
         }

-   **Passo 2**: criar um [MSCustomProtectedData](https://msdn.microsoft.com/library/dn758321.aspx) com o [MSUserPolicy](https://msdn.microsoft.com/library/dn790796.aspx) do **Passo 1** e ler a partir do mesmo.

        + (void)customProtectedDataWith:(NSData *)protectedData
        {
            // Read header information from protectedData and extract the  protectedContentSize
            /*-------------------------------------------
            | PL length | PL | ContetSizeLength |
            -------------------------------------------*/
            NSUInteger protectedContentSize;
            [protectedData getBytes:&protectedContentSize
                         length:sizeof(protectedContentSize)];

            // Create the MSCustomProtector used for decrypting the content
            // The content start position is the header length
            [MSCustomProtectedData customProtectedDataWithPolicy:userPolicy
                                               protectedData:protectedData
                                        contentStartPosition:sizeof(NSUInteger) + serializedPolicySize
                                                 contentSize:protectedContentSize
                                             completionBlock:^(MSCustomProtectedData *customProtector,
                                                               NSError *error)
            {
             //Read the content from the custom protector, this will decrypt the data
             NSData *content = [customProtector retrieveData];
             NSLog(@"%@", content);
            }];
         }

### <a name="scenario-create-a-custom-protected-file-using-a-custom-ad-hoc-policy"></a>Cenário: criar um ficheiro protegido personalizado utilizando uma política personalizada (ad hoc)


-   **Passo 1**: com um endereço de e-mail fornecido pelo utilizador, criar um descritor de política.

    **Descrição**: na prática, seria possível criar os seguintes objetos com entradas do utilizador a partir da interface do dispositivo; [MSUserRights](https://msdn.microsoft.com/en-us/library/dn790811.aspx) e [MSPolicyDescriptor](https://msdn.microsoft.com/library/dn758339.aspx).

        + (void)policyDescriptor
        {
            MSUserRights *userRights = [[MSUserRights alloc] initWithUsers:[NSArray arrayWithObjects: @"user1@domain.com", @"user2@domain.com", nil] rights:[MSEmailRights all]];

            MSPolicyDescriptor *policyDescriptor = [[MSPolicyDescriptor alloc] initWithUserRights:[NSArray arrayWithObjects:userRights, nil]];
            policyDescriptor.contentValidUntil = [[NSDate alloc] initWithTimeIntervalSinceNow:NSTimeIntervalSince1970 + 3600.0];
            policyDescriptor.offlineCacheLifetimeInDays = 10;
        }

-   **Passo 2**: criar um [MSUserPolicy](https://msdn.microsoft.com/library/dn790796.aspx) personalizado do descritor de política, *selectedDescriptor*.

        + (void)userPolicyWithPolicyDescriptor:(MSPolicyDescriptor *)policyDescriptor
        {
            [MSUserPolicy userPolicyWithPolicyDescriptor:policyDescriptor
                                          userId:@"user@domain.com"
                          authenticationCallback:authenticationCallback
                                         options:None
                                 completionBlock:^(MSUserPolicy *userPolicy, NSError *error)
            {
              // use userPolicy (Note: will be nil on error)
            }];
        }

-   **Passo 3**: criar e escrever os conteúdos no [MSMutableCustomProtectedData](https://msdn.microsoft.com/library/dn758321.aspx) e fechar.

        + (void)mutableCustomProtectedData:(NSMutableData *)backingData policy:(MSUserPolicy *)policy contentToProtect:(NSString *)contentToProtect
        {
            //Get the serializedPolicy from a given policy
            NSData *serializedPolicy = [policy serializedPolicy];

            // Write header information to backing data including the PL
            // ------------------------------------
            // | PL length | PL | ContetSizeLength |
            // -------------------------------------
            NSUInteger serializedPolicyLength = [serializedPolicy length];
            [backingData appendData:[NSData dataWithBytes:&serializedPolicyLength length:sizeof(serializedPolicyLength)]];
            [backingData appendData:serializedPolicy];
            NSUInteger protectedContentLength = [MSCustomProtectedData getEncryptedContentLengthWithPolicy:policy contentLength:unprotectedData.length];
            [backingData appendData:[NSData dataWithBytes:&protectedContentLength length:sizeof(protectedContentLength)]];

            NSUInteger headerLength = sizeof(serializedPolicyLength) + serializedPolicyLength + sizeof(protectedContentLength);

            // Create the MSMutableCustomProtector used for encrypting content
            // The content start position is the current length of the backing data
            // The encryptedContentSize content size is 0 since there is no content yet
            [MSMutableCustomProtectedData customProtectorWithUserPolicy:policy
                                                        backingData:backingData
                                             protectedContentOffset:headerLength
                                                    completionBlock:^(MSMutableCustomProtectedData *customProtector,
                                                                      NSError *error)
            {
                //Append data to the custom protector, this will encrypt the data and write it to the backing data
                [customProtector appendData:[contentToProtect dataUsingEncoding:NSUTF8StringEncoding] error:&error];

                //close the custom protector so it will flush and finalise encryption
                [customProtector close:&error];

            }];
          }

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


<!--HONumber=Jan17_HO1-->


