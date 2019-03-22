---
title: O cliente do Azure Information Protection
description: O Microsoft Azure Information Protection fornece uma solução de servidor cliente que ajuda a proteger os dados de uma organização. O cliente (o cliente do Azure Information Protection ou o cliente Rights Management) está integrado nas aplicações executadas em computadores e dispositivos móveis.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 03/20/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: a6fa85be-f92a-4e00-9efc-9dbfd4dfbfcb
ms.suite: ems
ms.openlocfilehash: f797ffc63e38c15649e5bf590ad11dd5a009e957
ms.sourcegitcommit: 3a3f1051c5a58c2bd2f230f1c8ece919df3dc23e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/20/2019
ms.locfileid: "58221019"
---
# <a name="the-client-side-of-azure-information-protection"></a>O lado do cliente do Azure Information Protection

>*Aplica-se a: Serviços de gestão de direitos do Active Directory [do Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 com SP1, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2*

O Azure Information Protection fornece uma solução de servidor cliente que ajuda a proteger os documentos e os e-mails de uma organização:

- O cliente pode ser o cliente do Azure Information Protection ou do Rights Management e está integrado nas aplicações executadas em computadores e dispositivos móveis. 

- O serviço reside na cloud (Azure Information Protection, que utiliza o serviço Azure Rights Management para a proteção de dados) ou no local (Active Directory Rights Management Services, mais comumente conhecido como o AD RMS). 

O cliente do Azure Information Protection suporta classificação e proteção com a etiquetagem, bem como proteção sem etiquetagem. Este cliente está integrado nas aplicações do Office e tem de ser instalado em separado.

O cliente Rights Management (RMS) é instalado automaticamente com algumas aplicações, tais como as aplicações do Office, o cliente do Azure Information Protection, a aplicação de partilha RMS e as aplicações otimizadas para o RMS de fornecedores de software. No entanto, também pode ser [instalado por si só](https://www.microsoft.com/en-us/download/details.aspx?id=38396), para suportar [sincronização de arquivos de bibliotecas protegidas por IRM e o OneDrive para empresas](https://support.office.com/article/Deploy-the-new-OneDrive-sync-client-in-an-enterprise-environment-3f3a511c-30c6-404a-98bf-76f95c519668)e para os programadores que pretendam integrar a gestão de direitos proteção em aplicativos de linha de negócio.

## <a name="choose-which-azure-information-protection-client-to-use"></a>Escolha qual cliente Azure Information Protection para utilizar

O **cliente Azure Information Protection** que transfere as etiquetas e definições de política do portal do Azure está em disponibilidade geral e tem uma versão de pré-visualização para testar novas funcionalidades e correções. Para obter mais informações sobre estas versões do cliente, consulte o [cliente Azure Information Protection: Política de histórico e suporte de lançamento de versão](client-version-release-history.md). 

O **do Azure Information Protection unified cliente etiquetagem** transfere etiquetas e as definições de política a partir do Centro de conformidade e segurança do Office 365. Este cliente está atualmente em pré-visualização para fins de teste. Para obter mais informações sobre esta versão do cliente, consulte o [do Azure Information Protection unified cliente etiquetagem: Informações de lançamento de versão](unifiedlabelingclient-version-release-history.md).

O cliente deve instalar?

- Se estiver a implementar em produção, utilize o cliente do Azure Information Protection que está disponível em geral.

- Se estiver numa fase de teste e avaliação, utilize um dos clientes de pré-visualização.
    
    Atualmente, as versões de pré-visualização do cliente do Azure Information Protection e o cliente de etiquetagem unificado do Azure Information Protection não tem paridade para as respetivas funcionalidades. No entanto, contam com essa lacuna para fechar e, em seguida, novas funcionalidades a adicionar apenas para o Azure Information Protection unified cliente etiquetagem. Por esse motivo, recomendamos que testar com o cliente de etiquetagem unificado do Azure Information Protection se a sua atual conjunto de recursos e funcionalidade de cumprem os requisitos comerciais. Se não, ou se tiver configurado as etiquetas no portal do Azure que ainda não ainda [migrados para a loja de etiquetagem unificada](../configure-policy-migrate-labels.md), utilizar o cliente do Azure Information Protection.

### <a name="feature-comparisons-for-the-clients"></a>Comparação entre recursos para os clientes

Utilize a tabela seguinte para ajudar a comparar as funcionalidades são suportadas pelas duas versões de pré-visualização atual.

|Funcionalidade|Cliente do Azure Information Protection|Azure Information Protection<br /> cliente de etiquetagem unificada|
|-------|-----------------------------------|----------------------------------------------------|
|Etiquetagem ações: Manual, automática, recomendado| Sim | Sim |
|Central de relatórios (análise):| Sim | Sim |
|Repor as definições e exportar registos:| Sim | Sim |
|Permissões definidas pelo utilizador:| Sim | Para Outlook única (efetue não reencaminhar) |
|Permissões personalizadas:| Sim | Apenas o Explorador de ficheiros <br /><br /> Nas aplicações do Office, como alternativa, podem selecionar os utilizadores **informações do ficheiro** > **Proteger documento** > **restringir acesso** |
|Barra do Information Protection nas aplicações do Office:| Sim | Sim, com limitações:<br /><br /> -Sem título ou a dica de ferramenta personalizável<br /><br /> -Cor de etiqueta não é apresentado para a etiqueta aplicada|
|Explorador de ficheiros, faça duplo clique ações:| Sim | Sim, com limitações:<br /><br /> -Não é possível proteger documentos PDF para o formato. ppdf <br /><br />  -Sem suporte para o modo apenas de proteção|
|Um visualizador para ficheiros protegidos:| Sim | Sim, com limitações:<br /><br /> -Para ficheiros protegidos genericamente (. pfile), ao contrário do Visualizador do cliente do Azure Information Protection, não existe nenhuma capacidade para guardar as alterações para o ficheiro aberto originalmente.|
|Comandos do PowerShell:| Sim | Sim, com limitações:<br /><br />-Cmdlets incluídos: [Get-AIPFileStatus](/powershell/module/azureinformationprotection/get-aipfilestatus), [Set-AIPFileClassification](/powershell/module/azureinformationprotection/set-aipfileclassification), [Set-AIPFileLabel](/powershell/module/azureinformationprotection/set-aipfilelabel), [Set-AIPAuthentication](/powershell/module/azureinformationprotection/set-aipauthentication) <br /><br />-Cmdlets que se ligam diretamente a um serviço de proteção não estão incluídos|
|Suporte offline para ações de proteção:| Sim | Sim, com limitações: <br /><br />-Para comandos de Explorador de ficheiros e o PowerShell, o utilizador tem de estar ligado à Internet para proteger ficheiros. |
|Suporte HYOK:| Sim | Não<br /><br /> As etiquetas que migra a partir do portal do Azure e que estão configurados para proteção do HYOK são apresentadas pelo cliente etiquetagem unificado do Azure Information Protection, mas não se aplicam a proteção. |
|Registo de utilização no Visualizador de eventos:| Sim | Não|
|Herança de etiqueta de anexos de e-mail:| Sim | Não |
|Exibir o botão não reencaminhar no Outlook| Sim | Não |
|[Personalizações](client-admin-guide-customizations.md#available-advanced-client-settings) que incluem:<br />-Etiqueta de predefinida para o e-mail<br />-Ativar permissões personalizadas <br />-Suporte de S/MIME<br />-Uma opção de problema de relatório| Sim | Não |
|Scanner para arquivos de dados no local:| Sim | Não |
|Controlar e revogar:| Sim | Não |
|Modo apenas de proteção (sem etiquetas):| Sim | Não |
|Faça o botão não reencaminhar no Outlook:| Sim | Não |
|Suporte a vários idiomas:| Sim | Não |
|Suporte para o AD RMS:| Sim | A ação seguinte só é suportada:<br /><br /> -O Visualizador pode abrir documentos protegidos quando implementa o [extensão de dispositivo de móveis de serviços do Rights Management Active Directory](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn673574\(v=ws.11\))|

#### <a name="functional-comparison-for-the-clients"></a>Comparação funcional para os clientes

Quando ambos os clientes suportam a mesma funcionalidade, utilize a tabela seguinte para ajudar a identificar algumas diferenças funcionais entre as duas versões de pré-visualização atual.

|Funcionalidade |Cliente do Azure Information Protection|Azure Information Protection<br /> cliente de etiquetagem unificada|
|--------------|-----------------------------------|-----------------------------------------------------------|
|Programa de configuração:| Opção para instalar a política de demonstração local | Nenhuma política de demonstração local|
|Etiqueta de seleção e apresentar quando aplicada nas aplicações do Office:|Partir do **Protect** botão na faixa de opções <br /><br /> A partir da barra de Information Protection (de barra horizontal sob a faixa de opções)|Partir do **sensibilidade** botão na faixa de opções<br /><br /> A partir da barra de Information Protection (de barra horizontal sob a faixa de opções)|
|Gerir a barra do Information Protection nas aplicações do Office:|Para os utilizadores: <br /><br />-Opção para mostrar ou ocultar a barra do **Protect** botão na faixa de opções<br /><br />-Quando um utilizador seleciona para ocultar a barra, por predefinição, a barra está oculta nessa aplicação, mas continua a apresentar automaticamente nas aplicações recentemente abertas <br /><br /> Para administradores: <br /><br />-Definições de política Mostrar ou ocultar a barra quando uma aplicação automaticamente pela primeira vez é aberto e controlar se a barra automaticamente permanece oculta para aplicações recentemente abertas após um utilizador seleciona para ocultar a barra|Para os utilizadores: <br /><br />-Opção para mostrar ou ocultar a barra do **sensibilidade** botão na faixa de opções<br /><br />-Quando um utilizador seleciona para ocultar a barra, a barra está oculta nessa aplicação e também nas aplicações recentemente abertas <br /><br />Para administradores: <br /><br />-Sem definições de política para gerir a barra|
|Cor da etiqueta: | Configurar no portal do Azure | Mantidos após a migração de etiqueta para o Office 365 <br /><br /> Novas etiquetas criadas no Centro de conformidade de segurança e não tem uma cor|
|Atualização da política: | Quando se abre uma aplicação do Office <br /><br /> Quando rato para classificar e proteger um ficheiro ou pasta <br /><br />Quando executa os cmdlets do PowerShell para etiquetagem e proteção<br /><br />A cada 24 horas | Quando se abre uma aplicação do Office <br /><br /> Quando rato para classificar e proteger um ficheiro ou pasta <br /><br />Quando executa os cmdlets do PowerShell para etiquetagem e proteção<br /><br />Cada 4 horas|
|Formatos com suporte para PDF:| Proteção: <br /><br /> -Standard ISO para a encriptação de PDF (predefinição) <br /><br /> - .ppdf <br /><br /> Consumo: <br /><br /> -Standard ISO para a encriptação de PDF <br /><br />- .ppdf<br /><br />-Proteção de IRM do SharePoint| Proteção: <br /><br /> -Standard ISO para a encriptação de PDF <br /><br /> <br /><br /> Consumo: <br /><br /> -Standard ISO para a encriptação de PDF <br /><br />- .ppdf<br /><br />-Proteção de IRM do SharePoint|
|Cmdlets suportados:| Todos os cmdlets documentados para [AzureInformatioProtection](/powershell/module/azureinformationprotection) | Set-AIPFileClassification e Set-AIPFileLabel não suportam o *proprietário* parâmetro ou bibliotecas do SharePoint Server <br /><br /> Além disso, há um único comentário de "Nenhuma etiqueta para aplicar" para todos os cenários em que uma etiqueta não é aplicada <br /><br /> Set-AIPFileLabel não suporta o *EnableTracking* parâmetro <br /><br /> Get-AIPFileStatus não retorna as informações de rótulo de outros inquilinos e não apresenta o *RMSIssuedTime* parâmetro<br /><br />Além disso, o *LabelingMethod* parâmetro para Get-AIPFileStatus apresenta **privilegiado**, **padrão**, ou **automática** em vez de **Manual** ou **automática**. Para obter mais informações, consulte a [documentação online](/powershell/module/azureinformationprotection/get-aipfilestatus).|
|Pedidos de justificação (se configurada) por ação no Office: | Frequência de: Por ficheiro <br /><br /> Reduzir o nível de sensibilidade <br /><br /> Remover uma etiqueta<br /><br /> Remover a proteção | Frequência de: Por sessão <br /><br /> Reduzir o nível de sensibilidade<br /><br /> Remover uma etiqueta|
|Remover aplicada ações de etiqueta: | É pedido ao utilizador para confirmar <br /><br />Etiqueta predefinida ou etiqueta automática (se configurada) não é aplicada automaticamente da próxima vez que a aplicação do Office abre o ficheiro.  <br /><br />| Não é pedido ao utilizador para confirmar<br /><br /> Etiqueta predefinida ou etiqueta automática (se configurada) é aplicada automaticamente da próxima vez que a aplicação do Office abre o ficheiro.|
|Classificação automática e recomendada: | Configurado como [Etiquetar condições](../configure-policy-classification.md) no portal do Azure com tipos de informações internas e condições personalizadas que utilizam frases ou expressões regulares <br /><br />Opções de configuração incluem: <br /><br />-Contagem exclusiva / não exclusiva <br /><br /> -Contagem mínima| Configurado no Centro de conformidade de segurança e com os tipos de informações confidenciais incorporadas e [tipos de informações personalizadas](https://docs.microsoft.com/office365/securitycompliance/create-a-custom-sensitive-information-type)<br /><br />Opções de configuração incluem:  <br /><br />-Apenas a contagem exclusiva <br /><br />-Mínimo e máxima contagem <br /><br />- E e ou de suporte com os tipos de informações <br /><br />-Dicionário palavra-chave<br /><br />-Confiança personalizável proximidade de caracteres e nível|

Para obter uma comparação mais detalhada das diferenças de comportamento para definições de proteção específico, consulte [comparar o comportamento das definições de proteção para uma etiqueta](../configure-policy-migrate-labels.md#comparing-the-behavior-of-protection-settings-for-a-label).

#### <a name="features-that-will-not-be-in-the-azure-information-protection-unified-labeling-client"></a>Funcionalidades não estarão disponíveis no cliente de etiquetagem unificado do Azure Information Protection

Embora o cliente de etiquetagem unificado do Azure Information Protection ainda está em desenvolvimento, as seguintes funcionalidades e as diferenças de comportamento do cliente do Azure Information Protection não estarão disponíveis em versões futuras para obter as informações do Azure Cliente de etiquetagem unificada de proteção: 

- Permissões personalizadas nas aplicações do Office: Word, Excel e PowerPoint

- Controlar e revogar a partir de aplicações do Office e o Explorador de ficheiros

- Barra de título e descrição do Information Protection

- Suporte offline para ações de proteção no PowerShell e o Explorador de ficheiros

- Modo apenas de proteção (sem etiquetas)

- Proteger o documento PDF como formato. ppdf

- Exibir o botão não reencaminhar no Outlook

- Política de demonstração

- Justificação para remover a proteção

- Pedido de confirmação antes de eliminar uma etiqueta aplicada

- Uma ligação de problema na caixa de diálogo de ajuda e Feedback de relatório

- Etiqueta de um documento do Office usando uma propriedade personalizada existente (SyncPropertyName e SyncPropertyState definições de cliente avançadas)

- Separar os cmdlets do PowerShell para ligar a um serviço de Rights Management

- Proteção única do AD RMS


##### <a name="parent-labels-and-their-sublabels"></a>Etiquetas de principal e respetivas subetiquetas 

O cliente do Azure Information Protection não suporta as configurações que especifique uma etiqueta principal com subetiquetas. Estas configurações incluem a especificação de uma etiqueta predefinida e uma etiqueta para a classificação recomendada ou automática. Quando uma etiqueta tiver subetiquetas, pode especificar uma das subetiquetas, mas não a etiqueta principal.

Para paridade, o cliente de etiquetagem unificado do Azure Information Protection também não suporta a aplicar etiquetas de principal que tem subetiquetas, mesmo que pode selecionar estas etiquetas no Centro de conformidade e segurança do Office 365. Neste cenário, o cliente de etiquetagem unificado do Azure Information Protection não será aplicada a etiqueta principal.

## <a name="see-also"></a>Consulte também
Utilize a seguinte documentação quando precisar de mais informações sobre como implementar e utilizar estes clientes:

- [Cliente do Azure Information Protection](AIP-client.md)

- [O Azure Information Protection unified cliente etiquetagem](unifiedlabelingclient-version-release-history.md)

- [Notas de implementação do cliente RMS](client-deployment-notes.md)

Embora o cliente do Azure Information Protection pode ser utilizado com o AD RMS, o cliente do Azure Information Protection é mais adequado para funcionar com os seus serviços do Azure; O Azure Information Protection e o respetivo serviço de proteção de dados, Azure Rights Management. Para obter uma comparação lado do serviço do Azure Information Protection, consulte [comparar o Azure Information Protection e o AD RMS](../compare-on-premise.md).
