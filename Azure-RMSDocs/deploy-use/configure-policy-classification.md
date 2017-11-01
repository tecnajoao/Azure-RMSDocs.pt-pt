---
title: "Configurar condições para uma etiqueta do Azure Information Protection"
description: "Quando configurar as condições para uma etiqueta, pode atribuir automaticamente uma etiqueta a um documento ou a um e-mail. Em alternativa, pode pedir aos utilizadores que selecionem a etiqueta recomendada."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 10/23/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: e915f959-eafb-4375-8d2c-2f312edf2d29
ms.openlocfilehash: 1c37f1b05126b8e8d9a5e64f033c503f27a8a1fc
ms.sourcegitcommit: a8140a7215c8704f34c247f602e1f12eb7b49aa2
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/23/2017
---
# <a name="how-to-configure-conditions-for-automatic-and-recommended-classification-for-azure-information-protection"></a>Como configurar as condições para classificação automática e recomendada para o Azure Information Protection

>*Aplica-se a: Azure Information Protection*

Quando configurar as condições para uma etiqueta, pode atribuir automaticamente uma etiqueta a um documento ou a um e-mail. Em alternativa, pode pedir aos utilizadores que selecionem a etiqueta recomendada. 

Quando configurar estas condições, pode utilizar padrões predefinidos, tais como **número de cartão de crédito** ou **número de Segurança Social dos E.U.A. (SSN)**. Em alternativa, pode definir uma cadeia personalizada ou um padrão como condição para classificação automática. Estas condições aplicam-se ao corpo de texto em documentos e e-mails, bem como a cabeçalhos e rodapés. Para obter mais informações sobre as condições, consulte o passo 5 do [seguir o procedimento](#to-configure-recommended-or-automatic-classification-for-a-label).

Para a melhor experiência de utilizador e para assegurar a continuidade do negócio, recomendamos que comece pela classificação recomendada ao utilizador em vez da classificação automática. Esta configuração permite aos utilizadores aceitar a classificação e qualquer proteção associado ou substituir estas sugestões se não forem adequados para o seu documento ou mensagem de e-mail.

Um exemplo de aviso para quando configura uma condição para aplicar uma etiqueta como uma ação recomendada, com uma sugestão de política personalizada:

![Deteção e recomendação do Azure Information Protection](../media/info-protect-recommend-calloutsv2.png)

Neste exemplo, o utilizador pode clicar em **alterar agora** para aplicar a etiqueta recomendada ou substituir a recomendação selecionando **dispensar**.

> [!IMPORTANT]
>Não configure uma etiqueta para a classificação automática e uma permissão definido pelo utilizador. A opção de permissões definidas pelo utilizador é um [definição de proteção](configure-policy-protection.md) que permita aos utilizadores que especifique que devem ser concedidas permissões.
>
>Quando uma etiqueta está configurada para classificação automática e permissões definidas pelo utilizador, o conteúdo é verificado para as condições e a definição de permissão definido pelo utilizador não é aplicada. Pode utilizar a classificação recomendada e permissões definidas pelo utilizador.

## <a name="how-automatic-or-recommended-labels-are-applied"></a>Como são aplicadas as etiquetas automáticas ou recomendadas

**Para a versão de disponibilidade geral do cliente Azure Information Protection:**

- A classificação automática aplica-se ao Word, Excel e PowerPoint quando os documentos são guardados e aplicam-se ao Outlook quando os e-mails são enviados. 
    
    Não é possível utilizar a classificação automática para documentos e e-mails que foram anteriormente etiquetados de forma manual ou anteriormente automaticamente com a etiqueta com uma classificação superior. 

- A classificação recomendada aplica-se ao Word, Excel e PowerPoint quando os documentos são guardados. Não é possível utilizar a classificação recomendada para o Outlook.
    
    Pode utilizar a classificação recomendada para os documentos que foram anteriormente com a etiqueta, com ou sem uma classificação superior. 


**Para a versão de pré-visualização atual do cliente Azure Information Protection:**

- A classificação automática aplica-se ao Word, Excel, PowerPoint e Outlook. Para documentos, a classificação automática é executada [continuamente em segundo plano](#more-information-about-running-continuously). Para o Outlook, a classificação automática é executada quando os e-mails são enviados. 
    
    Não é possível utilizar a classificação automática para documentos que foram anteriormente etiquetados de forma manual ou anteriormente automaticamente com a etiqueta com uma classificação superior. A exceção a este comportamento é se utilizar a análise do Azure Information Protection com o parâmetro de OverrideLabel definido no.

- A classificação recomendada aplica-se ao Word, Excel e PowerPoint. Para estes documentos, recomendado execuções de classificação [continuamente em segundo plano](#more-information-about-running-continuously). Não é possível utilizar a classificação recomendada para o Outlook.
    
    Pode utilizar a classificação recomendada para os documentos que foram anteriormente com a etiqueta, com ou sem uma classificação superior. 

#### <a name="more-information-about-running-continuously"></a>Obter mais informações sobre como executar continuamente

A versão de pré-visualização atual do cliente Azure Information Protection verifica periodicamente a documentos para as regras de condição que especificar. Este comportamento permite que a classificação automática e recomendada e a proteção de documentos que estão armazenados no SharePoint Online. Ficheiros grandes também guardar mais rapidamente porque as regras de condição já estiver a executar. 

As regras da condição não são executados em tempo real como tipos de utilizador. Em vez disso, executam periodicamente como uma tarefa em segundo plano se o documento está modificado. 

### <a name="how-multiple-conditions-are-evaluated-when-they-apply-to-more-than-one-label"></a>São avaliadas como várias condições quando estas são aplicadas a mais do que uma etiqueta

Para a versão de disponibilidade geral do cliente Azure Information Protection e o cliente de pré-visualização atual:

1. As etiquetas são ordenadas para avaliação de acordo com a respetiva posição que especificou na política: a etiqueta posicionada em primeiro tem a posição mais baixa (menos confidencial) e a etiqueta posicionada em último tem a posição mais elevada (mais confidencial).

2. A etiqueta mais confidencial é aplicada.
 
3. É aplicada a última subetiqueta.


## <a name="to-configure-recommended-or-automatic-classification-for-a-label"></a>Para configurar a classificação recomendada ou automática para uma etiqueta

1. Se ainda não o tiver feito, abra uma nova janela do browser e inicie sessão para o [portal do Azure](https://portal.azure.com) como um administrador de segurança ou um administrador global. Em seguida, navegue para o painel **Azure Information Protection**.     
    Por exemplo, no menu do hub, clique em **Mais serviços** e comece a escrever **Information** na caixa Filtrar. Selecione **Azure Information Protection**.

2. Se a etiqueta que pretende configurar será aplicada a todos os utilizadores, permaneça o **Azure Information Protection - política Global** painel.
    
    Se a etiqueta que pretende configurar está a ser um [âmbito política](configure-policy-scope.md) para que o se aplica apenas a utilizadores selecionados do **políticas** selecção de menu, selecione **âmbito políticas**. Em seguida, selecione a política de âmbito do **políticas do Azure Information Protection - âmbito** painel.

3. Do **Azure Information Protection - política Global** painel, ou o **política:\<nome >** painel, selecione a etiqueta a configurar. 

4. No painel **Etiqueta**, na secção **Configurar condições para aplicar esta etiqueta automaticamente**, clique em **Adicionar uma nova condição**.

5. No **condição** painel, selecione **tipos de informações** se pretender utilizar uma condição predefinida, ou **personalizada** se pretender especificar os seus próprios:
    - Para **tipos de informações**: selecione na lista de condições disponíveis e, em seguida, selecione o número mínimo de ocorrências e se a ocorrência deve ter um valor único a ser incluído na contagem de ocorrências.
        
        Os tipos de informações utilizam os tipos de informações de sensibilidade perda prevenção (DLP) do Office 365 dados e a deteção de padrão. Pode escolher entre vários tipos comuns de informações confidenciais, algumas das quais são específicas para diferentes regiões. Para obter mais informações, consulte [que os tipos de informações confidenciais serve para](https://support.office.com/article/What-the-sensitive-information-types-look-for-fd505979-76be-4d9f-b459-abef3fc9e86b) na documentação do Office. 
        
        A lista de tipos de informações que pode selecionar a partir do portal do Azure é atualizada periodicamente para incluir quaisquer novas adições de DLP do Office. No entanto, a lista exclui quaisquer tipos de informações confidenciais personalizadas que tenha definido e carregado como um pacote de regra para o Office 365 segurança & Centro de conformidade. 
        
        Quando o Azure Information Protection avalia os tipos de informações que selecionar, não utiliza a definição de nível de confiança de DLP do Office mas coincide de acordo com a confiança mais baixa.
    
    - Para **Personalizada**: especifique um nome e uma expressão correspondente, que tem de excluir aspas e carateres especiais. Em seguida, especifique se correspondente como uma expressão regular, sensibilidade às maiúsculas e de utilização e o número mínimo de ocorrências e se a ocorrência deve ter um valor único a ser incluído na ocorrência da contagem.
        
        As expressões regulares, utilize os padrões de regex do Office 365. Para obter mais informações, consulte [que define a expressão regular com a base de correspondências](https://technet.microsoft.com/library/jj674702(v=exchg.150).aspx#Anchor_2) na documentação do Office.
        
6. Decida se precisa de alterar o **número mínimo de ocorrências** e **ocorrência de contagem com valor exclusivo apenas**e, em seguida, selecione **guardar**. 
    
    Exemplo das opções de ocorrências: selecione o tipo de informações para o número de segurança social, conjunto o número mínimo de ocorrências como 2 e um documento tiver o mesmo número de segurança social listado duas vezes: Se definir o **contagem de ocorrências com valor exclusivo apenas** para **no**, a condição não for cumprida. Se definir esta opção para **desativar**, a condição for satisfeita.

7. Reverter o **etiqueta** painel, configure o seguinte e, em seguida, clique em **guardar**:
    
    - Escolha a classificação automática ou recomendada: para **Selecionar a forma como esta etiqueta é aplicada: automaticamente ou recomendada para o utilizador**, selecione **Automática** ou **Recomendada**.
    
    - Especifique o texto do aviso ao utilizador ou da sugestão de política: mantenha o texto predefinido ou especifique uma cadeia própria.

8. Para disponibilizar as alterações aos utilizadores, no painel inicial **Azure Information Protection**, clique em **Publicar**.

## <a name="next-steps"></a>Próximos passos

Considere implementar o [scanner do Azure Information Protection](deploy-aip-scanner.md), que pode utilizar as regras de classificação automática para detetar, classificar e proteger os ficheiros nos arquivos de ficheiros de locais e partilhas de rede.  

Para mais informações sobre como configurar a política do Azure Information Protection, utilize as ligações na secção [Configurar política da organização](configure-policy.md#configuring-your-organizations-policy).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]

