---
title: Instalar o cliente do Azure Information Protection | Azure Information Protection
description: "Instruções para instalar o cliente que adiciona uma barra de Proteção de Informações às suas aplicações do Office, para que possa selecionar etiquetas de classificação para documentos e e-mails."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 4445adff-4c5a-450f-aff8-88bf5bd4ca78
translationtype: Human Translation
ms.sourcegitcommit: 23c437479c756f2a9335606e686f117d514a38f6
ms.openlocfilehash: 71972b0a057b1958dfa5e5b4af41b65d5080a086


---

# <a name="installing-the-azure-information-protection-client"></a>Instalar o cliente do Azure Information Protection

>*Aplica-se a: Azure Information Protection*

Para classificar documentos e e-mails utilizando a Azure Information Protection, tem de instalar primeiro o cliente do Azure Information Protection. Esta instalação adiciona uma barra Information Protection às aplicações do Office (Word, Excel, PowerPoint e Outlook) que apresenta as etiquetas de classificação para a organização, para além de um novo grupo **Proteção** no separador **Base** (Word, Excel, PowerPoint), que tem um botão com o nome **Proteger**:

A imagem seguinte mostra a barra Information Protection e as etiquetas da [política predefinida](../deploy-use/configure-policy-default.md):

![Barra do Azure Information Protection com a política predefinida](../media/info-protect-bar-default.png)

Transfira o cliente do Azure Information Protection a partir do [Centro de Transferências da Microsoft](https://www.microsoft.com/en-us/download/details.aspx?id=53018). Atualmente, pode instalar a versão de Disponibilidade Geral (DG) e a versão de pré-visualização. A versão de pré-visualização inclui novas funcionalidades para fins de avaliação e está sujeita a alterações. Para obter mais informações, veja o seguinte anúncio de mensagem de blogue: [Azure Information Protection December preview now available (Pré-visualização de Dezembro do Azure Information Protection já disponível)](https://blogs.technet.microsoft.com/enterprisemobility/2016/12/07/azure-information-protection-december-preview-now-available/)

Antes de instalar o cliente, verifique se tem as versões de sistema operativo e as aplicações necessárias para o cliente do Azure Information Protection: [Requisitos do Azure Information Protection](../get-started/requirements-azure-rms.md). Além disso, para a versão de pré-visualização do cliente, os computadores a executar o Windows 7 SP1 necessitam da atualização [KB 2533623](https://support.microsoft.com/en-us/kb/2533623), que pode ser instalada após a instalação do cliente. Se esta atualização for necessária, mas não estiver instalada, ser-lhe-á pedido para a instalar.

## <a name="to-install-the-azure-information-protection-client-manually"></a>Para instalar o cliente do Azure Information Protection manualmente

1. Depois de ter [transferido o cliente](https://www.microsoft.com/en-us/download/details.aspx?id=53018), execute o ficheiro executável, tal como **AzInfoProtection.exe**, e siga as instruções para instalar o cliente. Esta instalação requer permissões administrativas locais.

    Selecione a opção para instalar uma política de demonstração se não puder ligar-se ao Office 365 ou ao Azure Active Directory e pretender ver e experimentar o lado do cliente do Azure Information Protection utilizando uma política local para efeitos de demonstração. Quando o cliente se liga a um serviço do Azure Information Protection, esta política de demonstração é substituída pela política do Azure Information Protection da organização. 

2. Para começar a utilizar o cliente do Azure Information Protection: se o computador executar o Office 2010, reinicie o computador. Para outras versões do Office, reinicie todas as aplicações do Office.

## <a name="to-install-the-azure-information-protection-client-for-users"></a>Para instalar o cliente do Azure Information Protection para os utilizadores

Pode executar scripts e automatizar a instalação do cliente do Azure Information Protection ao utilizar as opções da linha de comandos. Para ver as opções de instalação, execute o ficheiro executável com **/help**. Por exemplo: `AzInfoProtection.exe /help`.

Como instalar automaticamente o cliente: `AzInfoProtection.exe /passive | quiet`

A versão de disponibilidade geral do cliente Azure Information Protection também está incluída no catálogo Microsoft Update, pelo que pode instalar e atualizar o cliente com qualquer serviço de atualização de software que utilize o catálogo. As versões de pré-visualização do cliente não estão incluídas no catálogo Microsoft Update.

## <a name="to-uninstall-the-azure-information-protection-client"></a>Para instalar o cliente do Azure Information Protection

Pode utilizar uma das seguintes opções:

- Utilize o Painel de Controlo para desinstalar um programa: clique em **Microsoft Azure Information Protection** > **Desinstalar**

- Volte a executar o ficheiro executável (por exemplo, **AzInfoProtection.exe**) e, na página **Modificar Configuração**, clique em **Desinstalar**. 

- Execute o ficheiro executável com **/uninstall**. Por exemplo: `AzInfoProtection.exe /uninstall`


## <a name="to-verify-installation-connection-status-or-report-a-problem"></a>Para verificar a instalação, o estado da ligação ou comunicar um problema

1. Abra uma aplicação do Office, no separador **Base**, no grupo **Proteção**, clique em **Proteger** e, em seguida, clique em **Ajuda e feedback**.

2. Na caixa de diálogo **Microsoft Azure Information Protection**, tenha em consideração o seguinte:

    - Na secção **estado do cliente**: utilize o valor **Versão** para verificar que a instalação foi efetuada com êxito. Para além disso, pode ver quando é que o cliente se ligou ao serviço Azure Information Protection da sua organização pela última vez e quando é que a política do Azure Information Protection foi instalada ou atualizada pela última vez. Quando o cliente se liga ao serviço, é transferida automaticamente a política mais recente se forem detetadas alterações em relação à política atual. Se tiver efetuado alterações de política após a hora apresentada, feche e reabra a aplicação do Office.
    
        Também o seu nome de utilizador apresentado, que identifica a conta utilizada para o autenticar no Azure Information Protection. Este nome de utilizador tem de corresponder a uma conta que utiliza para o Office 365 ou o Azure Active Directory e que pertence a um inquilino configurado para o Azure Information Protection.

    - Na secção **Ajuda e feedback**: a **ligação Mais informações** direciona-o, por predefinição, para o site do [Azure Information Protection](https://www.microsoft.com/en-us/cloud-platform/azure-information-protection), mas pode ser configurada para um URL personalizado, de acordo com uma das [definições da política](../deploy-use/configure-policy-settings.md) da política do Azure Information Protection.
        
        Utilize a ligação **Enviar feedback** para anexar automaticamente os registos de cliente a um e-mail que pode ser enviado à equipa do Information Protection para investigar o problema. 
    
        Para ver as informações de diagnóstico e para repor o cliente, clique em **Executar diagnósticos**. Quando os testes de diagnóstico forem concluídos, clique em **Copiar Resultados** para colar as informações num e-mail que pode enviar em seguida para o seu apoio técnico ou para o suporte da Microsoft. Quando os testes forem concluídos, também pode repor o cliente.
        
        Mais informações acerca da opção **Repor**:
        
        - Não precisa de ser um administrador local para utilizar esta opção e esta ação não é registada no Visualizador de Eventos. 
        
        - A menos que os ficheiros estejam bloqueados, esta ação elimina todos os ficheiros existentes em **%localappdata%\Microsoft\MSIPC**, que é o local onde os certificados de cliente e os modelos de gestão de direitos estão armazenados. Não elimina a política do Azure Information Protection ou os ficheiros de registo de clientes nem termina a sessão do utilizador.
        
        - A chave de registo e definições seguintes são eliminadas: **HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC**. Caso configure definições para esta chave de registo (por exemplo, definições de redirecionamento para o seu inquilino do Azure Information Protection porque está a migrar do AD RMS e ainda tem um Ponto de Ligação de Serviço na sua rede), tem de voltar a configurar as definições de registo após efetuar a reposição do cliente.
        
        - Caso tenha efetuado a reposição do cliente, tem de reiniciar o ambiente do utilizador (também conhecido como "bootstrapping"), o que irá transferir para o cliente certificados e os modelos mais recentes. Para o fazer, feche todas as instâncias do Office e, em seguida, reinicie uma aplicação do Office. Esta ação também irá verificar se transferiu a política do Azure Information Protection mais recente. Não execute novamente os testes de diagnóstico até ter efetuado esta ação.


## <a name="usage-logging"></a>Registo de utilização

**[Esta funcionalidade requer a versão de pré-visualização do cliente e está sujeita a alterações.]**

Para a versão de pré-visualização do cliente do Azure Information Protection, o cliente regista a atividade do utilizador no registo de eventos locais **Aplicações e Serviços** do Windows, **Azure Information Protection**. Os eventos incluem as seguintes informações:

- Data, versão do cliente, ID de política

- Nome de utilizador da sessão iniciada, nome do computador

- Nome e localização do ficheiro

- Ação:

    - Definir Etiqueta: ID de Informações 101
    
    - Definir Etiqueta (inferior): ID de Informações 102
    
    - Definir Etiqueta (superior): ID de Informações 103
    
    - Remover etiqueta: ID de Informações 104
   
    - Sugestão recomendada: Informações 105
    
    - Aplicar proteção personalizada: ID de Informações 201
    
    - Remover proteção personalizada: ID de Informações 202
    
    - Início de Sessão (operacional): ID de informações 902
    
    - Transferir política (operacional): ID de informações 901
    
- Origem da ação:
    
    - Manual 
    
    - Recomendado
    
    - Automático  
    
    - Sistema (para iniciar sessão e transferir a política)
    
- Etiqueta antes e depois da ação 
    
- Proteção antes e depois da ação
    
- Justificação do utilizador (quando aplicável)
    

## <a name="keyboard-shortcuts-for-the-azure-information-protection-bar"></a>Atalhos de teclado da barra Azure Information Protection

Para aceder à barra Azure Information Protection através de atalhos de teclado, utilize a seguinte combinação de teclas:

- Prima **Ctrl** + **Shift** + **~** 

Em seguida, utilize a Tecla de Tabulação para selecionar as etiquetas e outros controlos na barra (o ícone **Ocultar etiquetas** e o ícone **Remover etiqueta**) e a tecla Enter para os selecionar.


## <a name="file-locations"></a>Localizações dos ficheiros

Ficheiros de cliente:   

- Para sistemas operativos de 64 bits: **\ProgramFiles (x86)\Microsoft Azure Information Protection**

- Para sistemas operativos de 32 bits: **\Program Files\Microsoft Azure Information Protection**

Ficheiros de registo de cliente e ficheiro da política atualmente instalada:

- Sistemas operativos de 64 bits e de 32 bits: **%localappdata%\Microsoft\MSIP**


## <a name="next-steps"></a>Passos seguintes

Para alterar as etiquetas na barra Information Protection, tem de configurar a política do Azure Information Protection. Para mais informações, consulte [configurar política do Azure Information Protection](../deploy-use/configure-policy.md).

Para obter um exemplo de como personalizar a política predefinida e ver o comportamento resultante de uma aplicação do Office, experimente o [Tutorial de inicio rápido do Azure Information Protection](../get-started/infoprotect-quick-start-tutorial.md).

para verificar as informações da versão de lançamento do cliente, consulte o [Histórico de lançamento de versões](client-version-release-history.md).



<!--HONumber=Dec16_HO1-->


