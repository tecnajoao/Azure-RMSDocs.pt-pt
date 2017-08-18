---
title: "Configurar condições para uma etiqueta do Azure Information Protection"
description: "Quando configurar as condições para uma etiqueta, pode atribuir automaticamente uma etiqueta a um documento ou a um e-mail. Em alternativa, pode pedir aos utilizadores que selecionem a etiqueta recomendada."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 08/11/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: e915f959-eafb-4375-8d2c-2f312edf2d29
ms.openlocfilehash: 3aad6eb4956b6565e44c4b1019c984a28cb41fdc
ms.sourcegitcommit: 17f593b099dddcbb1cf0422353d594ab964b2736
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/11/2017
---
# <a name="how-to-configure-conditions-for-automatic-and-recommended-classification-for-azure-information-protection"></a>Como configurar as condições para classificação automática e recomendada para o Azure Information Protection

>*Aplica-se a: Azure Information Protection*

Quando configurar as condições para uma etiqueta, pode atribuir automaticamente uma etiqueta a um documento ou a um e-mail. Em alternativa, pode pedir aos utilizadores que selecionem a etiqueta que lhes recomende: 

- A classificação automática aplica-se ao Word, ao Excel e ao PowerPoint quando os ficheiros são guardados e aplica-se ao Outlook quando os e-mails são enviados. Não é possível utilizar a classificação automática para ficheiros que foram anteriormente etiquetados de forma manual.
 
- A classificação recomendada aplica-se ao Word, ao Excel e ao PowerPoint quando os ficheiros são guardados.

Quando configurar as condições, pode utilizar padrões predefinidos, tais como "números de cartão de crédito" ou "EUA número de Segurança Social." Em alternativa, pode definir uma cadeia personalizada ou um padrão como condição para classificação automática. Estas condições aplicam-se ao corpo de texto em documentos e e-mails, bem como a cabeçalhos e rodapés. Para mais informações sobre as condições, consulte a secção [Informações sobre as condições incorporadas](#information-about-the-built-in-conditions).

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

1. Caso ainda não o tenha feito, numa nova janela de browser, inicie sessão no [portal do Azure](https://portal.azure.com) como administrador de segurança ou administrador global e navegue para o painel **Azure Information Protection**. 
    
    Por exemplo, no menu do hub, clique em **Mais serviços** e comece a escrever **Information** na caixa Filtrar. Selecione **Azure Information Protection**.

2. Se a etiqueta que pretende configurar para classificação automática ou recomendada aplica-se a todos os utilizadores, selecione a etiqueta a alterar o **política: Global** painel e, em seguida, efetue as alterações no **etiqueta** painel e em quaisquer painéis subsequentes, conforme necessário. 

     Se a etiqueta que pretende configurar estiver numa [política de âmbito](configure-policy-scope.md) para ser aplicada apenas a utilizadores selecionados, selecione primeiro essa política de âmbito no painel inicial do **Azure Information Protection**.  

3. No painel **Etiqueta**, na secção **Configurar condições para aplicar esta etiqueta automaticamente**, clique em **Adicionar uma nova condição**.

4. No painel **Condição**, selecione **Incorporada** se pretender utilizar uma condição predefinida, ou **Personalizada** se pretender especificar a sua própria condição e, em seguida, clique em **Guardar**:

    - Para **incorporada**: selecione na lista de condições disponíveis e, em seguida, selecione o número mínimo de ocorrências e se a ocorrência deve ter um valor único a ser incluído na contagem de ocorrências.
        
        Para mais informações sobre as regras de deteção para estas condições e alguns exemplos, consulte a secção [Informações sobre as condições incorporadas](#information-about-the-built-in-conditions).

    - Para **Personalizada**: especifique um nome e uma expressão correspondente, que tem de excluir aspas e carateres especiais. Em seguida, especifique se correspondente como uma expressão regular, sensibilidade às maiúsculas e de utilização e o número mínimo de ocorrências e se a ocorrência deve ter um valor único a ser incluído na ocorrência da contagem.
        
    **Exemplo das opções de ocorrências**: se selecionar a opção de número de segurança social incorporado e definir o número mínimo de ocorrências como 2 e um documento tiver o mesmo número de segurança social listado duas vezes: se definir **Contar ocorrências apenas com valores únicos** como **Ativada**, a condição não é satisfeita. Se definir esta opção como **Desativada**, a condição é satisfeita.

5. No painel **Etiqueta**, configure as seguintes opções e, em seguida, clique em **Guardar**:

    - Escolha a classificação automática ou recomendada: para **Selecionar a forma como esta etiqueta é aplicada: automaticamente ou recomendada para o utilizador**, selecione **Automática** ou **Recomendada**.

    - Especifique o texto do aviso ao utilizador ou da sugestão de política: mantenha o texto predefinido ou especifique uma cadeia própria.

6. Para disponibilizar as alterações aos utilizadores, no painel **Azure Information Protection**, clique em **Publicar**.

## <a name="information-about-the-built-in-conditions"></a>Informações sobre as condições incorporadas

Pode selecionar as seguintes condições:

- [Código SWIFT](#swift-code )

- [Número do Cartão de Crédito](#credit-card-number )

- [Número de Encaminhamento ABA](#aba-routing-number )

- [Número de Segurança Social dos EUA (SSN)](#usa-social-security-number-ssn)

- [Número de Conta Bancária Internacional (IBAN)](#international-banking-account-number-iban)


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


