---
title: FAQ e problemas conhecidos - SDK do Microsoft Information projeção.
description: FAQs do SDK de proteção de informações da Microsoft (MIP) e orientações para a resolução de problemas e erros.
author: msmbaldwin
ms.service: information-protection
ms.topic: troubleshooting
ms.collection: M365-security-compliance
ms.date: 03/05/2019
ms.author: mbaldwin
ms.openlocfilehash: 78dc655d8244378fcc37b22030d3060fd291ef16
ms.sourcegitcommit: ea76aade54134afaf5023145fcb755e40c7b84b7
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/15/2019
ms.locfileid: "59574232"
---
# <a name="microsoft-information-protection-mip-sdk-faqs-and-issues"></a>Problemas e perguntas frequentes do SDK de proteção de informações da Microsoft (MIP)

Este artigo fornece respostas a perguntas mais frequentes (FAQs) e orientações de resolução de problemas para problemas conhecidos e erros comuns.

## <a name="frequently-asked-questions"></a>Perguntas Mais Frequentes 

### <a name="sdk-string-handling"></a>Manipulação de cadeia de caracteres SDK

**Pergunta**: Como o SDK manipular cadeias de caracteres, e que tipo de cadeia de caracteres deve eu estar usando em meu código?

O SDK se destina a ser utilizada para várias plataformas e usa [UTF-8 (Unicode Transformation Format - 8 bits)](https://wikipedia.org/wiki/UTF-8) para a manipulação de cadeia de caracteres. Documentação de orientação específica depende da plataforma que está a utilizar:

| Plataforma | Orientação |
|-|-|
| Nativo do Windows | Para clientes de C++ SDK, o tipo de biblioteca de padrão de C++ [ `std::string` ](https://wikipedia.org/wiki/C%2B%2B_string_handling) é usada para passar cadeias de caracteres de/para funções da API. Conversão de/para UTF-8 é gerenciado internamente pelo MIP SDK. Quando um `std::string` é devolvido a partir de uma API, tem de esperar a codificação UTF-8 e gerir em conformidade se a cadeia a converter. Em alguns casos, uma cadeia de caracteres é retornada como parte de um `uint8_t` vetoriais (por exemplo, uma licença de publicação (PL)), mas deve ser tratado como um blob opaco.<br><br>Para obter mais informações e exemplos, consulte:<ul><li>[Função de WideCharToMultiByte](/windows/desktop/api/stringapiset/nf-stringapiset-widechartomultibyte) para obter assistência com a conversão de cadeias de caracteres largos para multi-byte, por exemplo, UTF-8.<li>O seguinte de ficheiros incluídos no exemplo a [download do SDK](setup-configure-mip.md#configure-your-client-workstation):<ul><li>Exemplo de funções de utilitário de cadeia de caracteres no `file\samples\common\string_utils.cpp`, para a conversão de/para o grandes cadeias de caracteres UTF-8.<li>Uma implementação do `wmain(int argc, wchar_t *argv[])` em `file\samples\file\main.cpp`, que utiliza as funções de conversão de cadeia de caracteres anterior.</li></ul></ul>|
| .NET | Para clientes do SDK do .NET, todas as cadeias de caracteres, utilize a codificação predefinida UTF-16 e não é necessária nenhuma conversão especial. Conversão de/para UTF-16 é gerenciado internamente pelo MIP SDK. |
| Outras plataformas | Todas as outras plataformas suportadas pelo MIP SDK tem suporte nativo para UTF-8. |

## <a name="issues-and-errors-reference"></a>Referência de problemas e erros

### <a name="error-file-format-not-supported"></a>Erro: "Formato de ficheiro não suportado"  

**Pergunta**: Por que motivo recebo o seguinte erro ao tentar proteger ou identifique um ficheiro PDF?

> Formato de ficheiro não suportado

Esta exceção resulta de tentar proteger ou identifique um ficheiro PDF que foram assinado digitalmente ou protegidos por senha. Ver [novo suporte para encriptação de PDF com proteção de informações do Microsoft](https://techcommunity.microsoft.com/t5/Azure-Information-Protection/New-support-for-PDF-encryption-with-Microsoft-Information/ba-p/262757) para obter mais informações sobre a proteção e etiquetagem ficheiros PDF.

### <a name="error-failed-to-parse-the-acquired-compliance-policy"></a>Erro: "Falha ao analisar a política de conformidade adquirida"  

**Pergunta**: Por que obtenho o erro seguinte depois de baixar o SDK de MIP e tentar utilizar o exemplo de ficheiro para listar todas as etiquetas?

> Algo ruim aconteceu: Falha ao analisar a política de conformidade adquirida. Falhou com o: [classe mip::CompliancePolicyParserException] marca não encontrado: política, NodeType: 15, nome: Não encontrar o nome, valor:, predecessores: <SyncFile> <Content>, correlationId: [34668a40-blll-4ef8-b2af-00005aa674z9]

Isto indica que ainda não tiver migrado as etiquetas do Azure Information Protection para a experiência unificada de etiquetagem. Siga [como migrar as etiquetas do Azure Information Protection para o Centro de conformidade e segurança do Office 365](/azure/information-protection/configure-policy-migrate-labels) para migrar as etiquetas, em seguida, criar uma política de etiqueta no Centro de conformidade e de segurança do Office 365. 

### <a name="error-systemcomponentmodelwin32exception-loadlibrary-failed"></a>Erro: "System.ComponentModel.Win32Exception: LoadLibrary falhou"

**Pergunta**: Por que obtenho o erro seguinte ao utilizar o Wrapper do .NET SDK MIP?

> System.ComponentModel.Win32Exception: LoadLibrary falhou para: [sdk_wrapper_dotnet.dll] ao chamar MIP. Initialize ().

Seu aplicativo não tem o tempo de execução necessário, ou não foi criado como versão. Ver [Certifique-se de que a aplicação tem o tempo de execução necessário](setup-configure-mip.md#ensure-your-app-has-the-required-runtime) para obter mais informações. 

### <a name="error-proxyautherror-exception"></a>Erro: "ProxyAuthError exceção"

**Pergunta**: Por que obtenho o erro seguinte ao utilizar o SDK de MIP?

> "ProxyAuthenticatonError: Não é suportada a autenticação de proxy"

O SDK de MIP não suporta a utilização de proxies autenticados. Para corrigir esta mensagem, os administradores de proxy devem definir os pontos de extremidade do serviço do Microsoft Information Protection para ignorar o proxy. Está disponível numa lista desses pontos de extremidade a [intervalos de endereços IP e URLs do Office 365](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges) página. SDK de MIP requer que `*.protection.outlook.com` (linha 9) e os pontos de extremidade de serviço do Azure Information Protection (linha 73) ignorar a autenticação de proxy.
