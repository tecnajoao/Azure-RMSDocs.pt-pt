---
title: Guia do administrador do cliente do Azure Information Protection
description: "Instruções e informações para administradores numa rede empresarial responsáveis por implementar o cliente do Azure Information Protection para o Windows."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 09/20/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 33a5982f-7125-4031-92c2-05daf760ced1
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: 96eb4a9fde5c5664a41ad7f68c550af697e8216f
ms.sourcegitcommit: 73973986ae7086e6f30cab579187241fd98bef61
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/21/2017
---
# <a name="azure-information-protection-client-administrator-guide"></a>Guia do administrador do cliente do Azure Information Protection

>*Aplica-se a: Serviços de Gestão de Direitos do Active Directory, Azure Information Protection, Windows 10, Windows 8.1, Windows 8, Windows 7 with SP1, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2*

Utilize as informações deste guia se for responsável pelo cliente do Azure Information Protection numa rede empresarial ou se pretender mais informações técnicas além das que estão no [Guia do utilizador do cliente do Azure Information Protection](client-user-guide.md). 

Por exemplo:

- Entender os diferentes componentes do cliente e se o deve instalar

- Como instalar o cliente para utilizadores, com informações sobre pré-requisitos, opções de instalação e parâmetros e verificações

- Como inserir configurações personalizadas que muitas vezes exigem a edição do registo

- Encontre os ficheiros de cliente e registos de utilização

- Identifique os tipos de ficheiro suportados pelo cliente

- Configure e utilize o site de controlo de documentos para os utilizadores

- Utilize o cliente com o PowerShell para controlo de linha de comandos

**Tem uma pergunta que não foi respondida nesta documentação?** Visite o nosso [site Yammer do Azure Information Protection](https://www.yammer.com/AskIPTeam). 

## <a name="technical-overview-of-the-azure-information-protection-client"></a>Descrição geral técnica sobre o cliente do Azure Information Protection

O cliente do Azure Information Protection inclui o seguinte:

- Um suplemento Office, que instala a barra do Azure Information Protection aos utilizadores selecionar etiquetas de classificação, e um **proteger** botão no friso para obter opções adicionais. Para o Outlook, um **não reencaminhar** botão também é adicionado ao Friso.

- Opções de clique com o botão direito do rato do Explorador de Ficheiros do Windows para os utilizadores aplicarem etiquetas de classificação e proteção a ficheiros.

- Um visualizador para apresentar ficheiros protegidos quando uma aplicação nativa não consegue abri-los.

- Um módulo do PowerShell para aplicar e remover etiquetas de classificação e proteção de ficheiros. 
    
    Este módulo inclui cmdlets para instalar e configurar o [scanner do Azure Information Protection](../deploy-use/deploy-aip-scanner.md) (atualmente em pré-visualização) que é executado como um serviço no Windows Server. Este serviço permite-lhe detetar, classificar e proteger os ficheiros nos arquivos de dados, como partilhas de rede e de bibliotecas do SharePoint Server.

- O cliente do Rights Management que comunica com o Azure Rights Management (Azure RMS) ou os Serviços de Gestão de Direitos do Active Directory (AD RMS).

O cliente do Azure Information Protection é mais adequado para funcionar com os respetivos serviços do Azure; o Azure Information Protection e o respetivo serviço de proteção de dados, o Azure Rights Management. No entanto, com algumas limitações, o cliente do Azure Information Protection também funciona com a versão no local do Rights Management, o AD RMS. Para ver uma comparação detalhada das funcionalidades suportadas pelo Azure Information Protection e pelo AD RMS, veja [Comparar o Azure Information Protection e o AD RMS](../understand-explore/compare-azure-rms-ad-rms.md). 

Se tiver o AD RMS e quiser migrar para o Azure Information Protection, veja [Migrar do AD RMS para o Azure Information Protection](../plan-design/migrate-from-ad-rms-to-azure-rms.md).


## <a name="should-you-deploy-the-azure-information-protection-client"></a>Deve implementar o cliente do Azure Information Protection?

Implemente o cliente do Azure Information Protection no caso de se aplicar alguma das seguintes condições:

- Quer classificar (e, opcionalmente, proteger) documentos e e-mails ao selecionar etiquetas a partir das suas aplicações do Office (Word, Excel, PowerPoint, Outlook).

- Quer classificar (e, opcionalmente, proteger) documentos e e-mails através do Explorador de Ficheiros, que suporta outros tipos de ficheiro, a seleção múltipla e as pastas.

- Quer executar scripts que classificam (e, opcionalmente, protegem) documentos ao utilizar comandos do PowerShell.

- Pretende executar um serviço que Deteta, classifica (e, opcionalmente, protege) ficheiros que estão armazenados no local. Este serviço de scanner está atualmente em pré-visualização.

- Quer ver documentos protegidos quando uma aplicação nativa para apresentar o ficheiro não está instalada ou não consegue abrir estes documentos.

- Quer apenas proteger os ficheiros através do Explorador de Ficheiros ou através de comandos do PowerShell.

- Quer que os utilizadores e os administradores possam monitorizar e revogar documentos protegidos.

- Quer remover a encriptação dos ficheiros e contentores (desproteger) em massa para fins de recuperação de dados.

- Utiliza o Office 2010 e quer proteger documentos e e-mails através do serviço Azure Rights Management.

O exemplo que mostra o cliente Azure Information Protection suplemento para uma aplicação do Office, que apresenta as etiquetas de classificação para a sua organização e a nova **proteger** botão no Friso:

![Barra do Azure Information Protection com a política predefinida](../media/word2016-calloutsv2.png)

## <a name="installing-and-supporting-the-azure-information-protection-client"></a>Instalar e que suportam o cliente Azure Information Protection

Pode instalar o cliente Azure Information Protection utilizando o Windows Update, um executável ou um ficheiro do Windows installer. Para obter mais informações sobre cada opção e instruções, consulte [instalar o cliente Azure Information Protection para os utilizadores](client-admin-guide-install.md).  

Utilize as secções seguintes para informações sobre como instalar o cliente de suporte. 

### <a name="installation-checks-and-troubleshooting"></a>Verificações de instalação e a resolução de problemas

Quando o cliente é instalado, utilize o **ajuda e comentários** opção para abrir o **Microsoft Azure Information Protection** caixa de diálogo:

- A partir de uma aplicação do Office: no separador **Base**, no grupo **Proteção**, clique em **Proteger** e, em seguida, selecione **Ajuda e Feedback**.

- No Explorador de Ficheiros: selecione com o botão direito do rato um ficheiro, ficheiros ou pasta, selecione **Classificar e proteger** e, em seguida, selecione **Ajuda e Feedback**. 

#### <a name="help-and-feedback-section"></a>Secção **Ajuda e Feedback**

A **ligação Mais informações** direciona-o, por predefinição, para o site do [Azure Information Protection](https://www.microsoft.com/cloud-platform/azure-information-protection), mas pode configurá-la para um URL personalizado, de acordo com uma das [definições da política](../deploy-use/configure-policy-settings.md) da política do Azure Information Protection.

Utilize a ligação **Enviar Comentários** para enviar pedidos ou sugestões para a equipa do Information Protection. Não utilize esta opção para o suporte técnico e, em vez disso, veja [Opções de suporte e recursos da comunidade](../get-started/information-support.md#support-options-and-community-resources). 

**Exportar Registos** recolhe e anexa automaticamente ficheiros de registo para o cliente de Azure Information Protection se lhe tiver sido pedido para os enviar ao Suporte da Microsoft. Esta opção também serve para os utilizadores finais enviarem estes ficheiros de registo ao suporte técnico.

O **repor definições** termina a sessão do utilizador, elimina a política do Azure Information Protection atualmente transferida e repõe as definições de utilizador para o serviço Azure Rights Management.

##### <a name="more-information-about-the-reset-settings-option"></a>Obter mais informações sobre a opção Repor definições

- Não precisa de ser um administrador local para utilizar esta opção e esta ação não é registada no Visualizador de Eventos. 

- A menos que os ficheiros estejam bloqueados, esta ação elimina todos os ficheiros nas seguintes localizações. Estes ficheiros incluem certificados de cliente, modelos do Rights Management, a política do Azure Information Protection e as credenciais de utilizador em cache. Não são eliminados os ficheiros de registo de cliente.
    
    - %LocalAppData%\Microsoft\DRM
    
    - %LocalAppData%\Microsoft\MSIPC
    
    - %LocalAppData%\Microsoft\MSIP\Policy.msip
    
    - %LocalAppData%\Microsoft\MSIP\TokenCache

- As seguintes chaves do registo e definições são eliminadas. Se tiver configurado definições para alguma destas chaves do registo, terá de as reconfigurar após efetuar a reposição do cliente. Por exemplo, configurou as definições de forma a redirecionar para o seu inquilino do Azure Information Protection porque está a migrar a partir do AD RMS e ainda tem um Ponto de Ligação de Serviço na sua rede:
    
    - HKEY_CURRENT-USER\SOFTWARE\Microsoft\Office\15.0\Common\Identity
    
    - HKEY_CURRENT-USER\SOFTWARE\Microsoft\Office\14.0\Common\DRM
    
    - HKEY_CURRENT-USER\SOFTWARE\Microsoft\Office\15.0\Common\DRM
    
    - HKEY_CURRENT-USER\SOFTWARE\Microsoft\Office\16.0\Common\DRM
    
    - HKEY_CURRENT-USER\SOFTWARE\Classes\Local Settings\Software\Microsoft\MSIPC    

- É terminada a sessão do utilizador com sessão iniciada atualmente.

#### <a name="client-status-section"></a>Secção **Estado de cliente**

Utilize o valor **Ligado como** para confirmar que o nome de utilizador apresentado identifica a conta a ser utilizada para autenticação do Azure Information Protection. Este nome de utilizador tem de corresponder a uma conta utilizada no Office 365 ou no Azure Active Directory. A conta também tem de pertencer a um inquilino configurado para o Azure Information Protection.

Se precisar de iniciar sessão como um utilizador diferente do apresentado, veja a personalização [Iniciar sessão como um utilizador diferente](client-admin-guide-customizations.md#sign-in-as-a-different-user).

A **Última ligação** mostra quando o cliente esteve ligado pela última vez ao serviço Azure Information Protection da organização. Pode utilizar esta informação com a data e hora apresentada em **A política do Information Protection foi instalada a** para confirmar quando foi a última vez em que a política do Azure Information Protection foi instalada ou atualizada. Quando o cliente se liga ao serviço, será transferida automaticamente a política mais recente se forem detetadas alterações em relação à política atual e, também, a cada 24 horas. Se tiver efetuado alterações de política após a hora apresentada, feche e reabra a aplicação do Office.

Se vir **O cliente não está licenciado para o Office Professional Plus**: significa que o cliente do Azure Information Protection detetou que a edição instalada do Office não suporta a aplicação da proteção Rights Management. Quando esta deteção é feita, as etiquetas que aplicam a proteção não são apresentadas na barra do Azure Information Protection.

Utilize as informações da **Versão** para confirmar que versão do cliente está instalada. Pode verificar se esta é a versão mais recente, bem como as correções correspondentes e as novas funcionalidades, ao clicar na ligação **Novidades**, para ler o [Histórico do Lançamento de Versões](client-version-release-history.md) do cliente.

## <a name="support-for-multiple-languages"></a>Suporte para múltiplos idiomas

O cliente Azure Information Protection suporta os mesmos idiomas de que suporta o Office 365. Para obter uma lista destas linguagens, consulte o **do Office 365, Exchange Online Protection e o Power BI** secção o [disponibilidade internacional](https://products.office.com/business/international-availability) página do Office.

Estes idiomas, opções de menu, caixas de diálogo e mensagens do Azure Information Protection cliente apresentado no idioma do utilizador. Não há um programa de instalação único que Deteta a linguagem de, pelo que não é necessária nenhuma configuração adicional para instalar o cliente Azure Information Protection para idiomas diferentes. 

No entanto, a etiqueta nomes e descrições que especificou não são convertidas automaticamente quando configurar as etiquetas na política do Azure Information Protection. A partir de 30 de Agosto de 2017, atual [política predefinida](../deploy-use/configure-policy-default.md) inclui suporte para alguns idiomas. Para os utilizadores vejam as etiquetas no respetivo idioma preferencial, fornecem as suas próprias traduções e configure a política do Azure Information Protection para utilizar estes traduções. Para obter mais informações, veja [Como configurar etiquetas para diferentes idiomas no Azure Information Protection](../deploy-use/configure-policy-languages.md). Marcas visuais não são convertidos e não suportam mais do que um idioma.

## <a name="uninstalling-the-azure-information-protection-client"></a>Desinstalar o cliente Azure Information Protection

Pode utilizar qualquer uma das seguintes opções para desinstalar o cliente:

- Utilize o Painel de Controlo para desinstalar um programa: clique em **Microsoft Azure Information Protection** > **Desinstalar**

- Volte a executar o ficheiro executável (por exemplo, **AzInfoProtection.exe**) e, na página **Modificar Configuração**, clique em **Desinstalar**. 

- Execute o ficheiro executável com **/uninstall**. Por exemplo: `AzInfoProtection.exe /uninstall`

## <a name="next-steps"></a>Próximos passos
Para instalar o cliente, consulte [instalar o cliente Azure Information Protection para os utilizadores](client-admin-guide-install.md).

Se já tiver instalado o cliente, consulte o seguinte para obter informações adicionais que poderá ter para suportar este cliente:

- [Personalizações](client-admin-guide-customizations.md)

- [Ficheiros de cliente e registo de utilização](client-admin-guide-files-and-logging.md)

- [Controlo de documentos](client-admin-guide-document-tracking.md)

- [Tipos de ficheiro suportados](client-admin-guide-file-types.md)

- [Comandos do PowerShell](client-admin-guide-powershell.md)


[!INCLUDE[Commenting house rules](../includes/houserules.md)]
