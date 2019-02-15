---
title: Configurar condições para uma etiqueta do Azure Information Protection – AIP
description: Condições de uma etiqueta permitem-lhe atribuir automaticamente uma etiqueta a um documento ou e-mail. Em alternativa, pode pedir aos utilizadores selecionarem uma etiqueta recomendada.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 01/16/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: e915f959-eafb-4375-8d2c-2f312edf2d29
ms.openlocfilehash: b7d0bf743d23083e2f9c6ca18044e26cb8c2ae6f
ms.sourcegitcommit: a78d4236cbeff743703c44b150e69c1625a2e9f4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/14/2019
ms.locfileid: "56256571"
---
# <a name="how-to-configure-conditions-for-automatic-and-recommended-classification-for-azure-information-protection"></a>Como configurar as condições para classificação automática e recomendada para o Azure Information Protection

>*Aplica-se a: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

Quando configurar as condições para uma etiqueta, pode atribuir automaticamente uma etiqueta a um documento ou a um e-mail. Em alternativa, pode pedir aos utilizadores que selecionem a etiqueta recomendada. 

Quando configurar estas condições, pode utilizar padrões predefinidos, como **número de cartão de crédito** ou **número da Previdência Social dos EUA (SSN)**. Em alternativa, pode definir uma cadeia personalizada ou um padrão como condição para classificação automática. Estas condições aplicam-se ao corpo de texto em documentos e e-mails, bem como a cabeçalhos e rodapés. Para obter mais informações sobre as condições, consulte a etapa 5 na [seguindo o procedimento](#to-configure-recommended-or-automatic-classification-for-a-label).

Para a melhor experiência de utilizador e para assegurar a continuidade do negócio, recomendamos que comece pela classificação recomendada ao utilizador em vez da classificação automática. Esta configuração permite aos usuários aceitar a classificação e qualquer proteção associados ou substituir estas sugestões, se eles não são adequados para a sua mensagem de e-mail ou documento.

Um exemplo de aviso para quando configura uma condição para aplicar uma etiqueta como uma ação recomendada, com uma sugestão de política personalizada:

![Deteção e recomendação do Azure Information Protection](./media/info-protect-recommend-calloutsv2.png)

Neste exemplo, o utilizador pode clicar **alterar agora** para aplicar a etiqueta recomendada ou ignorar a recomendação selecionando **dispensar**. Se o utilizador optar por ignorar a recomendação e a condição ainda se aplica quando o documento é aberto em seguida, a recomendação de etiqueta é apresentada novamente.

Se configurar a classificação automática em vez de recomendado, a etiqueta é aplicada automaticamente e o utilizador ainda verá uma notificação em seus aplicativos do Office. No entanto, o **alterar agora** e **dispensar** botões são substitua **OK**.

> [!IMPORTANT]
>Não configure uma etiqueta para a classificação automática e uma permissão definida pelo utilizador. A opção de permissões definidas pelo utilizador é um [definição de proteção](configure-policy-protection.md) que permita aos utilizadores especificar que deve ser concedido permissões.
>
>Quando uma etiqueta está configurada para classificação automática e permissões definidas pelo utilizador, o conteúdo é analisado relativamente as condições e a definição de permissão definida pelo utilizador não é aplicada. Pode utilizar a classificação recomendada e permissões definidas pelo utilizador.

## <a name="how-automatic-or-recommended-labels-are-applied"></a>Como são aplicadas etiquetas automáticas ou recomendadas

- A classificação automática aplica-se ao Word, Excel e PowerPoint quando os documentos são guardados e aplicam ao Outlook quando os e-mails são enviados. 
    
    Não é possível utilizar a classificação automática para documentos e e-mails que foram anteriormente etiquetados de forma manual ou anteriormente identificados automaticamente com uma classificação mais elevada. 

- Classificação recomendada aplica-se ao Word, Excel e PowerPoint quando os documentos são guardados. Não é possível utilizar classificação recomendada para o Outlook, a menos que configure uma [definição de cliente avançado](./rms-client/client-admin-guide-customizations.md#enable-recommended-classification-in-outlook) que está atualmente em pré-visualização.
    
    Não é possível utilizar a classificação recomendada para documentos que foram anteriormente etiquetados com uma classificação mais elevada. 

Pode alterar este comportamento para que o cliente do Azure Information Protection verifica periodicamente a documentos para as regras de condição que especificar. Esta configuração requer uma [definição de cliente avançado](./rms-client/client-admin-guide-customizations.md#turn-on-classification-to-run-continuously-in-the-background) que está atualmente em pré-visualização.

### <a name="how-multiple-conditions-are-evaluated-when-they-apply-to-more-than-one-label"></a>Como várias condições são avaliadas quando estas são aplicadas a mais do que uma etiqueta

1. As etiquetas são ordenadas para avaliação, de acordo com a respetiva posição que especificou na política: A etiqueta posicionada em primeiro lugar tem a posição mais baixa (menos confidencial) e a etiqueta posicionada em último tem a posição mais elevada (mais confidencial).

2. A etiqueta mais confidencial é aplicada.
 
3. A última subetiqueta é aplicada.


## <a name="to-configure-recommended-or-automatic-classification-for-a-label"></a>Para configurar a classificação recomendada ou automática para uma etiqueta

1. Se ainda não o tiver feito, abra uma nova janela do browser e [inicie sessão no portal do Azure](configure-policy.md#signing-in-to-the-azure-portal). Em seguida, navegue para o painel **Azure Information Protection**. 
    
    Por exemplo, no hub menu, clique em **todos os serviços** e comece a escrever **informações** na caixa Filtro. Selecione **Azure Information Protection**.

2. Do **classificações** > **etiquetas** opção de menu: Sobre o **do Azure Information Protection – etiquetas** painel, selecione a etiqueta para configurar.

3. No painel **Etiqueta**, na secção **Configurar condições para aplicar esta etiqueta automaticamente**, clique em **Adicionar uma nova condição**.

4. Na **condição** painel, selecione **tipos de informação** se pretender utilizar uma condição predefinida, ou **personalizado** se pretender especificar seus próprios:
    - Para **tipos de informações**: Selecione na lista de condições disponíveis e, em seguida, selecione o número mínimo de ocorrências e se a ocorrência deve ter um valor único a ser incluído na contagem de ocorrências.
        
        Os tipos de informações utilizam os tipos de informações de sensibilidade perda prevenção (DLP) do Office 365 dados e a deteção de padrão. Pode escolher entre vários tipos comuns de informações confidenciais, algumas das quais são específicas para diferentes regiões. Para obter mais informações, consulte [o que procurar os tipos de informações confidenciais](/office365/securitycompliance/what-the-sensitive-information-types-look-for) na documentação do Office 365.
        
        A lista de tipos de informações que pode selecionar a partir do portal do Azure é periodicamente atualizada para incluir quaisquer novas adições de DLP do Office. No entanto, a lista exclui quaisquer tipos de informações confidenciais personalizados que tenha definido e carregado como um pacote de regra para o Centro de conformidade e segurança do Office 365.
        
        > [!IMPORTANT]
        > Alguns dos tipos de informações requerem uma versão mínima do cliente. [Mais informações](#sensitive-information-types-that-require-a-minimum-version-of-the-client) 
        
        Quando o Azure Information Protection avalia os tipos de informações que selecionar, ele não utiliza a definição de nível de confiança de DLP do Office, mas coincide de acordo com a confiança de mais baixa.
    
    - Para **personalizado**: Especifique um nome e uma expressão correspondente, que tem de excluir aspas e carateres especiais. Em seguida, especifique se para fazer corresponder como uma expressão regular, utilize maiúsculas e minúsculas e o número mínimo de ocorrências e se a ocorrência deve ter um valor único a ser incluído na ocorrência contagem.
        
        As expressões regulares, use os padrões de regex do Office 365. Para ajudar a especificar expressões regulares para suas condições personalizadas, consulte a seguinte versão específica do [sintaxe de expressão Regular do Perl](https://www.boost.org/doc/libs/1_37_0/libs/regex/doc/html/boost_regex/syntax/perl_syntax.html) de aumento.
        
5. Decida se é preciso alterar a **número mínimo de ocorrências** e o **contagem de ocorrências com apenas o valor exclusivo**e, em seguida, selecione **guardar**. 
    
    Exemplo das opções de ocorrências: Selecionar o tipo de informações para o número da Previdência social, o número mínimo de ocorrências como 2 e um documento do conjunto tem o mesmo número de segurança social listado duas vezes: Se definir o **Contar ocorrências com apenas o valor exclusivo** ao **no**, a condição não for cumprida. Se definir esta opção como **desativar**, a condição é cumprida.

6. Novamente o **rótulo** painel, configure o seguinte e, em seguida, clique em **guardar**:
    
    - Escolha a classificação automática ou recomendada: Para **selecione a forma como esta etiqueta é aplicada: automaticamente ou recomendada para o usuário**, selecione **automática** ou **recomendado**.
    
    - Especifique o texto para a sugestão de linha de comandos ou a política de utilizador: Mantenha o texto predefinido ou especifique sua própria cadeia de caracteres.

Quando clica em **guardar**, as suas alterações estão automaticamente disponíveis para utilizadores e serviços. Já não existe uma opção de publicar separado.

### <a name="sensitive-information-types-that-require-a-minimum-version-of-the-client"></a>Tipos de informações confidenciais que requerem uma versão mínima do cliente

Os seguintes tipos de informações confidenciais requerem a versão mínima do 1.37.19.0 para o cliente do Azure Information Protection:

- **Número de telefone celular da UE**
- **Número de Passport da UE**
- **Número de licença do controlador da UE**
- **Número de identificação do National da UE**
- **Número da Previdência Social (SSN) da UE, ou equivalente ID**
- **Número de identificação de imposto da UE (TIN)**
- **Código de identificação de população em tailandês**
- **Número de identificação nacional turco**
- **Número de cartão de residência japonês**


Os seguintes tipos de informações confidenciais requerem a versão de pré-visualização atual do cliente do Azure Information Protection:

- **Cadeia de ligação do Azure Service Bus**
- **Cadeia de ligação do IoT do Azure**
- **Conta de armazenamento do Azure**
- **Cadeia de ligação de base de dados IAAS do Azure e a cadeia de ligação de SQL do Azure**
- **Cadeia de ligação de Cache de Redis do Azure**
- **Azure SAS**
- **Cadeia de ligação do SQL Server**
- **Chave de autenticação do Azure DocumentDB**
- **A definição de palavra-passe de publicação do Azure**
- **Chave de conta de armazenamento do Azure (genérico)**

Além disso, os seguintes tipos de informações confidenciais não são suportados para a versão de pré-visualização atual do cliente Azure Information Protection e já não apresentar no portal do Azure:

- **Número de telefone da UE**
- **Coordenadas do GPS da UE**

## <a name="next-steps"></a>Passos Seguintes

Considere implementar o [scanner do Azure Information Protection](deploy-aip-scanner.md), que pode utilizar as regras de classificação automática para detetar, classificar e proteger ficheiros em arquivos de ficheiros de partilhas e no local de rede.  

Para mais informações sobre como configurar a política do Azure Information Protection, utilize as ligações na secção [Configurar política da organização](configure-policy.md#configuring-your-organizations-policy).


