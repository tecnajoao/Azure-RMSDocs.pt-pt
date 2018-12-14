---
title: Como funciona o Azure RMS – AIP
description: Descrição detalhada de como o Azure RMS funciona, os controlos criptográficos que utiliza e diagramas passo a passo sobre o funcionamento deste processo.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 11/05/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: ed6c964e-4701-4663-a816-7c48cbcaf619
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 7c1d488ff738b0eea9042f1580ea74b7099f3ac5
ms.sourcegitcommit: 5b4eb0e17fb831d338d8c25844e9e6f4ca72246d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/10/2018
ms.locfileid: "53174119"
---
# <a name="how-does-azure-rms-work-under-the-hood"></a>Como funciona o Azure RMS? Nos bastidores

>*Aplica-se a: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Uma coisa importante para entender sobre como funciona o Azure RMS, é que este serviço de proteção de dados do Azure Information Protection, veja ou armazenar seus dados como parte do processo de proteção. Informações que proteger nunca são enviadas para ou armazenadas no Azure, a menos que explicitamente armazená-la no Azure ou utilize outro serviço em nuvem que as armazene no Azure. O Azure RMS simplesmente torna os dados num documento ilegível para todas as pessoas que não sejam utilizadores e serviços autorizados:

- Os dados são encriptados ao nível da aplicação e incluem uma política que define a utilização autorizada para esse documento.

- Quando um documento protegido é utilizado por um utilizador legítimo ou processado por um serviço autorizado, os dados no documento são desencriptados e os direitos que estão definidos na política são aplicados.

Pode ver como este processo funciona de modo geral na imagem seguinte. O documento com a fórmula secreta é protegido e, em seguida, aberto com êxito por um utilizador ou serviço autorizado. O documento é protegido por uma chave de conteúdo (a chave verde nesta imagem). Esta é exclusiva para cada documento e é colocada no cabeçalho do ficheiro, onde é protegida pela sua chave de raiz de inquilino do Azure Information Protection (a chave vermelha nesta imagem). A sua chave de inquilino pode ser gerada e gerida pela Microsoft ou o utilizador pode gerar e fazer a gestão da sua própria chave de inquilino.

Ao longo do processo de proteção quando o Azure RMS é encriptar e desencriptar, autorizar e impor restrições, a fórmula secreta nunca é enviada para o Azure.

![Como o Azure RMS protege um ficheiro](./media/AzRMS_SecretColaFormula_final.png)

Para obter uma descrição detalhada do que está acontecendo, consulte o [instruções sobre como funciona o Azure RMS: Primeira utilização, proteção de conteúdos, consumo de conteúdos](#walkthrough-of-how-azure-rms-works-first-use-content-protection-content-consumption) secção deste artigo.

Para obter detalhes técnicos sobre os algoritmos e os comprimentos de chave utilizados pelo Azure RMS, consulte a secção seguinte.

## <a name="cryptographic-controls-used-by-azure-rms-algorithms-and-key-lengths"></a>Controlos criptográficos utilizados pelo Azure RMS: Algoritmos e comprimentos de chave
Mesmo que não precise se conheça detalhadamente como funciona essa tecnologia, pode ser solicitado sobre os controlos criptográficos que utiliza. Por exemplo, para confirmar que a proteção de segurança padrão do setor.


|Controlos criptográficos|Função no Azure RMS|
|-|-|
|Algoritmo: AES<br /><br />Comprimento da chave: 128 bits e 256 bits [[1]](#footnote-1)|Proteção da documentação|
|Algoritmo: RSA<br /><br />Comprimento da chave: 2048 bits [[2]](#footnote-2)|Proteção da chave|
|SHA-256|Assinatura do certificado|

###### <a name="footnote-1"></a>Nota de rodapé 1 

O controlo de 256 bits é utilizado pelo cliente do Azure Information Protection e pela aplicação de partilha Rights Management para proteção genérica e nativa quando o ficheiro tem uma extensão de nome de ficheiro .ppdf ou quando se trata de um ficheiro de imagem ou de texto protegido (tal como .ptxt ou .pjpg).

###### <a name="footnote-2"></a>Nota de rodapé 2

2048 bits é o comprimento da chave de quando o serviço Azure Rights Management está ativado. 1024 bits é suportada para os seguintes cenários opcionais:

- Durante uma migração no local se o cluster de AD RMS estiver em execução no modo criptográfico 1.

- Após uma migração no local, se o cluster de AD RMS estava a utilizar o Exchange Online.

- Para obter chaves arquivadas que foram criadas no local antes da migração, para que o conteúdo que foi anteriormente protegido pelo AD RMS pode continuar a ser aberto pelo serviço Azure Rights Management após a migração.

- Se os clientes optarem por trazer a sua própria chave (BYOK) através do Cofre de Chaves do Azure. O Azure Information Protection suporta comprimentos de chave de 1024 bits e 2048 bits. Para uma maior segurança, recomendamos um comprimento de chave de 2048 bits.

### <a name="how-the-azure-rms-cryptographic-keys-are-stored-and-secured"></a>Como as chaves criptográficas do Azure RMS são armazenadas e protegidas

O Azure RMS cria uma chave AES única (a "chave de conteúdo") para cada documento ou mensagem de e-mail que protege. Essa chave é incorporada no documento e persiste nas várias edições do documento. 

A chave de conteúdo é protegida com a chave RSA da organização (a "chave de inquilino do Azure Information Protection") como parte da política no documento e a política também é assinada pelo autor do documento. Esta chave de inquilino é comum a todos os documentos e e-mails protegidos pelo serviço Azure Rights Management da organização e esta chave só poderá ser alterada por um administrador do Azure Information Protection se a organização estiver a utilizar uma chave de inquilino gerida pelo cliente, conhecida como BYOK (Bring Your Own Key – Traga a Sua Própria Chave). 

Esta chave de inquilino está protegida nos serviços online da Microsoft, num ambiente altamente controlado e sob monitorização rigorosa. Quando utiliza uma chave de inquilino gerida pelo cliente (BYOK), esta segurança é melhorada pela utilização de uma matriz de módulos de segurança de hardware de ponta (HSMs) em cada região do Azure, sem a capacidade para as chaves ser extraídos, exportação ou partilha em nenhuma circunstância. Para obter mais informações sobre a chave de inquilino e a BYOK, veja [Planear e implementar a sua chave de inquilino do Azure Information Protection](plan-implement-tenant-key.md).

As licenças e certificados enviados para um dispositivo Windows estão protegidos pela chave privada do dispositivo do cliente, que é criada quando um utilizador usa o Azure RMS pela primeira vez num dispositivo. Por sua vez, esta chave privada está protegida com a DPAPI do cliente, que protege estes segredos com uma chave derivada da palavra-passe do utilizador. Em dispositivos móveis, as chaves são utilizadas apenas uma vez, pois como não estão armazenadas nos clientes, não precisam de ser protegidas no dispositivo. 


## <a name="walkthrough-of-how-azure-rms-works-first-use-content-protection-content-consumption"></a>Instruções sobre como funciona o Azure RMS: Primeiro, utilização, proteção de conteúdo, consumo de conteúdos
Para compreender melhor como funciona o Azure RMS, iremos mostrar-lhe um fluxo típico após o [serviço Azure Rights Management ser ativado](activate-service.md) e o que acontece quando um utilizador usa pela primeira vez o serviço Rights Management no seu computador Windows (um processo por vezes conhecido como **inicializar o ambiente de utilizador** ou arranque do sistema), **protege conteúdos** (um documento ou e-mail) e, em seguida, **consome** (abre e utiliza) os conteúdos que foram protegidos por outra pessoa.

Após o ambiente de utilizador ser iniciado, esse utilizador pode proteger documentos ou consumir documentos protegidos nesse computador.

> [!NOTE]
> Se o utilizador mudar de computador Windows ou outro utilizador usar este computador Windows, o processo de iniciação é repetido.

### <a name="initializing-the-user-environment"></a>Inicializar o ambiente de utilizador
Antes de um utilizador poder proteger conteúdos ou consumir conteúdos protegidos num computador Windows, o ambiente de utilizador tem de ser preparado no dispositivo. Este é um processo único e ocorre automaticamente sem a intervenção do utilizador quando este tenta proteger ou consumir conteúdos protegidos:

![Processo de ativação do Cliente de RMS – passo 1, autenticar o cliente](./media/AzRMS.png)

**O que acontece no passo 1**: Primeiro, o cliente do RMS no computador liga ao serviço Azure Rights Management e autentica o utilizador ao utilizar a respetiva conta do Azure Active Directory.

Quando a conta de utilizador está federada com o Azure Active Directory, esta autenticação é automática e o utilizador não será pedido credenciais.

![Ativação do Cliente de RMS – passo 2, os certificados são transferidos para o cliente](./media/AzRMS_useractivation2.png)

**O que acontece no passo 2**: Depois do utilizador é autenticado, a ligação é automaticamente redirecionada para o inquilino do Azure Information Protection da organização, que se emitir certificados que permitem ao utilizador autenticar para o serviço Azure Rights Management para poder consumir protegidos conteúdo e proteger conteúdos offline.

Um destes certificados é o certificado de conta de direitos, frequentemente abreviado para RAC. Este certificado autentica o utilizador ao Azure Active Directory e é válido durante 31 dias. O certificado é renovado automaticamente pelo cliente do RMS, fornecendo a conta de utilizador ainda está no Azure Active Directory e a conta está ativada. Este certificado não é configurável por um administrador. 

Uma cópia deste certificado é armazenada no Azure, para que se o utilizador usar outro dispositivo, os certificados sejam criados usando as mesmas chaves.

### <a name="content-protection"></a>Proteção de conteúdos
Quando um utilizador protege um documento, o cliente de RMS efetua as seguintes ações num documento não protegido:

![Proteção de documentos pelo RMS – passo 1, o documento é encriptado](./media/AzRMS_documentprotection1.png)

**O que acontece no passo 1**: O cliente de RMS cria uma chave aleatória (a chave de conteúdo) e encripta o documento com esta chave com o algoritmo de encriptação simétrica AES.

![Proteção de documentos pelo RMS – passo 2, a política é criada](./media/AzRMS_documentprotection2.png)

**O que acontece no passo 2**: O cliente do RMS, em seguida, cria um certificado que inclua uma política para o documento que inclui a [direitos de utilização](configure-usage-rights.md) para utilizadores ou grupos e outras restrições, como uma data de expiração. Estas definições podem ser definidas num modelo que um administrador anteriormente configurado, ou ser especificada no momento que o conteúdo é protegido (por vezes referido como uma "política ad hoc").   

O principal atributo do Azure AD utilizado para identificar os utilizadores e grupos selecionados é o atributo ProxyAddresses do Azure AD, que armazena todos os endereços de e-mail de um utilizador ou grupo. No entanto, se uma conta de utilizador não tiver nenhum valor no atributo ProxyAddresses do AD, o valor UserPrincipalName do utilizador é utilizado.

Em seguida, o cliente de RMS utiliza a chave da organização obtida quando o ambiente de utilizador foi inicializado para encriptar a política e a chave de conteúdo simétrica. O cliente RMS também assina a política com o certificado do utilizador obtido quando o ambiente do utilizador foi inicializado.

![Proteção de documentos pelo RMS – passo 3, a política é incorporada no documento](./media/AzRMS_documentprotection3.png)

**O que acontece no passo 3**: Por fim, o cliente de RMs incorpora a política para um ficheiro com o corpo do documento previamente encriptado e que em conjunto, compõem um documento protegido.

Este documento pode ser armazenado em qualquer lugar ou partilhado com qualquer método e a política permanece sempre com o documento encriptado.

### <a name="content-consumption"></a>Consumo de conteúdos
Se um utilizador quiser consumir um documento protegido, o cliente de RMS começa por pedir acesso ao serviço Azure Rights Management:

![Consumo de documentos pelo RMS – passo 1, o utilizador é autenticado e obtém a lista de direitos](./media/AzRMS_documentconsumption1.png)

**O que acontece no passo 1**: O utilizador autenticado envia a política do documento e os certificados do utilizador para o serviço Azure Rights Management. O serviço desencripta e avalia a política e cria uma lista de direitos (se aplicável) que o utilizador tem sobre o documento. Para identificar o utilizador, é utilizado o atributo ProxyAddresses do Azure AD para a conta do utilizador e para os grupos dos quais este é membro. Por motivos de desempenho, a associação a grupos é [colocada em cache](prepare.md#group-membership-caching-by-azure-information-protection). Se a conta de utilizador não tiver nenhum valor para o atributo ProxyAddresses do Azure AD, é utilizado o valor no atributo UserPrincipalName do Azure AD.

![Consumo de documentos pelo RMS – passo 2, a licença de utilização é dada ao cliente](./media/AzRMS_documentconsumption2.png)

**O que acontece no passo 2**: O serviço, em seguida, extrai a chave de conteúdo AES da política desencriptada. Esta chave é então encriptada com a chave RSA pública do utilizador que foi obtida com o pedido.

A chave de conteúdo encriptada novamente é incorporada numa licença de utilização encriptada com a lista de direitos de utilizador que, em seguida, é devolvida ao cliente de RMS.

![Documento consumo pelo RMS – passo 3, o documento é desencriptado e são impostos direitos](./media/AzRMS_documentconsumption3.png)

**O que acontece no passo 3**: Por fim, o cliente do RMS leva a licença de utilização encriptada e desencripta a mesma com sua própria chave privada do utilizador. Isto permite que o cliente de RMS desencripte o corpo do documento conforme necessário e o apresente no ecrã.

O cliente também desencripta a lista de direitos e passa-a para a aplicação, que impõe esses direitos na interface de utilizador da aplicação.

> [!NOTE]
> Quando os utilizadores externos à sua organização consomem conteúdos que protegeu, o processo de consumo é o mesmo. O que muda neste cenário é a forma como o utilizador é autenticado. Para obter mais informações, veja [Quando partilho um documento protegido com alguém fora da minha empresa, como é que esse utilizador é autenticado?](./faqs-rms.md#when-i-share-a-protected-document-with-somebody-outside-my-company-how-does-that-user-get-authenticated)


### <a name="variations"></a>Variações
Os passos anteriores abrangem os cenários padrão, mas existem algumas variações:

- **Proteção de e-mail**: Quando o Exchange Online e encriptação de mensagens do Office 365 com os novos recursos é utilizado para proteger mensagens de e-mail, a autenticação para consumo também pode utilizar federação com um fornecedor de identidade social ou por meio de um código de acesso único. Em seguida, os fluxos do processo são muito semelhantes, exceto pelo fato de consumo de conteúdo do lado do serviço acontece numa sessão de navegador da web através de uma cópia temporariamente em cache da mensagem de e-mail de saída.

- **Dispositivos móveis**: Quando os dispositivos móveis protegem ou consomem ficheiros com o serviço Azure Rights Management, os fluxos do processo são muito mais simples. Os dispositivos móveis não passam pelo processo de inicialização do utilizador efetuado em primeiro lugar, pois cada transação (para proteger ou consumir conteúdos) é independente. À semelhança dos computadores Windows, os dispositivos móveis ligam-se ao serviço Azure Rights Management e efetuam a autenticação. Para proteger os conteúdos, os dispositivos móveis submetem uma política e o serviço Azure Rights Management envia-lhes uma licença de publicação e uma chave simétrica para proteger o documento. Para consumir conteúdos, quando os dispositivos móveis se ligam ao serviço Azure Rights Management e efetuam a autenticação, os mesmos enviam a política do documento para o serviço Azure Rights Management e pedem uma licença de utilização para consumir o documento. Em resposta, o serviço Azure Rights Management envia as chaves e restrições necessárias para os dispositivos móveis. Ambos os processos utilizam o TLS para proteger a troca de chaves e outras comunicações.

- **Conector do RMS**: Quando o serviço Azure Rights Management é utilizado com o conector RMS, os fluxos do processo permanecem iguais. A única diferença é que o conector funciona como um reencaminhamento entre os serviços no local (como o Exchange Server e o SharePoint Server) e o serviço Azure Rights Management. O conector propriamente dito não executa quaisquer operações, como a inicialização do ambiente de utilizador, a encriptação ou a desencriptação. Apenas reencaminha a comunicação que normalmente iria para um servidor AD RMS, o processamento da tradução entre os protocolos que são utilizados em cada lado. Este cenário permite-lhe utilizar o serviço Azure Rights Management com serviços no local.

- **Proteção genérica (. pfile)**: Quando o serviço Azure Rights Management protege genericamente um ficheiro, o fluxo é basicamente o mesmo para a proteção de conteúdo, exceto que o cliente de RMS cria uma política que concede todos os direitos. Quando o ficheiro é consumido, é desencriptado antes de ser transmitido para a aplicação de destino. Este cenário permite-lhe proteger todos os ficheiros, mesmo que não suportem o RMS originalmente.

- **PDF protegido (. ppdf)**: Quando o serviço Azure Rights Management protege originalmente um ficheiro do Office, também cria uma cópia desse ficheiro e protege-o da mesma forma. A única diferença é que a cópia do ficheiro está no formato de ficheiro PPDF, que o visualizador do cliente do Azure Information Protection e a aplicação de partilha RMS sabem como abrir no modo só de visualização. Este cenário permite-lhe enviar anexos protegidos por e-mail, sabendo que o destinatário num dispositivo móvel pode sempre lê-los, mesmo que o dispositivo móvel não tem uma aplicação que suporta nativamente protegidos de arquivos do Office.

- **As contas Microsoft**: O Azure Information Protection pode autorizar os endereços de e-mail para consumo, quando os utilizadores são autenticados com uma conta Microsoft. No entanto, nem todos os aplicativos podem abrir conteúdo protegido, quando uma conta Microsoft é utilizada para autenticação. [Obter mais informações](secure-collaboration-documents.md#supported-scenarios-for-opening-protected-documents).

## <a name="next-steps"></a>Passos Seguintes

Para saber mais sobre o serviço Azure Rights Management, utilize os outros artigos a **compreender e explorar** secção, tal como [como as aplicações suportam o serviço Azure Rights Management](applications-support.md) para saber mais como seus aplicativos existentes, podem integrar com o Azure Rights Management para fornecer uma solução de proteção de informações. 

Consulte a [Terminologia do Azure Information Protection](./terminology.md) para se familiarizar com os termos que possam ser apresentados quando estiver a configurar e utilizar o serviço Azure Rights Management e certifique-se de que também consulta os [Requirements for Azure Information Protection (Requisitos para o Azure Information Protection – em inglês)](requirements.md) antes de iniciar a implementação. Se quiser começar já e experimente mesmo, utilize o [editar a política e criar uma nova etiqueta](infoprotect-quick-start-tutorial.md) tutorial.

Se estiver pronto para iniciar a implementação da proteção de dados na sua organização, utilize o [Plano de implementação do Azure Information Protection](deployment-roadmap.md) para obter os passos da sua implementação e ligações para instruções sobre como proceder.

> [!TIP]
> Para obter ajuda e informações adicionais, utilize os recursos e ligações em [Informações e suporte do Azure Information Protection](information-support.md).
