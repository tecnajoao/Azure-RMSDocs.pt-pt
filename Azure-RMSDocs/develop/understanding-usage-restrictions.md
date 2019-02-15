---
title: Compreender as restrições de utilização | Azure RMS
description: Todas as aplicações com suporte RMS têm de impor restrições de utilização.
keywords: ''
author: bryanla
ms.author: bryanla
manager: barbkess
ms.date: 02/23/2017
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: E388B16C-ECDA-4696-A040-D457D3C96766
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: 5e62518965f2cea04b3b26df6a96646945567b9c
ms.sourcegitcommit: a78d4236cbeff743703c44b150e69c1625a2e9f4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/14/2019
ms.locfileid: "56257897"
---
# <a name="understanding-usage-restrictions"></a>Compreender as restrições de utilização

Todas as aplicações com suporte RMS têm de impor restrições de utilização. Uma restrição de utilização é uma condição que resulta quando um utilizador tenta executar uma ação (por exemplo, imprimir um documento), mas a política do RMS desse documento não lhes concede a permissão ou o direito de executar essa ação (por exemplo, o direito de IMPRIMIR).

As permissões de um utilizador num documento podem ser consultadas ao utilizar a função [IpcAccessCheck](https://msdn.microsoft.com/library/hh535253.aspx).

## <a name="designing-with-usage-restrictions"></a>Conceber com restrições de utilização

-   Familiarizar-se com os direitos padrão do RMS

    Para ver o conjunto completo de direitos do RMS que a sua aplicação pode impor, consulte [Referência das restrições de utilização](#usage-restriction-reference).

    Tenha em atenção que é possível criar direitos definidos para a aplicação específicos da sua situação e que vão para além dos direitos padrão do RMS.

-   Identificar pontos de imposição de restrições de utilização

    Um *ponto de imposição de restrição de utilização* é um local no fluxo de controlo da sua aplicação onde precisa de impor uma restrição de utilização. O tópico [Referência das restrições de utilização](#usage-restriction-reference) fornece vários exemplos de pontos de imposição comuns.

    Avalie a sua própria aplicação para determinar os pontos de imposição de restrições de utilização a aplicar.

    A sua aplicação pode não necessitar de todos os pontos de imposição descritos na [Referência das restrições de utilização](#usage-restriction-reference). Por exemplo, se a sua aplicação não permitir que os utilizadores imprimam conteúdo, não é necessário verificar o direito **IPC\_GENERIC\_PRINT**.

-   Atualizar o código para executar uma verificação de acesso em cada ponto de imposição

    Para obter orientações acerca de como impor direitos específicos, consulte [Referência das restrições de utilização](#usage-restriction-reference).

## <a name="usage-restriction-reference"></a>Referência das restrições de utilização

As restrições de utilização são definidas pelas seguintes constantes.

Cada direito de utilizador, listado na coluna da direita do AD RMS, tem uma descrição, um ponto de imposição e métodos de imposição sugeridos.

| Direito/descrição do AD RMS | Como impor |
|--------------------------|----------------|
|**IPC_GENERIC_ALL** <br><br> Concede todos os direitos ao utilizador. <br><br> **Pontos de Imposição Comuns**: Nenhum |Este direito é utilizado pelo sistema e geralmente não deve ser verificado diretamente. <br><br> [IpcAccessCheck](https://msdn.microsoft.com/library/hh535253.aspx) utiliza este direito para determinar se deve conceder ao utilizador outros direitos tal como neste exemplo.<br><br> `/* fAccessGranted is set to TRUE if either the IPC_GENERIC_WRITE or the IPC_GENERIC_ALL right is granted */` <br><br> `IpcAccessCheck(hKey, IPC_GENERIC_WRITE, &fAccessGranted);`|
|**IPC_GENERIC_READ** <br><br> O direito de ler o conteúdo de documentos. <br><br> **Pontos de Imposição Comuns**: Carregamento de documentos|Não carregar ou apresentar o conteúdo de documentos|
|**IPC_GENERIC_WRITE** <br><br> O direito de editar o conteúdo de documentos <br><br> **Pontos de Imposição Comuns**: Modificação de documentos|Torne os controlos de IU que possam ser utilizados para modificar o conteúdo de documentos não editáveis. <br><br> Desative quaisquer itens de menu que acionam alterações em documentos. **Editar** > **Cortar**, **Editar** > **Colar** e **Inserir** são exemplos típicos. <br><br>Desative quaisquer itens de menu de atalho que acionam alterações em documentos.|
|Nenhum direito do AD RMS <br><br> Sem descrição <br><br> **Pontos de Imposição Comuns**: Guardar | Desative o menu **Ficheiro** > **Guardar**. <br><br> **Nota:** este direito não controla o menu **Ficheiro** > **Guardar Como**, porque o direito não representa uma alteração ao documento original.<br><br> Desative qualquer atalho de teclado que possa ser utilizado para acionar uma gravação (por exemplo, Ctrl + G).<br><br> **Sugestão** Um procedimento recomendado é atualizar o seu código nuclear **Ficheiro** > **Guardar** para falhar caso o utilizador não tenha este direito. Isto funciona como uma rede de segurança se perder algum mecanismo UX que possa ser utilizado para acionar uma gravação. |
|**IPC_GENERIC_EXTRACT** <br><br> O direito de extrair conteúdo de um formato protegido e colocá-lo num formato não protegido. <br><br> **Pontos de Imposição Comuns**: Cópia para a área de transferência | Desative o menu **Editar** > **Copiar**. Desative o menu **Editar** > **Cortar**. <br><br>Desative **Copiar** e **Cortar** nos menus de atalho.<br><br>Desative qualquer atalho de teclado que possa ser utilizado para acionar uma cópia (por exemplo, Ctrl + C ou Ctrl + X).<br><br>Atualize os processadores de mensagens de janela para [**WM_CUT**](https://msdn.microsoft.com/library/ms649023) para rejeitar a cópia dos dados se o utilizador não tiver este direito. Se a janela estiver a utilizar o processador de mensagens fornecido pelo Windows predefinido, atribua esta janela a uma subclasse e forneça os seus próprios processadores para **WM_COPY** e **WM_CUT**. |
|Nenhum direito do AD RMS <br><br> Sem descrição <br><br> **Pontos de Imposição Comuns**: Guardar Como |Na caixa de diálogo **Guardar Como**, desative quaisquer formatos de ficheiro que possam fazer com que o documento seja guardado sem proteção do RMS.|
|Nenhum direito do AD RMS <br><br> Sem descrição <br><br> **Pontos de Imposição Comuns**: Alt+PrtScn|Chame [IpcProtectWindow](https://msdn.microsoft.com/library/hh535268.aspx) em todas as janelas que componham conteúdos de documentos.|
|**IPC_GENERIC_EXPORT** <br><br> O direito de extrair conteúdo de um formato protegido e colocá-lo num formato diferente protegido pelo AD RMS. <br><br> **Pontos de Imposição Comuns**: Guardar Como|Na sua caixa de diálogo **Guardar Como**, desative a capacidade de guardar noutros formatos de ficheiro.<br><br>**Sugestão**Um procedimento recomendado é atualizar o seu código nuclear **Ficheiro** > **Guardar Como** para falhar caso o utilizador tente guardar este ficheiro num formato diferente e não tenha este direito. Isto funciona como uma rede de segurança se perder algum mecanismo UX que possa ser utilizado para acionar um menu guardar como.|
|**IPC_GENERIC_PRINT** <br><br> O direito de imprimir conteúdo de documentos. <br><br> **Pontos de Imposição Comuns**: Imprimir|Desative o menu **Ficheiro** > **Imprimir**.<br><br>Desative qualquer atalho de teclado que possa ser utilizado para acionar uma impressão (por exemplo, Ctrl + P).<br><br>Desative os itens de menu de atalho que possam ser utilizados para acionar uma impressão.<br><br>**Sugestão** Um procedimento recomendado é atualizar o seu código nuclear **Ficheiro** > **Imprimir** para falhar caso o utilizador não tenha este direito. Isto funciona como uma rede de segurança se perder algum mecanismo UX que possa ser utilizado para acionar uma impressão.|
|**IPC_GENERIC_COMMENT** <br><br> Algumas aplicações suportam a capacidade de adicionar comentários e anotações ao documento sem atualizar o conteúdo nuclear de documentos.<br><br>Este direito concede ao utilizador o acesso a esta capacidade. <br><br> **Pontos de Imposição Comuns**: <br><br> Rever > Inserir comentário <br><br> Rever > Eliminar Comentário | Desative quaisquer itens de menu que possam ser utilizados para modificar os comentários ou as anotações do documento. **Rever** > **Inserir comentário** e **Rever** > **Eliminar Comentário** são exemplos. <br><br>Desative qualquer atalho de teclado que possa acionar a modificação de comentários do documento.<br><br>**Nota:** uma implementação predefinida requer o **IPC_GENERIC_COMMENT** e o **IPC_GENERIC_WRITE** para manter novos comentários num ficheiro. As aplicações podem optar por adicionar suporte para o caso onde o direito **IPC_GENERIC_COMMENT** é concedido e o direito **IPC_GENERIC_WRITE** não. Neste caso, é possível permitir Guardar, desde que as modificações a documentos estejam restritas apenas a comentários.|
|**IPC_VIEW_RIGHTS** <br><br> Sem descrição <br><br> **Pontos de Imposição Comuns**: N/A|Imposto pelo sistema. O sistema não permitirá que o programador consulte a [**lista de direitos de utilizador**](https://msdn.microsoft.com/library/hh535286.aspx) de uma licença, exceto se este direito estiver concedido.
|**IPC_EDIT_RIGHTS** <br><br> Algumas aplicações permitem que os utilizadores modifiquem o conjunto de utilizadores e os direitos para conteúdo protegido por AD RMS.<br><br>Este direito concede ao utilizador o acesso a esta capacidade. <br><br> **Pontos de Imposição Comuns**: Controlo de IU de edição de direitos de aplicações|Desative o acesso de utilizadores a qualquer IU que possa ser utilizada para editar a política de RMS de um documento.|


## <a name="related-topics"></a>Tópicos relacionados

* [IpcAccessCheck](https://msdn.microsoft.com/library/hh535253.aspx)
