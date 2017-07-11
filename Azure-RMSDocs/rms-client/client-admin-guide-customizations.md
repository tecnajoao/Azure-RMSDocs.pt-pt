---
title: "Configurações personalizadas do cliente do Azure Information Protection"
description: "Informações sobre a personalização do cliente do Azure Information Protection para Windows."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 05/23/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 5eb3a8a4-3392-4a50-a2d2-e112c9e72a78
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: 6ab5465db1527e6236d2dca466936c36b260f03d
ms.sourcegitcommit: 04eb4990e2bf0004684221592cb93df35e6acebe
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/30/2017
---
<a id="custom-configurations-for-the-azure-information-protection-client" class="xliff"></a>

# Configurações personalizadas do cliente do Azure Information Protection

>*Aplica-se a: Serviços de Gestão de Direitos do Active Directory, Azure Information Protection, Windows 10, Windows 8.1, Windows 8, Windows 7 with SP1, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012*

Utilize as seguintes informações para as configurações avançadas que poderá precisar para cenários específicos ou um subconjunto de utilizadores ao gerir o cliente do Azure Information Protection. 

<a id="prevent-sign-in-prompts-for-ad-rms-only-computers" class="xliff"></a>

## Impedir pedidos de início de sessão para computadores só com AD RMS

Por predefinição, o cliente do Azure Information Protection tenta automaticamente estabelecer ligação ao serviço Azure Information Protection. Para computadores que só comunicam com AD RMS, isto pode resultar num pedido desnecessário de início de sessão aos utilizadores. Pode impedir este pedido de início de sessão ao editar o registo:

Localize o nome do valor seguinte e, em seguida, defina os dados do valor como **0**:

**HKEY_CURRENT_USER\SOFTWARE\Microsoft\MSIP\EnablePolicyDownload** 

Independentemente desta definição, o cliente do Azure Information Protection segue o [processo de deteção do serviço RMS](../rms-client/client-deployment-notes.md#rms-service-discovery) padrão, para localizar o respetivo cluster AD RMS.

<a id="sign-in-as-a-different-user" class="xliff"></a>

## Iniciar sessão como um utilizador diferente

Num ambiente de produção, normalmente, os utilizadores não precisam de iniciar sessão como um utilizador diferente quando estão a utilizar o cliente do Azure Information Protection. No entanto, poderá ter de o fazer como administrador se tiver vários inquilinos. Por exemplo, tem um inquilino de teste além do inquilino do Office 365 ou do Azure que a sua organização utiliza.

Pode verificar com que conta tem sessão iniciada atualmente através da caixa de diálogo do **Microsoft Azure Information Protection**: abra uma aplicação do Office e, no separador **Base**, no grupo **Proteção**, clique em **Proteger** e, em seguida, clique em **Ajuda e comentários**. O nome da sua conta é apresentado na secção **Estado do cliente**.

Especialmente quando estiver a utilizar uma conta de administrador, verifique o nome de domínio da conta com sessão iniciada que é apresentada. Por exemplo, se tiver uma conta de administrador em dois inquilinos diferentes, pode não perceber que tem sessão iniciada com o nome da conta certo, mas com o domínio errado. Um sinal de tal engano pode ser a impossibilidade de transferir a política do Azure Information Protection ou não ver as etiquetas ou o comportamento esperado.

Para iniciar sessão como um utilizador diferente:

1. Com um editor de registo, navegue até **HKEY_CURRENT_USER\SOFTWARE\Microsoft\MSIP** e elimine o valor **TokenCache** (e os dados do valor associados).

2. Reinicie as aplicações do Office abertas e inicie sessão com a sua conta de utilizador diferente. Se não vir um pedido na aplicação do Office para iniciar sessão no serviço Azure Information Protection, volte à caixa de diálogo do **Microsoft Azure Information Protection** e clique em **Iniciar sessão** na secção **Estado do cliente** atualizada.

Além disso,

- Se estiver a utilizar o início de sessão único, terá de terminar sessão no Windows e iniciar sessão com a sua outra conta de utilizador após editar o registo. O cliente do Azure Information Protection fará a autenticação automaticamente através da conta de utilizador com sessão iniciada.

- Se pretender reinicializar o ambiente do serviço Azure Rights Management (também conhecido como arranque do sistema), pode fazê-lo através da opção **Repor** da [ferramenta RMS Analyzer](https://www.microsoft.com/en-us/download/details.aspx?id=46437).

- Se pretender eliminar a política do Azure Information Protection atualmente transferida, elimine o ficheiro **Policy.msip** da pasta **%localappdata%\Microsoft\MSIP**.

<a id="hide-the-classify-and-protect-menu-option-in-windows-file-explorer" class="xliff"></a>

## Ocultar a opção de menu Classificar e Proteger no Explorador de Ficheiros do Windows

Pode configurar esta configuração avançada ao editar o registo quando tiver a versão do cliente do Azure Information Protection 1.3.0.0 ou superior. 

Crie o nome do valor DWORD seguinte (com quaisquer dados do valor):

**HKEY_CLASSES_ROOT\AllFilesystemObjects\shell\Microsoft.Azip.RightClick\LegacyDisable**

<a id="support-for-disconnected-computers" class="xliff"></a>

## Suporte para computadores desligados

Por predefinição, o cliente do Azure Information Protection tenta automaticamente estabelecer ligação ao serviço Azure Information Protection para transferir a política do Azure Information Protection mais recente. Se tiver um computador que sabe que não poderá estabelecer ligação à Internet durante um período de tempo, poderá impedir o cliente de tentar estabelecer ligação ao serviço ao editar o registo. Localize o nome do valor seguinte e defina os dados do valor como **0**:

**HKEY_CURRENT_USER\SOFTWARE\Microsoft\MSIP\EnablePolicyDownload** 

Confirme se o cliente tem um ficheiro de política válido denominado **Policy.msip** na pasta **%localappdata%\Microsoft\MSIP**. Se necessário, pode exportar a política a partir do portal do Azure e copiar o ficheiro exportado para o computador cliente. Também pode utilizar este método para substituir um ficheiro de política desatualizada pela política publicada mais recente.

<a id="integration-with-exchange-message-classification-for-a-mobile-device-labeling-solution" class="xliff"></a>

## Integração com a classificação de mensagem do Exchange para uma solução de etiquetagem do dispositivo móvel

Embora o Outlook na Web ainda não ofereça suporte à proteção e à classificação do Azure Information Protection, pode utilizar a classificação de mensagem do Exchange para expandir as etiquetas do Azure Information Protection para os seus utilizadores móveis.

Para obter esta solução: 

1. Utilize o cmdlet [New-MessageClassification](https://technet.microsoft.com/library/bb124400) do Exchange PowerShell para criar classificações de mensagens com a propriedade Nome que mapeia os seus nomes de etiquetas na sua política do Azure Information Protection. 

2. Crie uma regra de transporte do Exchange para cada etiqueta: aplique a regra quando as propriedades da mensagem incluírem a classificação que configurou e modifique as propriedades das mensagens para definir um cabeçalho da mensagem. 

    Para o cabeçalho da mensagem, encontrará as informações a especificar ao inspecionar os cabeçalhos de Internet do e-mail que enviou e classificou com a etiqueta do Azure Information Protection. Procure o cabeçalho **msip_labels** e a cadeia que imediatamente a seguir, até ao ponto e vírgula, inclusive. Utilizando o exemplo anterior:
    
    **msip_labels: MSIP_Label_0e421e6d-ea17-4fdb-8f01-93a3e71333b8_Enabled=True;**
    
    Em seguida, para o cabeçalho da mensagem na regra, especifique **msip_labels** para o cabeçalho e a parte restante da cadeia para o valor do cabeçalho. Por exemplo:
    
    ![Exemplo de uma regra de transporte do Exchange Online que define o cabeçalho de mensagem de uma etiqueta específica do Azure Information Protection](../media/exchange-rule-for-message-header.png)

Antes de testar esta opção, lembre-se de que é frequente ocorrer um atraso ao criar ou editar regras de transporte (por exemplo, poderá ter de esperar uma hora). Quando a regra entrar em vigor, agora acontecerá o seguinte quando os utilizadores utilizarem o Outlook na Web ou um cliente para dispositivos móveis que suporte a proteção do Rights Management: 

- Os utilizadores selecionam a classificação de mensagens do Exchange e enviam o e-mail.

- A regra do Exchange deteta a classificação do Exchange e modifica o cabeçalho da mensagem em conformidade para adicionar a classificação do Azure Information Protection.

- Quando os destinatários que executam o cliente do Azure Information Protection veem o e-mail no Outlook, verão a etiqueta do Azure Information Protection atribuída e quaisquer cabeçalhos, rodapés ou marcas de água de e-mail correspondentes. 

Se as suas etiquetas do Azure Information Protection aplicarem a proteção da gestão de direitos, adicione esta opção à configuração da regra ao selecionar a opção para modificar a segurança da mensagem, aplique a proteção de direitos e, em seguida, selecione a opção Não Reencaminhar ou modelo do RMS.

Também pode configurar as regras de transporte para proceder ao mapeamento inverso: quando uma etiqueta do Azure Information Protection é detetada, é definida uma classificação de mensagens do Exchange correspondente. Para efetuar este procedimento:

- Para cada etiqueta do Azure Information Protection, crie uma regra de transporte que seja aplicada quando o cabeçalho **msip_labels** incluir o nome da sua etiqueta (por exemplo, **Geral**) e aplique uma classificação de mensagens que mapeie esta etiqueta.


<a id="next-steps" class="xliff"></a>

## Próximos passos
Agora que personalizou o cliente do Azure Information Protection, veja o seguinte para obter informações adicionais que poderá precisar para suportar este cliente:

- [Ficheiros de cliente e registo de utilização](client-admin-guide-files-and-logging.md)

- [Controlo de documentos](client-admin-guide-document-tracking.md)

- [Tipos de ficheiro suportados](client-admin-guide-file-types.md)

- [Comandos do PowerShell](client-admin-guide-powershell.md)


[!INCLUDE[Commenting house rules](../includes/houserules.md)]
