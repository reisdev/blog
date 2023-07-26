---
title: "Design: Arte ou Processo?"
datePublished: Thu Mar 25 2021 03:00:00 GMT+0000 (Coordinated Universal Time)
cuid: cknawmuul03m2h2s1fxnhb82f
slug: design-arte-ou-processo
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1618008631602/DvMIztlj_.png
tags: creativity, design, developer

---

<span>Capa por <a href="https://unsplash.com/@uxindo?utm_source=unsplash&amp;utm_medium=referral&amp;utm_content=creditCopyText">UX Indonesia</a> no <a href="https://unsplash.com/s/photos/design-process?utm_source=unsplash&amp;utm_medium=referral&amp;utm_content=creditCopyText">Unsplash</a></span>

Recentemente cursei uma disciplina chamada "Visualização de Dados", e, semanalmente, a professora selecionava um conjunto de artigos sobre design, processo criativo e visualização de dados para discutirmos. Gostei tanto de um dos conjuntos de artigos que resolvi escrever sobre eles.

Todos os artigos estão em inglês e foram publicados na <i>[Nature Methods](https://www.nature.com/nmeth/)</i>. Cada tópico deste artigo está acompanhado do seu respectivo link.

## Sumário

- [Saliência para Relevância](#saliência-para-relevância)
- [Elementos do Estilo Visual](#elementos-do-estilo-visual)
- [Narrativa](#narrativa)

### Saliência para Relevância

[Link para o artigo](https://www.nature.com/articles/nmeth.1762)

Este primeiro artigo fala especialmente sobre destacar visualmente uma informação sobre as demais. O autor usa um exemplo bem interessante na figura 2a:

![Alt Text](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/di7asonv8csnqvrjoz67.png)
Fonte: https://www.nature.com/articles/nmeth.1762/figures/2

Segundo o autor: Combinar saliência com relevância chama a atenção visual para as informações importantes.

No <i>heat map</i> acima, a intenção era destacar os pontos vermelhos em detrimento dos pontos azuis. Porém, o efeito foi inverso. Os pontos azuis escuro sobressaem aos pontos avermelhados. Logo, o objetivo dessa visualização não foi atingido.

A ideia destacada neste artigo é exatamente a de tentar mostrar relevância através de saliência. Destacar uma informação é muito útil, mas precisa ser eficiente. O uso de cores e figuras deve ser feito com cuidado.

Na figura 2b o autor destaca o problema do uso de figuras em movimento. O formato usado sugere que os conteúdos em textos são relevantes para o <i>slide</i> em questão. Porém, as figuras em movimento do lado esquerdo podem distrair o leitor e prejudicar a compreensão da informação.

### Elementos do Estilo Visual

[Link para o artigo](https://www.nature.com/articles/nmeth.2444)

Esse artigo fala mais especificamente sobre a construção de elementos visuais e como a escolha dos seus componentes influencia na compreensão do leitor.

O primeiro exemplo que o artigo usa é a figura a seguir:

![Imagem com um grafo multicolorido, com 3 a 4 nós conectando pares de nós. As arestas também tem várias cores](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/5aj3ycr4y415vi5cqtym.png)
Fonte: https://www.nature.com/articles/nmeth.2444/figures/1

Segundo o autor: Uma enxurrada de símbolos idênticos desencadeia uma "saciedade semântica", um fenômeno em que a repetição exagerada resulta em uma perda de significado.

O problema nessa imagem é que os elementos tem cores diferentes, tanto os nós quanto as arestas. Logo, o uso de cores não tem significado na imagem. A ausência de legenda também impossibilita a compreensão do que as cores representam. Usar um conjunto limitado de cores e apresentar o significado de cada torna a leitura de elemento visual muito mais fácil.

![Uma imagem com um conjunto de figuras: um gráfico de barras, um gráfico de pizza com várias cores, um cromossomo, uma sequência de figuras geométricas, um cilindro com uma espécie de corda ao redor, uma seta verde com círculo vermelho em cima, com a escrita K3 e por fim, um balão com a escrita "Cancer"](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/ofvfjkteerh6ey4cyj4l.png)
Fonte: https://www.nature.com/articles/nmeth.2444/figures/2

Segundo o autor: Use a representação mais simples para objetos e omita informações desnecessárias.

O uso de elementos com diferentes formas na figura A, além de dificultar a interpretação, não acrescentam nada em seu significado. A figura B torna a compreensão muito mais fácil, e as informações mais importantes estão de fato em destaque.

![Conjunto de figuras com formatos diferentes. Na primeira linha, dois conjuntos demonstrando interseção, o primeiro com múltiplas clores e o segundo com apenas uma escala de cores. Na segunda linha, 8 figuras: um desenho indefinido com a escrita "FOXA1", um retângulo arredondado escrito "FOXJ1", um hexágono escrito "FOSL1" e um círculo com a escrita "FOXR2". E à direita, 4 retângulos regulares com as mesmas escritas. Na terceira linha, temos as escritas "Cancer STEM","Cancer" e "Neoplastic". À esquerda, com 2 figuras irregulares abaixo de cada escrita. À direita,2 figuras regulares abaixo de cada escrita](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/jbsl74w5oppdi9jjwrpi.png)
Fonte: https://www.nature.com/articles/nmeth.2444/figures/3

Segundo o autor: Objetos que interagem ou que tem significado em comum devem ser formatados de maneira similar, para induzir a intuição.

Mais uma vez, a escolha de formas e cores afetando a compreensão da informação contida em um elemento visual. As imagens a esquerda não induzem uma correlação entre os elementos que deveriam ser similares, já que eles possuem cores diferentes e formatos irregulares. Os itens à direita, diferentemente, sugerem uma relação entre os itens e inclusive possibilitam o destaque de alguns deles.

### Narrativa
[Link para o artigo](https://www.nature.com/articles/nmeth.2571)

Esse artigo fala a respeito do uso de elementos visuais para contar histórias, também conhecido como "Storytelling". As visualizações desse tipo relacionam eventos durante um intervalo de tempo ou de valores definido.

![Alt Text](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/wo39y0w3g67dt8c2psmg.png)
Fonte: https://www.nature.com/articles/nmeth.2571/figures/1

Segundo o autor: Use agregação para reduzir o detalhe dos dados e enfatizar a mensagem: Existem relativamente de médio intervalo.

Começando em um conjunto dos valores e finalizando em um gráfico de barras, a imagem anterior apresenta o processo de transformação dos dados em uma visualização que transmita uma ideia de maneira mais sucinta, sem precisar de muitas informações visíveis.

![Alt Text](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/2o0ipsxquexgstk2gcfp.png)
Fonte: https://www.nature.com/articles/nmeth.2571/figures/2

Segundo os autores: Uma história adiciona significado e clareza para estatísticas complexas.

Em alguns casos, apenas elementos visuais não são suficientes para apresentar uma informação de maneira clara. Quando se tem estatísticas mais complexas, apresentar uma contextualização do problema/situação pode facilitar a compreensão por parte do leitor.

## Conclusão

Depois de tantos exemplos de como o design funciona e os critérios que ele deve obedecer para cumprir seu propósito, o que você acha? Design é apenas uma "arte", fruto da imaginação e criatividade, ou ele é resultado de um processo minucioso que exige conhecimento e dedicação? Ou talvez ambos?

Gostou deste artigo? Deixe suas reações e me siga em outras redes: [Twitter](https://twitter.com/reisdev) | [Instagram](https://instagram.com/reisdev) | [Youtube](https://youtube.com/reisdev). 

Até o próximo artigo!👋🏽


