---
title: Descrição geral - RMS SDK 4.2 | Azure RMS
description: O AD RMS e o Azure RMS são uma tecnologia de proteção de informações que ajudam a salvaguardar as informações digitais contra a utilização não autorizada.
keywords: ''
author: bryanla
ms.author: bryanla
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 8A13494E-C1D7-407D-BCD1-A406915EA578
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: a1d251daac312e8a6b39da445cdffc0bca3343ea
ms.sourcegitcommit: bd2b31dd97c8ae08c28b0f5688517110a726e3a1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/08/2019
ms.locfileid: "54071386"
---
# <a name="overview"></a>Descrição geral

SDK Microsoft Rights Management 4.2 é uma tecnologia de proteção de informações e está disponível para várias plataformas.  Fornece um software developer kit (SDK) ou framework, que foi concebido para computadores cliente e dispositivos para ajudar a proteger o acesso e utilização das informações que circulam pelas aplicações com «capacidade para direitos». Os SDKs para estas plataformas fornecem uma API simples para um programador de aplicações proteger ou consumir conteúdos digitais, obter modelos e adquirir políticas de um servidor e outras tarefas de gestão de direitos relacionados.

Para obter mais informações sobre as plataformas atualmente suportadas, consulte o nosso portal de documentação para programadores do [SDK Microsoft Rights Management](active-directory-rights-management-services-multi-platform-thin-client-sdk-portal.md).

Seguem-se alguns dos possíveis cenários:

-   Uma firma de advogados pretende impedir que as mensagens de e-mail confidenciais sejam impressas ou reencaminhadas num dispositivo móvel.
-   Os programadores do projeto assistido por computador e software de fabrico pretendem limitar o acesso de desenho a um pequeno grupo de utilizadores dentro da divisão de pesquisa sem a necessidade da utilização de palavras-passe.
-   Os proprietários de uma aplicação móvel de design gráfico pretendem utilizar uma única licença que permita a livre visualização de cópias de baixa resolução das suas imagens, mas requer o pagamento para o acesso a versões de alta resolução.
-   Os proprietários de uma biblioteca de documentos online pretendem ativar direitos para ver, imprimir ou editar documentos com base na identidade do utilizador quando os documentos são transferidos para um dispositivo móvel.
-   Uma empresa pretende publicar informações confidenciais sobre os funcionários num Web site interno que restringe a visualização e edição de privilégios a determinados utilizadores.

SDK MS RMS 4.2 pode ser transferido, com a confirmação e a aceitação do respetivo contrato de licença, distribuído gratuitamente com o seu software de terceiros para permitir o acesso de cliente ao conteúdo que foi protegido por direitos através da utilização e implementação de servidores do AD RMS no seu ambiente ou serviços do Azure RMS. Para obter mais informações, consulte [Introdução](get-started.md).

## <a name="sdk-highlights"></a>Destaques do SDK


SDK MS RMS 4.2 oferece algumas funcionalidades novas que incluem o seguinte:

-   **API reformulada** – API do MS RMS SDK 4.2 foi reformulada para uma simplicidade máxima para que os programadores possam desfrutar de uma simples e transparente de encriptação e desencriptação API, que fornece os comportamentos de RMS consistentes com esforços mínimos.
-   **Suporte híbrido para o AD RMS e o Azure RMS** – uma única aplicação com suporte RMS pode consumir e proteger conteúdo do servidor AD RMS (utilizando a extensão do dispositivo móvel do AD RMS) e do serviço do Azure RMS. SDK MS RMS 4.2 Deteta de forma transparente o ponto final relevante que os administradores de TI podem configurar.
-   **Traga a sua própria biblioteca de autenticação** – como um programador de aplicações, pode escolher que biblioteca de autenticação é utilizada com o SDK MS RMS 4.2. Seja [do Azure AD Authentication Library](https://msdn.microsoft.com/library/jj573266.aspx) ou à biblioteca personalizada da sua organização, divide de SDK MS RMS 4.2, a pilha de autorização para que possa escolher a biblioteca que mais se adequa às suas necessidades.
-   **Traga a sua própria interface do usuário** -SDK MS RMS 4.2 agora permite que implemente a personalizar a interface do usuário. Desde proteger conteúdo e escolher modelos para mostrar e alterar as permissões enquanto é consumido conteúdo protegido, o SDK MS RMS 4.2 não impõe qualquer IU incorporada nas suas aplicações. Se quiser, no entanto, pode utilizar bibliotecas da IU do Microsoft RMS para todas as plataformas através da nossa [Conta do GitHub](https://github.com/AzureAD/).
-   **Aceder aos conteúdos protegidos offline** – SDK MS RMS 4.2 permite que os utilizadores da aplicação aceder aos conteúdos protegidos, mesmo quando não há nenhuma conectividade com a internet. SDK MS RMS 4.2 em segurança armazena em cache as políticas de consumo dos conteúdos protegidos para que os utilizadores podem aceder a dados protegidos por RMS offline.

Utilize o guia de [Introdução](get-started.md) para iniciar o projeto de aplicação do dispositivo de informações protegidas.

## <a name="related-topics"></a>Tópicos relacionados

* [Microsoft Rights Management SDK](active-directory-rights-management-services-multi-platform-thin-client-sdk-portal.md)
* [Introdução](get-started.md)
* [Azure AD Authentication Library](https://msdn.microsoft.com/library/jj573266.aspx)
* [Conta do GitHub](https://github.com/AzureAD/)
