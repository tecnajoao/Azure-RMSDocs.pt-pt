---
title: Exemplos de código de iOS/OS X | Azure RMS
description: Este tópico apresenta-lhe elementos de código importantes para a versão iOS/OS X do SDK RMS.
keywords: ''
author: bryanla
ms.author: bryanla
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 7E12EBF2-5A19-4A8D-AA99-531B09DA256A
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: c71fe41da2eb29645c3c25d0044f969ebdca1c9a
ms.sourcegitcommit: bd2b31dd97c8ae08c28b0f5688517110a726e3a1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/08/2019
ms.locfileid: "54070243"
---
# <a name="iosos-x-code-examples"></a>Exemplos de código de iOS/OS X

Este tópico apresenta-lhe elementos de código importantes para a versão iOS/OS X do SDK RMS.

**Nota:** no código de exemplo e nas descrições que se seguem, utilizamos o termo MSIPC (Microsoft Information Protection and Control) para referenciar o processo de cliente.



## <a name="using-the-microsoft-rights-management-sdk-42---key-scenarios"></a>Utilizar o SDK Microsoft Rights Management 4.2 – cenários principais


Seguem-se exemplos de código do **Objetivo C** de uma aplicação de exemplo maior que representam cenários de desenvolvimento importantes para se orientar neste SDK. Estes demonstram a utilização do formato de Ficheiro Protegido da Microsoft referido como ficheiro protegido, a utilização de formatos de ficheiros protegidos personalizados e a utilização de controlos de IU personalizados.

### <a name="scenario-consume-an-rms-protected-file"></a>Cenário: Consumir um ficheiro de RMS protegido


- **Passo 1**: Criar uma [MSProtectedData](https://msdn.microsoft.com/library/dn758348.aspx) objeto

 **Descrição**: Criar uma instância de um [MSProtectedData](https://msdn.microsoft.com/library/dn758348.aspx) , através de objeto seu método de criação que implementa o serviço de autenticação através do [MSAuthenticationCallback](https://msdn.microsoft.com/library/dn758312.aspx) para obter um token transferindo uma instância de **MSAuthenticationCallback**, como o parâmetro *authenticationCallback*, para a API de MSIPC. Consulte a chamada para [MSProtectedData protectedDataWithProtectedFile](https://msdn.microsoft.com/library/dn758351.aspx) na secção de código de exemplo seguinte.

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

- **Passo 2**: Configurar a autenticação com o Active Directory Authentication Library (ADAL).

  **Descrição**: Neste passo, verá a ADAL utilizada para implementar um [MSAuthenticationCallback](https://msdn.microsoft.com/library/dn758312.aspx) com parâmetros de autenticação de exemplo. Para obter mais informações sobre a utilização da ADAL, consulte a Azure AD Authentication Library (ADAL).

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

-   **Passo 3**: Verifique se o direito de edição existe para o utilizador com estes conteúdos através da [MSUserPolicy accessCheck](https://msdn.microsoft.com/library/dn790789.aspx) método de um [MSUserPolicy](https://msdn.microsoft.com/library/dn790796.aspx) objeto.

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

### <a name="scenario-create-a-new-protected-file-using-a-template"></a>Cenário: Criar um novo ficheiro protegido com um modelo

Este cenário começa com a obtenção de uma lista de modelos, [MSTemplateDescriptor](https://msdn.microsoft.com/library/dn790785.aspx), ao selecionar o primeiro para criar uma política e, em seguida, ao criar e escrever no novo ficheiro protegido.

-   **Passo 1**: Obter lista de modelos

        + (void)templateListUsageWithAuthenticationCallback:(id<MSAuthenticationCallback>)authenticationCallback
        {
            [MSTemplateDescriptor templateListWithUserId:@"user@domain.com"
                            authenticationCallback:authenticationCallback
                                   completionBlock:^(NSArray/*MSTemplateDescriptor*/ *templates, NSError *error)
                                   {
                                     // use templates array of MSTemplateDescriptor (Note: will be nil on error)
                                   }];
        }

-   **Passo 2**: Criar uma [MSUserPolicy](https://msdn.microsoft.com/library/dn790796.aspx) utilizando o primeiro modelo na lista.

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

-   **Passo 3**: Criar uma [MSMutableProtectedData](https://msdn.microsoft.com/library/dn758325.aspx) e escrever conteúdo no mesmo.

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

### <a name="scenario-open-a-custom-protected-file"></a>Cenário: Abra um ficheiro protegido personalizado


-   **Passo 1**: Criar uma [MSUserPolicy](https://msdn.microsoft.com/library/dn790796.aspx) de um *serializedContentPolicy*.

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

-   **Passo 2**: Criar uma [MSCustomProtectedData](https://msdn.microsoft.com/library/dn758321.aspx) utilizando o [MSUserPolicy](https://msdn.microsoft.com/library/dn790796.aspx) partir **passo 1** e lê-lo.

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

### <a name="scenario-create-a-custom-protected-file-using-a-custom-ad-hoc-policy"></a>Cenário: Criar um ficheiro protegido personalizado utilizando uma política personalizada (ad-hoc)


-   **Passo 1**: Com um endereço de e-mail fornecido pelo usuário, crie um descritor de política.

    **Descrição**: Na prática seriam ser criar os seguintes objetos utilizando entradas do utilizador a partir da interface do dispositivo; [MSUserRights](https://msdn.microsoft.com/library/dn790811.aspx) e [MSPolicyDescriptor](https://msdn.microsoft.com/library/dn758339.aspx).

        + (void)policyDescriptor
        {
            MSUserRights *userRights = [[MSUserRights alloc] initWithUsers:[NSArray arrayWithObjects: @"user1@domain.com", @"user2@domain.com", nil] rights:[MSEmailRights all]];

            MSPolicyDescriptor *policyDescriptor = [[MSPolicyDescriptor alloc] initWithUserRights:[NSArray arrayWithObjects:userRights, nil]];
            policyDescriptor.contentValidUntil = [[NSDate alloc] initWithTimeIntervalSinceNow:NSTimeIntervalSince1970 + 3600.0];
            policyDescriptor.offlineCacheLifetimeInDays = 10;
        }

-   **Passo 2**: Criar um personalizado [MSUserPolicy](https://msdn.microsoft.com/library/dn790796.aspx) descritor de política *selectedDescriptor*.

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

-   **Passo 3**: Criar e escrever conteúdo para o [MSMutableCustomProtectedData](https://msdn.microsoft.com/library/dn758321.aspx) e, em seguida, feche.

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
