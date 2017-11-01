---
title: "Migrar do AD RMS para o Azure Information Protection – fase 2"
description: "Fase 2 da migração do AD RMS para o Azure Information Protection, que abrange os passos 4 a 6 de Migrar do AD RMS para o Azure Information Protection."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 10/31/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 5a189695-40a6-4b36-afe6-0823c94993ef
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: b65e3d803f94e6c8a494217e2a494c704640e5fc
ms.sourcegitcommit: 3952fc01c6182c143df7f0d2e748594e49bf1da8
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/01/2017
---
# <a name="migration-phase-2---server-side-configuration-for-ad-rms"></a>Fase 2 da migração – configuração do AD RMS do lado do servidor

>*Aplica-se a: Serviços de Gestão de Direitos do Active Directory, Azure Information Protection, Office 365*

Utilize as seguintes informações para a Fase 2 da migração do AD RMS para o Azure Information Protection. Estes procedimentos incluem os passos 4 a 6 de [Migrar do AD RMS para o Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md).


## <a name="step-4-export-configuration-data-from-ad-rms-and-import-it-to-azure-information-protection"></a>Passo 4: exportar os dados de configuração do AD RMS e importá-los para o Azure Information Protection
Este passo divide-se em duas partes:

1. Exportar os dados de configuração do AD RMS através da exportação dos domínios de publicação fidedignos (TPD) para um ficheiro. xml. Este processo é igual para todas as migrações.

2. Importar os dados de configuração para o Azure Information Protection. Existem diferentes processos para este passo consoante a configuração da implementação atual do AD RMS e a topologia preferida para a sua chave de inquilino do Azure RMS.

### <a name="export-the-configuration-data-from-ad-rms"></a>Exportar os dados de configuração do AD RMS

Efetue o seguinte procedimento em todos os clusters do AD RMS de todos os domínios de publicação fidedignos que possuem conteúdos protegidos da sua organização. Não precisa de executar este procedimento em clusters só de licenciamento.

#### <a name="to-export-the-configuration-data-trusted-publishing-domain-information"></a>Para exportar os dados de configuração (informações de domínio de publicação fidedigno)

1. Inicie sessão no cluster do AD RMS como utilizador com permissões de administração do AD RMS.

2. Na consola de gestão do AD RMS (**Serviços de Gestão de Direitos do Active Directory**), expanda o nome do cluster do AD RMS, expanda as **Políticas de Fidedignidade** e, em seguida, clique em **Domínios de Publicação Fidedignos**.

3. No painel de resultados, selecione o domínio de publicação fidedigno e, em seguida, no painel Ações, clique em **Exportar Domínio de Publicação Fidedigno**.

4. Na caixa de diálogo **Exportar Domínio de Publicação Fidedigno**:

    - Clique em **Guardar Como** e guarde no caminho e com um nome de ficheiro à sua escolha. Certifique-se de que especifica **. xml** a extensão de nome de ficheiro (esta não é acrescentada automaticamente).

    - Especifique e confirme uma palavra-passe segura. Lembre-se desta palavra-passe, dado que precisará dela mais tarde quando importar os dados de configuração para o Azure Information Protection.

    - Não marque a caixa de verificação para guardar o ficheiro de domínio fidedigno na versão 1.0 do RMS.

Após exportar todos os domínios de publicação fidedignos, estará pronto para iniciar a importação destes dados para o Azure Information Protection.

Tenha em atenção que os domínios de publicação fidedignos incluem as chaves do Certificado de Licenciante para Servidor (SLC) para desencriptar os ficheiros protegidos anteriormente, pelo que é importante que exporte (e depois importe para o Azure) todos os domínios de publicação fidedignos e não apenas o domínio atualmente ativo.

Por exemplo, terá vários domínios de publicação fidedignos se tiver atualizado os seus servidores do AD RMS do Modo Criptográfico 1 para o Modo Criptográfico 2. Se não exportar e importar o domínio de publicação fidedigno que contém a chave arquivada que utilizou o Modo Criptográfico 1, no final da migração, os utilizadores não poderão abrir o conteúdo que foi protegido com a chave do Modo Criptográfico 1.


### <a name="import-the-configuration-data-to-azure-information-protection"></a>Importar os dados de configuração para o Azure Information Protection
Os procedimentos exatos para este passo dependem da configuração da sua implementação atual do AD RMS e da topologia preferida para a sua chave de inquilino do Azure Information Protection.

A sua implementação atual do AD RMS utiliza uma das seguintes configurações para a sua chave do certificado de licenciante para servidor (SLC):

- Proteção por palavra-passe na base de dados do AD RMS. Esta é a configuração predefinida.

- Proteção HSM através da utilização de um módulo de hardware de segurança (HSM) da Thales.

- Proteção HSM através da utilização de um módulo de hardware de segurança (HSM) de um fornecedor diferente da Thales.

- Proteção por palavra-chave através de um fornecedor de serviços de criptografia externo.

> [!NOTE]
> Para obter mais informações sobre a utilização de módulos de hardware de segurança com o AD RMS, veja [Utilizar o AD RMS com Módulos de Hardware de Segurança](http://technet.microsoft.com/library/jj651024.aspx).

As duas opções de topologia de chaves de inquilino do Azure Information Protection estão relacionadas com o facto de a sua chave de inquilino poder ser gerida pela Microsoft (**gerida pela Microsoft**) ou por si (**gerida pelo cliente**) no Azure Key Vault. Quando gere a sua própria chave de inquilino do Azure Information Protection, é por vezes, referido como "traga a sua própria chave" (BYOK). Para obter mais informações, veja [Planear e implementar a sua chave de inquilino do Azure Information Protection](plan-implement-tenant-key.md).

Utilize a seguinte tabela para identificar o procedimento a utilizar para a sua migração. 

|Implementação atual do AD RMS|Topologia de chave de inquilino do Azure Information Protection selecionada|Instruções de migração|
|-----------------------------|----------------------------------------|--------------------------|
|Proteção por palavra-passe na base de dados do AD RMS|Gerida pela Microsoft|Consulte o procedimento de migração **Chave protegida por software para chave protegida por software** que se encontra após esta tabela.<br /><br />Este é o caminho de migração mais simples e requer apenas que transfira os seus dados de configuração para o Azure Information Protection.|
|Proteção HSM através da utilização de um módulo de hardware de segurança (HSM) nShield da Thales. |Gerida pelo cliente (BYOK)|Consulte o procedimento de migração **Chave protegida por HMS para chave protegida por HMS**  que se encontra após esta tabela.<br /><br />Este procedimento necessita do conjunto de ferramentas BYOK do Azure Key Vault e três conjuntos de passos para transferir primeiro a chave HSM no local para os HSMs do Azure Key Vault e, em seguida, autorizar o serviço Azure Rights Management a partir do Azure Information Protection para utilizar a sua chave de inquilino e, por último, transferir os dados de configuração para o Azure Information Protection.|
|Proteção por palavra-passe na base de dados do AD RMS|Gerida pelo cliente (BYOK)|Consulte o procedimento de migração **Chave protegida por software para chave protegida por HMS**  que se encontra após esta tabela.<br /><br />Este procedimento requer o conjunto de ferramentas BYOK do Azure Key Vault e quatro conjuntos de passos para, em primeiro lugar, extrair a sua chave de software e importá-la para um HSM no local, transferir a chave do seu HSM no local para os HSMs do Azure Information Protection, em seguida transferir os dados do Key Vault para o Azure Information Protection e, por último, transferir os dados de configuração para o Azure Information Protection.|
|Proteção HSM através da utilização de um módulo de hardware de segurança (HSM) a partir de um fornecedor que não seja a Thales |Gerida pelo cliente (BYOK)|Contacte o seu fornecedor do HSM para obter instruções sobre como transferir a chave deste HSM para um módulo de hardware de segurança (HSM) nShield da Thales. Em seguida, siga as instruções do procedimento de migração **Chave protegida por HMS para chave protegida por HMS** que se encontram após esta tabela.|
|Proteção por palavra-passe através de um fornecedor de serviços de criptografia externo|Gerida pelo cliente (BYOK)|Contacte o seu fornecedor de serviços de criptografia para obter instruções sobre como transferir a sua chave para um módulo de hardware de segurança (HSM) nShield da Thales. Em seguida, siga as instruções do procedimento de migração **Chave protegida por HMS para chave protegida por HMS** que se encontram após esta tabela.|

Se tiver uma chave protegida por HMS que não pode exportar, ainda pode migrar para o Azure Information Protection ao configurar o seu cluster do AD RMS para o modo só de leitura. Neste modo, continua a poder abrir os conteúdos anteriormente protegidos, mas os conteúdos protegidos recentemente utilizam uma nova chave de inquilino gerida por si (BYOK) ou pela Microsoft. Para obter mais informações, veja [An update is available for Office to support migrations from AD RMS to Azure RMS](https://support.microsoft.com/help/4023955/an-update-is-available-for-office-to-support-migrations-from-ad-rms-to) (Está disponível uma atualização do Office para suportar migrações do AD RMS para o Azure RMS).

Antes de começar estes procedimentos de migração de chaves, certifique-se de que consegue aceder aos ficheiros. xml que criou anteriormente, quando exportou os domínios de publicação fidedignos. Estes poderão estar guardados, por exemplo, numa pen USB que pode ser movida do servidor do AD RMS para uma estação de trabalho com ligação à Internet.

> [!NOTE]
> Independentemente da forma como guarda estes ficheiros, siga os procedimentos de segurança recomendados para os proteger, uma vez que estes dados incluem a sua chave privada.

Para concluir o Passo 4, escolha e selecione as instruções para o seu caminho de migração: 

- [Chave protegida por software para chave protegida por software](migrate-softwarekey-to-softwarekey.md)
- [Chave protegida por HSM para chave protegida por HSM](migrate-hsmkey-to-hsmkey.md)
- [Chave protegida por software para chave protegida por HSM](migrate-softwarekey-to-hsmkey.md)

## <a name="step-5-activate-the-azure-rights-management-service"></a>Passo 5: ativar o serviço Azure Rights Management

Abra uma sessão do PowerShell e execute os seguintes comandos:

1. Ligue ao serviço Azure Rights Management e quando lhe for pedido, especifique as credenciais de administrador global:
    
        Connect-Aadrmservice

2. Ative o serviço Azure Rights Management:
    
        Enable-Aadrm

**E se o seu inquilino do Azure Information Protection já estiver ativado?** Se o serviço Azure Rights Management já se encontra ativado para a sua organização e criou modelos personalizados que pretende utilizar após a migração, tem de exportar e importar estes modelos. Este procedimento é descrito no passo seguinte. 

## <a name="step-6-configure-imported-templates"></a>Passo 6: configurar modelos importados

Como os modelos que importou estão predefinidos para o estado **Arquivado**, tem de alterar este estado para **Publicado** se quiser que os utilizadores possam utilizar estes modelos com o Azure Rights Management.

Os modelos que importa do AD RMS parecer e comportar-se, tal como modelos personalizados que pode criar no portal do Azure. Para alterar modelos importados a publicar para que os utilizadores possam ver e selecionar a partir de aplicações, consulte [configurar e gerir modelos do Azure Information Protection](../deploy-use/configure-policy-templates.md).

Para além da publicação de modelos recentemente importados, existem apenas duas alterações importantes para os modelos que poderá ter de fazer antes de continuar com a migração. Para que os utilizadores tenham uma experiência mais consistente durante o processo de migração, não faça alterações adicionais aos modelos importados, não publique os dois modelos predefinidos do Azure Information Protection nem crie novos modelos nesta altura. Em alternativa, aguarde até que o processo de migração esteja concluído e que tenha desaprovisionado os servidores do AD RMS.

As alterações de modelo que poderá ter de fazer para este passo:

- Se criou modelos personalizados no Azure Information Protection antes da migração, tem de os exportar e importar manualmente.

- Se os modelos no AD RMS utilizavam o **ANYONE** grupo, poderá ter de adicionar utilizadores ou grupos a partir de fora da sua organização. 
    
    No AD RMS, o grupo qualquer pessoa direitos para todos os utilizadores autenticados. Este grupo é automaticamente convertido em todos os utilizadores no seu inquilino do Azure AD. Se não pretender conceder direitos para os utilizadores adicionais, é necessária nenhuma ação adicional. Mas se estava a utilizar o grupo ANYONE para incluir utilizadores externos, tem de adicionar manualmente estes utilizadores e os direitos que pretende conceder-lhes.

### <a name="procedure-if-you-created-custom-templates-before-the-migration"></a>Procedimento se criou modelos personalizados antes da migração

Se tiver criado modelos personalizados antes da migração, antes ou depois de ativar o serviço Azure Rights Management, os modelos não estarão disponíveis para os utilizadores após a migração, mesmo que tenham sido definidos como **Publicado**. Para que fiquem disponíveis para os utilizadores, tem primeiro de: 

1. Identificar estes modelos e anotar o ID de modelo executando [Get-AadrmTemplate](/powershell/aadrm/vlatest/get-aadrmtemplate). 

2. Exportar os modelos utilizando o cmdlet do PowerShell do Azure RMS, [Export-AadrmTemplate](/powershell/aadrm/vlatest/export-aadrmtemplate).

3. Exportar os modelos utilizando o cmdlet do PowerShell do Azure RMS, [Import-AadrmTemplate](/powershell/aadrm/vlatest/Import-AadrmTpd).

Em seguida, pode publicar ou arquivar estes modelos como faria com qualquer modelo criado após a migração.

### <a name="procedure-if-your-templates-in-ad-rms-used-the-anyone-group"></a>Procedimento se os modelos no AD RMS utilizavam o grupo **ANYONE**

Se os modelos no AD RMS utilizavam o **ANYONE** grupo, este grupo é automaticamente convertido para utilizar o grupo com o nome **AllStaff-7184AB3F-CCD1-46F3-8233-3E09E9CF0E66@\<nome_de_inquilino >. onmicrosoft.com**. Por exemplo, para a Contoso, este grupo poderá ser semelhante ao seguinte: **AllStaff-7184AB3F-CCD1-46F3-8233-3E09E9CF0E66@contoso.onmicrosoft.com**. Este grupo contém todos os utilizadores do seu inquilino do Azure AD.

Quando gere modelos e as etiquetas no portal do Azure, este grupo é apresentado como nome de domínio do seu inquilino no Azure AD. Por exemplo, este grupo aspeto que poderá ter o seguinte procedimento para Contoso: **contoso.onmicrosoft.com**. Para adicionar este grupo, a opção apresenta **adicionar \<nome da organização >-todos os membros**.

Se não tiver a certeza se os seus modelos do AD RMS incluem o grupo ANYONE, pode utilizar o script de exemplo do Windows PowerShell para identificar estes modelos. Para obter mais informações sobre como utilizar o Windows PowerShell com o AD RMS, consulte [utilizando o Windows PowerShell para administrar o AD RMS](https://technet.microsoft.com/library/ee221079%28v=ws.10%29.aspx).

Pode facilmente adicionar utilizadores externos para modelos quando converter estes modelos para etiquetas no portal do Azure. Em seguida, no **adicionar permissões** painel, escolha **Introduza detalhes** especificar manualmente os endereços de e-mail para estes utilizadores. 

Para obter mais informações sobre esta configuração, consulte [como configurar uma etiqueta para a proteção Rights Management](../deploy-use/configure-policy-protection.md).

#### <a name="sample-windows-powershell-script-to-identify-ad-rms-templates-that-include-the-anyone-group"></a>Script de exemplo do Windows PowerShell para identificar modelos do AD RMS que incluem o grupo ANYONE
Esta secção contém o script de exemplo para ajudar a identificar os modelos de AD RMS com o grupo ANYONE definido, conforme descrito na secção anterior.

**Exclusão de responsabilidade:** este script de exemplo não é suportado por nenhum serviço ou programa de suporte padrão da Microsoft. Este script de exemplo é fornecido TAL COMO ESTÁ, sem qualquer tipo de garantia.

```
import-module adrmsadmin 

New-PSDrive -Name MyRmsAdmin -PsProvider AdRmsAdmin -Root https://localhost -Force 

$ListofTemplates=dir MyRmsAdmin:\RightsPolicyTemplate

foreach($Template in $ListofTemplates) 
{ 
                $templateID=$Template.id

                $rights = dir MyRmsAdmin:\RightsPolicyTemplate\$Templateid\userright

     $templateName=$Template.DefaultDisplayName 

        if ($rights.usergroupname -eq "anyone")

                         {
                           $templateName = $Template.defaultdisplayname

                           write-host "Template " -NoNewline

                           write-host -NoNewline $templateName -ForegroundColor Red

                           write-host " contains rights for " -NoNewline

                           write-host ANYONE  -ForegroundColor Red
                         }
 } 
Remove-PSDrive MyRmsAdmin -force
```


## <a name="next-steps"></a>Próximos passos
Avance para a [fase 3 – configuração do lado do cliente](migrate-from-ad-rms-phase3.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]