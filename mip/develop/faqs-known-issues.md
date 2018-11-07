---
title: FAQ e problemas conhecidos - SDK do Microsoft Information projeção.
description: FAQs do SDK de proteção de informações da Microsoft (MIP) e orientações para a resolução de problemas e erros.
author: BryanLa
ms.service: information-protection
ms.topic: troubleshooting
ms.date: 10/19/2018
ms.author: bryanla
ms.openlocfilehash: f213b31d9b0e41ea9c1e076055a90e9f62b31b3a
ms.sourcegitcommit: fa0be701b85b1fba5e75428714bb4525dd739a93
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/07/2018
ms.locfileid: "51223930"
---
# <a name="microsoft-information-protection-mip-sdk-faqs-and-issues"></a>Problemas e perguntas frequentes do SDK de proteção de informações da Microsoft (MIP)

Este artigo fornece respostas a perguntas mais frequentes (FAQs) e orientações de resolução de problemas para problemas conhecidos e erros comuns.

## <a name="frequently-asked-questions"></a>Perguntas Mais Frequentes 

### <a name="question-which-platforms-are-supported-by-the-mip-sdk"></a>Pergunta: que plataformas são suportadas pelo MIP SDK?

O SDK de MIP é suportado nas seguintes plataformas:

[!INCLUDE [MIP SDK platform support](../include/mip-sdk-platform-support.md)]

### <a name="question-how-does-the-sdk-handle-strings-and-what-string-type-should-i-be-using-in-my-code"></a>Pergunta: como é que as cadeias de caracteres de identificador do SDK e o tipo de cadeia de caracteres deve ser usando em meu código?

O SDK se destina a ser utilizada para várias plataformas e usa [UTF-8 (Unicode Transformation Format - 8 bits)](https://wikipedia.org/wiki/UTF-8) para a manipulação de cadeia de caracteres. Documentação de orientação específica depende da plataforma que está a utilizar:

| Platform | Orientação |
|-|-|
| Nativo do Windows | Para clientes de C++ SDK, o tipo de biblioteca de padrão de C++ [ `std::string` ](https://wikipedia.org/wiki/C%2B%2B_string_handling) é usada para passar cadeias de caracteres de/para funções da API. Conversão de/para UTF-8 é gerenciado internamente pelo MIP SDK. Quando um `std::string` é devolvido a partir de uma API, tem de esperar a codificação UTF-8 e gerir em conformidade se a cadeia a converter. Em alguns casos, uma cadeia de caracteres é retornada como parte de um `uint8_t` vetoriais (por exemplo, uma licença de publicação (PL)), mas deve ser tratado como um blob opaco.<br><br>Para obter mais informações e exemplos, consulte:<ul><li>[Função de WideCharToMultiByte](/windows/desktop/api/stringapiset/nf-stringapiset-widechartomultibyte) para obter assistência com a conversão de cadeias de caracteres largos para multi-byte, por exemplo, UTF-8.<li>O seguinte de ficheiros incluídos no exemplo a [download do SDK](setup-configure-mip.md#configure-your-client-workstation):<ul><li>Exemplo de funções de utilitário de cadeia de caracteres no `file\samples\common\string_utils.cpp`, para a conversão de/para o grandes cadeias de caracteres UTF-8.<li>Uma implementação do `wmain(int argc, wchar_t *argv[])` em `file\samples\file\main.cpp`, que utiliza as funções de conversão de cadeia de caracteres anterior.</li></ul></ul>|
| .NET | Para clientes do SDK do .NET, todas as cadeias de caracteres, utilize a codificação predefinida UTF-16 e não é necessária nenhuma conversão especial. Conversão de/para UTF-16 é gerenciado internamente pelo MIP SDK. |
| Outras plataformas | Todas as outras plataformas suportadas pelo MIP SDK tem suporte nativo para UTF-8. |

## <a name="issues-and-errors-reference"></a>Referência de problemas e erros

### <a name="error-file-format-not-supported"></a>Erro: "formato de ficheiro não suportado"  

| Error | Solução |
|-|-|
|*Formato de ficheiro não suportado*| Esta exceção resulta de tentar proteger ou identifique um ficheiro PDF, que foi assinado digitalmente ou protegidos por senha. Ver [novo suporte para encriptação de PDF com proteção de informações do Microsoft](https://techcommunity.microsoft.com/t5/Azure-Information-Protection/New-support-for-PDF-encryption-with-Microsoft-Information/ba-p/262757) para obter mais informações sobre a proteção e etiquetagem ficheiros PDF.|

### <a name="error-failed-to-parse-the-acquired-compliance-policy"></a>Erro: "Falha ao analisar a política de conformidade adquirida"  

Transferiu o SDK de MIP e executou os aplicativos de exemplo. Utilize o exemplo de ficheiro para experimentar listar todas as etiquetas, mas o erro seguinte:

| Error | Solução |
|-|-|
|*Algo ruim aconteceu: Falha ao analisar a política de conformidade adquirida. Falhou com o: [classe mip::CompliancePolicyParserException] marca não encontrado: política, NodeType: 15, nome: não encontrar o nome, valor:, predecessores: <SyncFile> <Content>, correlationId: [34668a40-blll-4ef8-b2af-00005aa674z9]*| Isto indica que ainda não migrados suas etiquetas do Azure Information Protection, para a experiência unificada de etiquetagem. Siga [como migrar as etiquetas do Azure Information Protection para o Centro de conformidade e segurança do Office 365](/azure/information-protection/configure-policy-migrate-labels) para migrar as etiquetas, em seguida, criar uma política de etiqueta no Centro de conformidade e de segurança do Office 365. Quando terminar, o exemplo será executado com êxito.|
