---
title: Exemplos de código do Linux | Azure RMS
description: Este tópico apresenta-lhe elementos de código e cenários importantes para a versão do Linux do SDK RMS.
keywords: ''
author: lleonard-msft
ms.author: alleonar
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 0F7714CA-1D3E-4846-B187-739825B7DE26
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: 610356d02579cd37baacc97588fe3193eb2eef00
ms.sourcegitcommit: 44ff610dec678604c449d42cc0b0863ca8224009
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/31/2018
ms.locfileid: "39371089"
---
# <a name="linux-code-examples"></a>Exemplos de código do Linux

Este tópico apresenta-lhe elementos de código e cenários importantes para a versão do Linux do SDK RMS.

Os fragmentos de código abaixo são das aplicações de amostra, *rms\_sample* and *rmsauth\_sample*. Para obter mais informações, consulte [amostras](https://github.com/AzureAD/rms-sdk-for-cpp/tree/master/samples) no repositório GitHub.

## <a name="scenario-access-protection-policy-information-from-a-protected-file"></a>Cenário: aceder às informações da política de proteção a partir de um ficheiro protegido

**Abre e lê um ficheiro protegido do RMS**
**Origem**: [rms\_sample/mainwindow.cpp](https://github.com/AzureAD/rms-sdk-for-cpp/tree/master/samples/rms_sample)

**Descrição**: após obter um nome de ficheiro do utilizador, ler os certificados (consulte *MainWindow::addCertificates*), configurar a chamada de retorno de autorização com o ID de Cliente e o URL de Redirecionamento, chamar *ConvertFromPFile* (consulte o seguinte o exemplo de código), obtenha o nome da política de proteção, a descrição e a data de validade do conteúdo.

**C++**:

    void MainWindow::ConvertFromPFILE(const string& fileIn,
        const string& clientId,
        const string& redirectUrl,
        const string& clientEmail) 
    {
    // add trusted certificates using HttpHelpers of RMS and Auth SDKs
    addCertificates();
    
    // create shared in/out streams
    auto inFile = make_shared<ifstream>(
    fileIn, ios_base::in | ios_base::binary);
    
    if (!inFile->is_open()) {
     AddLog("ERROR: Failed to open ", fileIn.c_str());
    return;
    }
    
    string fileOut;
    
    // generate output filename
    auto pos = fileIn.find_last_of('.');
    
    if (pos != string::npos) {
     fileOut = fileIn.substr(0, pos);
    }
    
     // create streams
    auto outFile = make_shared<fstream>(
    fileOut, ios_base::in | ios_base::out | ios_base::trunc | ios_base::binary);
    
    if (!outFile->is_open()) {
     AddLog("ERROR: Failed to open ", fileOut.c_str());
     return;
      }
    
    try
    {
    // create authentication context
    AuthCallback auth(clientId, redirectUrl);
    
    // process convertion
    auto pfs = PFileConverter::ConvertFromPFile(
      clientEmail,
      inFile,
      outFile,
      auth,
      this->consent);
    
    AddLog("Successfully converted to ", fileOut.c_str());
    }
    catch (const rmsauth::Exception& e)
    {
    AddLog("ERROR: ", e.error().c_str());
    }
    catch (const rmscore::exceptions::RMSException& e) {
    AddLog("ERROR: ", e.what());
    }
    inFile->close();
    outFile->close();
    }

**Criar um fluxo de ficheiros protegidos**
**Origem**: [rms\_sample/pfileconverter.cpp](https://github.com/AzureAD/rms-sdk-for-cpp/tree/master/samples/rms_sample)

**Descrição**: este método cria uma sequência de ficheiros protegidos do fluxo subjacente transmitido através do método SDK *ProtectedFileStream::Aquire* que, em seguida, é devolvida ao autor da chamada.

**C++**:

    shared_ptr<GetProtectedFileStreamResult>PFileConverter::ConvertFromPFile(
    const string           & userId,
    shared_ptr<istream>      inStream,
    shared_ptr<iostream>     outStream,
    IAuthenticationCallback& auth,
    IConsentCallback       & consent)
    {
    auto inIStream = rmscrypto::api::CreateStreamFromStdStream(inStream);
    
    auto fsResult = ProtectedFileStream::Acquire(
    inIStream,
    userId,
    auth,
    consent,
    POL_None,
    static_cast<ResponseCacheFlags>(RESPONSE_CACHE_INMEMORY
                                    | RESPONSE_CACHE_ONDISK));
    
    if ((fsResult.get() != nullptr) && (fsResult->m_status == Success) &&
      (fsResult->m_stream != nullptr)) {
    auto pfs = fsResult->m_stream;
    
    // preparing
    readPosition  = 0;
    writePosition = 0;
    totalSize     = pfs->Size();
    
    // start threads
    for (size_t i = 0; i < THREADS_NUM; ++i) {
      threadPool.push_back(thread(WorkerThread,
                                  static_pointer_cast<iostream>(outStream), pfs,
                                  false));
    }
    
    for (thread& t: threadPool) {
      if (t.joinable()) {
        t.join();
      }
    }
    }
      return fsResult;
    }

## <a name="scenario-create-a-new-protected-file-using-a-template"></a>Cenário: criar um novo ficheiro protegido através de um modelo

**Protege um ficheiro com um modelo selecionado pelo utilizador**
**Origem**: [rms\_sample/mainwindow.cpp](https://github.com/AzureAD/rms-sdk-for-cpp/tree/master/samples/rms_sample)

**Descrição**: após obter um nome de ficheiro do utilizador, ler os certificados (consulte *MainWindow::addCertificates*) e configurar a chamada de retorno de autorização com o ID de Cliente e o URL de Redirecionamento, o ficheiro selecionado é protegido ao chamar *ConvertFromPFile* (consulte o seguinte exemplo de código).

**C++**:

    void MainWindow::ConvertToPFILEUsingTemplates(const string& fileIn,
                                              const string& clientId,
                                              const string& redirectUrl,
                                              const string& clientEmail) 
    {
    // generate output filename
    string fileOut = fileIn + ".pfile";
    
    // add trusted certificates using HttpHelpers of RMS and Auth SDKs
    addCertificates();
    
    // create shared in/out streams
    auto inFile = make_shared<ifstream>(
    fileIn, ios_base::in | ios_base::binary);
    auto outFile = make_shared<fstream>(
    fileOut, ios_base::in | ios_base::out | ios_base::trunc | ios_base::binary);
    
    if (!inFile->is_open()) {
    AddLog("ERROR: Failed to open ", fileIn.c_str());
    return;
    }
    
    if (!outFile->is_open()) {
    AddLog("ERROR: Failed to open ", fileOut.c_str());
    return;
    }
    
    // find file extension
    string fileExt;
    auto   pos = fileIn.find_last_of('.');
    
    if (pos != string::npos) {
    fileExt = fileIn.substr(pos);
    }
    
    try {
    // create authentication callback
    AuthCallback auth(clientId, redirectUrl);
    
    // process convertion
    PFileConverter::ConvertToPFileTemplates(
      clientEmail, inFile, fileExt, outFile, auth,
      this->consent, this->templates);
    
    AddLog("Successfully converted to ", fileOut.c_str());
    }
   catch (const rmsauth::Exception& e) { AddLog("ERROR: ", e.error().c_str()); outFile->close(); remove(fileOut.c_str()); } catch (const rmscore::exceptions::RMSException& e) { AddLog("ERROR: ", e.what());
    
    outFile->close();
    remove(fileOut.c_str());
    }
    inFile->close();
    outFile->close();
    }


**Protege um ficheiro através de uma política criada a partir de um modelo**
**Origem**: [rms\_sample/pfileconverter.cpp](https://github.com/AzureAD/rms-sdk-for-cpp/tree/master/samples/rms_sample)

**Descrição**: uma lista dos modelos associados ao utilizador é obtida e o modelo selecionado é utilizado para criar uma política que, por sua vez, é utilizada para proteger o ficheiro.

**C++**:

    void PFileConverter::ConvertToPFileTemplates(const string           & userId,
                                             shared_ptr<istream>      inStream,
                                             const string           & fileExt,
                                             std::shared_ptr<iostream>outStream,
                                             IAuthenticationCallback& auth,
                                             IConsentCallback& /*consent*/,
                                             ITemplatesCallback     & templ)
    {
    auto templates = TemplateDescriptor::GetTemplateList(userId, auth);
    
    rmscore::modernapi::AppDataHashMap signedData;
    
    size_t pos = templ.SelectTemplate(templates);
    
    if (pos < templates.size()) {
    auto policy = UserPolicy::CreateFromTemplateDescriptor(
      templates[pos],
      userId,
      auth,
      USER_AllowAuditedExtraction,
      signedData);
   
    ConvertToPFileUsingPolicy(policy, inStream, fileExt, outStream);
    }
    }

**Protege um ficheiro com base numa política**
**Origem**: [rms\_sample/pfileconverter.cpp](https://github.com/AzureAD/rms-sdk-for-cpp/tree/master/samples/rms_sample)

**Descrição**: crie uma sequência de ficheiros protegidos através da política em questão e, em seguida, proteja esse ficheiro.

**C++**:

    void PFileConverter::ConvertToPFileUsingPolicy(shared_ptr<UserPolicy>   policy,
                                               shared_ptr<istream>      inStream,
                                               const string           & fileExt,
                                               std::shared_ptr<iostream>outStream)
    {
    if (policy.get() != nullptr) {
    auto outIStream = rmscrypto::api::CreateStreamFromStdStream(outStream);
    auto pStream    = ProtectedFileStream::Create(policy, outIStream, fileExt);
    
    // preparing
    readPosition  = 0;
    writePosition = pStream->Size();
    
    inStream->seekg(0, ios::end);
    totalSize = inStream->tellg();
    
    // start threads
    for (size_t i = 0; i < THREADS_NUM; ++i) {
      threadPool.push_back(thread(WorkerThread,
                                  static_pointer_cast<iostream>(inStream),
                                  pStream,
                                  true));
    }
    
    for (thread& t: threadPool) {
      if (t.joinable()) {
        t.join();
      }
    }
    
    pStream->Flush();
    }
    


## <a name="scenario-protect-a-file-using-custom-protection"></a>Cenário: proteger um ficheiro com proteção personalizada

**Protege um ficheiro com proteção personalizada**
**Origem**: [rms\_sample/mainwindow.cpp](https://github.com/AzureAD/rms-sdk-for-cpp/tree/master/samples/rms_sample)

**Descrição**: após obter um nome de ficheiro do utilizador, ler os certificados (consulte *MainWindow::addCertificates*), recolher informações de direitos de utilizador e configurar a chamada de retorno de autorização com o ID de Cliente e o URL de Redirecionamento, o ficheiro selecionado é protegido ao chamar *ConvertToPFilePredefinedRights* (consulte o seguinte o exemplo de código).

**C++**:

    void MainWindow::ConvertToPFILEUsingRights(const string            & fileIn,
                                           const vector<UserRights>& userRights,
                                           const string            & clientId,
                                           const string            & redirectUrl,
                                           const string            & clientEmail)
    {
    // generate output filename
    string fileOut = fileIn + ".pfile";
    
    // add trusted certificates using HttpHelpers of RMS and Auth SDKs
    addCertificates();
    
    // create shared in/out streams
    auto inFile = make_shared<ifstream>(
    fileIn, ios_base::in | ios_base::binary);
    auto outFile = make_shared<fstream>(
    fileOut, ios_base::in | ios_base::out | ios_base::trunc | ios_base::binary);
    
    if (!inFile->is_open()) {
    AddLog("ERROR: Failed to open ", fileIn.c_str());
    return;
    }
    
    if (!outFile->is_open()) {
    AddLog("ERROR: Failed to open ", fileOut.c_str());
    return;
    }
    
    // find file extension
    string fileExt;
    auto   pos = fileIn.find_last_of('.');
    
    if (pos != string::npos) {
    fileExt = fileIn.substr(pos);
    }
    
    // is anything to add
    if (userRights.size() == 0) {
    AddLog("ERROR: ", "Please fill email and check rights");
    return;
    }
    
    
    try {
    // create authentication callback
    AuthCallback auth(clientId, redirectUrl);
    
    // process convertion
    PFileConverter::ConvertToPFilePredefinedRights(
      clientEmail,
      inFile,
      fileExt,
      outFile,
      auth,
      this->consent,
      userRights);
    
    AddLog("Successfully converted to ", fileOut.c_str());
    }
    catch (const rmsauth::Exception& e) {
    AddLog("ERROR: ", e.error().c_str());
    
    outFile->close();
    remove(fileOut.c_str());
    }
    catch (const rmscore::exceptions::RMSException& e) {
    AddLog("ERROR: ", e.what());
    
    outFile->close();
    remove(fileOut.c_str());
    }
    inFile->close();
    outFile->close();
    }


**Cria uma política de proteção para conceder os direitos selecionados ao utilizador**
**Origem**: [rms\_sample/pfileconverter.cpp](https://github.com/AzureAD/rms-sdk-for-cpp/tree/master/samples/rms_sample)

**Descrição**: crie um descritor de política e preencha-o com as informações de direitos do utilizador e, em seguida, utilize-o para criar uma política de utilizador. Esta política é utilizada para proteger o ficheiro selecionado através de uma chamada para *ConvertToPFileUsingPolicy* (consulte a descrição numa secção anterior deste tópico).

**C++**:

    void PFileConverter::ConvertToPFilePredefinedRights(
    const string            & userId,
    shared_ptr<istream>       inStream,
    const string            & fileExt,
    shared_ptr<iostream>      outStream,
    IAuthenticationCallback & auth,
    IConsentCallback& /*consent*/,
    const vector<UserRights>& userRights)
    {
    auto endValidation = chrono::system_clock::now() + chrono::hours(48);
    
    
    PolicyDescriptor desc(userRights);
    
    desc.Referrer(make_shared<string>("https://client.test.app"));
    desc.ContentValidUntil(endValidation);
    desc.AllowOfflineAccess(false);
    desc.Name("Test Name");
    desc.Description("Test Description");
    
    auto policy = UserPolicy::Create(desc, userId, auth,
                                   USER_AllowAuditedExtraction);
    ConvertToPFileUsingPolicy(policy, inStream, fileExt, outStream);
    

## <a name="workerthread---a-supporting-method"></a>WorkerThread – um método de suporte


O método *WorkerThread()* é chamado por dois dos cenários de exemplo anteriores; **Criar uma sequência de ficheiros protegidos** e **Protege um ficheiro ao qual é atribuído uma política** da seguinte forma:

**C++**:

    threadPool.push_back(thread(WorkerThread,
                                  static_pointer_cast<iostream>(outStream), pfs,
                                  false));


**Método de suporte, WorkerThread()**

**C++**:

    static mutex   threadLocker;
    static int64_t totalSize     = 0;
    static int64_t readPosition  = 0;
    static int64_t writePosition = 0;
    static vector<thread> threadPool;
    
    static void WorkerThread(shared_ptr<iostream>           stdStream,
                         shared_ptr<ProtectedFileStream>pStream,
                         bool                           modeWrite) {
    vector<uint8_t> buffer(4096);
    int64_t bufferSize = static_cast<int64_t>(buffer.size());
    
    while (totalSize - readPosition > 0) {
    // lock
    threadLocker.lock();
    
    // check remain
    if (totalSize - readPosition <= 0) {
      threadLocker.unlock();
      return;
    }
    
    // get read/write offset
    int64_t offsetRead  = readPosition;
    int64_t offsetWrite = writePosition;
    int64_t toProcess   = min(bufferSize, totalSize - readPosition);
    readPosition  += toProcess;
    writePosition += toProcess;
    
    // no need to lock more
    threadLocker.unlock();
    
    if (modeWrite) {
      // stdStream is not thread safe!!!
      try {
        threadLocker.lock();
    
        stdStream->seekg(offsetRead);
        stdStream->read(reinterpret_cast<char *>(&buffer[0]), toProcess);
        threadLocker.unlock();
        auto written =
          pStream->WriteAsync(
            buffer.data(), toProcess, offsetWrite, std::launch::deferred).get();
    
        if (written != toProcess) {
          throw rmscore::exceptions::RMSStreamException("Error while writing data");
        }
      }
      catch (exception& e) {
        qDebug() << "Exception: " << e.what();
      }
    } else {
      auto read =
        pStream->ReadAsync(&buffer[0],
                           toProcess,
                           offsetRead,
                           std::launch::deferred).get();
    
      if (read == 0) {
        break;
      }
    
      try {
        // stdStream is not thread safe!!!
        threadLocker.lock();
    
        // seek to write
        stdStream->seekp(offsetWrite);
        stdStream->write(reinterpret_cast<const char *>(buffer.data()), read);
        threadLocker.unlock();
      }
      catch (exception& e) {
        qDebug() << "Exception: " << e.what();
      }
    }
    }
    }


## <a name="scenario-rms-authentication"></a>Cenário: autenticação de RMS

Os exemplos seguintes mostram duas abordagens de autenticação diferentes: obter o token oAuth2 de Autenticação do Azure com e sem a IU.
**Adquirir o Token de Autenticação oAuth2 com IU**
**Origem**: [rmsauth\_sample/mainwindow.cpp](https://github.com/AzureAD/rms-sdk-for-cpp/tree/master/samples/rmsauth_sample)

**Passo 1**: crie um ponto partilhado do objeto **rmsauth::FileCache**.
Descrição: pode definir o caminho da cache ou utilizar a predefinição.

**C++**:

    auto FileCachePtr = std::make_shared< rmsauth::FileCache>();


**Passo 2**: crie o objeto **rmsauth::AuthenticationContext** Descrição: especifique o objeto *authority URI* e *FileCache* do Azure.

**C++**:

    AuthenticationContext authContext(
                              std::string(“https://sts.aadrm.com/_sts/oauth/authorize”),
                              AuthorityValidationType::False,
                              FileCachePtr);


**Passo 3**: chame o método **aquireToken** do objeto **authContext** e especifique os parâmetros seguintes: Descrição:

-   *Recurso requerido* – recurso protegido ao qual pretende aceder
-   *ID único de cliente* – normalmente, um GUID
-   *URI de Redirecionamento* – o URI que irá ser retomado depois de obtido o token de autenticação
-   *Comportamento de aviso de autenticação* – se definiu **PromptBehavior::Auto**, a biblioteca tenta utilizar a cache e atualizar o token, se necessário
-   *ID de utilizador* – nome de utilizador apresentado na janela da linha de comandos

**C++**:

    auto result = authContext.acquireToken(
                std::string(“api.aadrm.com”),
                std::string(“4a63455a-cfa1-4ac6-bd2e-0d046cf1c3f7”),
                std::string(“https://client.test.app”),
                PromptBehavior::Auto,
                std::string(“john.smith@msopentechtest01.onmicrosoft.com”));


**Passo 4**: obtenha o token de acesso a partir do resultado Descrição: chame o método **result-> accessToken()**

**Nota** Qualquer um dos métodos de autenticação da biblioteca pode gerar **rmsauth::Exception**

 
**Adquirir Token de Autenticação oAuth2 sem IU**
**Origem**: [rmsauth\_sample/mainwindow.cpp](https://github.com/AzureAD/rms-sdk-for-cpp/tree/master/samples/rmsauth_sample)

**Passo 1**: crie um ponto partilhado do objeto **rmsauth::FileCache** Descrição: pode definir o caminho da cache ou utilizar a predefinição

**C++**:

    auto FileCachePtr = std::make_shared< rmsauth::FileCache>();


**Passo 2**: crie o objeto **UserCredential** Descrição: especifique *user login* e *password*

**C++**:

    auto userCred = std::make_shared<UserCredential>("john.smith@msopentechtest01.onmicrosoft.com",
                                                 "SomePass");


**Passo 3**: crie o objeto **rmsauth::AuthenticationContext** Descrição: especifique o objeto *URI* e *FileCache* da autoridade do Azure

**C++**:

    AuthenticationContext authContext(
                        std::string(“https://sts.aadrm.com/_sts/oauth/authorize”),
                        AuthorityValidationType::False,
                        FileCachePtr);


**Passo 4**: chame o método **aquireToken** de **authContext** e especifique os parâmetros:
-   *Recurso requerido* – recurso protegido ao qual pretende aceder
-   *ID único de cliente* – normalmente, um GUID
-   *Credenciais do utilizador* – transmitir o objeto criado

**C++**:

    auto result = authContext.acquireToken(
                std::string(“api.aadrm.com”),
                std::string(“4a63455a-cfa1-4ac6-bd2e-0d046cf1c3f7”),
                userCred);


**Passo 5**: obtenha o token de acesso a partir do resultado Descrição: chame o método **result-> accessToken()**

**Nota** Qualquer um dos métodos de autenticação da biblioteca pode gerar **rmsauth::Exception**
