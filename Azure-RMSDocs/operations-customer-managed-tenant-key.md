---
title: Cliente-- AIP de inquilino geridas pelo operações de ciclo de vida de chaves
description: Informações sobre as operações de ciclo de vida relevantes se gerir a sua chave de inquilino do Azure Information Protection (a traga a sua própria chave ou BYOK, cenário).
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 08/29/2018
ms.topic: article
ms.service: information-protection
ms.assetid: c5b19c59-812d-420c-9c54-d9776309636c
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 4dd322c95d9aadc6df73e426fb92d2bb77312ed4
ms.sourcegitcommit: 0bc877840b168d05a16964b4ed0d28a9ed33f871
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/30/2018
ms.locfileid: "43298043"
---
# <a name="customer-managed-tenant-key-life-cycle-operations"></a>Gerida pelo cliente: Operações de ciclo de vida de chave de inquilino

>*Aplica-se a: [do Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Se gerir a sua chave de inquilino do Azure Information Protection (a traga a sua própria chave ou BYOK, cenário), utilize as secções seguintes para obter mais informações sobre as operações de ciclo de vida que são relevantes para esta topologia.

## <a name="revoke-your-tenant-key"></a>Revogar a chave de inquilino
No Azure Key Vault, pode alterar as permissões no cofre de chaves que contêm a chave de inquilino do Azure Information Protection, de modo a que o serviço Azure Rights Management já não possa aceder à chave. No entanto, ao fazê-lo, ninguém conseguirá abrir documentos e e-mails que anteriormente eram protegidos com o serviço Azure Rights Management.

Quando cancelar a sua subscrição do Azure Information Protection, o Azure Information Protection deixará de utilizar a sua chave de inquilino e não será necessário que faça mais nada.

## <a name="rekey-your-tenant-key"></a>Recodificar a sua chave de inquilino
A recodificação também é conhecida como implementação da chave. Quando efetuar esta operação, o Azure Information Protection deixará de utilizar a chave de inquilino existente para proteger documentos e e-mails e começa a utilizar uma chave diferente. As políticas e os modelos são imediatamente está novamente assinados mas esta mudança é gradual para clientes existentes e serviços com o Azure Information Protection. Então, por algum tempo, algum conteúdo novo continua a ser protegida com a chave de inquilino antiga.

A recodificação, tem de configurar o objeto de chave de inquilino e especificar a chave alternativa a utilizar. Em seguida, a chave utilizada anteriormente está marcada automaticamente como arquivada para o Azure Information Protection. Esta configuração garante que o conteúdo que foi protegido ao utilizar esta chave permanece acessível.

Exemplos de quando poderá ter de recodificação para o Azure Information Protection:

- A sua empresa foi dividida em duas ou mais empresas. Quando efetua a recodificação da chave de inquilino, a nova empresa não terá acesso ao conteúdo novo que os seus funcionários publicam. Estes podem aceder ao conteúdo antigo se tiverem uma cópia da chave de inquilino antiga.

- Pretende mover de uma topologia de gestão de chaves para outro. 

- Considerar que a cópia principal da sua chave de inquilino (a cópia em sua posse) é comprometida.

Para recodificar a chave de outro por si, pode criar uma nova chave no Cofre de chaves do Azure ou utilizar uma chave diferente que já se encontra no Azure Key Vault. Em seguida, siga os mesmos procedimentos que utilizou para implementar o BYOK do Azure Information Protection. 

1. Apenas se a nova chave está num cofre de chaves diferente para aquele já estiver a utilizar para o Azure Information Protection: autorizar o Azure Information Protection para utilizar o Cofre de chaves, com o [Set-AzureRmKeyVaultAccessPolicy](/powershell/module/azurerm.keyvault/set-azurermkeyvaultaccesspolicy) cmdlet.

2. Se o Azure Information Protection já não sabe sobre a chave de que pretende utilizar, execute [Use-AadrmKeyVaultKey](/powershell/module/aadrm/use-aadrmkeyvaultkey) cmdlet.

3. Configurar o objeto de chave de inquilino, com a execução [Set-AadrmKeyProperties](/powershell/module/aadrm/set-aadrmkeyproperties) cmdlet.

Para obter mais informações sobre cada um destes passos:

- Para recodificar a chave de outro por si, veja [implementar o BYOK para a sua chave de inquilino do Azure Information Protection](plan-implement-tenant-key.md#implementing-byok-for-your-azure-information-protection-tenant-key).
    
    Se estiver a recodificação uma chave protegida por HSM que criar no local e a transferência para o Key Vault, pode utilizar o mesmo universo de segurança e cartões de acesso que tenha utilizado para a sua chave atual.

- Para recodificar a, a alteração para uma chave que a Microsoft gere por si, consulte a [recodificar a sua chave de inquilino](operations-microsoft-managed-tenant-key.md#rekey-your-tenant-key) secção para operações de gerida pela Microsoft.

## <a name="backup-and-recover-your-tenant-key"></a>Efetuar cópia de segurança e recuperar a chave de inquilino
Uma vez que estiver a gerir a chave de inquilino, é responsável por fazer backup da chave que utiliza o Azure Information Protection. 

Se gerou a chave de inquilino no local, num HSM da Thales: para fazer uma cópia de segurança da chave, criar cópias de segurança o ficheiro de chave tokenized, o ficheiro de universo e os cartões de administrador. Quando transferir a chave para o Azure Key Vault, o serviço guarda o ficheiro de chave tokenized, para proteger contra falhas de quaisquer nós de serviço. Este ficheiro está vinculado ao mundo da segurança da instância ou região do Azure específica. No entanto, não considere este ficheiro de chave tokenized para ser uma cópia de segurança completa. Por exemplo, se alguma vez precisar de uma cópia de texto simples da sua chave para utilizar fora de um HSM da Thales, Azure Key Vault não é possível recuperá-lo para, porque tem apenas uma cópia não recuperável.

O Azure Key Vault tem um [cmdlet de cópia de segurança](/powershell/module/azurerm.keyvault/Backup-AzureKeyVaultKey) que pode usar para fazer cópias de segurança de uma chave baixá-lo e armazenando-o num ficheiro. Uma vez que o conteúdo baixado é criptografado, não pode ser utilizado fora do Azure Key Vault. 

## <a name="export-your-tenant-key"></a>Exportar a chave de inquilino
Se utiliza o BYOK, não pode exportar a chave de inquilino do Azure Key Vault ou do Azure Information Protection. A cópia no Azure Key Vault não é recuperável. 

## <a name="respond-to-a-breach"></a>Responder a uma violação
Nenhum sistema de segurança, por mais forte que seja, está completo sem um processo de resposta a violações. A sua chave de inquilino pode estar comprometida ou ter sido roubada. Mesmo quando ela é protegida, podem existir vulnerabilidades na tecnologia de chave de geração atual ou nos algoritmos e comprimentos de chaves atuais.

A Microsoft tem uma equipa dedicada para responder a incidentes de segurança nos seus produtos e serviços. Assim que existir um relatório credível de um incidente, esta equipa investiga o âmbito, a causa raiz e as resoluções. Se este incidente afetar os recursos, a Microsoft notifica os administradores de inquilinos do Azure Information Protection por e-mail ao utilizar o endereço que especificou aquando da subscrição.

Se ocorrer uma violação, a melhor ação que o utilizador ou a Microsoft pode efetuar depende do âmbito da violação; a Microsoft irá trabalhar consigo ao longo deste processo. A tabela seguinte mostra algumas situações típicas e a resposta provável, embora a resposta exata dependa de todas as informações que são reveladas durante a investigação.

|Descrição do incidente|Resposta provável|
|------------------------|-------------------|
|Ocorreu uma fuga da chave de inquilino.|Recodifique a sua chave de inquilino. Consulte [Recodificar a sua chave de inquilino](#rekey-your-tenant-key).|
|Um indivíduo não autorizado ou um software maligno obteve direitos para utilizar a sua chave de inquilino, mas não houve uma fuga da própria chave.|Efetuar a recodificação da chave de inquilino não ajuda neste caso e requer a análise da causa principal. Se um erro no processo ou software tiver sido responsável pelo acesso que o indivíduo não autorizado obteve, essa situação tem de ser resolvida.|
|Vulnerabilidade detetada na tecnologia HSM de geração atual.|A Microsoft tem de atualizar os HSMs. Se houver um motivo para acreditar que a vulnerabilidade expôs chaves, a Microsoft instruirá todos os clientes a recodificar a sua chave de inquilino.|
|Foi detetada uma vulnerabilidade no algoritmo RSA, ou no comprimento da chave, ou ataques de força bruta tornaram-se exequíveis a nível informático.|Microsoft tem de atualizar o Azure Key Vault ou do Azure Information Protection para oferecer suporte a novos algoritmos e maiores comprimentos de chaves que são resilientes e instruir todos os clientes a recodificar a sua chave de inquilino.|


