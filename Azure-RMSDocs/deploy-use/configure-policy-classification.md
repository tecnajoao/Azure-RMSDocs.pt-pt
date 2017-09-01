---
title: "Configurar condições para uma etiqueta do Azure Information Protection"
description: "Quando configurar as condições para uma etiqueta, pode atribuir automaticamente uma etiqueta a um documento ou a um e-mail. Em alternativa, pode pedir aos utilizadores que selecionem a etiqueta recomendada."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 08/30/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: e915f959-eafb-4375-8d2c-2f312edf2d29
ms.openlocfilehash: ef84f3ceb8f732dd475b4db8eae489e715d4b7da
ms.sourcegitcommit: 13e95906c24687eb281d43b403dcd080912c54ec
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/30/2017
---
# <a name="how-to-configure-conditions-for-automatic-and-recommended-classification-for-azure-information-protection"></a>Como configurar as condições para classificação automática e recomendada para o Azure Information Protection

>*Aplica-se a: Azure Information Protection*

Quando configurar as condições para uma etiqueta, pode atribuir automaticamente uma etiqueta a um documento ou a um e-mail. Em alternativa, pode pedir aos utilizadores que selecionem a etiqueta que lhes recomende: 

- A classificação automática aplica-se ao Word, ao Excel e ao PowerPoint quando os ficheiros são guardados e aplica-se ao Outlook quando os e-mails são enviados. Não é possível utilizar a classificação automática para ficheiros que foram anteriormente etiquetados de forma manual.
 
- A classificação recomendada aplica-se ao Word, ao Excel e ao PowerPoint quando os ficheiros são guardados.

Quando configurar as condições, pode utilizar padrões predefinidos, tais como **número de cartão de crédito** ou **número de Segurança Social dos E.U.A. (SSN)**. Em alternativa, pode definir uma cadeia personalizada ou um padrão como condição para classificação automática. Estas condições aplicam-se ao corpo de texto em documentos e e-mails, bem como a cabeçalhos e rodapés. Para obter mais informações sobre as condições, consulte o [detalhes sobre os tipos de informações](#details-about-the-information-types) secção.

Como são avaliadas várias condições quando estas são aplicadas a mais do que uma etiqueta:

1. As etiquetas são ordenadas para avaliação de acordo com a respetiva posição que especificou na política: a etiqueta posicionada em primeiro tem a posição mais baixa (menos confidencial) e a etiqueta posicionada em último tem a posição mais elevada (mais confidencial).

2. A etiqueta mais confidencial é aplicada.
 
3. É aplicada a última subetiqueta.

> [!TIP]
>Para a melhor experiência de utilizador e para assegurar a continuidade do negócio, recomendamos que comece pela classificação recomendada ao utilizador em vez da classificação automática. Esta configuração permite aos utilizadores aceitar a ação de etiquetagem ou proteção ou substituir estas sugestões se não forem adequados para o seu documento ou mensagem de e-mail.

Um exemplo de aviso para quando configura uma condição para aplicar uma etiqueta como uma ação recomendada, com uma sugestão de política personalizada:

![Deteção e recomendação do Azure Information Protection](../media/info-protect-recommend-calloutsv2.png)

Neste exemplo, o utilizador pode clicar em **alterar agora** para aplicar a etiqueta recomendada ou substituir a recomendação selecionando **dispensar**.

## <a name="to-configure-recommended-or-automatic-classification-for-a-label"></a>Para configurar a classificação recomendada ou automática para uma etiqueta

1. Se ainda não o tiver feito, abra uma nova janela do browser e inicie sessão para o [portal do Azure](https://portal.azure.com) como um administrador de segurança ou um administrador global. Em seguida, navegue para o painel **Azure Information Protection**. 
    
    Por exemplo, no menu do hub, clique em **Mais serviços** e comece a escrever **Information** na caixa Filtrar. Selecione **Azure Information Protection**.

2. Se a etiqueta que pretende configurar será aplicada a todos os utilizadores, permaneça o **Azure Information Protection - política Global** painel.
    
    Se a etiqueta que pretende configurar está a ser um [âmbito política](configure-policy-scope.md) para que o se aplica apenas a utilizadores selecionados do **políticas** selecção de menu, selecione **âmbito políticas**. Em seguida, selecione a política de âmbito do **políticas do Azure Information Protection - âmbito** painel.

3. Do **Azure Information Protection - política Global** painel, ou o **política:\<nome >** painel, selecione a etiqueta a configurar. 

4. No painel **Etiqueta**, na secção **Configurar condições para aplicar esta etiqueta automaticamente**, clique em **Adicionar uma nova condição**.

5. No **condição** painel, selecione **tipos de informações** se pretender utilizar uma condição predefinida, ou **personalizada** se pretender especificar a sua própria e, em seguida, clique em **Guardar**:
    - Para **tipos de informações**: selecione na lista de condições disponíveis e, em seguida, selecione o número mínimo de ocorrências e se a ocorrência deve ter um valor único a ser incluído na contagem de ocorrências.
        
        Para utilizar a lista completa das condições, tem de utilizar a versão de pré-visualização atual do cliente Azure Information Protection. Se tiver a versão de disponibilidade geral atual do cliente, as seguintes cinco condições só são suportadas: **código SWIFT**, **número de cartão de crédito**, **número de encaminhamento ABA**, **Número de Segurança Social dos E.U.A. (SSN)**, e **internacional (IBAN) do número de conta bancária**. [Mais informações](#details-about-the-information-types)
    
    - Para **Personalizada**: especifique um nome e uma expressão correspondente, que tem de excluir aspas e carateres especiais. Em seguida, especifique se correspondente como uma expressão regular, sensibilidade às maiúsculas e de utilização e o número mínimo de ocorrências e se a ocorrência deve ter um valor único a ser incluído na ocorrência da contagem.
        
        Se tiver a versão de pré-visualização atual do cliente Azure Information Protection, as expressões regulares utilizam os padrões de regex do Office 365. Para obter mais informações, consulte [que define a expressão regular com a base de correspondências](https://technet.microsoft.com/library/jj674702(v=exchg.150).aspx#Anchor_2) na documentação do Office. 
        
    **Exemplo das opções de ocorrências**: selecione a opção de número de segurança social incorporado, conjunto o número mínimo de ocorrências como 2 e um documento tiver o mesmo número de segurança social listado duas vezes: Se definir o **contagem de ocorrências com apenas valores exclusivos** para **no**, a condição não for cumprida. Se definir esta opção para **desativar**, a condição for satisfeita.

6. No painel **Etiqueta**, configure as seguintes opções e, em seguida, clique em **Guardar**:
    
    - Escolha a classificação automática ou recomendada: para **Selecionar a forma como esta etiqueta é aplicada: automaticamente ou recomendada para o utilizador**, selecione **Automática** ou **Recomendada**.
    
    - Especifique o texto do aviso ao utilizador ou da sugestão de política: mantenha o texto predefinido ou especifique uma cadeia própria.

7. Para disponibilizar as alterações aos utilizadores, no painel inicial **Azure Information Protection**, clique em **Publicar**.

## <a name="details-about-the-information-types"></a>Detalhes sobre os tipos de informações

Se tiver a versão de pré-visualização atual do cliente Azure Information Protection, a lista completa dos tipos de informações são suportadas e utilize os tipos de informações de sensibilidade perda prevenção (DLP) do Office 365 dados e a deteção de padrão. Pode escolher entre vários tipos comuns de informações confidenciais, algumas das quais são específicas para diferentes regiões. Para obter mais informações, consulte [que os tipos de informações confidenciais serve para](https://support.office.com/article/What-the-sensitive-information-types-look-for-fd505979-76be-4d9f-b459-abef3fc9e86b) na documentação do Office. Quando o Azure Information Protection avalia estes tipos de informações, não utiliza a definição de nível de confiança de DLP do Office mas coincide de acordo com a confiança mais baixa.  

Se tiver a versão de disponibilidade geral atual do cliente, os seguintes tipos de informações só são suportados:

- [Código SWIFT](#swift-code )

- [Número do Cartão de Crédito](#credit-card-number )

- [Número de Encaminhamento ABA](#aba-routing-number )

- [Número de Segurança Social dos EUA (SSN)](#usa-social-security-number-ssn)

- [Número de Conta Bancária Internacional (IBAN)](#international-banking-account-number-iban)

Consulte as secções seguintes para obter mais informações sobre cada um destes tipos de informações para a versão de disponibilidade geral do cliente.

### <a name="swift-code"></a>Código SWIFT

Corresponder a este tipo de informações quando o conteúdo inclui o seguinte:  

1. Uma das expressões seguintes: **swift**, **swiftnumber**, **swiftroutingnumber** 

2. Um código Swift, num padrão formatado:  

    a. 4 letras (código bancário)  

    b. 2 letras (código de país)  

    c. 2 letras ou dígitos (código de localização)  

    d. 3 letras ou dígitos opcionais (código de sucursal)  


Exemplos de teste:

- **NEDSZAJJXXX Swiftroutingnumber**

- **NEDSZAJJ100 Swiftnumber** 

----


### <a name="credit-card-number"></a>Número do Cartão de Crédito

Corresponder a este tipo de informações quando o conteúdo inclui o seguinte:  

- Um número de cartão de crédito válido, num padrão formatado ou não formatado, que passa a [verificação luhn](https://wikipedia.org/wiki/Luhn_algorithm). Este tipo de informações deteta cartões de todas as marcas principais em todo o mundo, incluindo Visa, MasterCard, Discover Card, American Express e Diners.

    - **Formatado**:
    
        - 16 dígitos: (dddd-dddd-dddd-dddd)  
        
    - **Não formatado**:
    
        - (dddddddddddddddd)  


Exemplos de teste:

- **4242-4242-4242-4242**

- **4242424242424242** 

----

### <a name="aba-routing-number"></a>Número de Encaminhamento ABA

Corresponder a este tipo de informações quando o conteúdo inclui o seguinte:  

1. Pelo menos uma das expressões seguintes: **aba**, **rtn**, **número de encaminhamento** 

2. Um número de encaminhamento ABA, que inclui 9 dígitos que podem ser num padrão formatado ou não formatado: 

    - **Formatado**: 
        
        a. Quatro dígitos que começam por 0, 1, 2, 3, 6, 7 ou 8 
        
        b. Um hífen 
        
        c. Quatro dígitos 
        
        d. Um hífen 
        
        e. Um dígito 
        
        Exemplo: 3456-9876-1 ABA 
        
    - **Não formatado**: 
        
        9 dígitos consecutivos que começam por 0, 1, 2, 3, 6, 7 ou 8 
        
        Exemplo: 345698761 RTN 
 

Exemplos de teste:

- **3456-9876-1 ABA**

- **345698761 RTN** 

----

### <a name="usa-social-security-number-ssn"></a>Número de Segurança Social dos E.U.A. (SSN)

Corresponder a este tipo de informações quando o conteúdo inclui o seguinte:  

1. Pelo menos uma das expressões seguintes: **ssn**, **segurança social**, **ssid**, **ss#** 

2. Um número de segurança social: 9 dígitos, que podem estar num padrão formatado ou não formatado:

    - **Formatado**: 
    
        - Nove dígitos no seguinte formato: ddd-dd-dddd OU ddd dd dddd 
        
    - **Não formatado**: 
    
        - Nove dígitos no seguinte formato: ddddddddd 


Exemplos de teste:

- **SSN 123-45-6789**

- **SS# 123456789** 


----

### <a name="international-banking-account-number-iban"></a>Número de Conta Bancária Internacional (IBAN)

Corresponder a este tipo de informações quando o conteúdo inclui o seguinte:  

1. A seguinte expressão: **IBAN** 

2. Um número IBAN: começa com um código de país (duas letras), seguido de dígitos de verificação (dois dígitos) e, em seguida, número de bban (até e incluindo 30 dígitos).


Exemplos de teste:

- **GB29 NWBK 6016 1331 9268 19 IBAN**


## <a name="next-steps"></a>Próximos passos

Para mais informações sobre como configurar a política do Azure Information Protection, utilize as ligações na secção [Configurar política da organização](configure-policy.md#configuring-your-organizations-policy).  

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


