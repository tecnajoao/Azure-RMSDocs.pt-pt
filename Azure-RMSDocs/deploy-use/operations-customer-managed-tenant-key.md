---
title: "Operações de ciclo de vida das chaves de inquilino geridas pelo cliente | Azure Information Protection"
description: "Informações sobre operações de ciclo de vida que são relevantes se gerir a sua chave de inquilino do Azure Information Protection (o cenário traga a sua própria chave ou BYOK)."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 11/04/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: c5b19c59-812d-420c-9c54-d9776309636c
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: f1fff17f76361f8236974c6aeb21ed317c7d9883
ms.openlocfilehash: 03c2e885bfb997fda2a2f675be3dee6bc8ea8138


---


# <a name="customermanaged-tenant-key-lifecycle-operations"></a>Operações de ciclo de vida das chaves de inquilino: geridas pelo cliente

>*Aplica-se a: Azure Information Protection, Office 365*

Se gerir a sua chave de inquilino para o Azure Information Protection (o cenário traga a sua própria chave ou BYOK), utilize as secções seguintes para obter mais informações sobre as operações de ciclo de vida que são relevantes para esta topologia.

## <a name="revoke-your-tenant-key"></a>Revogar a chave de inquilino
No Cofre de Chaves do Azure, pode alterar as permissões no cofre de chaves que contêm a chave de inquilino do Azure Information Protection, de modo a que o serviço Azure Rights Management já não possa aceder à chave. No entanto, ao fazê-lo, ninguém conseguirá abrir documentos e e-mails que anteriormente eram protegidos com o serviço Azure Rights Management.

Quando cancelar a sua subscrição do Azure Information Protection, o Azure Information Protection deixará de utilizar a sua chave de inquilino e não será necessário que faça mais nada.


## <a name="rekey-your-tenant-key"></a>Efetuar a recodificação da chave de inquilino
A recodificação também é conhecida como implementação da chave. Não efetue a recodificação da chave de inquilino, a menos que seja realmente necessário. Os clientes antigos, tal como o Office 2010, não foram concebidos para processar alterações de chave corretamente. Neste cenário, tem de limpar o estado do Rights Management nos computadores através da Política de Grupo ou um mecanismo equivalente. No entanto, existem alguns eventos legítimos que poderão forçá-lo a efetuar a recodificação da chave de inquilino. Por exemplo:

-   A sua empresa foi dividida em duas ou mais empresas. Quando efetua a recodificação da chave de inquilino, a nova empresa não terá acesso ao conteúdo novo que os seus funcionários publicam. Estes podem aceder ao conteúdo antigo se tiverem uma cópia da chave de inquilino antiga.

-   Considera que a cópia principal da sua chave de inquilino (a cópia na sua posse) foi comprometida.

Quando efetua a recodificação da chave de inquilino, o novo conteúdo é protegido através da utilização da nova chave de inquilino. Isto acontece de forma faseada, pelo que, durante um período de tempo, algum conteúdo novo irá continuar a ser protegido com a chave de inquilino antiga. O conteúdo previamente protegido permanece protegido para a sua chave de inquilino antiga. Para suportar este cenário, o Azure Information Protection retém a chave de inquilino antiga para poder emitir licenças para os antigos conteúdos.

Para recodificar a sua chave de inquilino, primeiro recodifique a chave de inquilino do Azure Information Protection no Cofre de Chaves. Em seguida, execute novamente o cmdlet Add-AadrmKeyVaultKey e especifique o novo URL da chave.

## <a name="backup-and-recover-your-tenant-key"></a>Efetuar cópia de segurança e recuperar a chave de inquilino
É responsável pela cópia de segurança da sua chave de inquilino. Se gerou a chave de inquilino num HSM da Thales, para efetuar a cópia de segurança da chave, basta efetuar uma cópia de segurança do Ficheiro de Chave com Token, do ficheiro de Universo e dos Cartões de Administrador.

Uma vez que transferiu a chave seguindo os procedimentos na secção [Implementar BYOK (traga a sua própria chave)](../plan-design/plan-implement-tenant-key.md#implementing-your-azure-information-protection-tenant-key) do artigo [Planear e implementar a chave de inquilino do Azure Rights Management](../plan-design/plan-implement-tenant-key.md), o Cofre de Chaves irá manter o Ficheiro de Chave com Token, para proteção contra falhas de quaisquer nós do serviço. Este ficheiro está vinculado ao mundo da segurança da instância ou região do Azure específica. No entanto, não considere que esta seja uma cópia de segurança completa. Por exemplo, se alguma vez precisar de uma cópia de texto simples da sua chave para utilizar fora de um HSM da Thales, o Cofre de Chaves do Azure não conseguirá recuperá-la porque apenas tem uma cópia não recuperável.

## <a name="export-your-tenant-key"></a>Exportar a chave de inquilino
Se utiliza o BYOK, não pode exportar a chave de inquilino do Cofre de Chaves do Azure ou do Azure Information Protection. A cópia no Cofre de Chaves do Azure não é recuperável. 

## <a name="respond-to-a-breach"></a>Responder a uma violação
Nenhum sistema de segurança, por mais forte que seja, está completo sem um processo de resposta a violações. A sua chave de inquilino pode estar comprometida ou ter sido roubada. Mesmo quando está bem protegida, podem existir vulnerabilidades na tecnologia HSM da geração atual ou nos algoritmos e comprimentos de chaves atuais.

A Microsoft tem uma equipa dedicada para responder a incidentes de segurança nos seus produtos e serviços. Assim que existir um relatório credível de um incidente, esta equipa investiga o âmbito, a causa raiz e as resoluções. Se este incidente afetar os seus recursos, a Microsoft irá notificar os administradores de inquilinos do Azure Information Protection por e-mail através do endereço que especificou aquando da subscrição.

Se ocorrer uma violação, a melhor ação que o utilizador ou a Microsoft pode efetuar depende do âmbito da violação; a Microsoft irá trabalhar consigo ao longo deste processo. A tabela seguinte mostra algumas situações típicas e a resposta provável, embora a resposta exata dependa de todas as informações que são reveladas durante a investigação.

|Descrição do incidente|Resposta provável|
|------------------------|-------------------|
|Ocorreu uma fuga da chave de inquilino.|Efetue a recodificação da chave de inquilino. Consulte [Efetuar a recodificação da chave de inquilino](#re-key-your-tenant-key).|
|Um indivíduo não autorizado ou um software maligno obteve direitos para utilizar a sua chave de inquilino, mas não houve uma fuga da própria chave.|Efetuar a recodificação da chave de inquilino não ajuda neste caso e requer a análise da causa raiz. Se um erro no processo ou software tiver sido responsável pelo acesso que o indivíduo não autorizado obteve, essa situação tem de ser resolvida.|
|Vulnerabilidade detetada na tecnologia HSM de geração atual.|A Microsoft tem de atualizar os HSMs. Se existir razão para considerar que a vulnerabilidade expôs chaves, a Microsoft instruirá todos os clientes a renovarem as respetivas chaves de inquilino.|
|Foi detetada uma vulnerabilidade no algoritmo RSA, ou no comprimento da chave, ou ataques de força bruta tornaram-se exequíveis a nível informático.|A Microsoft tem de atualizar o Cofre de Chaves do Azure ou o Azure Information Protection para suportarem os novos algoritmos e maiores comprimentos de chaves para serem resilientes e instruir todos os clientes a renovarem as respetivas chaves de inquilino.|





<!--HONumber=Nov16_HO2-->


