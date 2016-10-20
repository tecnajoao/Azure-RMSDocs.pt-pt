---
title: "Perguntas mais frequentes sobre a classificação e a etiquetagem | Azure Information Protection"
description: "Tem alguma pergunta sobre a versão de pré-visualização do Azure Information Protection? Verifique se a resposta está aqui."
author: cabailey
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 4b595b6a-7eb0-4438-b49a-686431f95ddd
ms.reviewer: adhall
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ce4fc256cf80fdd2e4a8212e2f64ffc6ca6a3964
ms.openlocfilehash: 9b341a53a85242839d737bc36c90a8f94637bae1


---

# Perguntas mais frequentes sobre a classificação e a etiquetagem no Azure Information Protection

>*Aplica-se a: Azure Information Protection, Office 365*

Tem uma pergunta sobre o Azure Information Protection especificamente sobre classificação e etiquetagem?  Verifique se a resposta está aqui. 

## O que posso fazer com as capacidades de classificação no Azure Information Protection?

O cliente do Azure Information Protection adiciona uma barra do Information Protection para aplicações do Microsoft Office que lhe permite ver e modificar etiquetas de classificação atribuídas a dados. A classificação pode ser efetuada manualmente, recomendada para si ou aplicada automaticamente. No que respeita às classificações que especificar, os dados podem ser protegidos com um serviço do Rights Management.  

As etiquetas de classificação e o comportamento são configurados no portal do Azure. Pode utilizar a política incorporada predefinida para avaliar rapidamente o Azure Information Protection ou personalizar por completo as suas políticas. Pode alterar as cores, os nomes e a ordem das etiquetas de classificação que os utilizadores veem. Também pode configurar descrições e marcas visuais de classificação como cabeçalho, rodapé ou uma marca d'água.

Experimente o nosso tutorial de início rápido para ver isto em funcionamento em apenas alguns minutos: [tutorial de início rápido do Azure Information Protection](infoprotect-quick-start-tutorial.md).

A versão atual apresenta as seguintes limitações. Procure anúncios no [Blogue Enterprise Mobility and Security](https://blogs.technet.microsoft.com/enterprisemobility/?product=azure-information-protection) e no nosso [site Yammer](https://www.yammer.com/askipteam/#/threads/inGroup?type=in_group&feedId=8652489&view=all) quando estiverem disponíveis funcionalidades e capacidades adicionais:

- Não existe nenhum registo centralizado para classificação e etiquetagem.

- Os nomes das etiquetas e descrições são suportadas apenas num idioma.

- As condições para classificação automática têm de ser expressões ou padrões.

- Os ficheiros não podem ser classificados a partir do Explorador de Ficheiros do Windows.

- As aplicações do Office para dispositivos móveis (iOS e Android), computadores Mac e aplicações Web do Office (Office Online) ainda não são suportadas.

- Não existe integração com o Exchange Online ou o SharePoint Online.

- O SDK para parceiros e programadores não está disponível.

## É necessário ser um administrador global para experimentar o Azure Information Protection?

Para configurar a política do Azure Information Protection, tem de iniciar sessão no portal do Azure como um administrador global do Azure Active Directory.

No entanto, se selecionar a opção para instalar a política de demonstração quando instalar o [cliente do Azure Information Protection](https://www.microsoft.com/en-us/download/details.aspx?id=53018), não precisa de iniciar sessão no portal para ver e experimentar a funcionalidade de etiquetagem. A política de demonstração instala localmente a política predefinida do Azure Information Protection, pelo que pode tentar etiquetar documentos e e-mails, mas não pode alterar ou adicionar novas etiquetas sem iniciar sessão no portal do Azure. 

## O Azure Information Protection suporta cenários no local e híbridos?

O Azure Information Protection é uma solução baseada na nuvem. Se estiver interessado em implementar o Azure Information Protection num cenário híbrido, contacte a equipa do Information Protection, enviando um e-mail para askipteam@microsoft.com.

## Como é que os computadores obtêm informações de política do Azure Information Protection e com que frequência são atualizados?

Sempre que um utilizador abre uma aplicação do Office, o cliente do Azure Information Protection verifica se existe uma versão posterior da política do Azure Information Protection. Além disso, as aplicações do Office são verificadas a cada 24 horas. Se houver uma versão posterior, o cliente transfere-a utilizando uma ligação HTTPS para proteger os dados. 

Se várias instâncias da aplicação Office forem carregadas quando uma nova política do Azure Information Protection é publicada, deve fechar todas as instâncias para obter a versão mais recente da política. Por exemplo, se tiver dois documentos do Word abertos e pretende testar a política do Azure Information Protection num único documento: feche ambos documentos do Word e reabra o documento que pretende utilizar com a política mais recente.

## Onde podem ser armazenados os ficheiros para utilizar o Azure Information Protection? 

Uma vez que o Azure Information Protection aplica etiquetas persistentes e proteção a ficheiros e e-mails, é irrelevante o local onde os ficheiros são armazenados.

## Posso classificar apenas novos dados ou posso também classificar dados existentes?

As ações de política do Azure Information Protection entram em vigor quando os documentos são guardados e os e-mails são enviados, tanto para novo conteúdo como para alterações a conteúdo existente. 

Se guardou ficheiros que pretende classificar, basta abri-los e guardá-los na sua aplicação do Office. 

De momento, não é possível analisar e aplicar classificação em massa e tem de abrir e guardar cada documento na aplicação do Office. 

## Posso utilizar o Azure Information Protection apenas para classificação, sem impor encriptação e restringir direitos de utilização?

Sim. Pode configurar uma política do Azure Information Protection que aplique apenas uma etiqueta. Na verdade, esperamos que seja este o caso da maior parte das redes de implementação em que é necessário proteger apenas um subconjunto de documentos ou e-mails que necessitam da gestão de dados especiais.

## Como funciona a classificação automática?

No portal do Azure, pode utilizar padrões predefinidos, como "Números de cartão de crédito" ou "Número de Segurança Social dos E.U.A.". Em alternativa, pode definir uma cadeia personalizada ou um padrão como condição para classificação automática.

Irá ver um exemplo desta situação no [Tutorial de início rápido do Azure Information Protection](infoprotect-quick-start-tutorial.md). 

A precisão da classificação depende da forma como configurar a regra de classificação, que se baseia em condições. Atualmente, as condições suportam padrões de texto e expressões regulares. Para obter uma explicação sobre cada uma das opções disponíveis durante a pré-visualização, com algumas sugestões de exemplos para testar, consulte [Como configurar condições para classificação automática e recomendada para o Azure Information Protection](../deploy-use/configure-policy-classification.md). A deteção é executada quando o documento é guardado ou um e-mail é enviado.

Para a melhor experiência de utilizador e para assegurar a continuidade do negócio, recomendamos que comece por ações de recomendação do utilizador em vez de ações totalmente automáticas. Isto permite aos utilizadores aceitar a ação de etiquetagem ou proteção ou substituir estas sugestões.   

## O Azure Information Protection pode pedir aos utilizadores para classificar ficheiros em vez de utilizar a classificação automática? 

Sim. Utilize o portal do Azure para configurar se pretende utilizar a classificação automática ou fazer uma recomendação aos utilizadores, definindo a opção **Selecione a forma como esta etiqueta é aplicada: automaticamente ou recomendada para o utilizador** como **Recomendada**.

Irá ver um exemplo desta situação no [Tutorial de início rápido do Azure Information Protection](infoprotect-quick-start-tutorial.md).  

## Posso impor a classificação de todos os documentos?

Sim. Se necessitar que os utilizadores classifiquem todos os ficheiros que guardam, no portal do Azure, defina a opção **Todos os documentos e e-mails têm de ter uma etiqueta** como **Ligado**. 

## Posso remover a classificação de um ficheiro?

Sim. Para remover a classificação de um ficheiro, abra-o na aplicação do Office, clique no ícone **Editar etiqueta** na barra do Information Protection, clique no ícone **Remover etiqueta** e, em seguida, clique em **OK** para confirmar a ação. 


## Posso solicitar aos utilizadores que indiquem a razão pela qual pretendem alterar o nível de classificação?

Sim. Para se certificar de que os utilizadores justificam as suas alterações de classificação, no portal do Azure, defina a opção **Os utilizadores têm de fornecer uma justificação para reduzir a etiqueta de classificação, remover uma etiqueta ou remover a proteção** como **Ativado**. Ao fazerem-no, a ação e a justificação são registadas no registo de eventos do Windows local: **Aplicação** > **Proteção do Microsoft Azure Information Protection**.

## Como posso proteger automaticamente o conteúdo depois de ter sido classificado?

No portal do Azure, pode selecionar um modelo do Rights Management para proteger automaticamente os conteúdos, de acordo com o nível de classificação que especificar.

Irá ver um exemplo desta situação no [Tutorial de início rápido do Azure Information Protection](infoprotect-quick-start-tutorial.md). Para mais informações, consulte [Como configurar uma etiqueta para aplicar proteção Rights Management](../deploy-use/configure-policy-protection.md).

## Um ficheiro pode ser classificado com duas classificações diferentes?

Se necessário, pode criar subetiquetas que melhor descrevam subcategorias para uma etiqueta de sensibilidade específica. Por exemplo, a etiqueta principal **Segredo** pode conter subetiquetas como **Segredo \ Legal** e **Segredo \ Finanças**. Em seguida, pode aplicar marcações visuais de classificação diferentes e modelos do Rights Management diferentes a subetiquetas diferentes.

Embora possa definir marcações visuais, proteção e condições em ambos os níveis, quando utiliza subníveis, configure estas definições apenas no subnível. Se configurar as mesmas definições na etiqueta principal e no respetivo subnível, as definições do subnível têm precedência.

## Quando um e-mail tem uma etiqueta, os anexos também recebem a mesma etiqueta automaticamente?

Não. Quando coloca uma etiqueta numa mensagem de e-mail com anexos, esses anexos não herdam a mesma etiqueta. Os anexos permanecem sem uma etiqueta ou retêm uma etiqueta aplicada separadamente. No entanto, se a etiqueta do e-mail aplicar proteção, essa proteção é aplicada aos anexos.

## Como podem as soluções DLP e outras aplicações ser integradas com o Azure Information Protection?

Uma vez que o Azure Information Protection utiliza metadados persistentes para classificação, que incluem uma etiqueta de texto não encriptado, estas informações podem ser lidas por soluções DLP e outras aplicações. Nos ficheiros, estes metadados são armazenados em propriedades personalizadas; nos e-mails, estas informações estão indicadas nos cabeçalhos de e-mail.

## Como funciona o controlo de documentos e a revogação em relação ao Azure Information Protection?

O controlo de documentos relativo a ficheiros que classifica e protege com o Azure Information Protection funciona com a proteção do Azure Rights Management e a aplicação de partilha RMS. Também pode aceder ao site de controlo de documentos utilizando o cliente do Azure Information Protection (versão 1.0.233 ou posterior): 

- Numa aplicação do Office, no separador **Base**, no grupo **Proteção**, clique em **Proteger** e, em seguida, clique em  > **Controlar utilização**. 

Para obter mais informações, veja [Controlar e revogar os documentos quando utiliza a aplicação de partilha RMS](../rms-client/sharing-app-track-revoke.md).

## Posso controlar que utilizadores podem utilizar o Azure Information Protection para classificar e proteger conteúdo?

Pode restringir os utilizadores que classificam e protegem os dados ao controlar a distribuição do cliente do Azure Information Protection. 

Os ficheiros e e-mails classificados pelo Azure Information Protection podem ser consumidos ou editados por qualquer utilizador, com ou sem o cliente do Azure Information Protection instalado. 

## Como posso comunicar um problema ou enviar feedback do Azure Information Protection?

Se tiver um problema com o Azure Information Protection e estiver a utilizar a versão atual do cliente: na aplicação do Office, no separador **Base**, no grupo **Proteção**, clique em **Proteger** e, em seguida, clique em **Ajuda e feedback**. Na caixa de diálogo **Microsoft Azure Information Protection**, clique em **Enviar comentários**. Esta ação envia um e-mail à equipa do Information Protection e anexa automaticamente os ficheiros de registo do seu PC para ajudar a diagnosticar o problema. 

Se tiver questões ou comentários, utilize o [site Yammer do Azure Information Protection](https://www.yammer.com/askipteam/). 


<!--HONumber=Sep16_HO4-->


