---
# required metadata

title: Referência das restrições de utilização | Azure RMS
description: As restrições de utilização são definidas pelas constantes listadas neste tópico.
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 16E36039-0FD6-4A0A-82C8-2C9DB19D27DD
# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Referência das restrições de utilização

As restrições de utilização são definidas pelas constantes listadas neste tópico.



Cada direito de utilizador, listado na coluna da direita do AD RMS, tem uma descrição, um ponto de imposição e métodos de imposição sugeridos.

| Direito do AD RMS | Descrição | Pontos de Imposição Comuns | Como Impor |
|--------------|-------------|---------------------------|----------------|
|IPC_GENERIC_ALL |Concede todos os direitos ao utilizador.| Nenhum |Este direito é utilizado pelo sistema e geralmente não deve ser verificado diretamente. <br><br> [**IpcAccessCheck**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcaccesscheck) utiliza este direito para determinar se deve conceder ao utilizador outros direitos tal como neste exemplo.<br><br> `/* fAccessGranted is set to TRUE if either the IPC_GENERIC_WRITE or the IPC_GENERIC_ALL right is granted */` <br><br> `IpcAccessCheck(hKey, IPC_GENERIC_WRITE, &fAccessGranted);`
|IPC_GENERIC_READ |O direito de ler o conteúdo de documentos.|Carregamento de documentos|Não carregar ou apresentar o conteúdo de documentos|
|IPC_GENERIC_WRITE|O direito de editar o conteúdo de documentos|Modificação de documentos|Torne os controlos de IU que possam ser utilizados para modificar o conteúdo de documentos não editáveis. <br><br> Desative quaisquer itens de menu que acionam alterações em documentos. **Editar** > **Cortar**, **Editar** > **Colar** e **Inserir** são exemplos típicos. <br><br>Desative quaisquer itens de menu de atalho que acionam alterações em documentos.|
|Nenhum direito do AD RMS|O chamador não tem direitos do AD RMS|Guardar|Desative o menu **Ficheiro** > **Guardar**. <br><br> **Nota** Este direito não controla o menu **Ficheiro** > **Guardar Como**, porque o direito não representa uma alteração ao documento original.<br><br> Desative qualquer atalho de teclado que possa ser utilizado para acionar uma gravação (por exemplo, Ctrl + G).<br><br> **Sugestão** Um procedimento recomendado é atualizar o seu código nuclear **Ficheiro** > **Guardar** para falhar caso o utilizador não tenha este direito. Isto funciona como uma rede de segurança se perder algum mecanismo UX que possa ser utilizado para acionar uma gravação.
|IPC_GENERIC_EXTRACT|O direito de extrair conteúdo de um formato protegido e colocá-lo num formato não protegido.|Cópia para a área de transferência|Desative o menu **Editar** > **Copiar**. Desative o menu **Editar** > **Cortar**. <br><br>Desative **Copiar** e **Cortar** nos menus de atalho.<br><br>Desative qualquer atalho de teclado que possa ser utilizado para acionar uma cópia (por exemplo, Ctrl + C ou Ctrl + X).<br><br>Atualize os processadores de mensagens de janela para [**WM_CUT**](https://msdn.microsoft.com/library/windows/desktop/ms649023) para rejeitar a cópia dos dados se o utilizador não tiver este direito. Se a janela estiver a utilizar o processador de mensagens fornecido pelo Windows predefinido, atribua esta janela a uma subclasse e forneça os seus próprios processadores para **WM_COPY** e **WM_CUT**.
|Nenhum direito do AD RMS|O chamador não tem direitos do AD RMS|Guardar Como|Na caixa de diálogo **Guardar Como**, desative quaisquer formatos de ficheiro que possam fazer com que o documento seja guardado sem proteção do RMS.|
|Nenhum direito do AD RMS|O chamador não tem direitos do AD RMS|Alt+PrtScn|Chame [**IpcProtectWindow**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcprotectwindow) em todas as janelas que componham conteúdo de documentos.|
|IPC_GENERIC_EXPORT|O direito de extrair conteúdo de um formato protegido e colocá-lo num formato diferente protegido pelo AD RMS.|Guardar Como|Na sua caixa de diálogo **Guardar Como**, desative a capacidade de guardar noutros formatos de ficheiro.<br><br>**Sugestão**Um procedimento recomendado é atualizar o seu código nuclear **Ficheiro** > **Guardar Como** para falhar caso o utilizador tente guardar este ficheiro num formato diferente e não tenha este direito. Isto funciona como uma rede de segurança se perder algum mecanismo UX que possa ser utilizado para acionar um menu guardar como.|
|IPC_GENERIC_PRINT|O direito de imprimir conteúdo de documentos.|Imprimir|Desative o menu **Ficheiro** > **Imprimir**.<br><br>Desative qualquer atalho de teclado que possa ser utilizado para acionar uma impressão (por exemplo, Ctrl + P).<br><br>Desative os itens de menu de atalho que possam ser utilizados para acionar uma impressão.<br><br>**Sugestão** Um procedimento recomendado é atualizar o seu código nuclear **Ficheiro** > **Imprimir** para falhar caso o utilizador não tenha este direito. Isto funciona como uma rede de segurança se perder algum mecanismo UX que possa ser utilizado para acionar uma impressão.|
|IPC_GENERIC_COMMENT|Algumas aplicações suportam a capacidade de adicionar comentários e anotações ao documento sem atualizar o conteúdo nuclear de documentos.<br><br>Este direito concede ao utilizador o acesso a esta capacidade.|Rever > Inserir comentário <br><br> Rever > Eliminar Comentário | Desative quaisquer itens de menu que possam ser utilizados para modificar os comentários ou as anotações do documento. **Rever** > **Inserir comentário** e **Rever** > **Eliminar Comentário** são exemplos. <br><br>Desative qualquer atalho de teclado que possa acionar a modificação de comentários do documento.<br><br>**Nota** Uma implementação predefinida requer o **IPC_GENERIC_COMMENT** e o **IPC_GENERIC_WRITE** para manter novos comentários num ficheiro. As aplicações podem optar por adicionar suporte para o caso onde o direito **IPC_GENERIC_COMMENT** é concedido e o direito **IPC_GENERIC_WRITE** não. Neste caso, é possível permitir Guardar, desde que as modificações a documentos estejam restritas apenas a comentários.|
|IPC_VIEW_RIGHTS||N/D|Imposto pelo sistema. O sistema não permitirá que o programador consulte a [**lista de direitos de utilizador**](/rights-management/sdk/2.1/api/win/structures#msipc_ipc_user_rights_list) de uma licença, exceto se este direito estiver concedido.
|IPC_EDIT_RIGHTS|Algumas aplicações permitem que os utilizadores modifiquem o conjunto de utilizadores e os direitos para conteúdo protegido por AD RMS.<br><br>Este direito concede ao utilizador o acesso a esta capacidade.|Controlo de IU de edição de direitos de aplicações|Desative o acesso de utilizadores a qualquer IU que possa ser utilizada para editar a política de RMS de um documento.|

 

 

 


<!--HONumber=May16_HO2-->

