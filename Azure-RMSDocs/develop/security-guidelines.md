---
title: Melhores Práticas de Segurança | Microsoft Information Protection
description: É recomendável seguir as melhores práticas do Azure Information Protection ao conceber aplicações com suporte RMS.
author: lleonard-msft
ms.author: alleonar
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: article
ms.prod: ''
ms.assetid: 4e9f72d5-9e7c-43e1-bb8a-5972dd22dcee
ms.service: information-protection
ms.technology: techgroup-identity
ms.suite: ems
ms.reviewer: kartikk
ms.openlocfilehash: 6c3669c1ada24afcf3b9ec48ea5bb9c38939b47e
ms.sourcegitcommit: 8e622a93ff8d07a180e3be6e8b14748354e640bd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/29/2018
ms.locfileid: "30258780"
---
# <a name="security-best-practices-for-azure-information-protection"></a>Melhores Práticas de Segurança do Azure Information Protection

O Software Development Kit (SDK) do Azure Information Protection (AIP) proporciona um sistema robusto para publicar e consumir informações protegidas de todos os tipos. Para permitir que um sistema AIP seja tão forte quanto possível, as aplicações com suporte AIP têm de ser concebidas tendo em conta as melhores práticas do AIP. As aplicações com suporte AIP têm a responsabilidade partilhada de ajudar a manter a segurança deste ecossistema. Identificar os riscos de segurança e proporcionar soluções de mitigação para esses riscos introduzidos durante o desenvolvimento da aplicação ajuda a minimizar a probabilidade de uma implementação de software menos segura.

As melhores práticas para a implementação de aplicações com o Software Development Kit (SDK) do Azure Information Protection incluem as seguintes categorias de sugestões:
- [Modelos de Ameaças e Mitigações](https://msdn.microsoft.com/library/aa362751.aspx)
- [Ataques de Segurança](https://msdn.microsoft.com/library/aa362736.aspx)

Estas informações complementam o contrato legal que é preciso assinar para obter os certificados digitais necessários para implementar aplicações com o SDK do AIP.

## <a name="subjects-not-covered-in-these-topics"></a>Assuntos Não Abrangidos Nestes Tópicos
Estes tópicos descrevem sucintamente os seguintes problemas, que são significativos quando se tenta criar um ambiente de desenvolvimento e uma aplicação segura:
- **Gestão do processo de desenvolvimento de software** – inclui informações sobre a gestão da configuração, a proteção do código fonte, a minimização do acesso ao código depurado e a atribuição de prioridade a erros. Para alguns dos seus clientes, ter um processo de desenvolvimento de software mais seguro reveste-se da maior importância. Alguns clientes prescrevem mesmo um processo de desenvolvimento.
- **Erros de codificação comuns** – inclui informações sobre como evitar transbordos da memória intermédia. Recomendamos a versão mais recente de “Writing Secure Code”, de Michael Howard e David LeBlanc (Microsoft Press, 2002), para rever estas ameaças e mitigações genéricas.
- **Engenharia social** – inclui informações sobre salvaguardas processuais e estruturais que ajudam a proteger contra a exploração do código por programadores ou outras pessoas na organização do fabricante.
- **Segurança física** – inclui informações sobre o bloqueio do acesso ao seu código base e a assinatura de certificados.
- **Implementação ou distribuição de software de pré-lançamento** – inclui informações sobre a distribuição de software beta.
- **Gestão de rede** – inclui informações sobre sistemas de deteção de intrusões nas suas redes físicas.

## <a name="threat-models-and-mitigations"></a>Modelos de Ameaças e Mitigações
Os proprietários de informações digitais têm de ser capazes de avaliar os ambientes nos quais os seus recursos serão desencriptados. Uma declaração de padrões de segurança mínimos pode proporcionar aos proprietários de informações um enquadramento que lhes permite compreender e avaliar o nível de segurança das aplicações às quais confiam as suas informações.

Alguns setores, como a administração pública e a saúde, têm processos e normas de certificação e acreditação que se podem aplicar ao seu produto. O cumprimento destas recomendações de segurança mínimas não substitui as necessidades de acreditação exclusivas dos seus clientes. No entanto, o objetivo dos padrões de segurança consiste em ajudá-lo a preparar-se para os requisitos atuais e futuros dos clientes e qualquer investimento que faça no início do ciclo de desenvolvimento será vantajoso para a sua aplicação. As informações aqui disponibilizadas são recomendações e não um programa de certificação formal da Microsoft.

Existem várias categorias principais de vulnerabilidades num sistema de serviços de gestão de direitos, incluindo as seguintes:
- **Fuga** – as informações aparecem em localizações não autorizadas.
- **Danos** – o software ou os dados são modificados de forma não autorizada.
- **Rejeição** – um recurso informático não está disponível para utilização.

Estes tópicos concentram-se principalmente nos problemas relacionados com as fugas. A integridade de um sistema AIP depende da respetiva capacidade de proteger as informações ao longo do tempo e de permitir o acesso apenas a entidades designadas. Estes tópicos abordam também os problemas relacionados com os danos. Os problemas de rejeição não são abrangidos.

A Microsoft não testa nem revê os resultados de testes relacionados com o cumprimento dos padrões mínimos; é da inteira responsabilidade do parceiro garantir que os padrões mínimos são cumpridos. A Microsoft disponibiliza dois níveis adicionais de recomendações para ajudar a mitigar ameaças comuns. Em geral, estas sugestões têm caráter aditivo. Por exemplo, para cumprir as recomendações preferenciais, parte-se do princípio de que cumpriu os padrões mínimos, onde aplicável, salvo especificação em contrário.

|Nível do padrão|    Descrição|
|---|---|
|Padrão mínimo|  É preciso determinar que uma aplicação que processa informações protegidas pelo AIP cumpre o padrão mínimo antes de poder ser assinada com o certificado de produção recebido da Microsoft. Geralmente, os parceiros utilizam o certificado de hierarquia de produção apenas no momento do lançamento final do software, depois de os seus próprios testes internos confirmarem que a aplicação satisfaz este padrão mínimo. O cumprimento do padrão mínimo não é uma garantia de segurança por parte da Microsoft e não deve ser interpretado como tal. A Microsoft não testa nem revê os resultados de testes relacionados com o cumprimento dos padrões mínimos; é da inteira responsabilidade do parceiro garantir que os padrões mínimos são cumpridos.|
|Padrão recomendado|  As diretrizes recomendadas traçam um caminho para uma maior segurança das aplicações, além de proporcionarem uma indicação da forma como o AIP pode evoluir à medida que são implementados mais critérios de segurança. Os fornecedores poderão tentar diferenciar as suas aplicações ao concebê-las de acordo com este nível mais elevado de diretrizes de segurança.|
|Padrão preferencial|    É a mais elevada categoria de segurança atualmente definida. Os fornecedores que desenvolvem aplicações comercializadas como altamente seguras devem ter em vista este padrão. As aplicações que satisfazem este padrão são, provavelmente, as menos vulneráveis a ataques.|




## <a name="malicious-software"></a>Software Malicioso
A Microsoft definiu padrões obrigatórios mínimos que a sua aplicação tem de satisfazer para proteger os conteúdos contra software malicioso.

### <a name="importing-malicious-software-by-using-address-tables"></a>Importar Software Malicioso Através de Tabelas de Endereços
O AIP não suporta a modificação do código durante o tempo de execução nem a modificação da tabela de endereços de importação (IAT). É criada uma tabela de endereços de importação para cada DLL carregado no seu espaço de processo. Essa tabela especifica os endereços de todas as funções que a sua aplicação importa. Um ataque comum consiste em modificar as entradas de IAT numa aplicação para, por exemplo, apontarem para software malicioso. O AIP para a aplicação quando deteta este tipo de ataque.

### <a name="minimum-standard"></a>Padrão mínimo
- Não pode modificar a tabela de endereços de importação no processo da aplicação durante a execução. A aplicação especifica muitas das funções chamadas durante o tempo de execução através da utilização de tabelas de endereços e estas não podem ser alteradas durante ou após o tempo de execução. Entre outras coisas, isto significa que não pode criar um perfil do código de uma aplicação assinada com o certificado de produção.
- Não pode chamar a função **DebugBreak** a partir de qualquer DLL especificado no manifesto.
- Não pode chamar **LoadLibrary** com o sinalizador **DONT_RESOLVE_DLL_REFERENCES** definido. Este sinalizador indica ao carregador para ignorar o enlace aos módulos importados, que modifica a tabela de endereços de importação.
- Não pode alterar o carregamento atrasado ao fazer alterações durante o tempo de execução ou subsequentes ao comutador de ligação /DELAYLOAD.
- Não pode alterar o carregamento atrasado ao fornecer a sua própria versão da função de programa auxiliar Delayimp.lib.
- Não pode descarregar módulos que tenham sido carregados com atraso por módulos autenticados enquanto o ambiente de AIP existir.
- Não pode utilizar o comutador de ligação **/DELAY:UNLOAD** para ativar a descarga dos módulos atrasados.


## <a name="incorrectly-interpreting-license-rights"></a>Interpretar Incorretamente Direitos de Licença

Se a sua aplicação não interpretar e impuser corretamente os direitos expressos na licença de emissão do AIP, poderá disponibilizar as informações de formas que o proprietário das mesmas não tencionava. Por exemplo, uma aplicação pode permitir a um utilizador guardar informações não encriptadas num novo suporte de dados quando a licença de emissão confere apenas o direito de ver as informações.

O sistema AIP organiza os direitos em alguns agrupamentos. Para obter mais informações, veja [Configuração de direitos de utilização para o Azure Rights Management](../deploy-use/configure-usage-rights.md).

### <a name="azure-information-protection"></a>Azure Information Protection  
O AIP permite que um utilizador desencripte informações ou não; as informações não têm qualquer proteção inerente. Se um utilizador tiver o direito de desencriptar informações, o AIP permite que o faça e a aplicação é responsável por gerir ou proteger essas informações depois de estarem a salvo. Uma aplicação é responsável por gerir o seu ambiente e interface de modo a impedir a utilização não autorizada de informações. Por exemplo, poderá desativar os botões **Imprimir** e **Copiar** se uma licença conceder apenas o direito REPRODUZIR. O seu conjunto de aplicações de teste deve confirmar se a aplicação atua corretamente em todos os direitos de licença que reconhece.

### <a name="minimum-standard"></a>Padrão mínimo
- A implementação de cliente de XrML v.1.2 direitos deve ser consistente com as definições destes direitos, conforme descrito nas especificações XrML, que estão disponíveis no site XrML Web (http://www.xrml.org). Quaisquer direitos que sejam específicos da sua aplicação têm de ser definidos para todas as entidades que têm um interesse na mesma.
- O seu conjunto de aplicações de teste e o seu processo de teste devem confirmar se a aplicação executa corretamente os direitos que suporta e que não atua com base em direitos não suportados.
- Se estiver a criar uma aplicação de publicação, tem de disponibilizar informações que expliquem que direitos intrínsecos são e não são suportados pela aplicação e como esses direitos devem ser interpretados. Além disso, a interface de utilizador deve explicar claramente ao utilizador final quais são as implicações de cada direito concedido ou negado a uma determinada informação.

- Quaisquer direitos que sejam abstraídos por inclusão em novos direitos implementados por uma aplicação têm de ser mapeados para a nova terminologia. Por exemplo, um novo direito denominado GESTOR pode incluir como direitos abstraídos os direitos IMPRIMIR, COPIAR e EDITAR.
Padrão recomendado    Nenhum neste momento.
Padrão preferencial  Nenhum neste momento.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]