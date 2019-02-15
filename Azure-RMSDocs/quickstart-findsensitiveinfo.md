---
title: Início rápido – localize as informações confidenciais nos ficheiros ao utilizar o scanner do Azure Information Protection – AIP
description: Utilize o scanner do Azure Information Protection para encontrar as informações confidenciais que tiver em ficheiros armazenados no local.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 02/15/2019
ms.topic: quickstart
ms.collection: M365-security-compliance
ms.service: information-protection
ms.openlocfilehash: 07baee062d994b6efd97084bf0b293adb2d5fb84
ms.sourcegitcommit: 89d2c2595bc7abda9a8b5e505b7dcf963e18c822
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/14/2019
ms.locfileid: "56266017"
---
# <a name="quickstart-find-what-sensitive-information-you-have-in-files-stored-on-premises"></a>Início rápido: Localizar as informações confidenciais que tiver no ficheiros armazenados no local

>*Aplica-se a: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

Neste início rápido, irá instalar e configurar o scanner do Azure Information Protection para encontrar as informações confidenciais que tiver em ficheiros que estão armazenados num arquivo de dados no local. Por exemplo, uma pasta local, compartilhamento de rede ou servidor do SharePoint.

Nota: Este início rápido utiliza a versão atual da disponibilidade geral do scanner e não a versão de pré-visualização, que utiliza o portal do Azure para a configuração.

Pode concluir esta configuração em menos de 10 minutos.

## <a name="prerequisites"></a>Pré-requisitos

Para concluir este início rápido, precisa de:

1. Uma subscrição que inclui o Azure Information Protection plano 1 ou plano 2.
    
    Se não tiver uma destas subscrições, pode criar uma [gratuita](https://portal.office.com/Signup/Signup.aspx?OfferId=87dd2714-d452-48a0-a809-d2f58c4f68b7) de conta para a sua organização.

2. O cliente do Azure Information Protection está instalado no seu computador. 
    
    Para instalar o cliente, vá para o [Centro de transferências da Microsoft](https://www.microsoft.com/en-us/download/details.aspx?id=53018) e transfira **AzInfoProtection.exe** da página do Azure Information Protection.
    
3. SQL Server Express também é instalado no seu computador.
    
    Se esta edição do SQL Server já não estiver instalada, poderá transferi-lo a partir da [Microsoft Download Center](https://www.microsoft.com/en-us/sql-server/sql-server-editions-express) e selecione uma instalação básica.

4. Sua conta de domínio está sincronizada com o Azure AD.

Para obter uma lista completa de pré-requisitos para utilizar o Azure Information Protection, consulte [requisitos do Azure Information Protection](requirements.md).

## <a name="prepare-a-test-folder-and-file"></a>Preparar uma pasta de teste e ficheiro

Para um teste inicial confirmar se o scanner está a funcionar:

1. Crie uma pasta local no seu computador. Por exemplo, **TestScanner** no disco local C.

2. Criar e guardar um documento do Word nessa pasta, que tem o texto **4242-4242-4242-4242** (um número de cartão de crédito conhecidos para fins de teste).

## <a name="install-the-scanner"></a>Instalar o scanner

1. Abra uma sessão do PowerShell com o **executar como administrador** opção.

2. Utilize o seguinte comando para instalar o scanner, especificando o nome do computador:
    
        Install-AIPScanner -SqlServerInstance <your computer name>\SQLEXPRESS
    
    Quando lhe for pedido, forneça suas próprias credenciais para o scanner utilizando o \<nome de domínio \ utilizador > formato e, em seguida, a palavra-passe. 

## <a name="specify-your-test-data-store"></a>Especificar o arquivo de dados de teste

Na sessão do PowerShell, escreva o seguinte comando:

    Add-AIPScannerRepository -Path C:\TestScanner

## <a name="configure-the-scanner-to-discover-all-information-types"></a>Configurar a deteção de impressão para detetar todos os tipos de informações

Na sessão do PowerShell, escreva o seguinte comando:

    Set-AIPScannerConfiguration -Enforce Off -Schedule Manual -DiscoverInformationTypes All

Este comando configura o scanner para o fazer uma deteção única de todos os ficheiros no seu repositório de dados especificada. Esta análise procura todos os tipos conhecidos de informações confidenciais e não exige que primeiro de configurar o Azure Information Protection etiquetas ou definições de política.

## <a name="start-the-scan-and-confirm-it-finished"></a>Iniciar a análise e confirme que foi concluída

1. Na sessão do PowerShell, escreva o seguinte comando para iniciar o scanner:
    
        Start-AIPScan
    
    Há apenas um pequeno ficheiro para inspecionar, para que esta análise inicial de teste será muito rápida. 

2. Aceda ao seu Windows **Visualizador de eventos** > **aplicações e serviços** > **Azure Information Protection** registo de eventos. 
    
    Confirme que o Azure Information Protection mostra o ID de evento informativo **911** para o **MSIP. Scanner** processo. A entrada de registo de eventos também tem um resumo dos resultados da análise.

## <a name="see-detailed-results"></a>Ver resultados detalhados

Utilizar o Explorador de ficheiros, localize os relatórios de scanner em %*localappdata*% \Microsoft\MSIP\Scanner\Reports. Abra o ficheiro de relatório detalhado que tem um formato de ficheiro. csv.

No Excel, as duas primeiras colunas exibem seu nome de ficheiro e de repositório da loja de dados. Quando examinar as colunas, verá um denominado **nome do tipo de informações**, que é a coluna que estiver mais interessado. Para nosso teste inicial, ele exibe **número de cartão de crédito**, um dos vários tipos de informações confidenciais que pode encontrar o scanner.

## <a name="scan-your-own-data"></a>Analisar os seus dados

1. Execute Add-AIPScannerRepository novamente, desta vez especificar a sua própria-local no arquivo de dados que pretende analisar as informações confidenciais. 
    
    Pode especificar uma pasta local, um compartilhamento de rede (caminho UNC) ou um URL do servidor SharePoint para um site do SharePoint ou biblioteca. 
    
    - Exemplo para uma pasta local:
        
            Add-AIPScannerRepository -Path D:\Data\Finance
    
    - Exemplo de uma partilha de rede
        
            Add-AIPScannerRepository -Path \\NAS\HR
    
    - Exemplo para uma pasta do SharePoint:
        
            Add-AIPScannerRepository -Path "http://sp2016/Shared Documents"

2. Reinicie o scanner:
    
        Start-AIPScan

3. Ver os novos resultados quando a análise estiver concluída. 
    
    Quanto tempo leva esta análise depende de quantos arquivos que lá estão em seu arquivo de dados, como grandes esses arquivos estão e o tipo de ficheiro. 

## <a name="clean-up-resources"></a>Limpar recursos

Num ambiente de produção, seria executado a deteção de impressão no Windows Server, usando uma conta de serviço que silenciosamente autentica para o serviço Azure Information Protection. Seria também utiliza uma versão de nível empresarial do SQL Server e provavelmente especificar vários repositórios de dados. 

Para limpar os recursos, prontos para essa implantação de produção, na sessão do PowerShell, execute o seguinte comando para desinstalar o scanner:

    Uninstall-AIPScanner

Em seguida, reinicie o computador.

Este comando não remove os seguintes itens e tem de remover manualmente-los se não quiser que eles após este início rápido:

- A base de dados do SQL Server com o nome **AzInfoProtection** que foi criada ao executar o cmdlet Install-AIPScanner quando o scanner do Azure Information Protection foi instalado. 

- Os relatórios de scanner localizado em %*localappdata*% \Microsoft\MSIP\Scanner\Reports.

- O **iniciar sessão como um serviço** atribuição de direito de utilizador que sua conta de domínio foi concedida para o seu computador local.


## <a name="next-steps"></a>Passos Seguintes

Este guia de introdução inclui a configuração mínima para que pode ver rapidamente como o scanner pode encontrar informações confidenciais num compartilhamento de rede. Se estiver pronto para instalar o scanner num ambiente de produção, veja [Implantando o scanner do Azure Information Protection para classificar e proteger ficheiros automaticamente](deploy-aip-scanner.md).

Se quiser classificar e proteger os ficheiros que contêm informações confidenciais, tem de configurar o Azure Information Protection etiquetas para classificação automática e proteção:

- [Como configurar condições para classificação automática e recomendada para o Azure Information Protection](configure-policy-classification.md)

- [Como configurar uma etiqueta para proteção do Rights Management](configure-policy-protection.md)
