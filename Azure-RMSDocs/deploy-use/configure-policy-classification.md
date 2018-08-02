---
title: Configurar condições para uma etiqueta do Azure Information Protection
description: Quando configurar as condições para uma etiqueta, pode atribuir automaticamente uma etiqueta a um documento ou a um e-mail. Em alternativa, pode pedir aos utilizadores que selecionem a etiqueta recomendada.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 08/01/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: e915f959-eafb-4375-8d2c-2f312edf2d29
ms.openlocfilehash: 49d8e060e337b16967407932b22f90c55e9fad3c
ms.sourcegitcommit: 95d26d88a5898e0afc1dde863119afd05ea4427d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/01/2018
ms.locfileid: "39401069"
---
# <a name="how-to-configure-conditions-for-automatic-and-recommended-classification-for-azure-information-protection"></a>Como configurar as condições para classificação automática e recomendada para o Azure Information Protection

>*Aplica-se a: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

Quando configurar as condições para uma etiqueta, pode atribuir automaticamente uma etiqueta a um documento ou a um e-mail. Em alternativa, pode pedir aos utilizadores que selecionem a etiqueta recomendada. 

Quando configurar estas condições, pode utilizar padrões predefinidos, como **número de cartão de crédito** ou **número da Previdência Social dos EUA (SSN)**. Em alternativa, pode definir uma cadeia personalizada ou um padrão como condição para classificação automática. Estas condições aplicam-se ao corpo de texto em documentos e e-mails, bem como a cabeçalhos e rodapés. Para obter mais informações sobre as condições, consulte a etapa 5 na [seguindo o procedimento](#to-configure-recommended-or-automatic-classification-for-a-label).

Para a melhor experiência de utilizador e para assegurar a continuidade do negócio, recomendamos que comece pela classificação recomendada ao utilizador em vez da classificação automática. Esta configuração permite aos usuários aceitar a classificação e qualquer proteção associados ou substituir estas sugestões, se eles não são adequados para a sua mensagem de e-mail ou documento.

Um exemplo de aviso para quando configura uma condição para aplicar uma etiqueta como uma ação recomendada, com uma sugestão de política personalizada:

![Deteção e recomendação do Azure Information Protection](../media/info-protect-recommend-calloutsv2.png)

Neste exemplo, o utilizador pode clicar **alterar agora** para aplicar a etiqueta recomendada ou ignorar a recomendação selecionando **dispensar**. Se o utilizador optar por ignorar a recomendação e a condição ainda se aplica quando o documento é aberto em seguida, a recomendação de etiqueta é apresentada novamente. 

> [!IMPORTANT]
>Não configure uma etiqueta para a classificação automática e uma permissão definida pelo utilizador. A opção de permissões definidas pelo utilizador é um [definição de proteção](configure-policy-protection.md) que permita aos utilizadores especificar que deve ser concedido permissões.
>
>Quando uma etiqueta está configurada para classificação automática e permissões definidas pelo utilizador, o conteúdo é analisado relativamente as condições e a definição de permissão definida pelo utilizador não é aplicada. Pode utilizar a classificação recomendada e permissões definidas pelo utilizador.

## <a name="how-automatic-or-recommended-labels-are-applied"></a>Como são aplicadas etiquetas automáticas ou recomendadas

- A classificação automática aplica-se ao Word, Excel e PowerPoint quando os documentos são guardados e aplicam ao Outlook quando os e-mails são enviados. 
    
    Não é possível utilizar a classificação automática para documentos e e-mails que foram anteriormente etiquetados de forma manual ou anteriormente identificados automaticamente com uma classificação mais elevada. 

- Classificação recomendada aplica-se ao Word, Excel e PowerPoint quando os documentos são guardados. Não é possível utilizar classificação recomendada para o Outlook, a menos que configure uma [definição de cliente avançado](../rms-client/client-admin-guide-customizations.md#enable-recommended-classification-in-outlook) que está atualmente em pré-visualização.
    
    Não é possível utilizar a classificação recomendada para documentos que foram anteriormente etiquetados com uma classificação mais elevada. 

Pode alterar este comportamento para que o cliente do Azure Information Protection verifica periodicamente a documentos para as regras de condição que especificar. Esta configuração requer uma [definição de cliente avançado](../rms-client/client-admin-guide-customizations.md#turn-on-classification-to-run-continuously-in-the-background) que está atualmente em pré-visualização.

### <a name="how-multiple-conditions-are-evaluated-when-they-apply-to-more-than-one-label"></a>Como várias condições são avaliadas quando estas são aplicadas a mais do que uma etiqueta

1. As etiquetas são ordenadas para avaliação de acordo com a respetiva posição que especificou na política: a etiqueta posicionada em primeiro tem a posição mais baixa (menos confidencial) e a etiqueta posicionada em último tem a posição mais elevada (mais confidencial).

2. A etiqueta mais confidencial é aplicada.
 
3. A última subetiqueta é aplicada.


## <a name="to-configure-recommended-or-automatic-classification-for-a-label"></a>Para configurar a classificação recomendada ou automática para uma etiqueta

1. Se ainda não o tiver feito, abra uma nova janela do browser e [inicie sessão no portal do Azure](configure-policy.md#signing-in-to-the-azure-portal). Em seguida, navegue para o painel **Azure Information Protection**. 
    
    Por exemplo, no hub menu, clique em **todos os serviços** e comece a escrever **informações** na caixa Filtro. Selecione **Azure Information Protection**.

2. Do **classificações** > **etiquetas** opção de menu: no **do Azure Information Protection – etiquetas** painel, selecione a etiqueta a configurar.

3. No painel **Etiqueta**, na secção **Configurar condições para aplicar esta etiqueta automaticamente**, clique em **Adicionar uma nova condição**.

4. Na **condição** painel, selecione **tipos de informação** se pretender utilizar uma condição predefinida, ou **personalizado** se pretender especificar seus próprios:
    - Para **tipos de informações**: selecione na lista de condições disponíveis e, em seguida, selecione o número mínimo de ocorrências e se a ocorrência deve ter um valor único a ser incluído na contagem de ocorrências.
        
        Os tipos de informações utilizam os tipos de informações de sensibilidade perda prevenção (DLP) do Office 365 dados e a deteção de padrão. Pode escolher entre vários tipos comuns de informações confidenciais, algumas das quais são específicas para diferentes regiões. Para obter mais informações, consulte [o que procurar os tipos de informações confidenciais](https://support.office.com/article/What-the-sensitive-information-types-look-for-fd505979-76be-4d9f-b459-abef3fc9e86b) na documentação do Office.
        
        A lista de tipos de informações que pode selecionar a partir do portal do Azure é periodicamente atualizada para incluir quaisquer novas adições de DLP do Office. No entanto, a lista exclui quaisquer tipos de informações confidenciais personalizados que tenha definido e carregado como um pacote de regra para o Centro de conformidade e segurança do Office 365.
        
        > [!IMPORTANT]
        > Alguns dos tipos de informações requerem uma versão mínima do cliente. [Mais informações](#sensitive-information-types-that-require-a-minimum-version-of-the-client) 
        
        Quando o Azure Information Protection avalia os tipos de informações que selecionar, ele não utiliza a definição de nível de confiança de DLP do Office, mas coincide de acordo com a confiança de mais baixa.
    
    - Para **Personalizada**: especifique um nome e uma expressão correspondente, que tem de excluir aspas e carateres especiais. Em seguida, especifique se para fazer corresponder como uma expressão regular, utilize maiúsculas e minúsculas e o número mínimo de ocorrências e se a ocorrência deve ter um valor único a ser incluído na ocorrência contagem.
        
        As expressões regulares, use os padrões de regex do Office 365. Para obter mais informações, consulte [definir a expressão regular com base em correspondências](https://technet.microsoft.com/library/jj674702(v=exchg.150).aspx#Anchor_2) na documentação do Office. Além disso, poderá considerar útil para referência [sintaxe de expressão Regular do Perl](http://www.boost.org/doc/libs/1_66_0/libs/regex/doc/html/boost_regex/syntax/perl_syntax.html) de aumento.
        
5. Decida se é preciso alterar a **número mínimo de ocorrências** e o **contagem de ocorrências com apenas o valor exclusivo**e, em seguida, selecione **guardar**. 
    
    Exemplo das opções de ocorrências: selecionar o tipo de informações para o número da Previdência social, o número mínimo de ocorrências como 2 e um documento do conjunto tem o mesmo número de segurança social listado duas vezes: Se definir o **contagem de ocorrências com apenas o valor exclusivo** para **no**, a condição não for cumprida. Se definir esta opção como **desativar**, a condição é cumprida.

6. Novamente o **rótulo** painel, configure o seguinte e, em seguida, clique em **guardar**:
    
    - Escolha a classificação automática ou recomendada: para **Selecionar a forma como esta etiqueta é aplicada: automaticamente ou recomendada para o utilizador**, selecione **Automática** ou **Recomendada**.
    
    - Especifique o texto do aviso ao utilizador ou da sugestão de política: mantenha o texto predefinido ou especifique uma cadeia própria.

Quando clica em **guardar**, as suas alterações estão automaticamente disponíveis para utilizadores e serviços. Já não existe uma opção de publicar separado.

### <a name="sensitive-information-types-that-require-a-minimum-version-of-the-client"></a>Tipos de informações confidenciais que requerem uma versão mínima do cliente

> [!NOTE]
> Os seguintes tipos de informações de sensibilidade agora a implementar aos inquilinos, mas não poderão ser apresentados para o selecionar. No entanto, se configurar o scanner do Azure Information Protection para [identificar todas as condições personalizadas e tipos de informações confidenciais conhecidos](deploy-aip-scanner.md#using-the-scanner-with-alternative-configurations), a versão de pré-visualização do scanner pode detectar esses novos tipos de informações, mesmo se não for possível Selecione-os no portal do Azure.

Os seguintes tipos de informações confidenciais atualmente requerem a versão de pré-visualização do cliente do Azure Information Protection:

- **Número de telefone da UE**
- **Número de telefone celular da UE**
- **Número de Passport da UE**
- **Número de licença do controlador da UE**
- **Coordenadas do GPS da UE**
- **Número de identificação do National da UE**
- **Número da Previdência Social (SSN) da UE, ou equivalente ID**
- **Número de identificação de imposto da UE (TIN)**
- **Código de identificação de população em tailandês**
- **Número de identificação nacional turco**
- **Número de cartão de residência japonês**


## <a name="next-steps"></a>Passos Seguintes

Considere implementar o [scanner do Azure Information Protection](deploy-aip-scanner.md), que pode utilizar as regras de classificação automática para detetar, classificar e proteger ficheiros em arquivos de ficheiros de partilhas e no local de rede.  

Para mais informações sobre como configurar a política do Azure Information Protection, utilize as ligações na secção [Configurar política da organização](configure-policy.md#configuring-your-organizations-policy).


