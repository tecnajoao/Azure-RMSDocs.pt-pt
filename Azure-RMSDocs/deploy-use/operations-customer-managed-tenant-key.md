---
title: Gerida pelo cliente - AIP operações de ciclo de vida chave inquilino
description: Informações sobre as operações de ciclo de vida que são relevantes se gerir a sua chave de inquilino do Azure Information Protection (a traga a sua própria chave ou BYOK, cenário).
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 03/07/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: c5b19c59-812d-420c-9c54-d9776309636c
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 16ded8f9bbe06069e1fefb925166af491d1b0caa
ms.sourcegitcommit: dbbfadc72f4005f81c9f28c515119bc3098201ce
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/28/2018
ms.locfileid: "30208231"
---
# <a name="customer-managed-tenant-key-life-cycle-operations"></a>Gerida pelo cliente: Operações de ciclo de vida de chave de inquilino

>*Aplica-se a: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Se gerir a sua chave de inquilino do Azure Information Protection (a traga a sua própria chave ou BYOK, cenário), utilize as secções seguintes para obter mais informações sobre as operações de ciclo de vida que são relevantes para esta topologia.

## <a name="revoke-your-tenant-key"></a>Revogar a chave de inquilino
No Azure Key Vault, pode alterar as permissões no cofre de chaves que contêm a chave de inquilino do Azure Information Protection, de modo a que o serviço Azure Rights Management já não possa aceder à chave. No entanto, ao fazê-lo, ninguém conseguirá abrir documentos e e-mails que anteriormente eram protegidos com o serviço Azure Rights Management.

Quando cancelar a sua subscrição do Azure Information Protection, o Azure Information Protection deixará de utilizar a sua chave de inquilino e não será necessário que faça mais nada.

## <a name="rekey-your-tenant-key"></a>Recodificar a sua chave de inquilino
A recodificação também é conhecida como implementação da chave. Quando efetuar esta operação, o Azure Information Protection deixa de utilizar a chave de inquilino existente para proteger documentos e e-mails e começa a utilizar uma chave diferente. As políticas e os modelos são imediatamente assinar mas este changeover é gradual de clientes existentes e serviços com o Azure Information Protection. Por isso, há algum tempo, algum conteúdo novo continua a ser protegidos com a chave de inquilino antiga.

Para recodificação, tem de configurar o objeto de chave de inquilino e especificar a chave alternativa a utilizar. Em seguida, a chave utilizada anteriormente automaticamente está marcada como arquivados para o Azure Information Protection. Esta configuração assegura esse conteúdo que foi protegido utilizando esta chave permanece acessível.

Exemplos de quando poderá ter de recodificação para o Azure Information Protection:

- A sua empresa foi dividida em duas ou mais empresas. Quando efetua a recodificação da chave de inquilino, a nova empresa não terá acesso ao conteúdo novo que os seus funcionários publicam. Estes podem aceder ao conteúdo antigo se tiverem uma cópia da chave de inquilino antiga.

- Pretender mover de uma topologia de gestão de chaves para outro. 

- Considerar que a cópia principal da sua chave de inquilino (a cópia na sua posse) é comprometida.

A recodificar a chave de outro por si, pode criar uma nova chave no Cofre de chaves do Azure ou utilizar uma chave diferente que já se encontra no Cofre de chaves do Azure. Em seguida, siga os mesmos procedimentos que fez para implementar o BYOK do Azure Information Protection.

1. Apenas se a nova chave está a ser um cofre de chaves diferentes para o já estiver a utilizar para o Azure Information Protection: autorizar o Azure Information Protection para utilizar o Cofre de chaves, utilizando o [Set-AzureRmKeyVaultAccessPolicy](/powershell/module/azurerm.keyvault/set-azurermkeyvaultaccesspolicy) cmdlet.

2. Se já não conhece o Azure Information Protection sobre a chave de que pretende utilizar, execute [utilize AadrmKeyVaultKey](/powershell/module/aadrm/use-aadrmkeyvaultkey) cmdlet.

3. Configurar o objeto de chave de inquilino, utilizando a execução [conjunto AadrmKeyProperties](/powershell/module/aadrm/set-aadrmkeyproperties) cmdlet.

Para obter mais informações sobre cada um destes passos:

- A recodificar a chave de outro por si, consulte [implementar o BYOK para a sua chave de inquilino do Azure Information Protection](../plan-design/plan-implement-tenant-key.md#implementing-byok-for-your-azure-information-protection-tenant-key).

- A recodificar, alterar para uma chave pela Microsoft gere por si, consulte o [recodificar a chave de inquilino](operations-microsoft-managed-tenant-key.md#rekey-your-tenant-key) secção para operações de gerida pela Microsoft.

## <a name="backup-and-recover-your-tenant-key"></a>Efetuar cópia de segurança e recuperar a chave de inquilino
Porque está a gerir a chave de inquilino, o utilizador é responsável pela cópia de segurança da chave que utiliza o Azure Information Protection. 

Se gerou a chave de inquilino no local, num HSM da Thales: fazer uma cópia de segurança da chave, criar cópias de segurança do ficheiro de chave tokenized, o ficheiro de universo e os cartões de administrador. Quando transferir a chave ao Cofre de chaves do Azure, o serviço guarda o ficheiro de chave tokenized, para proteger contra falhas de quaisquer nós de serviço. Este ficheiro está vinculado ao mundo da segurança da instância ou região do Azure específica. No entanto, não considere este ficheiro de chave tokenized seja uma cópia de segurança completa. Por exemplo, se alguma vez precisar de uma cópia de texto simples da sua chave para utilizar fora de um HSM da Thales, Cofre de chaves do Azure não é possível recuperá-la, porque tem apenas uma cópia não recuperável.

O Cofre de chaves do Azure tem um [cmdlet de cópia de segurança](/powershell/module/azurerm.keyvault/Backup-AzureKeyVaultKey) que pode utilizar para fazer uma cópia de segurança de uma chave transferindo-a e armazená-la num ficheiro. Porque o conteúdo transferido é encriptado, não pode ser utilizado fora do Cofre de chaves do Azure. 

## <a name="export-your-tenant-key"></a>Exportar a chave de inquilino
Se utiliza o BYOK, não pode exportar a chave de inquilino do Azure Key Vault ou do Azure Information Protection. A cópia no Azure Key Vault não é recuperável. 

## <a name="respond-to-a-breach"></a>Responder a uma violação
Nenhum sistema de segurança, por mais forte que seja, está completo sem um processo de resposta a violações. A sua chave de inquilino pode estar comprometida ou ter sido roubada. Mesmo quando este é também protegido, podem existir vulnerabilidades na tecnologia de chave de geração atual ou nos algoritmos e comprimentos de chave atuais.

A Microsoft tem uma equipa dedicada para responder a incidentes de segurança nos seus produtos e serviços. Assim que existir um relatório credível de um incidente, esta equipa investiga o âmbito, a causa raiz e as resoluções. Se este incidente afetar os recursos, o Microsoft notifica os administradores de inquilinos do Azure Information Protection por e-mail utilizando o endereço que especificou ao subscrever.

Se ocorrer uma violação, a melhor ação que o utilizador ou a Microsoft pode efetuar depende do âmbito da violação; a Microsoft irá trabalhar consigo ao longo deste processo. A tabela seguinte mostra algumas situações típicas e a resposta provável, embora a resposta exata dependa de todas as informações que são reveladas durante a investigação.

|Descrição do incidente|Resposta provável|
|------------------------|-------------------|
|Ocorreu uma fuga da chave de inquilino.|Recodifique a sua chave de inquilino. Consulte [Recodificar a sua chave de inquilino](#rekey-your-tenant-key).|
|Um indivíduo não autorizado ou um software maligno obteve direitos para utilizar a sua chave de inquilino, mas não houve uma fuga da própria chave.|Efetuar a recodificação da chave de inquilino não ajuda neste caso e requer a análise da causa principal. Se um erro no processo ou software tiver sido responsável pelo acesso que o indivíduo não autorizado obteve, essa situação tem de ser resolvida.|
|Vulnerabilidade detetada na tecnologia HSM de geração atual.|A Microsoft tem de atualizar os HSMs. Se existir razão para considerar que a vulnerabilidade expôs chaves, a Microsoft instruirá todos os clientes a recodificar as respetivas chaves de inquilino.|
|Foi detetada uma vulnerabilidade no algoritmo RSA, ou no comprimento da chave, ou ataques de força bruta tornaram-se exequíveis a nível informático.|Microsoft tem de atualizar o Cofre de chaves do Azure ou do Azure Information Protection, para suportar novos algoritmos e maiores comprimentos de chaves que são resilientes e instruir todos os clientes a recodificar a respetiva chave de inquilino.|

[!INCLUDE[Commenting house rules](../includes/houserules.md)]

