---
title: "Exemplos de código do Android | Azure RMS"
description: "Este tópico apresenta-lhe elementos de código importantes para a versão Android do SDK RMS."
keywords: 
author: bruceperlerms
ms.author: bruceper
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 58CC2E50-1E4D-4621-A947-25312C3FF519
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: f461827ad00c138dd0fda32d32032f79c69a4f7a
ms.sourcegitcommit: 04eb4990e2bf0004684221592cb93df35e6acebe
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/30/2017
---
# <a name="android-code-examples"></a>Exemplos de código do Android

Este tópico apresenta-lhe elementos de código importantes para a versão Android do SDK RMS.

**Nota:** no código de exemplo e nas descrições que se seguem, utilizamos o termo MSIPC (Microsoft Information Protection and Control) para referenciar o processo de cliente.


## <a name="using-the-microsoft-rights-management-sdk-42---key-scenarios"></a>Utilizar o SDK Microsoft Rights Management 4.2 – cenários principais

Seguem-se exemplos de código de uma aplicação de exemplo maior que representam cenários de desenvolvimento importantes para se orientar neste SDK. Estes demonstram a utilização do formato de Ficheiro Protegido da Microsoft referido como ficheiro protegido, a utilização de formatos de ficheiros protegidos personalizados e a utilização de controlos de IU personalizados.



A aplicação de exemplo, *MSIPCSampleApp*, está disponível para utilização com este SDK para o sistema operativo Android. Consulte [rms-sdk-ui-for-android](https://github.com/AzureAD/rms-sdk-ui-for-android) no GitHub para ter acesso a esta aplicação de exemplo.

### <a name="scenario-consume-an-rms-protected-file"></a>Cenário: consumir um ficheiro de RMS protegido

-   **Passo 1**: criar um [ProtectedFileInputStream](https://msdn.microsoft.com/library/dn790851.aspx)

    **Origem**: *MsipcAuthenticationCallback.java*

    **Descrição**: instanciar um objeto [ProtectedFileInputStream](https://msdn.microsoft.com/library/dn790851.aspx) através do respetivo método de criação que implementa o serviço de autenticação através do [AuthenticationRequestCallback](https://msdn.microsoft.com/library/dn758250.aspx) para obter um token transferido de uma instância de **AuthenticationRequestCallback** como o parâmetro *mRmsAuthCallback* para a API de MSIPC. Consulte a chamada para [ProtectedFileInputStream.create](https://msdn.microsoft.com/library/dn790851.aspx) perto do fim da seguinte secção de código de exemplo.

        public void startContentConsumptionFromPtxtFileFormat(InputStream inputStream)
        {
            CreationCallback<ProtectedFileInputStream> protectedFileInputStreamCreationCallback =
              new CreationCallback<ProtectedFileInputStream>()
            {
                @Override
                public Context getContext()
                {
                   …
               }

                @Override
                public void onCancel()
                {
                   …
                }

                @Override
                public void onFailure(ProtectionException e)
                {
                   …
                }

                @Override
                public void onSuccess(ProtectedFileInputStream protectedFileInputStream)
                {
                   …
                   …
                    byte[] dataChunk = new byte[16384];
                    try
                    {
                        while ((nRead = protectedFileInputStream.read(dataChunk, 0,
                                dataChunk.length)) != -1)
                        {
                            …
                        }
                         …
                        protectedFileInputStream.close();
                    }
                    catch (IOException e)
                    {
                      …
                    }  
              }
            };
            try
            {
               …
                ProtectedFileInputStream.create(inputStream, null, mRmsAuthCallback,
                                                PolicyAcquisitionFlags.NONE,
                                                protectedFileInputStreamCreationCallback);
            }
            catch (com.microsoft.rightsmanagement.exceptions.InvalidParameterException e)
            {
                …
            }
        }


-   **Passo 2**: configurar a autenticação com a Active Directory Authentication Library (ADAL).

    **Origem**: *MsipcAuthenticationCallback.java*.

    **Descrição**: neste passo, verá a ADAL utilizada para implementar um [AuthenticationRequestCallback](https://msdn.microsoft.com/library/dn758255.aspx) com parâmetros de autenticação de exemplo. Para obter mais informações sobre a utilização da ADAL, consulte [Biblioteca de Autenticação do Azure AD (ADAL)](https://msdn.microsoft.com/library/jj573266.aspx).


        class MsipcAuthenticationCallback implements AuthenticationRequestCallback
        {

        …

        @Override
        public void getToken(Map<String, String> authenticationParametersMap,
                             final AuthenticationCompletionCallback authenticationCompletionCallbackToMsipc)
        {
            String authority = authenticationParametersMap.get("oauth2.authority");
            String resource = authenticationParametersMap.get("oauth2.resource");
            String userId = authenticationParametersMap.get("userId");
            final String userHint = (userId == null)? "" : userId;
            AuthenticationContext authenticationContext = App.getInstance().getAuthenticationContext();
            if (authenticationContext == null || !authenticationContext.getAuthority().equalsIgnoreCase(authority))
            {
                try
                {
                    authenticationContext = new AuthenticationContext(App.getInstance().getApplicationContext(), authority, …);
                    App.getInstance().setAuthenticationContext(authenticationContext);
                }
                catch (NoSuchAlgorithmException e)
                {
                    …
                    authenticationCompletionCallbackToMsipc.onFailure();
                }
                catch (NoSuchPaddingException e)
                {
                    …
                    authenticationCompletionCallbackToMsipc.onFailure();
                }
           }
            App.getInstance().getAuthenticationContext().acquireToken(mParentActivity, resource, mClientId, mRedirectURI, userId, mPromptBehavior,
                           "&USERNAME=" + userHint, new AuthenticationCallback<AuthenticationResult>()
                            {
                                @Override
                                public void onError(Exception exc)
                                {
                                    …
                                    if (exc instanceof AuthenticationCancelError)
                                    {
                                         …
                                        authenticationCompletionCallbackToMsipc.onCancel();
                                    }
                                    else
                                    {
                                         …
                                        authenticationCompletionCallbackToMsipc.onFailure();
                                    }
                                }

                                @Override
                                public void onSuccess(AuthenticationResult result)
                                {
                                    …
                                    if (result == null || result.getAccessToken() == null
                                            || result.getAccessToken().isEmpty())
                                    {
                                         …
                                    }
                                    else
                                    {
                                        // request is successful
                                        …
                                        authenticationCompletionCallbackToMsipc.onSuccess(result.getAccessToken());
                                    }
                                }
                            }

                            );
                      }


-   **Passo 3**: verificar se o direito **Editar** existe para o utilizador com estes conteúdos através do método [UserPolicy.accessCheck](https://msdn.microsoft.comlibrary/dn790885.aspx).

    **Origem**: *TextEditorFragment.java*


         //check if user has edit rights and apply enforcements
                if (!mUserPolicy.accessCheck(EditableDocumentRights.Edit))
                {
                    mTextEditor.setFocusableInTouchMode(false);
                    mTextEditor.setFocusable(false);
                    mTextEditor.setEnabled(false);
                    …
                }


### <a name="scenario-create-a-new-protected-file-using-a-template"></a>Cenário: criar um novo ficheiro protegido através de um modelo

Este cenário começa com a obtenção de uma lista de modelo ao selecionar o primeiro para criar uma política e, em seguida, ao cria e escreve no novo ficheiro protegido.

-   **Passo 1**: obter a lista de modelos através de um objeto [TemplateDescriptor](https://msdn.microsoft.com/library/dn790871.aspx).

    **Origem**: *MsipcTaskFragment.java*



    CreationCallback<List<TemplateDescriptor>> getTemplatesCreationCallback = new CreationCallback<List<TemplateDescriptor>>() { @Override public Context getContext() { …
          }

          @Override
          public void onCancel()
          {
              …
          }

          @Override
          public void onFailure(ProtectionException e)
          {
              …
          }

          @Override
          public void onSuccess(List<TemplateDescriptor> templateDescriptors)
          {
             …
          }
      }; try { …
          mIAsyncControl = TemplateDescriptor.getTemplates(emailId, mRmsAuthCallback, getTemplatesCreationCallback); } catch (com.microsoft.rightsmanagement.exceptions.InvalidParameterException e) { …
      }


-    **Passo 2**: criar um [UserPolicy](https://msdn.microsoft.com/library/dn790887.aspx) com o primeiro modelo na lista.

    **Origem**: *MsipcTaskFragment.java*



      CreationCallback<UserPolicy> userPolicyCreationCallback = new CreationCallback<UserPolicy>() { @Override public Context getContext() { …
          }

          @Override
          public void onCancel()
          {
              …
          }

          @Override
          public void onFailure(ProtectionException e)
          {
              …
          }

          @Override
          public void onSuccess(final UserPolicy item)
          {
              …
          }
      }; try { …
          mIAsyncControl = UserPolicy.create((TemplateDescriptor)selectedDescriptor, mEmailId, mRmsAuthCallback, UserPolicyCreationFlags.NONE, userPolicyCreationCallback); …
      } catch (InvalidParameterException e) { …
      }


-    **Passo 3**: criar um [ProtectedFileOutputStream](https://msdn.microsoft.com/library/dn790855.aspx) e escrever os conteúdos no mesmo.

    **Origem**: *MsipcTaskFragment.java*


    private void createPTxt(final byte[] contentToProtect) { …
            CreationCallback<ProtectedFileOutputStream> protectedFileOutputStreamCreationCallback = new CreationCallback<ProtectedFileOutputStream>() { @Override public Context getContext() { …
                }

                @Override
                public void onCancel()
                {
                 …
                }

                @Override
                public void onFailure(ProtectionException e)
                {
                 …
                }

                @Override
                public void onSuccess(ProtectedFileOutputStream protectedFileOutputStream)
                {
                    try
                    {
                        // write to this stream
                        protectedFileOutputStream.write(contentToProtect);
                        protectedFileOutputStream.flush();
                        protectedFileOutputStream.close();
                        …
                    }
                    catch (IOException e)
                    {
                        …
                    }
                }
            };
            try
            {
                File file = new File(filePath);
                outputStream = new FileOutputStream(file);
                mIAsyncControl = ProtectedFileOutputStream.create(outputStream, mUserPolicy, originalFileExtension,
                        protectedFileOutputStreamCreationCallback);
            }
            catch (FileNotFoundException e)
            {
                 …
            }
            catch (InvalidParameterException e)
            {
                 …
            }
        }



### <a name="scenario-open-a-custom-protected-file"></a>Cenário: abrir um ficheiro protegido personalizado

-   **Passo 1**: criar um [UserPolicy](https://msdn.microsoft.com/library/dn790887.aspx) a partir de um *serializedContentPolicy*.

    **Origem**: *MsipcTaskFragment.java*


    CreationCallback<UserPolicy> userPolicyCreationCallbackFromSerializedContentPolicy = new CreationCallback<UserPolicy>() { @Override public void onSuccess(UserPolicy userPolicy) { …
                }

                @Override
                public void onFailure(ProtectionException e)
                {
                  …
                }

                @Override
                public void onCancel()
                {
                  …
                }

                @Override
                public Context getContext()
                {
                  …
                }
            };


    try {   ...

      // Read the serializedContentPolicyLength from the inputStream.
      long serializedContentPolicyLength = readUnsignedInt(inputStream);

      // Read the PL bytes from the input stream using the PL size.
      byte[] serializedContentPolicy = new byte[(int)serializedContentPolicyLength]; inputStream.read(serializedContentPolicy);

      ...

      UserPolicy.acquire(serializedContentPolicy, null, mRmsAuthCallback, PolicyAcquisitionFlags.NONE,           userPolicyCreationCallbackFromSerializedContentPolicy); } catch (com.microsoft.rightsmanagement.exceptions.InvalidParameterException e) {   ... } catch (IOException e) {   ... }



-    **Passo 2**: criar um [CustomProtectedInputStream](https://msdn.microsoft.com/library/dn758271.aspx) com o [UserPolicy](https://msdn.microsoft.com/library/dn790887.aspx) do **Passo 1**.

    **Origem**: *MsipcTaskFragment.java*



      CreationCallback<CustomProtectedInputStream> customProtectedInputStreamCreationCallback = new CreationCallback<CustomProtectedInputStream>() { @Override public Context getContext() { …
         }

         @Override
         public void onCancel()
         {
             …
         }

         @Override
         public void onFailure(ProtectionException e)
         {
             …
         }

         @Override
         public void onSuccess(CustomProtectedInputStream customProtectedInputStream)
         {
            …

             byte[] dataChunk = new byte[16384];
             try
             {
                 while ((nRead = customProtectedInputStream.read(dataChunk, 0, dataChunk.length)) != -1)
                 {
                      …
                 }
                  …
                 customProtectedInputStream.close();
             }
             catch (IOException e)
             {
                …
             }
             …
         }
     };

    try {  ...

      // Retrieve the encrypted content size.
      long encryptedContentLength = readUnsignedInt(inputStream);

      updateTaskStatus(new TaskStatus(TaskState.Starting, "Consuming content", true));

      CustomProtectedInputStream.create(userPolicy, inputStream,                                 encryptedContentLength,                                 customProtectedInputStreamCreationCallback); } catch (com.microsoft.rightsmanagement.exceptions.InvalidParameterException e) {  ... } catch (IOException e) {  ... }


-    **Passo 3**: ler os conteúdos do [CustomProtectedInputStream](https://msdn.microsoft.com/library/dn758271.aspx) para *mDecryptedContent* e fechar.

    **Origem**: *MsipcTaskFragment.java*


    @Override public void onSuccess(CustomProtectedInputStream customProtectedInputStream) {  mUserPolicy = customProtectedInputStream.getUserPolicy();  ByteArrayOutputStream buffer = new ByteArrayOutputStream();

      int nRead;                      
      byte[] dataChunk = new byte[16384];

      try  {    while ((nRead = customProtectedInputStream.read(dataChunk, 0,                                                        dataChunk.length)) != -1)    {       buffer.write(dataChunk, 0, nRead);    }

        buffer.flush();    mDecryptedContent = new String(buffer.toByteArray(), Charset.forName("UTF-8"));

        buffer.close();    customProtectedInputStream.close();  }  catch (IOException e)  {    ...  } }


### <a name="scenario-create-a-custom-protected-file-using-a-custom-ad-hoc-policy"></a>Cenário: criar um ficheiro protegido personalizado utilizando uma política personalizada (ad hoc)

-   **Passo 1**: com um endereço de e-mail fornecido pelo utilizador, criar um descritor de política.

    **Origem**: *MsipcTaskFragment.java*

    **Descrição**: na prática, seria possível criar os seguintes objetos com entradas do utilizador a partir da interface do dispositivo; [UserRights](https://msdn.microsoft.com/library/dn790911.aspx) e [PolicyDescriptor](https://msdn.microsoft.com/library/dn790843.aspx).



      // create userRights list   UserRights userRights = new UserRights(Arrays.asList("consumer@domain.com"),     Arrays.asList( CommonRights.View, EditableDocumentRights.Print));   ArrayList<UserRights> usersRigthsList = new ArrayList<UserRights>();   usersRigthsList.add(userRights);

      // Create PolicyDescriptor using userRights list   PolicyDescriptor policyDescriptor = PolicyDescriptor.createPolicyDescriptorFromUserRights(                                                          usersRigthsList);   policyDescriptor.setOfflineCacheLifetimeInDays(10);   policyDescriptor.setContentValidUntil(new Date());



-    **Passo 2**: criar um [UserPolicy](https://msdn.microsoft.com/library/dn790887.aspx) personalizado do descritor de política *selectedDescriptor*.

    **Origem**: *MsipcTaskFragment.java*


       mIAsyncControl = UserPolicy.create((PolicyDescriptor)selectedDescriptor,                                          mEmailId, mRmsAuthCallback,                                          UserPolicyCreationFlags.NONE,                                          userPolicyCreationCallback);



-   **Passo 3**: criar e escrever os conteúdos no [CustomProtectedOutputStream](https://msdn.microsoft.com/library/dn758274.aspx) e fechar.

    **Origem**: *MsipcTaskFragment.java*


    File file = new File(filePath); final OutputStream outputStream = new FileOutputStream(file); CreationCallback<CustomProtectedOutputStream> customProtectedOutputStreamCreationCallback = new CreationCallback<CustomProtectedOutputStream>() { @Override public Context getContext() { …
            }

            @Override
            public void onCancel()
            {
              …
            }

            @Override
            public void onFailure(ProtectionException e)
            {
              …
            }

            @Override
            public void onSuccess(CustomProtectedOutputStream protectedOutputStream)
            {
                try
                {
                    // write serializedContentPolicy
                    byte[] serializedContentPolicy = mUserPolicy.getSerializedContentPolicy();
                    writeLongAsUnsignedIntToStream(outputStream, serializedContentPolicy.length);
                    outputStream.write(serializedContentPolicy);
                    // write encrypted content
                    if (contentToProtect != null)
                    {
                        writeLongAsUnsignedIntToStream(outputStream,
                                CustomProtectedOutputStream.getEncryptedContentLength(contentToProtect.length,
                                        protectedOutputStream.getUserPolicy()));
                        protectedOutputStream.write(contentToProtect);
                        protectedOutputStream.flush();
                        protectedOutputStream.close();
                    }
                    else
                    {
                        outputStream.flush();
                        outputStream.close();
                    }
                    …
                }
                catch (IOException e)
                {
                  …
                }
            }
        };
        try
        {
            mIAsyncControl = CustomProtectedOutputStream.create(outputStream, mUserPolicy,
                    customProtectedOutputStreamCreationCallback);
        }
        catch (InvalidParameterException e)
        {
          …
        }

[!INCLUDE[Commenting house rules](../includes/houserules.md)]