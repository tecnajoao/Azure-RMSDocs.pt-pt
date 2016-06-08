---
# required metadata

title: De que forma este SDK é melhor | Azure RMS
description: Este tópico descreve de que forma o SDK RMS 2.1 é uma melhoria significativa em relação ao SDK dos Serviços de Gestão de Direitos do Active Directory original.
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 622D5C6E-07D5-4C71-A99D-9823C1FE6936
# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---
** Este conteúdo do SDK não está atualizado. Durante um curto período de tempo, pode encontrar a [versão atual](https://msdn.microsoft.com/library/windows/desktop/hh535290(v=vs.85).aspx) da documentação no MSDN. **
# De que forma este SDK é melhor
Este tópico descreve de que forma o SDK Rights Management Services 2.1 é uma melhoria significativa em relação ao [SDK dos Serviços de Gestão de Direitos do Active Directory](https://msdn.microsoft.com/library/Cc530379) original em termos de esforço exigido ao programador para criar uma aplicação com capacidade para direitos.

**Superfície de API** – A superfície de API foi significativamente reduzida através da sintetização, libertando-o de muitos dos detalhes da implementação de back-end. Numa superfície de API de 84 funções para o SDK RMS, o SDK RMS 2.1 inclui apenas 20 funções de API. A maioria das aplicações terá de utilizar apenas um pequeno subconjunto desta superfície de API.

**Tempo de lançamento** – Com o SDK RMS 2.1, poderá seguir um guia passo a passo para identificar quais são os recursos sensíveis da aplicação e como os pode proteger. Tal não acontecia no SDK RMS, no qual tinha de possuir um conhecimento detalhado dos certificados, formatos e topologias, bem como escrever código complexo para multithreading.

**Suporte multitopologia** – O SDK RMS 2.1 ajuda-o a minimizar a conversão de código; a sua aplicação deverá trabalhar com todas as topologias, já que sintetizamos a complexidade de topologia para o programador. Com o SDK RMS, tinha de compreender todas as topologias suportadas e, em seguida, escrever e testar código específico em cada uma delas.

**Preparado para o futuro** – O SDK RMS 2.1 ajuda-o a minimizar a conversão do código de ativação de direitos; a aplicação deverá funcionar em qualquer ambiente do RMS e tirar automaticamente partido das novas funcionalidades sempre que são lançadas funcionalidades do RMS essenciais. Tal não acontecia no SDK AD RMS, onde era necessário atualizar a aplicação para tirar partido explicitamente de quaisquer novas funcionalidades.

**Aviso Importante**  
Todos os tópicos no [SDK dos Serviços de Gestão de Direitos do Active Directory](https://msdn.microsoft.com/library/Cc530379) original na Biblioteca MSDN começam com a seguinte instrução de suporte:

A funcionalidade de aproveitamento do SDK AD RMS exposta pelo cliente no Msdrm.dll está disponível para utilização no Windows Server 2008, Windows Vista, Windows Server 2008 R2, Windows 7, Windows Server 2012 e Windows 8. Pode ser alterada ou não estar disponível em versões posteriores. Em alternativa, utilize o [SDK dos Serviços de Gestão de Direitos do Active Directory 2.1](microsoft-information-protection-and-control-client-portal.md), que tira partido da funcionalidade exposta pelo cliente no *Msipc.dll*.

 

## Tópicos relacionados ##
* [Descrição Geral](ad-rms-overview.md)
* [SDK dos Serviços de Gestão de Direitos do Active Directory](https://msdn.microsoft.com/library/Cc530379)
* [SDK Rights Management Services 2.1](microsoft-information-protection-and-control-client-portal.md)
 

 


<!--HONumber=Jun16_HO1-->


