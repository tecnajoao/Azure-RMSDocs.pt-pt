---
title: Planear e implementar a sua chave de inquilino do Azure Rights Management | Azure RMS
description: "Informações para o ajudar a planear e gerir a sua chave de inquilino do RMS (Rights Management) do Azure RMS. Por exemplo, em vez de a sua chave de inquilino ser gerida pela Microsoft (predefinição), poderá querer gerir a sua própria chave de inquilino para cumprir os regulamentos específicos que se aplicam à sua organização. A gestão da sua própria chave de inquilino também é referida como Bring Your Own Key (Traga a Sua Própria Chave) ou BYOK."
author: cabailey
manager: mbaldwin
ms.date: 09/01/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: f0d33c5f-a6a6-44a1-bdec-5be1bc8e1e14
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: eec7cc8b20435df11d7b8f89c4b9e9d0f039dc55
ms.openlocfilehash: 25d47ab488474ed756b3139bb9d42d420cea25f7


---

# Planear e implementar a sua chave de inquilino do Azure Rights Management

>*Aplica-se a: Azure Rights Management, Office 365*

Utilize as informações deste artigo para o ajudar a planear e gerir a sua chave de inquilino do RMS (Rights Management) do Azure RMS. Por exemplo, em vez de a sua chave de inquilino ser gerida pela Microsoft (predefinição), poderá querer gerir a sua própria chave de inquilino para cumprir os regulamentos específicos que se aplicam à sua organização.  A gestão da sua própria chave de inquilino também é referida como Bring Your Own Key (Traga a Sua Própria Chave) ou BYOK.

> [!NOTE]
> A chave de inquilino do RMS também é conhecida como a chave do Certificado de Licenciante para Servidor (SLC). O Azure RMS mantém uma ou mais chaves para cada organização que subscreve o Azure RMS. Sempre que uma chave é utilizada para o RMS numa organização (por exemplo, chaves de utilizador, chaves de computador, chaves de encriptação de documentos), esta associa-se criptograficamente à sua chave de inquilino do RMS.

**Resumindo:** utilize a seguinte tabela como um guia rápido para a sua topologia de chaves de inquilino recomendada. Em seguida, utilize a documentação adicional para obter mais informações.

Se implementar o Azure RMS com uma chave de inquilino gerida pela Microsoft, pode mudar para o BYOK mais tarde. No entanto, atualmente não pode alterar a gestão da sua chave de inquilino do Azure RMS do BYOK para gerida pela Microsoft.

|Necessidade comercial|Topologia de chaves de inquilino recomendada|
|------------------------|-----------------------------------|
|Implementar o Azure RMS rapidamente e sem necessitar de hardware especial|Gerida pela Microsoft|
|Necessita da funcionalidade IRM completa no Exchange Online com o Azure RMS|Gerida pela Microsoft|
|As suas chaves são criadas por si e protegidas num módulo de hardware de segurança (HSM)|BYOK<br /><br />Atualmente, esta configuração resultará na redução da funcionalidade IRM no Exchange Online. Para mais informações, consulte [Preços e restrições do BYOK](byok-price-restrictions.md).|

## Selecione a sua topologia de chaves de inquilino: gerida pela Microsoft (predefinição) ou gerida por si (BYOK)
Decida que topologia de chaves de inquilino é melhor para a sua organização. Por predefinição, o Azure RMS gera a sua chave de inquilino e gere a maioria dos aspetos do ciclo de vida da chave de inquilino. Esta é a opção mais simples e com menos tarefas administrativas adicionais. Na maioria dos casos, nem precisa de saber que tem uma chave de inquilino. Basta inscrever-se no Azure RMS e o processo de gestão de chaves restante é processado pela Microsoft.

Em alternativa, pode pretender o controlo total sobre a chave de inquilino, utilizando o [Cofre de Chaves do Azure](https://azure.microsoft.com/services/key-vault/). Este cenário envolve criar a sua chave de inquilino e manter a cópia principal no local. Este cenário é frequentemente referido como BYOK (Bring Your Own Key – Traga a Sua Própria Chave). Quando esta opção é selecionada, ocorre o seguinte:

1.  Gera a chave de inquilino no local, de acordo com as suas políticas de TI e de segurança.

2.  Transfere com segurança a chave de inquilino de um módulo de hardware de segurança (HSM) do qual é proprietário para HSMs que são propriedade da Microsoft e geridos pela mesma utilizando o Cofre de Chaves do Azure. Durante este processo, a sua chave de inquilino nunca ultrapassa o limite de proteção de hardware.

3.  Quando transfere a chave de inquilino para a Microsoft, esta permanece protegida pelo Cofre de Chaves do Azure.

Embora seja opcional, provavelmente também irá querer utilizar os registos de utilização quase em tempo real do Azure RMS, para saber exatamente como e quando a sua chave de inquilino está a ser utilizada.

> [!NOTE]
> Como medida de proteção adicional, o Cofre de Chaves do Azure utiliza domínios de segurança separados nos seus centros de dados em regiões como a América do Norte, EMEA (Europa, Médio Oriente e África) e Ásia. E para diferentes instâncias do Azure, como o Microsoft Azure Alemanha e o Azure Government. Quando faz a gestão da sua própria chave de inquilino, esta é associada ao domínio de segurança da região ou instância na qual o seu inquilino do RMS está registado. Por exemplo, não é possível utilizar uma chave de inquilino de um cliente europeu nos centros de dados da América do Norte ou da Ásia.

## O ciclo de vida das chaves de inquilino
Se decidir que a Microsoft deve gerir a sua chave de inquilino, a maioria das operações de ciclo de vida da chave será processada pela Microsoft. No entanto, se optar por gerir a sua chave de inquilino, fica responsável por muitas das operações de ciclo de vida da chave e por alguns procedimentos adicionais no Cofre de Chaves do Azure.

Os diagramas seguintes apresentam e comparam estas duas opções. O primeiro diagrama mostra que há poucas tarefas administrativas adicionais para si na configuração predefinida quando a Microsoft gere a chave de inquilino.

![Ciclo de vida da chave de inquilino do Azure RMS – gerida pela Microsoft (a predefinição)](../media/RMS_BYOK_cloud.png)

O segundo diagrama mostra os passos adicionais necessários quando gere a sua própria chave de inquilino.

![Ciclo de vida da chave de inquilino do Azure RMS – gerida por si (BYOK)](../media/RMS_BYOK_onprem4.png)

Se decidir deixar que a sua chave de inquilino seja gerida pela Microsoft, não precisa de tomar medidas adicionais para a gerar e pode ir diretamente para [Passos seguintes](plan-implement-tenant-key.md#next-steps).  

Se optar por gerir a sua chave de inquilino, leia as secções seguintes para obter mais informações.

## Implementar a sua chave de inquilino do Azure Rights Management

Utilize as informações e os procedimentos desta secção, se tiver decidido gerar e gerir a sua chave de inquilino – o cenário BYOK (Bring Your Own Key – Traga a Sua Própria Chave):


> [!IMPORTANT]
> Se tiver começado a utilizar o Azure RMS com uma chave de inquilino gerida pela Microsoft e pretender agora gerir a sua chave de inquilino (mudar para BYOK), os seus documentos e e-mails anteriormente protegidos continuarão acessíveis através da utilização de uma chave arquivada. No entanto, se tiver utilizadores com o Office 2010, [contacte o Suporte da Microsoft](../get-started/information-support.md#to-contact-microsoft-support) antes de executar estes procedimentos. Este computadores requerem passos de configuração adicionais.
> 
> Também pode [contactar o Suporte da Microsoft](../get-started/information-support.md#to-contact-microsoft-support) caso a sua organização disponha de políticas para processar chaves específicas.

### Pré-requisitos para o BYOK
Consulte a seguinte tabela para obter uma lista de pré-requisitos para o BYOK (Bring Your Own Key – Traga a Sua Própria Chave).

|Requisito|Mais informações|
|---------------|--------------------|
|Uma subscrição que suporta Azure RMS.|Para mais informações sobre as subscrições disponíveis, consulte [Subscrições na nuvem que suportam o Azure RMS](../get-started/requirements-subscriptions.md).|
|Não utilizar o RMS para utilizadores autónomos ou para o Exchange Online. Em alternativa, se utilizar o Exchange Online, compreender e aceitar as limitações da utilização do BYOK com esta configuração.|Para mais informações sobre as restrições e limitações atuais do BYOK, consulte [Preços e restrições do BYOK](byok-price-restrictions.md).<br /><br />**Importante**: o BYOK não é atualmente compatível com o Exchange Online.|
|Todos os pré-requisitos listados para BYOK do Cofre de Chaves.|Veja [Pré-requisitos para BYOK](https://azure.microsoft.com/documentation/articles/key-vault-hsm-protected-keys/#prerequisites-for-byok) na documentação do Cofre de Chaves do Azure. <br /><br />**Nota**: se estiver a migrar do AD RMS para o Azure RMS através da utilização de chave de software para chave de hardware, tem de ter uma versão de firmware da Thales igual ou posterior à 11.62.|
|O módulo de administração do Azure RMS para o Windows PowerShell.|Para obter instruções de instalação, consulte [Installing Windows PowerShell for Azure Rights Management (Instalar o Windows PowerShell para o Azure Rights Management – em inglês)](../deploy-use/install-powershell.md). <br /><br />Caso já tenha instalado este módulo do Windows PowerShell, execute o seguinte comando para verificar se o seu número de versão é **2.5.0.0** ou posterior: `(Get-Module aadrm -ListAvailable).Version`|

Para obter mais informações sobre HSMs da Thales e como são utilizados com o Cofre de Chaves do Azure, consulte o [site da Thales](https://www.thales-esecurity.com/msrms/cloud).

Para gerar e transferir a sua própria chave de inquilino para o Cofre de Chaves do Azure, siga os procedimentos em [Como gerar e transferir chaves protegidas por HSM para o Cofre de Chaves do Azure](https://azure.microsoft.com/documentation/articles/key-vault-hsm-protected-keys/) da documentação do Cofre de Chaves do Azure.

Quando a chave é transferida para o Cofre de Chaves, é fornecido um ID de chave no Cofre de Chaves, que é um URL que contém o nome do cofre, o contentor de chaves, o nome da chave e a versão da chave. Por exemplo: **https://contosorms-kv.vault.azure.net/keys/contosorms-byok/aaaabbbbcccc111122223333**. Terá de indicar ao Azure RMS para utilizar esta chave, especificando este URL.

No entanto, antes de o Azure RMS poder utilizar a chave, o Azure RMS tem de estar autorizado a utilizar a chave no cofre de chaves da sua organização. Para tal, o administrador do Cofre de Chaves do Azure utiliza o cmdlet PowerShell do Cofre de Chaves, [Set-AzureRmKeyVaultAccessPolicy](https://msdn.microsoft.com/library/mt603625.aspx) e concede permissões ao principal do serviço Azure RMS, **Microsoft.Azure.RMS**. Por exemplo:

    Set-AzureRmKeyVaultAccessPolicy -VaultName 'ContosoRMS-kv' -ResourceGroupName 'ContosoRMS-byok-rg' -ServicePrincipalName Microsoft.Azure.RMS -PermissionsToKeys decrypt,encrypt,unwrapkey,wrapkey,verify,sign 

Agora, está pronto para configurar o Azure RMS para utilizar esta chave como chave de inquilino do Azure RMS da sua organização. Utilizando os cmdlets do Azure RMS, ligue primeiro ao Azure RMS e inicie sessão:

    Connect-AadrmService

Em seguida, execute o [cmdlet Use-AadrmKeyVaultKey](https://msdn.microsoft.com/library/azure/mt759829.aspx) e especifique o URL da chave. Por exemplo:

    Use-AadrmKeyVaultKey -KeyVaultKeyUrl "https://contosorms-kv.vault.azure.net/keys/contosorms-byok/aaaabbbbcccc111122223333"

Se tiver de confirmar que o URL da chave está definido corretamente no Azure RMS, no Cofre de Chaves do Azure, pode executar [Get-AzureKeyVaultKey](https://msdn.microsoft.com/library/dn868053.aspx) para ver o URL da chave.


## Passos seguintes

Agora que já planeou e, se necessário, gerou a chave do inquilino, faça o seguinte:

1.  Comece a utilizar a sua chave de inquilino:

    -   Se ainda não o fez, tem agora de ativar o Rights Management para que a sua organização possa começar a utilizar o RMS. Os utilizadores começam a utilizar de imediato a sua chave de inquilino (gerida pela Microsoft ou por si no Cofre de Chaves do Azure).

        Para mais informações sobre a ativação, consulte [Ativar o Azure Rights Management](../deploy-use/activate-service.md).

    -   Se já tinha ativado o Rights Management e depois decidiu gerir a sua própria chave de inquilino, a transição dos utilizadores da chave de inquilino antiga para a nova chave de inquilino será efetuada gradualmente. A conclusão desta transição escalonada poderá demorar algumas semanas. Os documentos e ficheiros que foram protegidos com a chave de inquilino antiga permanecem acessíveis aos utilizadores autorizados.

2.  Pondere utilizar registos de utilização, que lhe permitem registar todas as transações efetuadas pelo Azure Rights Management.

    Se decidiu gerir a sua própria chave de inquilino, o registo incluirá informações sobre como utilizar a sua chave de inquilino. Veja o seguinte fragmento de um ficheiro de registo apresentado no Excel onde os tipos de pedido **KeyVaultDecryptRequest** e **KeyVaultSignRequest** mostram que a chave de inquilino está a ser utilizada.

    ![ficheiro de registo no Excel onde a chave de inquilino está a ser utilizada](../media/RMS_Logging.png)

    Para mais informações sobre o registo de utilização, consulte [Registo e análise da utilização do Azure Rights Management](../deploy-use/log-analyze-usage.md).

3.  Guarde a sua chave de inquilino.

    Para mais informações, consulte [Operações para a sua chave de inquilino do Azure Rights Management](../deploy-use/operations-tenant-key.md).




<!--HONumber=Sep16_HO1-->


