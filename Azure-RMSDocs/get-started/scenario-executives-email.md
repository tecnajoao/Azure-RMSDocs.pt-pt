---
title: "Cenário do AIP – executivos trocam informações privilegiadas"
description: "Este cenário e a documentação do utilizador associada utilizam a proteção do Azure Rights Management para que os executivos possam trocar em segurança e-mails e anexos por e-mail e as políticas restrinjam automaticamente o acesso dos executivos sem necessidade de ação especial por parte deles."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: get-started-article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: e18cf5df-859e-4028-8d19-39b0842df33d
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 2131f40b51f34de7637c242909f10952b1fa7d9f
ms.openlocfilehash: 1407a7bee800fec0ba8498d0439586378003ed54
ms.lasthandoff: 02/24/2017


---

# <a name="scenario---executives-securely-exchange-privileged-information"></a>Cenário – os executivos trocam informações privilegiadas em segurança

>*Aplica-se a: Azure Information Protection, Office 365*

Este cenário e a documentação do utilizador associada utilizam a tecnologia do Azure Rights Management do Azure Information Protection para que os executivos possam trocar em segurança e-mails e anexos por e-mail e as políticas restrinjam automaticamente o acesso dos executivos sem necessidade de ação especial por parte deles. Os e-mails e quaisquer anexos serão automaticamente protegidos pelo Azure Rights Management.

Se necessário, pode adicionar uma exceção à regra, tal como a abreviatura DNP (de “Não Proteger”) no assunto da mensagem de e-mail, para que os executivos a possam especificar caso necessitem de enviar um e-mail desprotegido para outros executivos, por exemplo, para rever antes de reencaminhar para outras pessoas.

As instruções aplicam-se às seguintes circunstâncias:

-   Os executivos partilham entre si informações confidenciais que não devem ser partilhadas com outras pessoas.

-   Os executivos não necessitam de fazer nada de forma diferente quando enviam estes e-mails, exceto enviá-los para um endereço de e-mail de trabalho em vez de um endereço de e-mail pessoal.

-   Os executivos têm uma forma de contornar a regra se alguma vez precisarem de enviar uma mensagem de e-mail desprotegida para outros executivos.

## <a name="deployment-instructions"></a>Instruções de Implementação
![Instruções do administrador para a Implementação Rápida do Azure RMS](../media/AzRMS_AdminBanner.png)

Certifique-se de que os seguintes requisitos são cumpridos e, em seguida, siga as instruções dos procedimentos de suporte antes de avançar para a documentação do utilizador.

## <a name="requirements-for-this-scenario"></a>Requisitos para este cenário
Para que as instruções para este cenário funcionem, é necessário o seguinte:

|Requisito|Se precisar de mais informações|
|---------------|--------------------------------|
|Preparou contas e grupos para o Office 365 ou o Azure Active Directory:<br /><br />- Um grupo com capacidade de correio com o nome **Executivos** e todos os executivos são membros deste grupo<br /><br />- Um grupo com capacidade de correio com o nome **Administradores de RMS** e todos os administradores que irão configurar o Azure RMS são membros deste grupo|[Preparação para o Azure Information Protection](../plan-design/prepare.md)|
|A sua chave de inquilino do Azure Information Protection é gerida pela Microsoft; não está a utilizar o BYOK|[Planear e implementar a sua chave de inquilino do Azure Information Protection](../plan-design/plan-implement-tenant-key.md)|
|O Azure Rights Management está ativado|[Ativar o Azure Rights Management](../deploy-use/activate-service.md)|
|Uma das seguintes configurações:<br /><br />- O Exchange Online está ativado para o Azure Rights Management<br /><br />- O conetor RMS está instalado e configurado para o Exchange no local|Para o Exchange Online: consulte as informações de [Exchange Online: configuração do IRM](../deploy-use/configure-office365.md#exchange-online-irm-configuration).<br /><br />Para o Exchange no local: [Implementar o conector Azure Rights Management](../deploy-use/deploy-rms-connector.md)|
|Configurou um modelo personalizado, tal como descrito a seguir|[Configurar modelos personalizados para o serviço Azure Rights Management](../deploy-use/configure-custom-templates.md)|
|Configurou uma regra de proteção de transporte para IRM, conforme descrito mais à frente neste artigo|Para o Exchange Online: [fluxo de correio ou regras de transporte](https://technet.microsoft.com/library/jj919238(v=exchg.150).aspx)<br /><br />Para o Exchange 2013: [criar uma Regra de Proteção de Transporte](https://technet.microsoft.com/en-us/library/dd302432(v=exchg.150))<br /><br />Para o Exchange 2010: [criar uma Regra de Proteção de Transporte](https://technet.microsoft.com/library/dd302432(v=exchg.141))|

### <a name="to-configure-the-custom-template-for-executives"></a>Para configurar o modelo personalizado para executivos

1.  No portal clássico do Azure: crie um novo modelo personalizado para o Azure Rights Management que contenha estes valores e definições:

    -   Nome: **Executivos**

    -   Direitos: conceda ao grupo **Executivos** com capacidade de correio direitos de **Coproprietário**

    -   Âmbito: selecione o grupo **Executivos** com capacidade de correio e o grupo **Administradores de RMS** com capacidade de correio.

2.  Publique o novo modelo.

3.  Apenas para o Exchange Online: atualize os modelos utilizando o seguinte comando do Windows PowerShell para o Exchange Online:

    ```
    Import-RMSTrustedPublishingDomain -Name "RMS Online -1" -RefreshTemplates -RMSOnline
    ```

### <a name="to-configure-the-transport-rule-for-irm"></a>Para configurar a regra de transporte para IRM

-   Utilize a documentação do Exchange referenciada na tabela para obter informações sobre os procedimentos para criar a regra de transporte com as seguintes definições:

    -   Nome: **aplicar os modelos Executivos a e-mail executivos**

    -   Especifique o grupo **Executivos** como o remetente e o destinatário da regra e da condição adicional.

    -   Para a ação, selecione **Aplicar proteção de direitos à mensagem com** e, em seguida, selecione o modelo **Executivos** que configurou.

    -   Adicione a exceção de **DNP** (como uma abreviatura de “Não Proteger”) ou a sua opção de palavras para identificar esta exceção, para ser incluída no assunto.

    -   Certifique-se de que a regra está configurada para **Impor**.

## <a name="user-documentation-instructions"></a>Instruções da documentação do utilizador
A não ser que pretenda fornecer instruções sobre como especificar **DNP** ou a sua opção de palavras ou expressões da exceção no assunto do e-mail, não existem instruções sobre procedimentos a dar aos utilizadores para este cenário, uma vez que proteger e-mails de e para executivos não requer qualquer ação especial por parte deles. As mensagens de e-mail e quaisquer anexos são automaticamente protegidos para que apenas os membros do grupo Executivos possam aceder aos mesmos.

No entanto, poderá ter de informar os executivos e o suporte técnico de que estes e-mails serão automaticamente protegidos e sobre a forma como tal pode restringir a utilização dos mesmos. Por exemplo, se os e-mails ou os anexos forem reencaminhados para outras pessoas mais tarde, estas não os conseguirão ler. Se tiver configurado a exceção DNP (ou equivalente), certifique-se de que o suporte técnico está ciente desta configuração para que os próprios executivos possam contornar a regra, sem necessidade de ação por parte de um administrador do Exchange.

Utilizando o modelo seguinte, copie e cole o anúncio numa comunicação destinada aos utilizadores finais e efetue estas alterações para refletir o seu ambiente:

1.  Substitua as instâncias de *&lt;nome da organização&gt;* pelo nome da sua organização.

2.  Caso tenha optado por uma cadeia diferente de DNP para a isenção, substitua esse valor e a explicação em conformidade.

3.  Substitua *&lt;domíniodee-mail&gt;* pelo nome de domínio de e-mail da sua organização.

4.  Substitua os *&lt;detalhes de contacto&gt;* por instruções sobre como os utilizadores podem contactar o suporte técnico, tais como uma ligação para um Web site, um endereço de e-mail ou um número de telefone.

5.  Efetue quaisquer modificações adicionais que pretenda ao anúncio e, em seguida, envie-o aos utilizadores.

A documentação de exemplo mostra que aspeto este anúncio poderá ter para os utilizadores depois das personalizações.

![Modelo de documentação do utilizador para a Implementação Rápida do Azure RMS](../media/AzRMS_UsersBanner.png)

### <a name="it-announcement-ltorganization-namegt-executive-emails-are-now-automatically-protected"></a>Anúncio de TI: os e-mails executivos da &lt;nome da organização&gt; são agora automaticamente protegidos
A partir de agora, sempre que enviar e-mails para outro executivo da &lt;nome da organização&gt; na empresa, os conteúdos desses e-mails e quaisquer anexos serão automaticamente protegidos de forma a que apenas outro executivo da empresa lhes possa aceder para ler as respetivas informações, imprimi-los, copiá-los, etc. Esta restrição aplica-se mesmo que reencaminhe a mensagem de e-mail para outras pessoas ou guarde os anexos. Esta proteção ajuda a evitar a perda de dados de informações confidenciais e delicadas.

Tenha em atenção que, se pretender que outras pessoas que não sejam executivos da &lt;nome da organização&gt; possam ler e editar as informações que envia nestes e-mails, tem de as enviar separadamente para essas pessoas. Em alternativa, para contornar a proteção automática, escreva as letras **DNP** (como uma abreviatura de Não Proteger) em qualquer parte do assunto da mensagem de e-mail.

Ao enviar informações confidenciais da empresa para outro executivo da &lt;nome da organização&gt;, não se esqueça de as enviar para o respetivo endereço de e-mail de trabalho (*nome*@&lt;domíniodee-mail&gt;) e não para um endereço de e-mail pessoal.

**Precisa de ajuda?**

-   Contacte o suporte técnico: &lt;detalhes de contacto&gt;

### <a name="example-user-documentation"></a>Exemplo de documentação do utilizador
![Exemplo de documentação do utilizador para a Implementação Rápida do Azure RMS](../media/AzRMS_ExampleBanner.png)

#### <a name="it-announcement-vanarsdel-executive-emails-are-now-automatically-protected"></a>Anúncio de TI: os e-mails executivos da VanArsdel são agora automaticamente protegidos
A partir de agora, sempre que enviar e-mails para outro executivo da VanArsdel na empresa, os conteúdos desses e-mails e quaisquer anexos serão automaticamente protegidos de forma a que apenas outro executivo da empresa possa aceder aos mesmos para ler as respetivas informações, imprimi-los, copiá-los, etc. Esta restrição aplica-se mesmo que reencaminhe a mensagem de e-mail para outras pessoas ou guarde os anexos. Esta proteção ajuda a evitar a perda de dados de informações confidenciais e delicadas.

Tenha em atenção que, se pretender que outras pessoas que não sejam executivos da VanArsdel possam ler e editar as informações que envia nestes e-mails, tem de as enviar separadamente para essas pessoas. Em alternativa, para contornar a proteção automática, escreva as letras **DNP** (como uma abreviatura de Não Proteger) em qualquer parte do assunto da mensagem de e-mail.

Ao enviar informações confidenciais da empresa para outro executivo da VanArsdel, não se esqueça de as enviar para o respetivo endereço de e-mail de trabalho (*nome*@vanarsdelltd.com) e não para um endereço de e-mail pessoal.

**Precisa de ajuda?**

-   Contactar o suporte técnico: helpdesk@vanarsdelltd.com

[!INCLUDE[Commenting house rules](../includes/houserules.md)]

