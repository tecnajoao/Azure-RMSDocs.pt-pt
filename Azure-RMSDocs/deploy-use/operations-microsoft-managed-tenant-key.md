---
title: "Gerida pela Microsoft - AIP operações de ciclo de vida chave inquilino"
description: "Informações sobre as operações de ciclo de vida que são relevantes se a Microsoft gere a chave de inquilino do Azure Information Protection (predefinição)."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 08/23/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 3c48cda6-e004-4bbd-adcf-589815c56c55
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: e4a484660aaf5a1820b04892ff006c08cceb5080
ms.sourcegitcommit: 0fa5dd38c9d66ee2ecb47dfdc9f2add12731485e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2017
---
# <a name="microsoft-managed-tenant-key-lifecycle-operations"></a>Operações de ciclo de vida das chaves de inquilino: geridas pela Microsoft

>*Aplica-se a: Azure Information Protection, Office 365*

Se a Microsoft gerir a sua chave de inquilino para o Azure Information Protection (a predefinição), utilize as secções seguintes para obter mais informações sobre as operações de ciclo de vida que são relevantes para esta topologia.

## <a name="revoke-your-tenant-key"></a>Revogar a chave de inquilino
Quando cancelar a sua subscrição do Azure Information Protection, o Azure Information Protection deixará de utilizar a sua chave de inquilino e não será necessário que faça mais nada.

## <a name="rekey-your-tenant-key"></a>Recodificar a sua chave de inquilino
A recodificação também é conhecida como implementação da chave. Quando efetuar esta operação, o Azure Information Protection deixa de utilizar a chave de inquilino existente para proteger documentos e e-mails e começa a utilizar uma chave diferente. As políticas e os modelos são imediatamente assinar mas este changeover é gradual de clientes existentes e serviços com o Azure Information Protection. Por isso, há algum tempo, algum conteúdo novo continua a ser protegidos com a chave de inquilino antiga.

Para recodificação, tem de configurar o objeto de chave de inquilino e especificar a chave alternativa a utilizar. Em seguida, a chave utilizada anteriormente automaticamente está marcada como arquivados para o Azure Information Protection. Esta configuração assegura esse conteúdo que foi protegido utilizando esta chave permanece acessível.

Exemplos de quando poderá ter de recodificação para o Azure Information Protection:

- A migração do Active Directory Rights Management Services (AD RMS) com uma chave de modo criptográfico 1. Quando a migração estiver concluída, pretender alterar a utilizar uma chave que utiliza o modo criptográfico 2.

- A sua empresa foi dividida em duas ou mais empresas. Quando efetua a recodificação da chave de inquilino, a nova empresa não terá acesso ao conteúdo novo que os seus funcionários publicam. Estes podem aceder ao conteúdo antigo se tiverem uma cópia da chave de inquilino antiga.

- Considerar que a cópia principal da sua chave de inquilino é comprometida.

Para recodificação, pode selecionar uma chave diferente para se tornar a sua chave de inquilino gerida pela Microsoft, mas não é possível criar uma nova chave gerida pela Microsoft. Para criar uma nova chave, tem de alterar a topologia de chave a ser gerida pelo cliente (BYOK).

Tiver mais do que uma chave gerida pela Microsoft se migrados a partir do Active Directory Rights Management Services (AD RMS) e escolher a topologia de chave gerida pela Microsoft para o Azure Information Protection. Neste cenário, tem, pelo menos, duas chaves gerida pela Microsoft para o seu inquilino. Chave de um ou mais, são a chave ou chaves importados do AD RMS. Também terá a chave predefinida que foi criada automaticamente para o seu inquilino do Azure Information Protection.

Para selecionar uma chave diferente para ser a sua chave de inquilino do Active Directory para o Azure Information Protection, utilize o [conjunto AadrmKeyProperties](/powershell/module/aadrm/set-aadrmkeyproperties) cmdlet do módulo AADRM. Para ajudar a identificar qual a chave a utilizar, utilize o [Get-AadrmKeys](/powershell/module/aadrm/get-aadrmkeys) cmdlet. Pode identificar a chave predefinida que foi criada automaticamente para o seu inquilino do Azure Information Protection, executando o seguinte comando:

    (Get-AadrmKeys) | Sort-Object CreationTime | Select-Object -First 1

Para alterar a topologia de chave a ser gerida pelo cliente (BYOK), consulte [implementar a sua chave de inquilino do Azure Information Protection](../plan-design/plan-implement-tenant-key.md#implementing-your-azure-information-protection-tenant-key).

## <a name="backup-and-recover-your-tenant-key"></a>Efetuar cópia de segurança e recuperar a chave de inquilino
A Microsoft é responsável pela cópia de segurança da sua chave de inquilino e não é necessária qualquer ação da sua parte.

## <a name="export-your-tenant-key"></a>Exportar a chave de inquilino
Pode exportar a configuração do Azure Information Protection e a chave de inquilino ao seguir as instruções seguintes três passos:

### <a name="step-1-initiate-export"></a>Passo 1: iniciar a exportação

- [Contacte o Support Microsoft](../get-started/information-support.md#to-contact-microsoft-support) para abrir um **caso de suporte do Azure Information Protection com um pedido de uma exportação de chave do Azure Information Protection**. Tem de provar que é um administrador do inquilino do Azure Information Protection e compreender que este processo demorará vários dias a ser confirmado. São aplicáveis encargos de suporte padrão; a exportação da chave do inquilino não é um serviço de suporte gratuito.

### <a name="step-2-wait-for-verification"></a>Passo 2: aguardar pela verificação

-   A Microsoft verifica se o seu pedido para libertar a chave de inquilino do Azure Information Protection é legítimo. Este processo pode demorar até três semanas.

### <a name="step-3-receive-key-instructions-from-css"></a>Passo 3: receber instruções relativamente à chave do CSS

-   O Suporte ao Cliente da Microsoft (CSS) enviar-lhe-á a configuração do Azure Information Protection e a chave de inquilino encriptadas num ficheiro protegido por palavra-passe. O ficheiro tem uma extensão de nome de ficheiro **.tpd**. Para o fazer, o CSS primeiro envia-lhe (como a pessoa que iniciou a exportação) uma ferramenta por e-mail. Tem de executar a ferramenta numa linha de comandos da seguinte forma:

    ```
    AadrmTpd.exe -createkey
    ```
    Isto gera um par de chaves RSA e guarda os meios públicos e privados como ficheiros na pasta atual. Por exemplo: **PublicKey-FA29D0FE-5049-4C8E-931B-96C6152B0441.txt** e **PrivateKey-FA29D0FE-5049-4C8E-931B-96C6152B0441.txt**.

    Responda ao e-mail a partir do CSS, anexando o ficheiro que tem um nome que começa com **PublicKey**. CSS junto envia-lhe um ficheiro TPD como um ficheiro. XML que está encriptado com a sua chave RSA. Copie este ficheiro para a mesma pasta que executou a ferramenta AadrmTpd originalmente e execute a ferramenta novamente, utilizando o ficheiro que começa com **PrivateKey** e o ficheiro do CSS. Por exemplo:

    ```
    AadrmTpd.exe -key PrivateKey-FA29D0FE-5049-4C8E-931B-96C6152B0441.txt -target TPD-77172C7B-8E21-48B7-9854-7A4CEAC474D0.xml
    ```
    Este comando deverá resultar em dois ficheiros: um contém a palavra-passe de texto simples para o TPD protegido por palavra-passe e o outro é o próprio TPD protegido por palavra-passe. Os ficheiros têm um novo GUID, por exemplo:
     
    - Palavra-passe-5E4C2018-8C8C-4548-8705-E3218AA1544E.txt

    - TPDExportado-5E4C2018-8C8C-4548-8705-E3218AA1544E.xml

    Efetue uma cópia de segurança destes ficheiros e armazene-os de forma segura para se certificar de que pode continuar a desencriptar o conteúdo que está protegido com esta chave de inquilino. Além disso, se está a migrar para o AD RMS, pode importar este ficheiro TPD (o ficheiro que começa com **ExportedTDP**) para o seu servidor AD RMS.

### <a name="step-4-ongoing-protect-your-tenant-key"></a>Passo 4: em curso: proteger a chave de inquilino

Depois de receber a chave de inquilino, mantenha-a bem protegida, uma vez que se alguém obtiver acesso à mesma, pode desencriptar todos os documentos que estão protegidos através dessa chave.

Se o motivo para exportar sua a chave do inquilino for o facto de já não querer utilizar o Azure Information Protection, uma boa prática é desativar o serviço Azure Rights Management do inquilino do Azure Information Protection. Não adie esta ação depois de receber a sua chave de inquilino porque esta precaução ajuda a minimizar as consequências de um acesso indevido à sua chave de inquilino. Para obter mais informações, consulte [Desativar o Azure Rights Management](decommission-deactivate.md).

## <a name="respond-to-a-breach"></a>Responder a uma violação
Nenhum sistema de segurança, por mais forte que seja, está completo sem um processo de resposta a violações. A sua chave de inquilino pode estar comprometida ou ter sido roubada. Mesmo quando este é também protegido, podem existir vulnerabilidades na tecnologia de chave de geração atual ou nos algoritmos e comprimentos de chave atuais.

A Microsoft tem uma equipa dedicada para responder a incidentes de segurança nos seus produtos e serviços. Assim que existir um relatório credível de um incidente, esta equipa investiga o âmbito, a causa raiz e as resoluções. Se este incidente afetar os seus recursos, a Microsoft irá notificar os administradores de inquilinos do Azure Information Protection por e-mail através do endereço que especificou aquando da subscrição.

Se ocorrer uma violação, a melhor ação que o utilizador ou a Microsoft pode efetuar depende do âmbito da violação; a Microsoft irá trabalhar consigo ao longo deste processo. A tabela seguinte mostra algumas situações típicas e a resposta provável, embora a resposta exata dependa de todas as informações que são reveladas durante a investigação.

|Descrição do incidente|Resposta provável|
|------------------------|-------------------|
|Ocorreu uma fuga da chave de inquilino.|Recodifique a sua chave de inquilino. Veja a secção [Recodificar a sua chave de inquilino](operations-microsoft-managed-tenant-key.md#rekey-your-tenant-key) neste artigo.|
|Um indivíduo não autorizado ou um software maligno obteve direitos para utilizar a sua chave de inquilino, mas não houve uma fuga da própria chave.|Efetuar a recodificação da chave de inquilino não ajuda neste caso e requer a análise da causa principal. Se um erro no processo ou software tiver sido responsável pelo acesso que o indivíduo não autorizado obteve, essa situação tem de ser resolvida.|
|Foi detetada uma vulnerabilidade no algoritmo RSA, ou no comprimento da chave, ou ataques de força bruta tornaram-se exequíveis a nível informático.|A Microsoft tem de atualizar o Azure Information Protection para suportar os novos algoritmos e maiores comprimentos de chaves para serem resilientes e instruir todos os clientes a renovarem as respetivas chaves de inquilino.|

[!INCLUDE[Commenting house rules](../includes/houserules.md)]

