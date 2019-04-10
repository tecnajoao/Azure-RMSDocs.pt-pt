---
title: Migrar o Azure Information Protection etiquetas para o Office 365 – AIP
description: Migre o Azure Information Protection etiquetas para etiquetas de sensibilidade do Office 365 para clientes e serviços que suportam etiquetas unificadas.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 04/09/2019
ms.topic: article
ms.collection: M365-security-compliance
ms.service: information-protection
ms.reviewer: demizets
ms.suite: ems
ms.openlocfilehash: 0cc09e58d49fe9515de0109c726af08e12937dd1
ms.sourcegitcommit: 729b12e1219c6dbf1bb2a6cfa7239f24d1d13cc5
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2019
ms.locfileid: "59364577"
---
# <a name="how-to-migrate-azure-information-protection-labels-to-office-365-sensitivity-labels"></a>Como migrar o Azure Information Protection etiquetas para etiquetas de sensibilidade do Office 365

>*Aplica-se a: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

> [!IMPORTANT]
> Esta funcionalidade está em pré-visualização e migra o seu inquilino para uma nova plataforma. Não é possível inverter a migração. A nova plataforma suporta a etiquetagem unificada, para que as etiquetas que criar e gerir podem ser utilizadas por clientes e serviços que suportam [soluções do Microsoft Information Protection](faqs.md#whats-the-difference-between-azure-information-protection-and-microsoft-information-protection).

Migrar as suas etiquetas para poder utilizá-los como etiquetas de sensibilidade do Office 365 por [os clientes e serviços que suportam a etiquetagem unificada](#clients-and-services-that-support-unified-labeling). Gerir e publicar estas etiquetas da segurança do Office 365 e o Centro de conformidade, ou o Centro de segurança do Microsoft 365 e o Centro de conformidade do Microsoft 365. Após a migração, o cliente do Azure Information Protection continua transferir as etiquetas com a política do Azure Information Protection a partir do portal do Azure. 

Antes de ler instruções detalhadas sobre como migrar as suas etiquetas, poderá considerar as seguintes perguntas mais frequentes sobre úteis:

- [O que é a diferença entre as etiquetas no Azure Information Protection e as etiquetas no Office 365?](faqs.md#whats-the-difference-between-labels-in-azure-information-protection-and-labels-in-office-365)

- [Quando é o momento certo para migrar os meus rótulos para Office 365?](faqs.md#when-is-the-right-time-to-migrate-my-labels-to-office-365)

- [Depois que tiver migrado meus rótulos, do portal de gestão que utilizo?](faqs.md?#after-ive-migrated-my-labels-which-management-portal-do-i-use )

### <a name="important-information-about-administrative-roles"></a>Informações importantes sobre as funções administrativas

O [função do Azure AD](/azure/active-directory/active-directory-assign-admin-roles-azure-portal) dos **administrador do Information Protection** não é suportada pela plataforma de etiquetagem unificada. Se esta função administrativa for utilizada na sua organização, antes de migrar as etiquetas, adicionar os utilizadores que tenham esta função para as funções do Azure AD de **administrador de segurança** ou **administrador de conformidade**. Se precisar de ajuda com este passo, consulte [conceder acesso de utilizadores para o Centro de conformidade e segurança do Office 365](https://docs.microsoft.com/office365/securitycompliance/grant-access-to-the-security-and-compliance-center). Também pode atribuir estas funções no portal do Azure AD, o Centro de segurança do Microsoft 365 e o Centro de conformidade do Microsoft 365.

Em alternativa ao uso de funções, nos centros de administração, pode criar um novo grupo de função para estes utilizadores e adicionar qualquer um **administrador de etiqueta de sensibilidade** ou **configuração de organização** funções a este grupo.

Se não conceder esses usuários acesso para os centros de administração utilizando uma das seguintes configurações, não poderá configurar o Azure Information Protection no portal do Azure depois das etiquetas são migradas.

Os administradores globais do seu inquilino podem continuar a gerir etiquetas e políticas no portal do Azure e os centros de administração, depois das etiquetas são migradas.


## <a name="considerations-for-unified-labels"></a>Considerações para procurar etiquetas de unificada

Antes de migrar as etiquetas, certifique-se de que está ciente das seguintes alterações e considerações:

- Nem todos os clientes atualmente suportam etiquetas unificadas. Certifique-se de que tenha [suportado clientes](#clients-and-services-that-support-unified-labeling) e estar preparado para administração no portal do Azure (para clientes que não suportam etiquetas unificadas) e os centros de administração (para o cliente que suportam etiquetas unificadas).

- Se estiver no meio de definir e configurar as etiquetas que pretende utilizar, recomendamos que conclua este processo com o portal do Azure e, em seguida, migre as etiquetas. Esta estratégia evita a duplicação de etiquetas durante o processo de migração, que, em seguida, vai ter de ser editado em centros de administração.

- As políticas, incluindo definições de política e quem tem acesso aos mesmos (políticas de âmbito) e todas as definições de cliente avançadas não são migradas. Para que essas alterações não são migradas, terá de configurar as opções relevantes nos centros de administração, depois das etiquetas são migradas.
    
    Para uma experiência de usuário mais consistente, recomendamos que publique as etiquetas mesmo no mesmos âmbitos nos centros de administração.

- Nem todas as definições de uma etiqueta migrada são compatíveis com os centros de administração. Utilize a tabela no [Etiquetar definições que não são suportadas nos centros de administração](#label-settings-that-are-not-supported-in-the-admin-centers) secção para ajudar a identificar estas definições e o método recomendado de ação.

- Modelos de proteção:
    
    - Modelos que utilizam uma chave com base na cloud e que fazem parte de uma configuração de etiqueta também são migrados com a etiqueta. Outros modelos de proteção não são migrados. 
    
    - Se tiver etiquetas que estão configuradas para um modelo predefinido, editar estas etiquetas e selecione o **definir permissões** opção para configurar as mesmas definições de proteção que tinha no seu modelo. Etiquetas com modelos predefinidos não irão bloquear a migração de etiqueta, mas esta configuração de etiqueta não é suportada nos centros de administração.
        
        Sugestão: Para ajudar a reconfigurar estas etiquetas, talvez seja útil ter duas janelas do browser: Uma janela na qual seleciona a **Editar modelo** botão para a etiqueta ver as definições de proteção e de outra janela para configurar as definições ao selecionar **definir permissões**.
    
    - Depois de uma etiqueta com as definições de proteção com base na cloud foi migrada, o âmbito resultante do modelo de proteção é o âmbito definido no portal do Azure (ou ao utilizar o módulo do PowerShell do AADRM) e o âmbito definido nos centros de administração. 

- Quando migra as etiquetas, verá a migração resulta apresentar se uma etiqueta foi **criado**, **atualizado**, ou **renomeado** devido à duplicação:

    - Quando é criada uma etiqueta, em seguida, pode publicá-lo em um dos centros de administração para disponibilizá-lo a aplicações e serviços.
    
    - Quando uma etiqueta for renomeada, tem, em seguida, editá-lo, que pode ser feito em um dos centros de administração ou o portal do Azure. 

- Para cada etiqueta, o portal do Azure mostra apenas etiqueta nome a apresentar, que pode editar. Os centros de administração mostram este nome a apresentar para uma etiqueta e o nome de rótulo. O nome de etiqueta é o nome inicial que especificou quando a etiqueta foi criada pela primeira vez e esta propriedade é utilizada pelo serviço de back-end para fins de identificação.

- Quaisquer cadeias de caracteres localizadas para as etiquetas não são migradas. Tem de definir novas cadeias de caracteres localizadas para as etiquetas migradas nos centros de administração.

- Após a migração, ao editar uma etiqueta migrada no portal do Azure, a mesma alteração é refletida automaticamente nos centros de administração. No entanto, ao editar uma etiqueta migrada em um dos centros de administração, terá de voltar para o portal do Azure, **unificada do Azure Information Protection – etiquetagem** painel e selecione **Publish**. Esta ação adicional é necessário para clientes do Azure Information Protection recolher as alterações de etiqueta.

### <a name="label-settings-that-are-not-supported-in-the-admin-centers"></a>Definições de etiquetas que não são suportadas nos centros de administração

Utilize a seguinte tabela para identificar quais as definições de configuração de uma etiqueta migrada não são suportadas pela segurança do Office 365 e Centro de conformidade, o Centro de segurança do Microsoft 365 ou o Centro de conformidade da Microsoft. Se tiver etiquetas com estas definições, quando a migração estiver concluída, utilize as orientações de administração na coluna final antes de publicar as etiquetas em um dos centros de administração.

Se não tiver a certeza de como as etiquetas são configuradas, ver as respetivas definições no portal do Azure. Se precisar de ajuda com este passo, consulte [configurar a política do Azure Information Protection](configure-policy.md).

Clientes do Azure Information Protection podem utilizar todas as definições de etiqueta listadas sem problemas, porque eles continuam a transferir as etiquetas do portal do Azure.

|Configuração de etiqueta|Suportados pelos clientes de etiquetas unificados| Documentação de orientação para os centros de administração|
|-------------------|---------------------------------------------|-------------------------|
|Estado ativado ou desativado<br /><br />Notas: Não sincronizados para os centros de administração |Não aplicável|O equivalente é se a etiqueta é publicada ou não. |
|Cor da etiqueta que selecione da lista ou especifique usando código RGB |Sim|Nenhuma opção de configuração para as cores de etiqueta. Em vez disso, pode configurar as cores de etiqueta no portal do Azure.|
|Proteção baseada na cloud ou um modelo predefinido a utilizar a proteção baseada em HYOK |Não|Nenhuma opção de configuração para modelos predefinidos. Não é recomendável que publicar uma etiqueta com esta configuração.|
|Proteção baseada na cloud com as permissões definidas pelo utilizador para o Word, Excel e PowerPoint |Não|Nenhuma opção de configuração para permissões definidas pelo utilizador para estas aplicações do Office. Não é recomendável que publicar uma etiqueta com esta configuração. Se o fizer, os resultados de aplicar a etiqueta estão listados na [seguinte tabela](#comparing-the-behavior-of-protection-settings-for-a-label).|
|Proteção baseada em HYOK usando permissões definidas pelo utilizador para o Outlook (não reencaminhar) |Não|Nenhuma opção de configuração para HYOK. Não é recomendável que publicar uma etiqueta com esta configuração. Se o fizer, os resultados de aplicar a etiqueta estão listados na [seguinte tabela](#comparing-the-behavior-of-protection-settings-for-a-label).|
|Remover proteção |Não|Nenhuma opção de configuração para remover a proteção. Não é recomendável que publicar uma etiqueta com esta configuração.<br /><br /> Se publicar esta etiqueta, quando aplicado, será possível remover a proteção se estava anteriormente aplicada por uma etiqueta. Se a proteção estava anteriormente aplicada independentemente de uma etiqueta, a proteção é preservada.|
|Tipo de letra personalizado e a cor do tipo de letra personalizados pelo código RGB para marcas visuais (cabeçalho, rodapé, marca d'água)|Sim|Configuração para marcas visuais está limitada a uma lista de cores e tamanhos de fonte. Pode publicar esta etiqueta sem alterações, embora não pode ver os valores configurados nos centros de administração. <br /><br />Para alterar estas opções, pode utilizar o portal do Azure. No entanto, para uma administração mais fácil, considere alterar a cor para uma das opções listadas nos centros de administração.|
|Variáveis em marcas visuais (cabeçalho, rodapé)|Não|Se publicar esta etiqueta sem alterações, as variáveis são apresentadas como texto em clientes em vez de apresentam os valores dinâmicos. Antes de publicar a etiqueta, edite as cadeias de caracteres para remover as variáveis.|
|Marcas visuais por aplicação|Não|Se publicar esta etiqueta sem alterações, as variáveis de aplicação são apresentadas como texto em clientes em todas as aplicações em vez de apresentam suas cadeias de caracteres de texto em aplicações escolhidas. Publicar esta etiqueta apenas se é adequado para todas as aplicações e editar as cadeias de caracteres para remover as variáveis de aplicação.|
|Condições e configurações associadas <br /><br />Notas: Inclui a etiquetagem automática e recomendada e suas descrições|Não aplicável|Reconfigure suas condições utilizando automática etiquetagem como uma configuração separada de configurações de rótulo.|

### <a name="comparing-the-behavior-of-protection-settings-for-a-label"></a>Comparar o comportamento das definições de proteção para uma etiqueta

Utilize a seguinte tabela para identificar como a mesma definição de proteção para uma etiqueta pode ter um comportamento diferente, dependendo se é utilizado pelo cliente do Azure Information Protection (versões de disponibilidade geral e versão de pré-visualização atual), a pré-visualização atual versão do cliente etiquetagem unificado do Azure Information Protection, ou por aplicações do Office com a etiquetagem incorporada (também conhecido como "nativo Office etiquetagem").

Se não tiver a certeza de como as suas definições de proteção são configuradas, ver suas configurações no **proteção** painel, no portal do Azure. Se precisar de ajuda com este passo, consulte [para configurar uma etiqueta para as definições de proteção](configure-policy-protection.md#to-configure-a-label-for-protection-settings).

Definições de proteção que se comportam da mesma forma, não estão listadas na tabela, com as seguintes exceções:
- Quando utilizar aplicações do Office com a etiquetagem incorporadas, as etiquetas não estão visíveis no Explorador de ficheiros, a menos que também instala o cliente de etiquetagem unificado do Azure Information Protection.
- Quando utilizar aplicações do Office com a etiquetagem incorporada, se a proteção estava anteriormente aplicada independentemente de uma etiqueta, essa proteção é preservada [[1]](#footnote-1).

|Definição de proteção para uma etiqueta |Cliente do Azure Information Protection|O Azure Information Protection unified cliente etiquetagem| Aplicações do Office com a etiquetagem incorporada
|-------------------|-----------------------------------|-----------------------------------------------------------|---------------
|Azure (chave da cloud) com permissões definidas pelo utilizador para o Word, Excel, PowerPoint e o Explorador de ficheiros:| Visível no Word, Excel, PowerPoint e o Explorador de ficheiros <br /><br /> Quando a etiqueta é aplicada:<br /><br /> -Os utilizadores que introduzam as permissões personalizadas que, em seguida, são aplicadas como proteção com uma chave com base na cloud| Não é visível |Visível no Word, Excel, PowerPoint e Outlook: <br /><br /> Quando a etiqueta é aplicada:<br /><br /> -Não é pedida aos utilizadores permissões personalizadas e sem proteção é aplicada <br /><br /> -Se a proteção estava anteriormente aplicada independentemente de uma etiqueta, essa proteção é preservada [[1]](#footnote-1)|
|HYOK (AD RMS) com um modelo:| Visível no Word, Excel, PowerPoint, Outlook e o Explorador de ficheiros<br /><br /> Quando esta etiqueta é aplicada: <br /><br />-A proteção do HYOK é aplicada a documentos e e-mails | Visível no Word, Excel, PowerPoint, Outlook e o Explorador de ficheiros  <br /><br /> Quando esta etiqueta é aplicada: <br /><br />-Sem proteção é aplicada e remover a proteção [[2]](#footnote-2) se estava anteriormente aplicada por uma etiqueta <br /><br />-Se a proteção estava anteriormente aplicada independentemente de uma etiqueta, essa proteção é preservada |Visível no Word, Excel, PowerPoint e Outlook <br /><br /> Quando esta etiqueta é aplicada: <br /><br />-Sem proteção é aplicada e remover a proteção [[2]](#footnote-2) se estava anteriormente aplicada por uma etiqueta <br /><br />-Se a proteção estava anteriormente aplicada independentemente de uma etiqueta, essa proteção é preservada [[1]](#footnote-1) |
|HYOK (AD RMS) com permissões definidas pelo utilizador para o Word, Excel, PowerPoint e o Explorador de ficheiros:| Visível no Word, Excel, PowerPoint e o Explorador de ficheiros<br /><br /> Quando esta etiqueta é aplicada:<br /><br /> -A proteção do HYOK é aplicada a documentos e e-mails| Visível no Word, Excel e PowerPoint <br /><br /> Quando esta etiqueta é aplicada: <br /><br />-Proteção não é aplicada e remover a proteção [[2]](#footnote-2) se estava anteriormente aplicada por uma etiqueta <br /><br />-Se a proteção estava anteriormente aplicada independentemente de uma etiqueta, essa proteção é preservada|Visível no Word, Excel e PowerPoint <br /><br /> Quando esta etiqueta é aplicada: <br /><br />-Proteção não é aplicada e remover a proteção [[2]](#footnote-2) se estava anteriormente aplicada por uma etiqueta <br /><br />-Se a proteção estava anteriormente aplicada independentemente de uma etiqueta, essa proteção é preservada |
|HYOK (AD RMS) com permissões definidas pelo utilizador para o Outlook:|Visível no Outlook<br /><br />Quando esta etiqueta é aplicada:<br /><br />-Não utilizar não reencaminhar a proteção do HYOK é aplicada a mensagens de correio eletrónico|Visível no Outlook<br /><br />Quando esta etiqueta é aplicada:<br /><br /> -Proteção não é aplicada e removida [[2]](#footnote-2) se estava anteriormente aplicada por uma etiqueta <br /><br />-Se a proteção estava anteriormente aplicada independentemente de uma etiqueta, essa proteção é preservada|Visível no Outlook<br /><br />Quando esta etiqueta é aplicada:<br /><br />-Proteção não é aplicada e removida [[2]](#footnote-2) se estava anteriormente aplicada por uma etiqueta <br /><br />-Se a proteção estava anteriormente aplicada independentemente de uma etiqueta, essa proteção é preservada [[1]](#footnote-1)|

###### <a name="footnote-1"></a>Nota de rodapé 1

No Outlook para Mac, a proteção é mantida com uma exceção: Quando uma mensagem de e-mail tenha sido protegida com a opção de criptografar apenas, essa proteção é removida.


###### <a name="footnote-2"></a>Nota de rodapé 2

É remover a proteção se o utilizador tiver um direito de utilização ou da função que suporta esta ação:
- O [direito de utilização](configure-usage-rights.md#usage-rights-and-descriptions) exportação ou controlo total.
- A função de [emissor do Rights Management ou proprietário do Rights Management](configure-usage-rights.md#rights-management-issuer-and-rights-management-owner), ou [Superutilizador](configure-super-users.md).

Se o utilizador não tem uma destas funções ou direitos de utilização, a etiqueta não é aplicada e a proteção original é preservada.


## <a name="to-migrate-azure-information-protection-labels"></a>Para migrar as etiquetas do Azure Information Protection

Utilize as seguintes instruções para migrar o seu inquilino e etiquetas do Azure Information Protection para utilizar a etiquetagem unificada novo armazenam.

Tem de ser um administrador global para migrar as suas etiquetas.

1. Se ainda não o tiver feito, abra uma nova janela do browser e [inicie sessão no portal do Azure](configure-policy.md#signing-in-to-the-azure-portal). Em seguida, navegue para o painel **Azure Information Protection**.
    
    Por exemplo, no hub menu, clique em **todos os serviços** e comece a escrever **informações** na caixa Filtro. Selecione **Azure Information Protection**.

2. Do **Manage** opção de menu, selecione **Unified etiquetagem (pré-visualização)**.

3. Sobre o **unificada do Azure Information Protection – etiquetagem** painel, selecione **ativar** e siga as instruções online.
    
    Verifique se a opção para ativar não estiver disponível, o **Unified etiquetagem estado**: Se vir **Activated**, o seu inquilino já está a utilizar a loja de etiquetagem unificada e não é necessário para migrar as suas etiquetas.

Para as etiquetas que migrado com êxito, eles podem agora ser utilizados pelo [os clientes e serviços que suportam a etiquetagem unificada](#clients-and-services-that-support-unified-labeling). No entanto, é necessário publicar primeiro estas etiquetas dos centros de administração: Segurança do Office 365 & o Centro de conformidade, o Centro de segurança do Microsoft 365 ou o Centro de conformidade do Microsoft 365.

> [!IMPORTANT]
> Se editar as etiquetas fora do portal do Azure, para clientes do Azure Information Protection, regresse a este **unificada do Azure Information Protection – etiquetagem** painel e selecione **Publish**.

### <a name="clients-and-services-that-support-unified-labeling"></a>Os clientes e serviços que suportam a etiquetagem unificada

Para confirmar se os clientes e serviços que utiliza suportam a etiquetagem unificado, consulte sua documentação para verificar se podem utilizar etiquetas de sensibilidade, que são publicadas a partir de um dos centros de administração: Segurança do Office 365 & o Centro de conformidade, o Centro de segurança do Microsoft 365 ou o Centro de conformidade do Microsoft 365. 

##### <a name="clients-that-currently-support-unified-labeling-include"></a>Os clientes que atualmente suportam a etiquetagem unificada incluem:

- O [do Azure Information Protection unified cliente etiquetagem para o Windows](./rms-client/unifiedlabelingclient-version-release-history.md) - na pré-visualização

- Aplicações do Office que estão em várias fases de disponibilidade. Para obter mais informações, consulte a **em que a funcionalidade está disponível hoje?** secção partir [aplicar etiquetas de sensibilidade aos seus documentos e e-mail do Office](https://support.office.com/en-us/article/apply-sensitivity-labels-to-your-documents-and-email-within-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9) na documentação do Office.
    
- Aplicações de fornecedores de software e desenvolvedores que utilizam o [SDK do Microsoft Information Protection](https://docs.microsoft.com/en-us/information-protection/develop/overview).

##### <a name="services-that-currently-support-unified-labeling-include"></a>Os serviços que suportam atualmente a etiquetagem unificada incluem:

- Proteção contra ameaças do Azure do Windows Defender

- Microsoft Cloud App Security
    
    Este serviço suporta etiquetas antes da migração para o arquivo de etiquetagem unificado e após a migração, usando a seguinte lógica:
    
    - Se no Centro de administração tem as etiquetas mesmo que os no portal do Azure: Etiquetas unificadas são obtidas a partir de centros de administração. Para selecionar estas etiquetas no Cloud App Security, pelo menos uma etiqueta tem de ser publicada pelo menos um utilizador.
    
    - Se no Centro de administração não tem as etiquetas mesmo que os no portal do Azure: Etiquetas unificadas não são utilizadas a partir de centros de administração e, em vez disso, as etiquetas são obtidas a partir do portal do Azure.

- Serviços de fornecedores de software e desenvolvedores que utilizam o [SDK do Microsoft Information Protection](https://docs.microsoft.com/en-us/information-protection/develop/overview).

## <a name="next-steps"></a>Passos Seguintes

Para obter mais informações sobre as etiquetas migradas que agora pode ser configurado e publicado em um dos centros de administração, consulte [descrição geral das etiquetas de sensibilidade](/Office365/SecurityCompliance/sensitivity-labels).

Para ler a mensagem de blogue de anúncio: [Anunciando a disponibilidade do unified a etiquetagem de gestão no Centro de conformidade e segurança do](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Announcing-the-availability-of-unified-labeling-management-in/ba-p/262492).
