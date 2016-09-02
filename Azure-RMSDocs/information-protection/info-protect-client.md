---
title: Instalar o cliente do Azure Information Protection | Azure Rights Management
description: "Para classificar documentos e e-mails utilizando a Azure Information Protection, tem de instalar primeiro o cliente Azure Information Protection. Esta instalação adiciona uma barra Information Protection às aplicações do Office (Word, Excel, PowerPoint e Outlook) que apresenta as etiquetas de classificação da organização, para além de um novo grupo Proteção no separador Base (Word, Excel, PowerPoint), que tem um botão com o nome Proteger."
manager: mbaldwin
ms.date: 07/29/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 4445adff-4c5a-450f-aff8-88bf5bd4ca78
translationtype: Human Translation
ms.sourcegitcommit: c9f9211e7c1dcf293caf81475515114b5433d6a7
ms.openlocfilehash: ab8388e03803d32a6891785f905a1ddef796bc25


---

# Instalar o cliente do Azure Information Protection

>*Aplica-se a: pré-visualização do Azure Information Protection*

**[Estas informações são preliminares e estão sujeitas a alterações. ]**

Para classificar documentos e e-mails utilizando a Azure Information Protection, tem de instalar primeiro o cliente Azure Information Protection. Esta instalação adiciona uma barra Information Protection às aplicações do Office (Word, Excel, PowerPoint e Outlook) que apresenta as etiquetas de classificação para a organização, para além de um novo grupo **Proteção** no separador **Base** (Word, Excel, PowerPoint), que tem um botão com o nome **Proteger**:

A imagem seguinte mostra a barra Information Protection e as etiquetas da [política predefinida](configure-policy-default.md):

![Barra do Azure Information Protection com a política predefinida](../media/info-protect-bar-default.png)

Transfira o cliente Azure Information Protection a partir do [Centro de Transferências da Microsoft](https://www.microsoft.com/en-us/download/details.aspx?id=53018).

Antes de instalar o cliente, verifique se tem as versões de sistema operativo e as aplicações necessárias: [Requisitos do Azure Information Protection](requirements-azure-infoprotect.md).


## Para instalar o cliente Azure Information Protection manualmente

1. Depois de [ter transferido o cliente](https://www.microsoft.com/en-us/download/details.aspx?id=53018), execute o **AZInfoProtection.exe** e siga as instruções para instalar o cliente. Esta instalação requer permissões administrativas locais.

    Selecione a opção para instalar uma política de demonstração se não puder ligar-se ao Office 365 ou ao Azure Active Directory e pretender ver e experimentar o lado do cliente Azure Information Protection utilizando uma política local para efeitos de demonstração. Quando o cliente se liga a um serviço do Azure Information Protection, esta política de demonstração é substituída pela política do Azure Information Protection da organização. 

2. Para começar a utilizar o cliente Azure Information Protection: se o computador executar o Office 2010, reinicie o computador. Para outras versões do Office, reinicie todas as aplicações do Office.

## Para instalar o cliente Azure Information Protection para os utilizadores

- Pode criar scripts e automatizar a instalação do cliente Azure Information Protection empacotando o AZInfoProtection.exe e utilizando as [Opções de linha de comandos do Windows Installer (msiexec)](https://technet.microsoft.com/library/cc759262(v=ws.10).aspx).

    Por exemplo, se a versão empacotada que criar for denominada InfoProtect.msi e pretender instalar o cliente de forma silenciosa: `msiexec /qn InfoProtection.msi`


## Para instalar o cliente Azure Information Protection

- Utilize o Painel de Controlo para desinstalar um programa: clique em **Microsoft Azure Information Protection** > **Desinstalar**

## Para verificar a instalação, o estado da ligação ou comunicar um problema

1. Abra uma aplicação do Office, no separador **Base**, no grupo **Proteção**, clique em **Proteger** e, em seguida, clique em **Ajuda e comentários**.

2. Na caixa de diálogo **Microsoft Azure Information Protection**, tenha em consideração o seguinte:

    - O valor **Última ligação** identifica quando o cliente esteve ligado pela última vez ao serviço Azure Information Protection da organização. Quando o cliente se liga ao serviço, é transferida automaticamente a política mais recente se forem detetadas alterações em relação à política atual. Se tiver efetuado alterações de política após a hora apresentada, feche e reabra a aplicação do Office.

    - O nome de utilizador apresentado que identifica a conta utilizada para autenticá-lo no Azure Information Protection. Este nome de utilizador tem de corresponder à conta que utiliza para o Office 365 ou para o Azure Active Directory.

    - Versão do cliente Azure Information Protection.

    - A ligação **Enviar comentários** pode ser utilizada para anexar automaticamente os registos de cliente a um e-mail que pode ser enviado à equipa do Information Protection para investigação.

    - Ligação **Executar diagnósticos**: esta funcionalidade não está atualmente implementada.

## Localizações dos ficheiros

Ficheiros de cliente:   

- Para sistemas operativos de 64 bits: **\ProgramFiles (x86)\Microsoft Azure Information Protection**

- Para sistemas operativos de 32 bits: **\Program Files\Microsoft Azure Information Protection**

Ficheiros de registo de cliente e ficheiro da política atualmente instalada:

- Sistemas operativos de 64 bits e de 32 bits: **%localappdata%\Microsoft\MSIP**


## Passos seguintes

Para alterar as etiquetas na barra Information Protection, tem de configurar a política do Azure Information Protection. Para mais informações, consulte [configurar política do Azure Information Protection](configure-policy.md).

Para obter um exemplo de como personalizar a política predefinida e ver o comportamento resultante de uma aplicação do Office, experimente o [Tutorial de inicio rápido do Azure Information Protection](infoprotect-quick-start-tutorial.md). 



<!--HONumber=Aug16_HO4-->


