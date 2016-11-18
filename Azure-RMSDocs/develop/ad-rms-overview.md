---
title: "Descrição geral - RMS SDK 2.1 | Azure RMS"
description: "O Rights Management Services (RMS) é uma tecnologia de proteção de informações que ajuda a salvaguardar as informações digitais contra a utilização não autorizada."
keywords: 
author: bruceperlerms
ms.author: bruceper
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: B546B6C1-ADC1-4EBD-95E2-B4A74E4E980B
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9d8354f2d68f211d349226970fd2f83dd0ce810b
ms.openlocfilehash: 816d665314fb77931433e36420b54c3ab6f689b9


---

# <a name="overview"></a>Descrição Geral

O SDK Rights Management Services (RMS) 2.1 é uma tecnologia de proteção de informações que ajuda a salvaguardar as informações digitais contra utilização não autorizada. Através da aplicação com capacidade para direitos, os proprietários de conteúdo conseguirão definir quem pode abrir, modificar, imprimir, reencaminhar ou efetuar outras ações no conteúdo.

O AD RMS consiste em componentes de [servidor](ad-rms-server.md) e de [cliente](ad-rms-client.md). O servidor, em execução no Azure ou no Windows Server, é constituído por vários serviços web.

O componente de [cliente](ad-rms-client.md) pode ser executado num sistema operativo de cliente ou de servidor e contém funções que permitem que uma aplicação encripte e desencripte conteúdo, obtenha modelos e listas de revogação, adquira licenças e certificados a partir de um servidor e outras tarefas de gestão de direitos relacionadas.

Para obter mais informações, consulte [Tipos de aplicações](application-types.md).

Seguem-se alguns dos cenários em que podem ser aplicadas aplicações incorporadas no SDK Rights Management Services 2.1.

-   Uma firma de advogados pretende impedir que as mensagens de e-mail confidenciais sejam impressas ou reencaminhadas.
-   Os programadores do projeto assistido por computador e software de fabrico pretendem limitar o acesso de desenho a um pequeno grupo de utilizadores dentro da divisão de pesquisa sem a necessidade da utilização de palavras-passe.
-   Os proprietários de um site de design gráfico pretendem utilizar uma única licença que permita a livre visualização de cópias de baixa resolução das suas imagens, mas requer o pagamento para o acesso a versões de alta resolução.
-   Os proprietários de uma biblioteca de documentos online pretendem ativar direitos para ver, imprimir ou editar documentos com base na identidade do utilizador.
-   Uma empresa pretende publicar informações confidenciais sobre os funcionários para um Web site interno que restringe a visualização e edição de privilégios a determinados utilizadores.

Para obter mais informações sobre o servidor AD RMS, o cliente de AD RMS e a respetiva funcionalidade, consulte o conteúdo da TechNet [Documentação de profissionais de TI para o AD RMS](https://TechNet.Microsoft.Com/library/cc771234.aspx).

Os tópicos restantes desta secção a Arquitetura RMS e as suas implementações.

## <a name="in-this-section"></a>Nesta secção

| Tópico | Descrição |
|-------|-------------|
|[Cliente](ad-rms-client.md) |Este tópico descreve a finalidade e a função do Rights Management Service Client 2.1 |
|[Servidor](ad-rms-server.md) | Este tópico descreve a finalidade e as funções do RMS Server para o Azure e Windows Server.|


## <a name="related-topics"></a>Tópicos relacionados

* [Conceitos do RMS](application-types.md)
* [Introdução](getting-started-with-ad-rms-2-0.md)
* [Documentação de profissionais de TI para o AD RMS](https://TechNet.Microsoft.Com/en-us/library/cc771234.aspx)
 

 



<!--HONumber=Nov16_HO2-->


