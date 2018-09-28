---
title: Migrar o Azure Information Protection etiquetas para o Centro de conformidade e segurança do Office 365
description: Migre as etiquetas do Azure Information Protection para o Centro de conformidade e segurança do Office 365 para o cliente suporta a etiquetagem unificada.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 09/28/2018
ms.topic: article
ms.service: information-protection
ms.reviewer: demizets
ms.suite: ems
ms.openlocfilehash: 64063af186f01a5829b7aa668260928e3b13656d
ms.sourcegitcommit: 304702a3f2f2ab2b32493c4aedeb5ee8424b925c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/27/2018
ms.locfileid: "47415014"
---
# <a name="how-to-migrate-azure-information-protection-labels-to-the-office-365-security--compliance-center"></a>Como migrar as etiquetas do Azure Information Protection para o Centro de conformidade e segurança do Office 365

>*Aplica-se a: [do Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

> [!IMPORTANT]
> Esta funcionalidade está em pré-visualização e migra o seu inquilino para uma nova plataforma que também está em pré-visualização. Não é possível inverter a migração. A nova plataforma suporta a etiquetagem unificada, para que as etiquetas que criar e gerir podem ser utilizadas por vários clientes e serviços.

Migrar as etiquetas, se pretender conseguir utilizá-los no Centro de conformidade, onde podem ser publicados e, em seguida, baixados por de segurança do Office 365 e [clientes que suportam a etiquetagem unificada](#clients-that-support-unified-labeling). O cliente do Azure Information Protection continua a transferir as etiquetas com a política do Azure Information Protection a partir do portal do Azure. 

Depois de ter migrado as etiquetas, em seguida, pode efetuar alterações aos mesmos no portal do Azure ou a segurança do Office 365 e o Centro de conformidade e os respetivos clientes irão transferir a mesma alteração.

## <a name="considerations-for-unified-labels"></a>Considerações para procurar etiquetas de unificada

Antes de migrar as etiquetas, certifique-se de que está ciente das seguintes alterações e considerações:

- Nem todos os clientes atualmente suportam etiquetas unificadas. Certifique-se de que tenha [suportado clientes](#clients-that-support-unified-labeling) e estar preparado para a administração em tanto o portal do Azure (para clientes que não suportam etiquetas unificadas) e o Centro de segurança e conformidade (para o cliente que suportam etiquetas unificadas ).

- Se estiver no meio de definir e configurar as etiquetas que pretende utilizar, recomendamos que conclua este processo com o portal do Azure e, em seguida, migre as etiquetas. Esta estratégia evita a duplicação de etiquetas durante o processo de migração, que, em seguida, vai ter de ser editado no Centro de conformidade e segurança do.

- As políticas, incluindo definições de política e quem tem acesso aos mesmos (políticas de âmbito) e todas as definições de cliente avançadas não são migradas. Para que essas alterações não são migradas, terá de configurar as opções relevantes no Centro de conformidade de segurança e, depois das etiquetas são migradas.
    
    Para uma experiência de usuário mais consistente, recomendamos que publique as etiquetas mesmo no mesmos âmbitos no Centro de conformidade e segurança do.

- Nem todas as definições de uma etiqueta migrada são compatíveis com o Centro de conformidade e segurança. Utilize a tabela no [Etiquetar definições que não são suportadas no Centro de conformidade e segurança do](#label-settings-that-are-not-supported-in-the-security--compliance-center) secção para ajudar a identificar estas definições e se deve excluir as etiquetas migradas de publicação na segurança & Centro de conformidade.

- Modelos de proteção:
    
    - Modelos que utilizam uma chave com base na cloud e que fazem parte de uma configuração de etiqueta também são migrados com a etiqueta. Outros modelos de proteção não são migrados. 
    
    - Depois de uma etiqueta com as definições de proteção com base na cloud foi migrada, o âmbito resultante do modelo de proteção é o âmbito definido no portal do Azure (ou ao utilizar o módulo do ADDRM PowerShell) e o âmbito definido na segurança & Centro de conformidade. 

- Quando migra as etiquetas, verá a migração resulta apresentar se uma etiqueta foi **criado**, **atualizado**, ou **renomeado** devido à duplicação:

    - Quando é criada uma etiqueta, em seguida, pode publicá-lo no Centro de segurança e conformidade para disponibilizá-lo a aplicações e serviços.
    
    - Quando uma etiqueta for renomeada, tem, em seguida, editá-lo, que pode ser feito na segurança e o Centro de conformidade ou o portal do Azure. 

- Para cada etiqueta, o portal do Azure mostra apenas etiqueta nome a apresentar, que pode editar. O Centro de conformidade e segurança mostra este nome a apresentar para uma etiqueta e o nome de rótulo. O nome de etiqueta é o nome inicial que especificou quando a etiqueta foi criada pela primeira vez e esta propriedade é utilizada pelo serviço de back-end para fins de identificação.

- Quaisquer cadeias de caracteres localizadas para as etiquetas não são migradas. Tem de definir novas cadeias de caracteres localizadas para as etiquetas migradas no Centro de conformidade e segurança do.

- Após a migração, ao editar uma etiqueta migrada no portal do Azure, a mesma alteração é refletida automaticamente no Centro de conformidade e segurança do. No entanto, ao editar uma etiqueta migrada no Centro de conformidade e a segurança, tem de atualizar, em seguida, a etiqueta no portal do Azure para a etiqueta de retirada a alteração. Por exemplo, editar a **adicionar notas para utilização do administrador** caixa de **etiqueta** painel. 

- Etiquetagem unificado é ainda a implementar aos inquilinos. Se ainda não é suportada para o seu inquilino, a migração não será concluída com êxito e corretamente anular as alterações. Até que é suportado para todos os inquilinos, tem de utilizar uma ligação para aceder a opção para migrar o seu inquilino e etiquetas. Esta ligação é fornecida nas instruções que se seguem.

### <a name="label-settings-that-are-not-supported-in-the-security--compliance-center"></a>Definições de etiquetas que não são suportadas no Centro de conformidade e segurança do

Utilize a tabela seguinte para identificar quais as definições de configuração de uma etiqueta migrada não são suportadas para clientes que utilizam estas etiquetas, e se deve editar e publicar a etiqueta migrada no Centro de conformidade e segurança do. Se publicar as etiquetas que são identificadas a serem excluídos da publicação, não existem etiquetas exibir para os clientes que suportam a etiquetagem unificada.

Clientes do Azure Information Protection podem utilizar estas definições de etiqueta sem problemas, porque eles continuam a transferir as etiquetas do portal do Azure.

|Configuração de etiqueta|Suportado no Centro de conformidade e segurança do|Excluir da edição e no Centro de conformidade de segurança e de publicação|
|-------------------|---------------------------------------------|-------------------------|
|Estado ativado ou desativado<br /><br />Notas: Não sincronizados para o Centro de conformidade e segurança |Não aplicável|Não aplicável|
|Cor da etiqueta: selecione na lista ou especifique usando código RGB<br /><br />Notas: Cores de etiqueta não são suportadas pelo centro de conformidade e segurança do |Não aplicável|Não aplicável|
|Proteção baseada na cloud ou um modelo predefinido a utilizar a proteção baseada em HYOK |Não|Sim|
|Proteção baseada na cloud com as permissões definidas pelo usuário no Word, Excel e PowerPoint |Não|Sim|
|Proteção baseada em HYOK usando permissões definidas pelo usuário no Outlook para a opção não reencaminhar |Não|Sim|
|Remover proteção |Não|Sim|
|Marcas visuais (cabeçalho, rodapé, marca d'água): tipo personalizada e o tipo de letra personalizado cor por código RGB|Não|Recomendado se utilizar variáveis<br /><br />-Nos clientes, as variáveis são apresentadas como texto em vez de exibir os valores dinâmicos|
|Marcas visuais por aplicação|Não|Recomendado se utilizar variáveis<br /><br />-Nos clientes, as variáveis são apresentadas como texto em vez de exibir os valores dinâmicos|
|Condições e configurações associadas <br /><br />Notas: Inclui a etiquetagem automática e recomendada e suas descrições|Não aplicável|Não|


## <a name="to-migrate-azure-information-protection-labels"></a>Para migrar as etiquetas do Azure Information Protection

> [!IMPORTANT]
> Não migre as etiquetas até que tiver confirmado que pode editar e publicar as etiquetas de sensibilidade no Centro de conformidade e a segurança do Office 365. Etiquetas de sensibilidade estão a começar a implementar para inquilinos do Office 365, mas ainda não estão disponíveis para todos os inquilinos.
> 
> Para verificar: Centro de conformidade e da segurança do Office 365, aceda a **classificações** > **etiquetas**e ver se tem um **sensibilidade** separador. Se não vir neste separador, o seu inquilino ainda não está pronto para procurar etiquetas de sensibilidade e não deve migrar suas etiquetas do Azure Information Protection neste momento.

Quando tiver confirmado que o seu inquilino suporta etiquetas de sensibilidade no Centro de conformidade de segurança e, utilize as seguintes instruções para migrar o seu inquilino e etiquetas do Azure Information Protection.

1. Abra uma nova janela do browser e inicie sessão no portal do Azure, utilizando a seguinte hiperligação: https://portal.azure.com/?ActivateMigration=true#blade/Microsoft_Azure_InformationProtection/DataClassGroupEditBlade/migrationActivationBlade 

2. Sobre o **unificada do Azure Information Protection – etiquetagem** painel, selecione **ativar** e siga as instruções online.

Para as etiquetas que migrar com êxito, eles podem agora ser utilizados pelo [clientes que suportam a etiquetagem unificada](#clients-that-support-unified-labeling) quando estas etiquetas forem publicadas no Centro de conformidade e segurança do.


### <a name="clients-that-support-unified-labeling"></a>Clientes que suportam a etiquetagem unificada

Os clientes que atualmente suportam a etiquetagem unificada incluem:

- Aplicações do programa Insiders do Office. Para obter mais informações, consulte a [em que a funcionalidade está disponível hoje?](https://support.office.com/article/2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9?ad=US#bkmk_whereavailable) seção na documentação do Office.
    
- Os clientes de fornecedores de software e os desenvolvedores que utilizam o [MIP SDK](https://docs.microsoft.com/azure/information-protection/develop/mip/mip-sdk-reference).


## <a name="next-steps"></a>Passos Seguintes

Para obter mais informações sobre como configurar as etiquetas migradas no Centro de conformidade e segurança do Office 365, consulte a postagem no blog [anunciar a disponibilidade de unificação de etiquetagem de gestão no Centro de conformidade e segurança do](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Announcing-the-availability-of-unified-labeling-management-in/ba-p/262492) .