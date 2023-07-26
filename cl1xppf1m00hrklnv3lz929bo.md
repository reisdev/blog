---
title: "Variáveis e Constantes em Swift"
datePublished: Wed Apr 13 2022 15:13:08 GMT+0000 (Coordinated Universal Time)
cuid: cl1xppf1m00hrklnv3lz929bo
slug: variaveis-e-constantes-em-swift
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1649862588135/gbs6RXskj.jpg
tags: swift, ios, beginners

---

Capa por <a href="https://unsplash.com/@blakeconnally?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Blake Connally</a> no <a href="https://unsplash.com/s/photos/programming?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Unsplash</a>

## Introdução

Uma das primeiras coisas para se conhecer ao aprender uma nova linguagem é o funcionamento das constantes e variáveis. Esse artigo traz uma breve explicação deste conceito dentro da linguagem Swift.

## Declarando constantes e variáveis

### Constantes

Para se declarar uma constante usamos a palavra-chave `let`. Como o próprio nome sugere, constantes não podem ter seu valor alterado. Quando declaradas, seu valor é atribuído e não poderá ser modificado. Abaixo, um exemplo:

```swift
let helloWorld = "Hello world!"

// Tentando atribuir um novo valor:
helloWorld = "Novo valor"

/*
* Irá resultar em um erro:
* "Cannot assign to value: ‘helloWorld’ is a ‘let’ constant"
*/
```

Como descrito no bloco de código acima, tentar atribuir outro valor à uma constante irá causar um erro. Então, lembre-se: a palavra chave `let` só deve ser usada quando o valor for constante. Inclusive, a própria documentação da linguagem recomenda que se use `let` sempre que possível.

### Variáveis

Para se declarar uma variável usamos a palavra-chave `var`. Sempre que for preciso armazenar um valor que pode mudar durante a execução de um código, deve-se usar `var`. É possível, inclusive, declarar mais de uma variável em uma mesma linha. Abaixo, temos alguns exemplos:

```swift
// Declarações únicas
var x = 0
var valido = true
var meuTexto = "Este é um texto"

// Declarações múltiplas
var x = 0, y = 10, z = 100
var string1 = "Primeira string", string2 = "Segunda string"
```

## Definindo o tipo

A linguagem Swift permite que sejam definidos tipos para variáveis e constantes(apesar de não ser obrigatório), e escrevemos da seguinte forma:

```swift
let meuTexto: String = "Este é um texto"
let contador: Int = 0
let medida: Float = 2.5
let valor: Double = 10.0
let hoje: Date = Date()
```

A linguagem Swift possui os tipos básicos, como tupla, array e dicionário. Os demais tipos são providos pelo framework `Foundation`, criado pela própria Apple. Você pode ver os tipos com mais detalhes [neste link](https://developer.apple.com/documentation/foundation).

Além dos exemplos acima, uma variável/constante também pode ser do tipo `Optional`, que é usado quando o valor pode ser indefinido, dessa forma:

```swift
// Valor "nil" explícito
var meuTexto: String? = nil

// Valor "nil" implícito
var meuTexto: String?
```

A palavra-chave `nil` é similar ao `null` em outras linguagens, usada para indicar um valor nulo. O tipo `Optional` possui muitos detalhes que serão explicados em outro artigo. Neste, iremos nos limitar apenas a saber que é possível utilizá-lo.

## Atribuindo valores

Para atribuir valores, sua variável/constante pode ter um tipo definido ou não. Se ela tiver, o valor atribuído deve ser do mesmo tipo da variável.

```swift
// Com tipo definido:
var meuTexto: String = "Esse é um texto"

// Sem tipo definido
var meuTexto = "Esse é um texto"
```

Se você não definir um tipo, o compilador irá considerar o tipo do valor atribuído. No caso acima, o tipo seria String.

Quando a variável/constante possui um tipo definido, o valor que for atribuído deverá ser desse mesmo tipo.

```swift
var meuTexto: String = 1
```

Como o valor atribuído acima é do tipo inteiro, mas o tipo da variável `meuTexto` é String, esse trecho irá disparar uma exceção:

> error: cannot convert value of type 'Int' to specified type 'String'

A própria linguagem já previne que você cometa erros ao atribuir valores de tipos diferentes do que foi definido para uma determinada variável/constante.

## Conclusão

Agora você já conhece o básico sobre o uso de variáveis e constantes em Swift. Recomendo que veja a [documentação da linguagem](https://docs.swift.org/swift-book/ReferenceManual/Types.html) e também do [framework Foundation](https://developer.apple.com/documentation/foundation) sobre os diferentes tipos disponíveis.

Gostou deste artigo? Compartilhe e me siga para mais conteúdos como esse!

Minhas redes:

[Twitter](https://twitter.com/reisdev) | [Instagram](https://instagram.com/reisdev) | [Blog](https://blog.reisdev.com.br) | [Youtube](https://youtube.com/reisdev) | [GitHub](https://github.com/reisdev) | [LinkedIn](https://linkedin.com/in/matheus-dos-reis-de-jesus) 

Até a próxima!👋🏽