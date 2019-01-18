---
title: Preparar utilizadores e grupos para o Azure Information Protection
description: Verifique se tem as contas de utilizador e de grupo de que precisa para começar a classificar, etiquetar e proteger os documentos e e-mails da sua organização.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 12/06/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: afbca2d6-32a7-4bda-8aaf-9f93f5da5abc
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: e707e84ccfafc7b3ed161d05cadac9f2314ad3ae
ms.sourcegitcommit: 9dc6da0fb7f96b37ed8eadd43bacd1c8a1a55af8
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/18/2019
ms.locfileid: "54394289"
---
# <a name="preparing-users-and-groups-for-azure-information-protection"></a>Preparar utilizadores e grupos para o Azure Information Protection

>*Aplica-se a: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Antes de implementar o Azure Information Protection na sua organização, confirme que tem contas de utilizadores e grupos no Azure AD para o inquilino da sua organização.

Existem várias formas de criar estas contas de utilizadores e grupos. Veja a seguir:

- Crie os utilizadores no centro de administração do Office 365 e os grupos no centro de administração do Exchange Online.

- Crie os utilizadores e os grupos no portal do Azure.

- Crie os utilizadores e os grupos através de cmdlets do Azure AD PowerShell e do Exchange Online.

- Crie os utilizadores e os grupos no Active Directory no local e sincronize-os com o Azure AD.

- Crie os utilizadores e os grupos noutro diretório e sincronize-os com o Azure AD.

Quando cria utilizadores e grupos através dos primeiros três métodos desta lista, são automaticamente criados no Azure AD e o Azure Information Protection pode utilizar essas contas diretamente. No entanto, várias redes empresariais utilizam um diretório no local para criar e gerir utilizadores e grupos. O Azure Information Protection não pode utilizar estas contas diretamente; tem de as sincronizar com o Azure AD.

## <a name="how-users-and-groups-are-used-by-azure-information-protection"></a>Como o Azure Information Protection utiliza os utilizadores e os grupos

Existem três cenários de utilização de utilizadores e grupos com o Azure Information Protection:

**Para atribuir etiquetas aos utilizadores** ao configurar a política do Azure Information Protection para que possam ser aplicadas etiquetas a documentos e e-mails. Apenas os administradores podem selecionar estes utilizadores e grupos:

- A política do Azure Information Protection predefinida é atribuída automaticamente a todos os utilizadores no Azure AD do seu inquilino. No entanto, também pode atribuir etiquetas adicionais a utilizadores ou grupos especificados através de políticas de âmbito.     

**Para atribuir direitos de utilização e controlos de acesso** quando utiliza o serviço Azure Rights Management para proteger documentos e e-mails. Os administradores e os utilizadores podem selecionar estes utilizadores e grupos:

- Os direitos de utilização determinam se um utilizador pode abrir um documento ou e-mail e como o pode utilizar. Por exemplo, se apenas o pode ler, se o pode ler e imprimir ou se o pode ler e editar. 

- Os controlos de acesso incluem uma data de expiração e se o acesso exige uma ligação à Internet. 

**Para configurar o serviço Azure Rights Management** para suportar cenários específicos e, por conseguinte, apenas os administradores podem selecionar estes grupos. Os exemplos incluem a configuração dos seguintes elementos:

- Superutilizadores, de modo a que as pessoas ou os serviços designados possam abrir conteúdos encriptados, se tal for preciso para a recuperação de dados ou a Deteção de Dados Eletrónicos.

- Administração delegada do serviço Azure Rights Management.

- Controlos de inclusão para suportar uma implementação faseada.

## <a name="azure-information-protection-requirements-for-user-accounts"></a>Requisitos do Azure Information Protection para contas de utilizador

Para atribuir etiquetas:

- Todas as contas de utilizador no Azure AD podem ser utilizadas para configurar políticas de âmbito que atribuem etiquetas adicionais aos utilizadores.

Para atribuir direitos de utilização e controlos de acesso, assim como configurar o serviço Azure Rights Management:

- Para autorizar utilizadores, são utilizados dois atributos no Azure AD: **proxyAddresses** e **userPrincipalName**.

- O atributo **proxyAddresses do Azure AD** armazena todos os endereços de e-mail de uma conta e pode ser preenchido de diferentes formas. Por exemplo, um utilizador do Office 365 que tem uma caixa de correio do Exchange Online terá automaticamente um endereço de e-mail que é armazenado neste atributo. Se atribuir um endereço de e-mail alternativo a um utilizador do Office 365, também será guardado neste atributo. De igual modo, pode ser preenchido com os endereços de e-mail que são sincronizados a partir de contas no local. 

    O Azure Information Protection poderá utilizar qualquer valor neste atributo proxyAddresses do Azure AD, desde que o domínio tenha sido adicionado ao inquilino (um "domínio verificado"). Para obter mais informações sobre a verificação de domínios:

    - Para o Azure AD: [Adicionar um nome de domínio personalizado ao Azure Active Directory](/azure/active-directory/fundamentals/add-custom-domain)

    - Para o office 365: [Adicionar um domínio ao Office 365](/office365/admin/setup/add-domain?view=o365-worldwide)

- O atributo **userPrincipalName do Azure AD** é utilizado apenas quando uma conta do seu inquilino não tem valores no atributo proxyAddresses do Azure AD. Por exemplo, quando cria um utilizador no portal do Azure ou cria um utilizador do Office 365 que não tem uma caixa de correio.

### <a name="assigning-usage-rights-and-access-controls-to-external-users"></a>Atribuir direitos de utilização e controlos de acesso a utilizadores externos

Além de utilizar os atributos proxyAddresses e userPrincipalName do Azure AD para os utilizadores do seu inquilino, o Azure Information Protection também utiliza estes atributos da mesma forma para autorizar os utilizadores de outro inquilino.

Outros métodos de autorização:

- Para endereços de e-mail que não estão no Azure AD, Azure Information Protection pode autorizar estes quando os utilizadores são autenticados com uma conta Microsoft. No entanto, nem todos os aplicativos podem abrir conteúdo protegido, quando uma conta Microsoft é utilizada para autenticação. [Mais informações](./secure-collaboration-documents.md#supported-scenarios-for-opening-protected-documents)

- Quando é enviado um e-mail ao utilizar a encriptação de mensagens do Office 365 com novos recursos para um utilizador que não tem uma conta no Azure AD, o utilizador é primeiramente autenticado utilizando o federação com um fornecedor de identidade social ou com um código de acesso único. Em seguida, o endereço de e-mail especificado no e-mail protegido é utilizado para autorizar o utilizador.

## <a name="azure-information-protection-requirements-for-group-accounts"></a>Requisitos do Azure Information Protection para contas de grupo

Para atribuir etiquetas:

- Para configurar políticas de âmbito que atribuem etiquetas adicionais aos membros do grupo, pode utilizar qualquer tipo de grupo no Azure AD que tenha um endereço de e-mail que contenha um domínio verificado do inquilino do utilizador. Um grupo que tem um endereço de e-mail é frequentemente referido como um grupo com capacidade de correio.

    Por exemplo, pode utilizar um grupo de segurança com capacidade de correio, um grupo de distribuição (que pode ser estático ou dinâmico) e um grupo do Office 365. Não pode utilizar um grupo de segurança (dinâmico ou estático), porque este tipo de grupo não tem um endereço de e-mail.

Para atribuir direitos de utilização e controlos de acesso:

- Pode utilizar qualquer tipo de grupo no Azure AD que tenha um endereço de e-mail com um domínio verificado do inquilino do utilizador. Um grupo que tem um endereço de e-mail é frequentemente referido como um grupo com capacidade de correio. 

Para configurar o serviço Azure Rights Management:

- Pode utilizar qualquer tipo de grupo no Azure AD que tenha um endereço de e-mail de um domínio verificado do seu inquilino, com uma exceção. Essa exceção verifica-se quando configura controlos de inclusão para utilizar um grupo, que tem de ser um grupo de segurança no Azure AD para o seu inquilino.

- Pode utilizar qualquer grupo no Azure AD (com ou sem um endereço de e-mail) de um domínio verificado no seu inquilino para administração delegada do serviço Azure Rights Management.

### <a name="assigning-usage-rights-and-access-controls-to-external-groups"></a>Atribuir direitos de utilização e controlos de acesso a grupos externos

Além de utilizar o atributo proxyAddresses do Azure AD para os grupos do seu inquilino, o Azure Information Protection também utiliza este atributo da mesma forma para autorizar grupos de outro inquilino.

## <a name="using-accounts-from-active-directory-on-premises-for-azure-information-protection"></a>Utilizar contas do Active Directory no local para o Azure Information Protection

Se tiver contas geridas no local que pretende utilizar com o Azure Information Protection, terá de as sincronizar com o Azure AD. Para facilitar a implementação, recomendamos que utilize o [Azure AD Connect](/azure/active-directory/hybrid/whatis-azure-ad-connect). No entanto, pode utilizar qualquer método de sincronização de diretórios que ofereça o mesmo resultado.

Quando sincroniza as suas contas, não precisa de sincronizar todos os atributos. Para obter uma lista dos atributos que têm de ser sincronizados, consulte a [secção Azure RMS](/azure/active-directory/connect/active-directory-aadconnectsync-attributes-synchronized#azure-rms) na documentação do Azure Active Directory.

Na lista de atributos do Azure Rights Management, verá que são necessários os atributos do AD no local **mail**, **proxyAddresses** e **userPrincipalName** para a sincronização de utilizadores. Os valores de **mail** e **proxyAddresses** são sincronizados com o atributo proxyAddresses do Azure AD. Para obter mais informações, veja [How the proxyAddresses attribute is populated in Azure AD (Como é preenchido o atributo proxyAddresses no Azure AD)](https://support.microsoft.com/help/3190357/how-the-proxyaddresses-attribute-is-populated-in-azure-ad)

## <a name="confirming-your-users-and-groups-are-prepared-for-azure-information-protection"></a>Confirmar se os utilizadores e os grupos estão preparados para o Azure Information Protection

Pode utilizar o Azure AD PowerShell para confirmar que os utilizadores e os grupos podem ser utilizados com o Azure Information Protection. Também pode utilizar o PowerShell para confirmar os valores que podem ser utilizados para lhes dar autorização. 

Por exemplo, através do módulo V1 do PowerShell do Azure Active Directory, [MSOnline](/powershell/module/msonline/?view=azureadps-1.0), numa sessão do PowerShell, primeiro estabeleça ligação ao serviço e indique as credenciais de administrador global:

    Connect-MsolService


Nota: Se este comando não funcionar, pode executar `Install-Module MSOnline` para instalar o módulo MSOnline.

Em seguida, configure a sua sessão do PowerShell para não truncar os valores:

    $Formatenumerationlimit =-1

### <a name="confirm-user-accounts-are-ready-for-azure-information-protection"></a>Confirmar se as contas de utilizador estão prontas para o Azure Information Protection

Para confirmar as contas de utilizador, execute o seguinte comando:

    Get-Msoluser | select DisplayName, UserPrincipalName, ProxyAddresses

Em primeiro lugar, confirme que os utilizadores que pretende utilizar com o Azure Information Protection são apresentados.

Em seguida, verifique se a coluna **ProxyAddresses** está preenchida. Se for, os valores de e-mail nesta coluna podem ser utilizados para autorizar o utilizador do Azure Information Protection.

Se a coluna **ProxyAddresses** não estiver preenchida, o valor do atributo **UserPrincipalName** será utilizado para autorizar o utilizador para o serviço Azure Rights Management.

Por exemplo:


|  Nome a Apresentar   |     UserPrincipalName      |                            ProxyAddresses                             |
|-----------------|----------------------------|-----------------------------------------------------------------------|
| Jorge Andrade | jagannathreddy@contoso.com |                                  {}                                   |
|    Afonso Faria    |    ankurroy@contoso.com    | {SMTP:ankur.roy@contoso.com, smtp: ankur.roy@onmicrosoft.contoso.com} |

Neste exemplo:

- A conta de utilizador de Jorge Andrade será autorizada por <strong>jagannathreddy@contoso.com</strong>.

- A conta de utilizador de Afonso Faria pode ser autorizada através de <strong>ankur.roy@contoso.com</strong> e <strong>ankur.roy@onmicrosoft.contoso.com</strong>, mas não <strong>ankurroy@contoso.com</strong>.

Na maioria dos casos, o valor de UserPrincipalName corresponde a um dos valores no campo ProxyAddresses. Esta é a configuração recomendada. No entanto, se não puder alterar o seu UPN para corresponder ao endereço de e-mail, terá de seguir os seguintes passos:

1. Se o nome de domínio no valor do UPN for um domínio verificado do seu inquilino do Azure AD, adicione o valor do UPN como outro endereço de e-mail no Azure AD para que o valor do UPN possa ser utilizado para autorizar a conta de utilizador do Azure Information Protection.

    Se o nome de domínio no valor do UPN não for um domínio verificado do seu inquilino, não poderá ser utilizado com o Azure Information Protection. No entanto, o utilizador ainda pode ser autorizado como membro de um grupo quando o endereço de e-mail de grupo utiliza um nome de domínio verificado.

2. Se o UPN não for encaminhável (por exemplo, <strong>ankurroy@contoso.local</strong>), configure um ID de início de sessão alternativo para os utilizadores e diga-lhes como iniciar sessão no Office com esse início de sessão alternativo. Também deve definir uma chave do registo para o Office.

    Para obter mais informações, veja [Configurar o ID de Início de Sessão Alternativo](/windows-server/identity/ad-fs/operations/configuring-alternate-login-id) e [As aplicações do Office pedem periodicamente credenciais para o SharePoint Online, o OneDrive e o Lync Online](https://support.microsoft.com/help/2913639/office-applications-periodically-prompt-for-credentials-to-sharepoint-online,-onedrive,-and-lync-online).

> [!TIP]
> Pode utilizar o cmdlet Export-Csv para exportar os resultados para uma folha de cálculo de modo a facilitar a gestão, tais como pesquisar e editar em massa para importação.
>
> Por exemplo: `Get-MsolGroup | select DisplayName, ProxyAddresses | Export-Csv -Path UserAccounts.csv`

### <a name="confirm-group-accounts-are-ready-for-azure-information-protection"></a>Confirmar se as contas de grupo estão prontas para o Azure Information Protection

Para confirmar as contas de grupo, utilize o seguinte comando:

    Get-MsolGroup | select DisplayName, ProxyAddresses

Confirme que os grupos que pretende utilizar com o Azure Information Protection são apresentados. Para os grupos apresentados, os endereços de e-mail na coluna **ProxyAddresses** podem ser utilizados para autorizar os membros do grupo para o serviço Azure Rights Management.

Em seguida, verifique se os grupos contêm os utilizadores (ou outros grupos) que pretende utilizar para o Azure Information Protection. Pode utilizar o PowerShell para o fazer (por exemplo, [Get-MsolGroupMember](/powershell/module/msonline/Get-MsolGroupMember?view=azureadps-1.0)) ou utilizar o portal de gestão.

Para os dois cenários de configuração do serviço Azure Rights Management que utilizam grupos de segurança, pode utilizar o seguinte comando do PowerShell para localizar o ID de objeto e o nome a apresentar que podem ser utilizados para identificar esses grupos. Também pode utilizar o portal do Azure para localizar esses grupos e copiar os valores do ID de objeto e do nome a apresentar:

    Get-MsolGroup | where {$_.GroupType -eq "Security"}

## <a name="considerations-for-azure-information-protection-if-email-addresses-change"></a>Considerações para o Azure Information Protection se os endereços de e-mail forem alterados

Se alterar o endereço de e-mail de um utilizador ou grupo, recomendamos que adicione o endereço de e-mail antigo como um endereço de e-mail secundário (também conhecido como um endereço proxy, alias ou endereço de e-mail alternativo) ao utilizador ou grupo. Ao fazê-lo, o endereço de e-mail antigo é adicionado ao atributo proxyAddresses do Azure AD. Esta administração da conta garante a continuidade empresarial de quaisquer direitos de utilização ou outras configurações que foram guardados quando o endereço de e-mail antigo estava a ser utilizado. 

Se não puder fazer isso, o utilizador ou grupo com os riscos de endereço de e-mail novo que está a ser negado o acesso a documentos e e-mails que anteriormente eram protegidos com o endereço de e-mail antigo. Neste caso, tem de repetir a configuração de proteção para guardar o novo endereço de e-mail. Por exemplo, se o utilizador ou grupo foi concedido direitos de utilização em modelos ou etiquetas, editar esses modelos ou rótulos e especifique o novo endereço de e-mail com os mesmos direitos de utilização à medida que concedidas para o endereço de e-mail antigo.

Tenha em atenção que é raro um grupo alterar o seu endereço de e-mail e, se atribuir direitos de utilização a um grupo em vez de utilizadores individuais, é irrelevante se o endereço de e-mail do utilizador é alterado. Neste cenário, os direitos de utilização são atribuídos ao endereço de e-mail de grupo e não a endereços de e-mail do utilizador individuais. Este é o método mais provável (e recomendado) para um administrador configurar os direitos de utilização que protegem documentos e e-mails. No entanto, os utilizadores podem atribuir permissões personalizadas a utilizadores individuais com maior frequência. Uma vez que nem sempre é possível saber se foi utilizado um grupo ou uma conta de utilizador para conceder acesso, é mais seguro adicionar sempre o endereço de e-mail antigo como um endereço de e-mail secundário.

## <a name="group-membership-caching-by-azure-information-protection"></a>Grupo de associação de colocação em cache pelo Azure Information Protection

Por motivos de desempenho, Azure Information Protection coloca em cache associação de grupo. Isso significa que qualquer alteração feita à associação a grupos no Azure AD pode demorar até três horas a entrar em vigor quando estes grupos são utilizados pelo Azure Information Protection e este período de tempo está sujeitas a alterações. 

Não se esqueça de consideração este atraso quaisquer alterações ou testes quando utilizar grupos para conceder direitos de utilização ou configurar o serviço Azure Rights Management, ou quando configurar políticas de âmbito.


## <a name="next-steps"></a>Passos Seguintes

Quando tiver confirmado que os seus utilizadores e grupos podem ser utilizados com o Azure Information Protection e estiver pronto para começar a proteger documentos e e-mails, verifique se é preciso ativar o serviço Azure Rights Management. Este serviço tem de ser ativado antes de poder proteger documentos e e-mails da sua organização: 

- A partir de Fevereiro de 2018: Se a sua subscrição que inclui o Azure Rights Management ou do Azure Information Protection foi adquirida durante ou após este mês, o serviço é automaticamente ativado para. 

- Se a sua subscrição foi obtida antes de Fevereiro de 2018: Tem de ativar o serviço por conta própria. 

Para obter mais informações, incluindo a verificar o estado de ativação, consulte [ativar o Azure Rights Management](./activate-service.md).

