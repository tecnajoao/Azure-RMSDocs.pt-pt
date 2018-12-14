---
title: Melhores práticas de segurança para proteção de informações
description: Aplicações com suporte RMS melhor são criadas utilizando as melhores práticas de proteção de informações.
author: lleonard-msft
ms.author: alleonar
manager: mbaldwin
ms.date: 12/13/2018
ms.topic: conceptual
ms.assetid: 4e9f72d5-9e7c-43e1-bb8a-5972dd22dcee
ms.service: information-protection
ms.suite: ems
ms.reviewer: kartikk
ms.openlocfilehash: c3a342dfa6be9640504bac4b44ef910534b1497d
ms.sourcegitcommit: c9a0d81c18ea79a2520baa4b3777b06a72f87f60
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53382457"
---
# <a name="security-best-practices-for-information-protection"></a>Melhores práticas de segurança para proteção de informações

Kits de desenvolvimento de Software de proteção de informações (SDKs) fornecem um sistema robusto para publicar e consumir informações protegidas de todos os tipos. Para ajudar a um sistema ser tão forte quanto possível, aplicativos de ativar a proteção de informações devem ser criados utilizando as melhores práticas. Aplicações partilham responsabilidade nos ajudar a manter a segurança deste ecossistema. Identificar os riscos de segurança e proporcionar soluções de mitigação para esses riscos introduzidos durante o desenvolvimento da aplicação ajuda a minimizar a probabilidade de uma implementação de software menos segura.

Estas informações complementam o contrato legal que deve estar assinado, para obter os certificados digitais para aplicações com os SDKs.

## <a name="subjects-not-covered"></a>Assuntos não abrangidos

Embora os seguintes assuntos são considerações importantes para a criação de um ambiente de desenvolvimento e aplicativos seguros, estão fora do escopo deste artigo:

- **Gerenciamento de processos de desenvolvimento de software** – gerenciamento de configuração, protegendo o código-fonte, minimizando o acesso ao código depurado e atribuir prioridade a erros. Para alguns clientes, ter um processo de desenvolvimento de software mais seguro é de fundamental importância aos mesmos. Alguns clientes prescrevem mesmo um processo de desenvolvimento.
- **Erros de codificação comuns** – informações para evitar saturações de buffer. Recomendamos a versão mais recente de “Writing Secure Code”, de Michael Howard e David LeBlanc (Microsoft Press, 2002), para rever estas ameaças e mitigações genéricas.
- **Engenharia social** – inclui informações sobre salvaguardas processuais e estruturais, para ajudar a proteger o código contra a exploração por programadores ou outras pessoas na organização do fabricante.
- **Segurança física** – inclui informações sobre o bloqueio do acesso ao seu código base e a assinatura de certificados.
- **Implementação ou distribuição de software de pré-lançamento** – inclui informações sobre a distribuição de software beta.
- **Gestão de rede** – inclui informações sobre sistemas de deteção de intrusões nas suas redes físicas.

## <a name="threat-models-and-mitigations"></a>Modelos de ameaças e mitigações

Os proprietários de informações digitais tem a capacidade de avaliar os ambientes em que os seus recursos serão desencriptados. Uma instrução de padrões de segurança mínima fornece aos proprietários de informações uma estrutura de compreender e avaliar o nível de segurança dos aplicativos.

Alguns setores, como a administração pública e a saúde, têm processos e normas de certificação e acreditação que se podem aplicar ao seu produto. Estas recomendações de segurança mínimo de reunião, não é um substituto para as necessidades de acreditação exclusivas dos seus clientes. No entanto, o objetivo dos padrões de segurança consiste em ajudá-lo a preparar-se para os requisitos atuais e futuros dos clientes e qualquer investimento que faça no início do ciclo de desenvolvimento será vantajoso para a sua aplicação. Essas diretrizes são recomendações e não um programa de certificação de Microsoft formal.

Existem várias categorias principais de vulnerabilidades num sistema de serviços de gestão de direitos, incluindo as seguintes:

- **Fuga** – as informações aparecem em localizações não autorizadas.
- **Danos** – o software ou os dados são modificados de forma não autorizada.
- **Negação** — um recurso informático não está disponível para utilização.

Estes tópicos concentram-se principalmente nos problemas relacionados com as fugas. A integridade de um sistema AIP depende da sua capacidade, ao longo do tempo, para proteger as informações, permitindo o acesso apenas a entidades designadas. Estes tópicos abordam também os problemas relacionados com os danos. Os problemas de rejeição não são abrangidos.

Microsoft não testa nem revê os resultados de testes relacionados com o cumprimento dos padrões mínimos. O parceiro é responsável por garantir que os padrões mínimos são cumpridos. A Microsoft disponibiliza dois níveis adicionais de recomendações para ajudar a mitigar ameaças comuns. Em geral, estas sugestões são cumulativas. Por exemplo, cumprir as recomendações preferenciais parte do princípio de que cumpriu os padrões mínimos, quando aplicável, salvo especificação em contrário.

|Nível do padrão|Descrição|
|---|---|
|Padrão mínimo| Um aplicativo que identificadores protegidos informações têm de cumprir o padrão mínimo, antes de ele pode ser assinado com o certificado de produção recebido da Microsoft. Parceiros em geral, utilizam o certificado de hierarquia de produção, no momento do lançamento final do software. Um parceiro proprietário interno os testes são usados para verificar se a aplicação satisfaz este padrão mínimo. Cumprimento dos padrões mínimos não é e não deve ser interpretada como uma garantia de segurança pela Microsoft. Microsoft não testa nem revê os resultados de testes relacionados com o cumprimento dos padrões mínimos. O parceiro é responsável por assegurar que o mínimo é cumprido.|
|Padrão recomendado| Diretrizes recomendadas traçam um caminho para maior segurança das aplicações tanto proporcionarem uma indicação da forma como o SDK pode evoluir à medida que são implementados mais critérios de segurança. Fornecedores podem diferenciar seus aplicativos pela criação para este nível mais elevado de diretrizes de segurança.|
|Padrão preferencial| Este padrão é a mais elevada categoria de segurança atualmente definida. Os fornecedores que desenvolvem aplicações comercializadas como altamente seguras devem ter em vista este padrão. As aplicações que satisfazem este padrão são, provavelmente, as menos vulneráveis a ataques.|

## <a name="malicious-software"></a>Software malicioso

A Microsoft definiu padrões obrigatórios mínimos que a sua aplicação tem de satisfazer para proteger os conteúdos contra software malicioso.

### <a name="importing-malicious-software-by-using-address-tables"></a>Importar software malicioso através de tabelas de endereços

O SDK do information protection não suporta a modificação do código em tempo de execução ou modificação da tabela de endereços de importação (IAT). É criada uma tabela de endereços de importação para cada DLL carregado no seu espaço de processo. Essa tabela especifica os endereços de todas as funções que a sua aplicação importa. Um ataque comum consiste em modificar as entradas de IAT numa aplicação para, por exemplo, apontarem para software malicioso. O SDK para a aplicação quando Deteta este tipo de ataque.

### <a name="minimum-standard"></a>Padrão mínimo

- Não é possível modificar a tabela de endereços de importação no processo do aplicativo durante a execução. A aplicação especifica muitas das funções chamadas durante o tempo de execução por usando tabelas de endereços. Estas tabelas não podem ser alteradas durante ou após o tempo de execução. Entre outras coisas, significa que esta restrição não é possível efetuar o perfil do código de uma aplicação assinada com o certificado de produção.
- Não pode chamar o **DebugBreak** funcionar de qualquer dll especificado no manifesto.
- Não pode chamar **LoadLibrary** com o **DONT_RESOLVE_DLL_REFERENCES** sinalizar o conjunto. Este sinalizador indica ao carregador para ignorar o enlace aos módulos importados, que modifica a tabela de endereços de importação.
- Não é possível alterar o carregamento atrasado ao fazer alterações de tempo de execução ou subsequentes ao comutador de ligação /delayload.
- Não é possível alterar o carregamento atrasado ao fornecer sua própria versão da função de programa auxiliar delayimp.
- Não pode descarregar módulos que são carregados com atraso por módulos autenticados, enquanto o ambiente de SDK de proteção de informações existe.
- Não é possível utilizar o **`/DELAY:UNLOAD`** comutador de ligação para ativar a descarga dos módulos de atrasados.

## <a name="incorrectly-interpreting-license-rights"></a>Interpretar incorretamente direitos de licença

Se seu aplicativo corretamente não interpretar e impor os direitos expressos na licença de emissão de SDK, pode disponibilizar informações disponíveis de forma a que o proprietário de informações não tinha a intenção. Por exemplo, quando um aplicativo permite que um utilizador guardar informações não encriptadas para o novo suporte de dados, quando a licença de emissão confere apenas o direito de ver as informações.

### <a name="azure-information-protection-aip"></a>Azure Information Protection (AIP)

O sistema de proteção de informações organiza os direitos em alguns agrupamentos. Para obter mais informações, veja [Configuração de direitos de utilização para o Azure Rights Management](../configure-usage-rights.md).

AIP permite que um utilizador desencripte informações ou não. As informações não têm qualquer proteção inerente. Se um utilizador tiver o direito de desencriptar, a API permite que o faça. A aplicação é responsável por gerir ou proteger essas informações depois é transparente. Uma aplicação é responsável por gerenciar seu ambiente e interface para impedir a utilização não autorizada de informações. Por exemplo, poderá desativar a **impressão** e **cópia** botões se uma licença conceder apenas a EXIBIÇÃO diretamente. O seu conjunto de aplicações de teste deve confirmar se a aplicação atua corretamente em todos os direitos de licença que reconhece.

### <a name="minimum-standard"></a>Padrão mínimo

- A implementação de cliente direitos de XrML v.1.2 deve ser consistente com as definições desses direitos, conforme descrito nas especificações de XrML, que estão disponíveis no site do XrML (http://www.xrml.org). Quaisquer direitos que sejam específicos da sua aplicação têm de ser definidos para todas as entidades que têm um interesse na mesma.
- O processo de teste suite e o teste deverá certificar-se de que a aplicação executa corretamente os direitos de que o aplicativo oferece suporte. Ele também deve verificar que ele **não** agir de acordo com os direitos não suportados.
- Se estiver a criar uma aplicação de publicação, tem de disponibilizar informações que explica os direitos intrínsecos utilizados. Isto inclui os que são e não são suportados pela aplicação e como esses direitos devem ser interpretados. Além disso, a interface de utilizador deve explicar claramente ao utilizador final quais são as implicações de cada direito concedido ou negado a uma determinada informação.
- Quaisquer direitos que sejam abstraídos por inclusão em novos direitos implementados por uma aplicação, tem de ser mapeados para a nova terminologia. Por exemplo, um novo direito denominado GESTOR pode incluir como direitos abstraídos os direitos IMPRIMIR, COPIAR e EDITAR.

### <a name="recommended-standard"></a>Padrão recomendado

Nenhum neste momento.

### <a name="preferred-standard"></a>Padrão preferencial

Nenhum neste momento.

## <a name="next-steps"></a>Passos Seguintes

Melhores práticas para implementar aplicações com o SDK do AIP incluem os seguintes artigos:

- [Modelos de Ameaças e Mitigações](https://msdn.microsoft.com/library/aa362751.aspx)
- [Ataques de Segurança](https://msdn.microsoft.com/library/aa362736.aspx)
