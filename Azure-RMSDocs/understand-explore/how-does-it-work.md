---
title: "Como funciona o Azure RMS – AIP"
description: "Descrição detalhada de como o Azure RMS funciona, os controlos criptográficos que utiliza e diagramas passo a passo sobre o funcionamento deste processo."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 12/06/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: ed6c964e-4701-4663-a816-7c48cbcaf619
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 1a7075287eebe2c68534de95d01cef455ebe63b5
ms.sourcegitcommit: f185b1d742c345a465927f88e606413421fe1150
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/07/2017
---
# <a name="how-does-azure-rms-work-under-the-hood"></a>Como funciona o Azure RMS? Os bastidores

>*Aplica-se a: Azure Information Protection, Office 365*

Um mais importante para compreender sobre como funciona o Azure RMS, é que este serviço de proteção de dados do Azure Information Protection, consulte ou armazenam os seus dados como parte do processo de proteção. Informações que protege nunca são enviadas para ou armazenadas no Azure, a menos que explicitamente armazene-o no Azure ou utilize outro serviço em nuvem que as armazene no Azure. O Azure RMS simplesmente torna os dados num documento ilegível para todas as pessoas que não sejam utilizadores e serviços autorizados:

- Os dados são encriptados ao nível da aplicação e incluem uma política que define a utilização autorizada para esse documento.

- Quando um documento protegido é utilizado por um utilizador legítimo ou processado por um serviço autorizado, os dados no documento são desencriptados e os direitos que estão definidos na política são aplicados.

Pode ver como este processo funciona de modo geral na imagem seguinte. O documento com a fórmula secreta é protegido e, em seguida, aberto com êxito por um utilizador ou serviço autorizado. O documento é protegido por uma chave de conteúdo (a chave verde nesta imagem). Esta é exclusiva para cada documento e é colocada no cabeçalho do ficheiro, onde é protegida pela sua chave de raiz de inquilino do Azure Information Protection (a chave vermelha nesta imagem). A sua chave de inquilino pode ser gerada e gerida pela Microsoft ou o utilizador pode gerar e fazer a gestão da sua própria chave de inquilino.

Ao longo de todo o processo de proteção, quando o Azure RMS está a encriptar, desencriptar, autorizar e a impor restrições, a fórmula secreta nunca é enviada para o Azure.

![Como o Azure RMS protege um ficheiro](../media/AzRMS_SecretColaFormula_final.png)

Para obter uma descrição detalhada do processo, consulte a secção [Explicação passo a passo sobre como funciona o Azure RMS: primeira utilização, proteção de conteúdos, consumo de conteúdos](#walkthrough-of-how-azure-rms-works-first-use-content-protection-content-consumption) neste artigo.

Para obter detalhes técnicos sobre os algoritmos e os comprimentos de chave utilizados pelo Azure RMS, consulte a secção seguinte.

## <a name="cryptographic-controls-used-by-azure-rms-algorithms-and-key-lengths"></a>Controlos criptográficos utilizados pelo Azure RMS: comprimentos de chave e algoritmos
Mesmo que não precisa de saber em detalhe como funciona esta tecnologia, poderá ser-lhe pedido sobre os controlos criptográficos que utiliza. Por exemplo, para confirmar que a proteção de segurança padrão da indústria.


|Controlos criptográficos|Função no Azure RMS|
|-|-|
|Algoritmo: AES<br /><br />Comprimento de chave: 128 bits e 256 bits [[1]](#footnote-1)|Proteção da documentação|
|Algoritmo: RSA<br /><br />Comprimento da chave: 2048 bits [[2]](#footnote-2)|Proteção da chave|
|SHA-256|Assinatura do certificado|

###### <a name="footnote-1"></a>Nota de rodapé 1 

O controlo de 256 bits é utilizado pelo cliente do Azure Information Protection e pela aplicação de partilha Rights Management para proteção genérica e nativa quando o ficheiro tem uma extensão de nome de ficheiro .ppdf ou quando se trata de um ficheiro de imagem ou de texto protegido (tal como .ptxt ou .pjpg).

###### <a name="footnote-2"></a>Nota de rodapé 2

2048 bits é o comprimento de chave quando o serviço Azure Rights Management está ativado. 1024 bits é suportada para os seguintes cenários opcionais:

- Durante uma migração no local se o cluster de AD RMS está em execução no modo criptográfico 1.

- Depois de uma migração no local, se o cluster de AD RMS estava a utilizar o Exchange Online.

- Para obter chaves arquivadas que foram criadas no local antes da migração, para que o conteúdo que foi anteriormente protegido pelo AD RMS pode continuar a ser aberta pelo serviço Azure Rights Management após a migração.

- Se os clientes optarem por trazer a sua própria chave (BYOK) através do Cofre de Chaves do Azure. O Azure Information Protection suporta comprimentos de chave de 1024 e 2048 bits. Para uma maior segurança, recomendamos um comprimento de chave de 2048 bits.

### <a name="how-the-azure-rms-cryptographic-keys-are-stored-and-secured"></a>Como as chaves criptográficas do Azure RMS são armazenadas e protegidas

O Azure RMS cria uma chave AES única (a "chave de conteúdo") para cada documento ou mensagem de e-mail que protege. Essa chave é incorporada no documento e persiste nas várias edições do documento. 

A chave de conteúdo é protegida com a chave RSA da organização (a "chave de inquilino do Azure Information Protection") como parte da política no documento e a política também é assinada pelo autor do documento. Esta chave de inquilino é comum a todos os documentos e e-mails protegidos pelo serviço Azure Rights Management da organização e esta chave só poderá ser alterada por um administrador do Azure Information Protection se a organização estiver a utilizar uma chave de inquilino gerida pelo cliente, conhecida como BYOK (Bring Your Own Key – Traga a Sua Própria Chave). 

Esta chave de inquilino está protegida nos serviços online da Microsoft, num ambiente altamente controlado e sob monitorização rigorosa. Quando utiliza uma chave de inquilino gerida pelo cliente (BYOK), esta segurança é melhorada pela utilização de uma matriz de módulos de segurança de hardware de alta gama (HSMs) em cada região do Azure, sem a capacidade para as chaves a ser extraído, exportação ou partilha em circunstância alguma. Para obter mais informações sobre a chave de inquilino e a BYOK, veja [Planear e implementar a sua chave de inquilino do Azure Information Protection](../plan-design/plan-implement-tenant-key.md).

As licenças e certificados enviados para um dispositivo Windows estão protegidos pela chave privada do dispositivo do cliente, que é criada quando um utilizador usa o Azure RMS pela primeira vez num dispositivo. Por sua vez, esta chave privada está protegida com a DPAPI do cliente, que protege estes segredos com uma chave derivada da palavra-passe do utilizador. Em dispositivos móveis, as chaves são utilizadas apenas uma vez, pois como não estão armazenadas nos clientes, não precisam de ser protegidas no dispositivo. 


## <a name="walkthrough-of-how-azure-rms-works-first-use-content-protection-content-consumption"></a>Explicação passo a passo sobre como funciona o Azure RMS: primeira utilização, proteção de conteúdos, consumo de conteúdos
Para compreender melhor como funciona o Azure RMS, iremos mostrar-lhe um fluxo típico após o [serviço Azure Rights Management ser ativado](../deploy-use/activate-service.md) e o que acontece quando um utilizador usa pela primeira vez o serviço Rights Management no seu computador Windows (um processo por vezes conhecido como **inicializar o ambiente de utilizador** ou arranque do sistema), **protege conteúdos** (um documento ou e-mail) e, em seguida, **consome** (abre e utiliza) os conteúdos que foram protegidos por outra pessoa.

Após o ambiente de utilizador ser iniciado, esse utilizador pode proteger documentos ou consumir documentos protegidos nesse computador.

> [!NOTE]
> Se o utilizador mudar de computador Windows ou outro utilizador usar este computador Windows, o processo de iniciação é repetido.

### <a name="initializing-the-user-environment"></a>Inicializar o ambiente de utilizador
Antes de um utilizador poder proteger conteúdos ou consumir conteúdos protegidos num computador Windows, o ambiente de utilizador tem de ser preparado no dispositivo. Este é um processo único e ocorre automaticamente sem a intervenção do utilizador quando este tenta proteger ou consumir conteúdos protegidos:

![Processo de ativação do Cliente de RMS – passo 1, autenticar o cliente](../media/AzRMS.png)

**O que acontece no passo 1**: primeiro, o cliente de RMS no computador liga-se ao serviço Azure Rights Management e autentica o utilizador com a respetiva conta do Azure Active Directory.

Quando a conta do utilizador está federada com o Azure Active Directory, esta autenticação é automática e não serão pedidas ao utilizador as suas credenciais.

![Ativação do Cliente de RMS – passo 2, os certificados são transferidos para o cliente](../media/AzRMS_useractivation2.png)

**O que acontece no passo 2**: após o utilizador ser autenticado, a ligação é automaticamente redirecionada para o inquilino do Azure Information Protection da organização, que emite certificados que permitem ao utilizador efetuar a autenticação no serviço Azure Rights Management para poder consumir conteúdos protegidos e proteger conteúdos offline.

É guardada uma cópia do certificado do utilizador no Azure para que, se o utilizador usar outro dispositivo, os certificados sejam criados com as mesmas chaves.

### <a name="content-protection"></a>Proteção de conteúdos
Quando um utilizador protege um documento, o cliente de RMS efetua as seguintes ações num documento não protegido:

![Proteção de documentos pelo RMS – passo 1, o documento é encriptado](../media/AzRMS_documentprotection1.png)

**O que acontece no passo 1**: o cliente de RMS cria uma chave aleatória (a chave de conteúdo) e encripta o documento com esta chave com o algoritmo de encriptação simétrica AES.

![Proteção de documentos pelo RMS – passo 2, a política é criada](../media/AzRMS_documentprotection2.png)

**I que acontece no passo 2**: em seguida, o cliente de RMS cria um certificado que adiciona uma política para o documento, que inclui os [direito de utilização](../deploy-use/configure-usage-rights.md) para utilizadores e grupos e outras restrições, como a data de expiração. Estas definições podem ser definidas num modelo que um administrador anteriormente configurado ou especificado no momento, que o conteúdo é protegido (por vezes referido como uma "política ad hoc").   

O principal atributo do Azure AD utilizado para identificar os utilizadores e grupos selecionados é o atributo ProxyAddresses do Azure AD, que armazena todos os endereços de e-mail de um utilizador ou grupo. No entanto, se uma conta de utilizador não tiver nenhum valor no atributo ProxyAddresses do AD, o valor UserPrincipalName do utilizador é utilizado.

Em seguida, o cliente de RMS utiliza a chave da organização obtida quando o ambiente de utilizador foi inicializado para encriptar a política e a chave de conteúdo simétrica. O cliente RMS também assina a política com o certificado do utilizador obtido quando o ambiente do utilizador foi inicializado.

![Proteção de documentos pelo RMS – passo 3, a política é incorporada no documento](../media/AzRMS_documentprotection3.png)

**O que acontece no passo 3**: por fim, o cliente de RMS incorpora a política num ficheiro com o corpo do documento previamente encriptado e que, em conjunto, constituem um documento protegido.

Este documento pode ser armazenado em qualquer lugar ou partilhado com qualquer método e a política permanece sempre com o documento encriptado.

### <a name="content-consumption"></a>Consumo de conteúdos
Se um utilizador quiser consumir um documento protegido, o cliente de RMS começa por pedir acesso ao serviço Azure Rights Management:

![Consumo de documentos pelo RMS – passo 1, o utilizador é autenticado e obtém a lista de direitos](../media/AzRMS_documentconsumption1.png)

**O que acontece no passo 1**: o utilizador autenticado envia a política do documento e os certificados do utilizador para o serviço Azure Rights Management. O serviço desencripta e avalia a política e cria uma lista de direitos (se aplicável) que o utilizador tem sobre o documento. Para identificar o utilizador, é utilizado o atributo ProxyAddresses do Azure AD para a conta do utilizador e para os grupos dos quais este é membro. Por motivos de desempenho, a associação a grupos é [colocada em cache](../plan-design/prepare.md#group-membership-caching-by-azure-rights-management). Se a conta de utilizador não tiver nenhum valor para o atributo ProxyAddresses do Azure AD, é utilizado o valor no atributo UserPrincipalName do Azure AD.

![Consumo de documentos pelo RMS – passo 2, a licença de utilização é dada ao cliente](../media/AzRMS_documentconsumption2.png)

**O que acontece no passo 2**: em seguida, o serviço extrai a chave de conteúdo AES da política desencriptada. Esta chave é então encriptada com a chave RSA pública do utilizador que foi obtida com o pedido.

A chave de conteúdo encriptada novamente é incorporada numa licença de utilização encriptada com a lista de direitos de utilizador que, em seguida, é devolvida ao cliente de RMS.

![Documento consumo pelo RMS – passo 3, documento é desencriptado e são impostos direitos](../media/AzRMS_documentconsumption3.png)

**O que acontece no passo 3**: por fim, o cliente de RMS obtém a licença de utilização encriptada e desencripta a mesma com a sua própria chave privada de utilizador. Isto permite que o cliente de RMS desencripte o corpo do documento conforme necessário e o apresente no ecrã.

O cliente também desencripta a lista de direitos e passa-a para a aplicação, que impõe esses direitos na interface de utilizador da aplicação.

> [!NOTE]
> Quando os utilizadores externos à sua organização consomem conteúdos que protegeu, o processo de consumo é o mesmo. O que muda neste cenário é a forma como o utilizador é autenticado. Para obter mais informações, veja [Quando partilho um documento protegido com alguém fora da minha empresa, como é que esse utilizador é autenticado?](../get-started/faqs-rms.md#when-i-share-a-protected-document-with-somebody-outside-my-company-how-does-that-user-get-authenticated)


### <a name="variations"></a>Variações
Os passos anteriores abrangem os cenários padrão, mas existem algumas variações:

-   **Dispositivos móveis**: quando os dispositivos móveis protegem ou consomem ficheiros com o serviço Azure Rights Management, os fluxos do processo são muito mais simples. Os dispositivos móveis não passam pelo processo de inicialização do utilizador efetuado em primeiro lugar, pois cada transação (para proteger ou consumir conteúdos) é independente. À semelhança dos computadores Windows, os dispositivos móveis ligam-se ao serviço Azure Rights Management e efetuam a autenticação. Para proteger os conteúdos, os dispositivos móveis submetem uma política e o serviço Azure Rights Management envia-lhes uma licença de publicação e uma chave simétrica para proteger o documento. Para consumir conteúdos, quando os dispositivos móveis se ligam ao serviço Azure Rights Management e efetuam a autenticação, os mesmos enviam a política do documento para o serviço Azure Rights Management e pedem uma licença de utilização para consumir o documento. Em resposta, o serviço Azure Rights Management envia as chaves e restrições necessárias para os dispositivos móveis. Ambos os processos utilizam o TLS para proteger a troca de chaves e outras comunicações.

-   **Conector RMS**: quando o serviço Azure Rights Management é utilizado com o conector RMS, os fluxos do processo mantêm-se os mesmos. A única diferença é que o conector funciona como um reencaminhamento entre os serviços no local (como o Exchange Server e o SharePoint Server) e o serviço Azure Rights Management. O conector propriamente dito não executa quaisquer operações, como a inicialização do ambiente de utilizador, a encriptação ou a desencriptação. Apenas reencaminha a comunicação que normalmente iria para um servidor AD RMS, através do processamento da tradução entre os protocolos que são utilizados em cada lado. Este cenário permite-lhe utilizar o serviço Azure Rights Management com serviços no local.

-   **Proteção genérica (.pfile)**: quando o serviço Azure Rights Management protege genericamente um ficheiro, o fluxo é basicamente o mesmo para a proteção de conteúdos com a exceção do facto de ser o cliente de RMS a criar uma política que concede todos os direitos. Quando o ficheiro é consumido, é desencriptado antes de ser transmitido para a aplicação de destino. Este cenário permite-lhe proteger todos os ficheiros, mesmo que não suportem o RMS originalmente.

-   **PDF protegido (.ppdf)**: quando o serviço Azure Rights Management protege originalmente um ficheiro do Office, também cria uma cópia desse ficheiro e protege-o da mesma forma. A única diferença é que a cópia do ficheiro está no formato de ficheiro PPDF, que o visualizador do cliente do Azure Information Protection e a aplicação de partilha RMS sabem como abrir no modo só de visualização. Este cenário permite-lhe enviar anexos protegidos por e-mail, sabendo que o destinatário num dispositivo móvel pode sempre lê-los, mesmo se o dispositivo móvel não tem uma aplicação que suporta nativamente protegidos ficheiros do Office.

## <a name="next-steps"></a>Próximos passos

Para saber mais sobre o serviço Azure Rights Management, utilize os outros artigos na secção **Compreender e Explorar**, por exemplo [Como as aplicações suportam o serviço Azure Rights Management](applications-support.md) para saber como é que as suas aplicações existentes se podem integrar com o serviço Azure Rights Management para fornecer uma solução de proteção de informações. 

Consulte a [Terminologia do Azure Information Protection](../get-started/terminology.md) para se familiarizar com os termos que possam ser apresentados quando estiver a configurar e utilizar o serviço Azure Rights Management e certifique-se de que também consulta os [Requirements for Azure Information Protection (Requisitos para o Azure Information Protection – em inglês)](../get-started/requirements-azure-rms.md) antes de iniciar a implementação. Se quiser começar já e experimentar, utilize o [Tutorial de início rápido do Azure Information Protection](../get-started/infoprotect-quick-start-tutorial.md).

Se estiver pronto para iniciar a implementação da proteção de dados na sua organização, utilize o [Plano de implementação do Azure Information Protection](../plan-design/deployment-roadmap.md) para obter os passos da sua implementação e ligações para instruções sobre como proceder.

> [!TIP]
> Para obter ajuda e informações adicionais, utilize os recursos e ligações em [Informações e suporte do Azure Information Protection](../get-started/information-support.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]