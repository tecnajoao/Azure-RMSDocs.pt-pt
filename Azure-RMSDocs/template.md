---
# required metadata

title: [TÍTULO DO ARTIGO | NOME DO SERVIÇO]
description:
keywords:
author: [GITHUB USERNAME]
manager: [ALIAS]
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service:
ms.technology:
ms.assetid: [GET ONE FROM guidgenerator.com]

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
#ms.reviewer: [ALIAS]
#ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Modelo de Metadados e de Markdown

Este modelo docs.ms contém exemplos de sintaxe de markdown, bem como orientações sobre a definição de metadados. Está disponível no diretório de raiz de cada repositório EM Piloto (por exemplo, ~/Azure-RMSDocs-pr
/template.md) e destina-se a ser lido como um ficheiro de markdown, embora possa consultar a [versão publicada](https://stage.docs.microsoft.com/en-us/rights-management/template) para ver como os exemplos de markdown são compostos.

Quando criar um ficheiro markdown, deve copiar o modelo para um novo ficheiro, preencher os metadados conforme especificado abaixo, definir o cabeçalho H1 acima do título do artigo e eliminar o conteúdo. 


## Metadados 

O bloco de metadados completo está acima, dividido em campos obrigatórios e opcionais; consulte a [Cábula de metadados OPS](https://ppe.msdn.microsoft.com/en-us/ce-csi-docs/ops/ops-onboarding/managing-content/content-meta-data) para obter mais detalhes. Algumas notas essenciais:

- **Tem** de existir um espaço entre os dois pontos (:) e o valor do elemento de metadados.
- Se o elemento de metadados opcional não tiver um valor, comente o elemento com um # (não o deixe em branco nem utilize o “ND”); se adicionar um valor a um elemento que foi comentado, certifique-se de que remove o #.
- Os dois pontos num valor (por exemplo, um título) quebram o parser de metadados. Em vez disso, utilize a codificação HTML de &#58; (por exemplo, “título: Azure Rights Management&#58; noções básicas | Azure RMS”).
- **título**: este título será apresentado nos resultados do motor de busca. O título deve terminar com uma barra vertical (|), seguido do nome do serviço (consulte exemplo acima). O título não precisa (e provavelmente não deve) de ser idêntico ao título do cabeçalho H1. Deve ter cerca de 65 carateres (incluindo | NOME DO SERVIÇO)
- **autor**, **gestor**, **revisor**: o campo autor deve conter o **nome de utilizador do Github** do autor, não o alias.  Os campos “gestor” e “revisor”, por outro lado, devem conter aliases. ms.reviewer especifica o nome do PM associado ao serviço ou ao artigo.
- **ms.assetid**: este é o GUID do artigo a partir de CAPS. Ao criar um novo ficheiro de markdown, obtenha um GUID em [https://www.guidgenerator.com](https://www.guidgenerator.com). 
- **ms.prod**, **ms.service**, **ms.technology**, **ms.devlang**, **ms.topic**, **ms.tgt_pltfrm**: os possíveis valores para estes elementos podem ser encontrados [aqui](https://microsoft.sharepoint.com/teams/STBCSI/Insights/_layouts/15/WopiFrame.aspx?sourcedoc=%7b7A321BF1-0611-4184-84DA-A0E964C435FA%7d&file=WEDCS_MasterList_CSIValues.xlsx&action=default).

## Markdown Básico e GFM

Todos os markdown básicos e caraterísticos do Github são suportados. Para obter mais informações acerca deste assunto, consulte:

- [Sintaxe de markdown de linha de base](https://daringfireball.net/projects/markdown/syntax)
- [Documentação markdown com caraterísticas do Github (GFM)](https://guides.github.com/features/mastering-markdown)

## Cabeçalhos

Consulte acima exemplos de títulos de primeiro e segundo nível. 

**Deve** existir apenas um cabeçalho de primeiro nível no tópico, que será apresentado como o título na página.  

Os cabeçalhos de segundo nível irão gerar o índice na página que aparece na secção “Neste artigo” sob o título na página.

### Cabeçalho de terceiro nível
#### Cabeçalho de quarto nível
##### Cabeçalho de quinto nível
###### Cabeçalho de sexto nível

## Estilos de texto

*Itálico* 

**Negrito** 

~~Rasurado~~



## Links

Para ligar a um ficheiro de markdown no mesmo repositório, utilize [ligações relativas](https://www.w3.org/TR/WD-html40-970917/htmlweb.html#h-5.1.2). 

- Exemplo: [O que é o Azure Rights Management](./understand-explore/what-is-azure-rms.md)

Para ligar a um cabeçalho no mesmo ficheiro de markdown, veja a origem do artigo publicado, localize o id do cabeçalho (por exemplo, `id="blockquote"` e ligue através de # + id (por exemplo, `#blockquote`).

- Exemplo: [Trechos em bloco](#blockquote)

Para ligar a um cabeçalho num ficheiro de markdown no mesmo repositório, utilize ligações relativas + ligações de hashtag.

- Exemplo: [descrição geral técnica do processo de inscrição](./understand-explore/rms-for-individuals-user-sign-up.md#technical-overview-of-the-sign-up-process)

Para ligar a um ficheiro externo, utilize o URL completo como a ligação.

- Exemplo: [Github](http://www.github.com)

Se aparecer um URL num ficheiro de markdown, será transformado numa ligação clicável.

- Exemplo: http://www.github.com

## Listas

### Listas ordenadas

1. Esta 
1. É
1. Uma
1. Lista
1. Ordenada  


#### Lista ordenada com uma lista incorporada

1. Aqui
1. está
1. uma
1. lista
    1. Menina Isabel
    1. Professor Brandão
1. ordenada
1. incorporada


### Listas não ordenadas

- Esta
- é
- uma
- lista
- com marcas


##### Lista não ordenada com listas incorporadas

- Esta 
- lista 
- com marcas
    - Sra. de Corte-Real
    - Dr. Pacheco
- contém  
- listas
    1. Coronel Monteiro
    1. Senhora Ana
- diferentes


## Régua horizontal

---

## Tabelas

| Tabelas        | São           | Interessantes  |
| ------------- |:-------------:| -----:|
| a col. 3 está      | alinhada à direita | $1600 |
| a col. 2 está      | centrada      |   $12 |
| a col. 1 é a predefinição | alinhada à esquerda     |    $1 |


## Código

### Bloco de código

    function fancyAlert(arg) {
      if(arg) {
        $.docs({div:'#foo'})
      }
    }

### Código em linha

Este é um exemplo de `in-line code`.

## Trechos em bloco

> A seca já durava há dez milhões de anos, e o reinado dos terríveis lagartos há muito havia terminado. Ali no equador, no continente que um dia seria conhecido como África, a luta pela existência chegara a um novo clímax de ferocidade, e ainda não se sabia quem seria o vencedor. Naquela terra deserta e árida, apenas os pequenos, os velozes e os ferozes conseguiam prosperar, ou sequer esperar sobreviver.

## Imagens

### Imagem Estática

![este é o texto alternativo](./media/AzRMS_elements.png)

### Imagem Ligada

[![atexto alternativo para a imagem ligada](./media/AzRMS_elements.png)](https://azure.microsoft.com) 

### Gif animado

![gif animado](./media/hololens.gif)

## Alertas

### Nota

> [!NOTE]
> Isto indica uma NOTA

### Aviso

> [!WARNING]
> Isto indica um AVISO

### Sugestão

> [!TIP]
> Isto indica uma SUGESTÃO

### Importante

> [!IMPORTANT]
> Isto é IMPORTANTE

## Vídeos

### Canal 9

<iframe src="http://channel9.msdn.com/Series/Azure-Active-Directory-Videos-Demos/Azure-Active-Directory-Connect-Express-Settings/player" width="960" height="540" allowFullScreen frameBorder="0"></iframe>


### YouTube

<iframe width="420" height="315" src="https://www.youtube.com/embed/R6_eWWfNB54" frameborder="0" allowfullscreen></iframe>

## Extensões do docs.ms

### Botão

> [!div class="botão"]
[ligações de botão](/rights-management)

### Seletor

> [!div class="op_single_selector"]
- [foo](/rights-management/template.md)
- [bar](/rights-management/scratch.md)

### Passo-a-Passo

>[!div class="passo a passo"]
[Anterior](https://www.example.com)
[Seguinte](https://www.example.com)

<!--HONumber=Apr16_HO3-->


