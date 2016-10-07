---
title: "Operações de ciclo de vida das chaves de inquilino geridas pela Microsoft | Azure Information Protection"
description: "Informações sobre as operações de ciclo de vida relevantes se a Microsoft gerir a sua chave de inquilino do Azure Information Protection (a predefinição)."
author: cabailey
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 3c48cda6-e004-4bbd-adcf-589815c56c55
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: d5b6a1fc3fa0a19f3a6b65aa7b8815eda7432cd7
ms.openlocfilehash: 9c2a7d9e65dc860e0bd90789a412a8ef46f946ad


---


# Operações de ciclo de vida das chaves de inquilino: geridas pela Microsoft

>*Aplica-se a: Azure Information Protection, Office 365*

Se a Microsoft gerir a sua chave de inquilino para o Azure Information Protection (a predefinição), utilize as secções seguintes para obter mais informações sobre as operações de ciclo de vida que são relevantes para esta topologia.

## Revogar a chave de inquilino
Quando cancelar a sua subscrição do Azure Information Protection, o Azure Information Protection deixará de utilizar a sua chave de inquilino e não será necessário que faça mais nada.

## Efetuar a recodificação da chave de inquilino
A recodificação também é conhecida como implementação da chave. Não efetue a recodificação da chave de inquilino, a menos que seja realmente necessário. Os clientes antigos, tal como o Office 2010, não foram concebidos para processar alterações de chave corretamente. Neste cenário, tem de limpar o estado do Rights Management nos computadores através da Política de Grupo ou um mecanismo equivalente. No entanto, existem alguns eventos legítimos que poderão forçá-lo a efetuar a recodificação da chave de inquilino. Por exemplo:

-   A sua empresa foi dividida em duas ou mais empresas. Quando efetua a recodificação da chave de inquilino, a nova empresa não terá acesso ao conteúdo novo que os seus funcionários publicam. Estes podem aceder ao conteúdo antigo se tiverem uma cópia da chave de inquilino antiga.

-   Considera que a cópia principal da sua chave de inquilino (a cópia na sua posse) foi comprometida.

Pode executar a recodificação da chave do inquilino ao [contactar o Suporte da Microsoft](../get-started/information-support.md#to-contact-microsoft-support) para abrir um **processo de suporte do Azure Information Protection com um pedido de recodificação da chave de inquilino do Azure Information Protection**. Tem de provar que é um administrador do inquilino do Azure Information Protection e compreender que este processo demorará vários dias a ser confirmado. São aplicáveis encargos de suporte padrão; a recodificação da chave de inquilino não é um serviço de suporte gratuito.

Quando efetua a recodificação da chave de inquilino, o novo conteúdo é protegido através da utilização da nova chave de inquilino. Isto acontece de forma faseada, pelo que, durante um período de tempo, algum conteúdo novo irá continuar a ser protegido com a chave de inquilino antiga. O conteúdo previamente protegido permanece protegido para a sua chave de inquilino antiga. Para suportar este cenário, o Azure Information Protection retém a chave de inquilino antiga para poder emitir licenças para os antigos conteúdos.

## Efetuar cópia de segurança e recuperar a chave de inquilino
A Microsoft é responsável pela cópia de segurança da sua chave de inquilino e não é necessária qualquer ação da sua parte.

## Exportar a chave de inquilino
Pode exportar a configuração do Azure Information Protection e a chave de inquilino ao seguir as instruções nestes três passos:

### Passo 1: iniciar a exportação

-   Para tal, [contacte o Suporte da Microsoft](../get-started/information-support.md#to-contact-microsoft-support) para abrir um **processo de suporte do Azure Information Protection com um pedido de exportação de chave do Azure Information Protection**. Tem de provar que é um administrador do inquilino do Azure Information Protection e compreender que este processo demorará vários dias a ser confirmado. São aplicáveis encargos de suporte padrão; a exportação da chave do inquilino não é um serviço de suporte gratuito.

### Passo 2: aguardar pela verificação

-   A Microsoft verifica se o seu pedido para libertar a chave de inquilino do Azure Information Protection é legítimo. Este processo pode demorar até 3 semanas.

### Passo 3: receber instruções relativamente à chave do CSS

-   O Suporte ao Cliente da Microsoft (CSS) enviar-lhe-á a configuração do Azure Information Protection e a chave de inquilino encriptadas num ficheiro protegido por palavra-passe que tem uma extensão de nome de ficheiro .tpd. Para o fazer, o CSS primeiro envia-lhe (como a pessoa que iniciou a exportação) uma ferramenta por e-mail. Tem de executar a ferramenta numa linha de comandos da seguinte forma:

    ```
    AadrmTpd.exe -createkey
    ```
    Isto gera um par de chaves RSA e guarda os meios públicos e privados como ficheiros na pasta atual. Por exemplo: **PublicKey-FA29D0FE-5049-4C8E-931B-96C6152B0441.txt** e **PrivateKey-FA29D0FE-5049-4C8E-931B-96C6152B0441.txt**.

    Responda ao e-mail a partir do CSS, anexando o ficheiro que tem um nome que começa com **PublicKey**. Em seguida, o CSS enviar-lhe-á um ficheiro TPD como um ficheiro .xml que está encriptado com a sua chave RSA. Copie este ficheiro para a mesma pasta que executou a ferramenta AadrmTpd originalmente e execute a ferramenta novamente, utilizando o ficheiro que começa com **PrivateKey** e o ficheiro do CSS. Por exemplo:

    ```
    AadrmTpd.exe -key PrivateKey-FA29D0FE-5049-4C8E-931B-96C6152B0441.txt -target TPD-77172C7B-8E21-48B7-9854-7A4CEAC474D0.xml
    ```
    A saída deste comando deve ser dois ficheiros: um contém a palavra-passe de texto simples para o TPD protegido por palavra-passe e o outro é o próprio TPD protegido por palavra-passe. Para fins de referência cruzada, ambos devem ter o mesmo GUID que os ficheiros de chaves públicas e privadas de quando executou o comando AadrmTpd.exe -createkey:

    -   Password-FA29D0FE-5049-4C8E-931B-96C6152B0441.txt

    -   ExportedTPD-FA29D0FE-5049-4C8E-931B-96C6152B0441.xml

    Efetue uma cópia de segurança destes ficheiros e armazene-os de forma segura para se certificar de que pode continuar a desencriptar o conteúdo que está protegido com esta chave de inquilino. Além disso, se está a migrar para o AD RMS, pode importar este ficheiro TPD (o ficheiro que começa com **ExportedTDP**) para o seu servidor AD RMS.

### Passo 4: em curso: proteger a chave de inquilino

-   Depois de receber a chave de inquilino, mantenha-a bem protegida, uma vez que se alguém obtiver acesso à mesma, pode desencriptar todos os documentos que estão protegidos através dessa chave.

    Se o motivo para exportar sua a chave do inquilino for o facto de já não querer utilizar o Azure Information Protection, uma boa prática é desativar o serviço Azure Rights Management do inquilino do Azure Information Protection. Não adie esta ação depois de receber a sua chave de inquilino porque esta precaução ajuda a minimizar as consequências se a sua chave de inquilino for acedida por alguém que não a deve ter. Para obter mais informações, consulte [Desativar o Azure Rights Management](decommission-deactivate.md).

## Responder a uma violação
Nenhum sistema de segurança, por mais forte que seja, está completo sem um processo de resposta a violações. A sua chave de inquilino pode estar comprometida ou ter sido roubada. Mesmo quando está bem protegida, podem existir vulnerabilidades na tecnologia HSM da geração atual ou nos algoritmos e comprimentos de chaves atuais.

A Microsoft tem uma equipa dedicada para responder a incidentes de segurança nos seus produtos e serviços. Assim que existir um relatório credível de um incidente, esta equipa investiga o âmbito, a causa raiz e as resoluções. Se este incidente afetar os seus recursos, a Microsoft irá notificar os administradores de inquilinos do Azure Information Protection por e-mail através do endereço que especificou aquando da subscrição.

Se ocorrer uma violação, a melhor ação que o utilizador ou a Microsoft pode efetuar depende do âmbito da violação; a Microsoft irá trabalhar consigo ao longo deste processo. A tabela seguinte mostra algumas situações típicas e a resposta provável, embora a resposta exata dependa de todas as informações que são reveladas durante a investigação.

|Descrição do incidente|Resposta provável|
|------------------------|-------------------|
|Ocorreu uma fuga da chave de inquilino.|Efetue a recodificação da chave de inquilino. Consulte a secção [Efetuar a recodificação da chave de inquilino](operations-microsoft-managed-tenant-key.md#re-key-your-tenant-key) neste artigo.|
|Um indivíduo não autorizado ou um software maligno obteve direitos para utilizar a sua chave de inquilino, mas não houve uma fuga da própria chave.|Efetuar a recodificação da chave de inquilino não ajuda neste caso e requer a análise da causa raiz. Se um erro no processo ou software tiver sido responsável pelo acesso que o indivíduo não autorizado obteve, essa situação tem de ser resolvida.|
|Foi detetada uma vulnerabilidade no algoritmo RSA, ou no comprimento da chave, ou ataques de força bruta tornaram-se exequíveis a nível informático.|A Microsoft tem de atualizar o Azure Information Protection para suportar os novos algoritmos e maiores comprimentos de chaves para serem resilientes e instruir todos os clientes a renovarem as respetivas chaves de inquilino.|





<!--HONumber=Sep16_HO4-->


