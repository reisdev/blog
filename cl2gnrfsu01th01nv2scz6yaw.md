---
title: "Optional em Swift"
datePublished: Tue Apr 26 2022 21:26:20 GMT+0000 (Coordinated Universal Time)
cuid: cl2gnrfsu01th01nv2scz6yaw
slug: optional-em-swift
canonical: https://dev.to/reisdev/optionals-em-swift-4lh0
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1651008246962/aHW3Q8fbC.jpg
tags: swift, ios, beginners

---

Capa por <a href="https://unsplash.com/@lamunix?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Ana Municio</a> no <a href="https://unsplash.com/s/photos/question-mark?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Unsplash</a>

## Introdução

É possível criar variáveis em Swift que não necessariamente tenham um valor definido(ou seja, nulo) e elas são conhecidas como opcionais. Para que uma variável não tenha valor usamos o valor `nil`. Definimos uma variável como opcional colocando uma interrogação após a definição do seu tipo, da seguinte forma:

```swift
var minhaString: String? = nil

print(minhaString)
// Saída: nil
```

A partir dessa atribuição, a variável `minhaString` ainda não tem valor definido. Agora, podemos tentar atribuir um valor à `minhaString` e verificar o resultado:

```swift
var minhaString: String? = "Olá mundo!"

print(minhaString)
// Saída: Optional("Olá mundo!")
```

## Lidando com `Optional`

Lidar com variáveis opcionais requer um pouco mais de atenção, pois é importante verificar se essa variável possui valor antes de utilizá-lo em algum trecho de código. Para isso, temos 4 opções:

- Usando o <i>force unwrapping</i>, com `!`
- Usando <i>binding</i> opcional, com `if let`
- Usando o <i>unwrapping</i> implícito de opcionais, com `!`
- Usando encadeamento opcional, com `a?.b?.c`
- Usando <i>unwrapping</i> incondicional

### Force unwrapping

<i>Force unwrapping</i>, que pode ser traduzido como "forçar a desembrulhar" é a forma explicita de extrair o valor de um `Optional`. Ele pode ser usado, por exemplo, em um parâmetro de uma função que não pode ser `nil`, dessa forma:

```swift

// O parâmetro 'nome' não é opcional
func minhaFuncao(nome: String) {
    print("Olá, \(nome)")
}

// A variável 'meuNome'é opcional e tem valor 'nil'
var meuNome: String? = nil

minhaFuncao(nome: meuNome!)
```

O trecho abaixo dispararia a seguinte exceção:

```swift
Unexpectedly found nil while unwrapping an Optional value
```

Por quê? Pelo fato de que o valor da variável `meuNome` foi atribuído como `nil`. Portanto, é importante ter em mente que, para usar o <i>force unwrapping</i>, é necessário atender pelo menos um dos seguintes critérios:

- Ter certeza de que o valor está definido
- Tratar a exceção que será lançada caso o valor seja `nil`

Se o valor da variável `meuNome` não fosse `nil`, o resultado seria diferente:

```swift
func minhaFuncao(nome: String) {
    print("Olá, \(nome)")
}

var meuNome: String? = "ReisDev"

minhaFuncao(nome: meuNome!)
// Saída: "Olá, ReisDev"
```

O uso do <i>force unwrapping</i> não é recomendado por conta dos erros que ele pode ocasionar caso alguma variável tenha o valor `nil`. Por isso, use com cautela.

### Binding opcional

#### `if let`

<i>Optional binding</i>, que pode ser traduzido como "amarração opcional", consiste em garantir que um trecho de código será executado apenas se um determinado valor não for `nil`. Inclusive, é possível verificar sub-condições, como atributos de objetos. Abaixo, um exemplo de uso:

```swift
var meuTexto: String? = nil

if let texto = meuTexto {
    /* 
     * Nesse contexto, a variável texto é
     * do tipo String, e não 'String?'
     */
}
```

No bloco de código acima, o trecho contido entre as chaves é chamado de `closure`, e você pode ver mais detalhes [neste link](https://docs.swift.org/swift-book/LanguageGuide/Closures.html)(em inglês). Dentro dessa closure a variável `texto`(que recebeu o valor da variável `meuTexto`) é do tipo `String` por conta da amarração opcional. Se o valor da variável `meuTexto` não for `nil`, ele será "amarrado" à variável `texto`, e o trecho de código dentro da <i>closure</i> será executado.

#### `guard let`

Além do `if let`, podemos usar também o `guard let`, que valida se uma variável tem valor e, caso não tenha, executa um trecho de código que deve encerrar a execução, seja do programa ou de uma função. Abaixo, um exemplo:

```swift
func validaTexto(meuTexto: String?) -> Bool {
    guard let texto = meuTexto else {
         return false
    }
    // Valida o texto ...
}

```
### Unwrapping implícito

O <i>unwrapping</i> implícito, que pode ser traduzido como "desembrulhamento" implícito, é usado para evitar ter que usar as outras abordagens citadas nesse artigo para obter o valor de uma variável `Optional`. Ele funciona da seguinte forma:

```swift
var pessoa: Pessoa! = nil
```

Como a variável `pessoa` é do tipo `Pessoa?` (sem o <i>unwrapping</i> implícito), se tentarmos acessar o atributo `endereco`, por exemplo, obteríamos o seguinte erro:

> value of optional type 'Pessoa?' must be unwrapped to refer to member 'endereco' of wrapped base type 'Pessoa'

Por quê? O compilador da linguagem sabe que é arriscado acessar uma variável `Optional` sem a garantia de que ela de fato tem um valor, pois isso pode causar um erro. Por isso, ele tenta garantir que quem está escrevendo o código faça essa verificação.

O <i>unwrapping</i> implícito é usado exatamente para não precisar fazer essa verificação todas as vezes. Parece prático, mas também pode ser arriscado. Se você utilizar esse recurso, tenha o cuidado de tratar exceções, pois pode acontecer de sua variável ter o valor  `nil`, e isso irá ocasionar em um erro. O uso desse recurso não é encorajado, por conta dos problemas que ele pode gerar. Por isso,<b> Use com moderação</b>.

### Encadeamento opcional

<i>Optional chaining</i>, que pode ser traduzido como "encadeamento opcional", é usado, por exemplo, quando se tem atributos de objetos que podem ser nulos, e esses objetos também tem atributos que podem ser nulos. Abaixo, um exemplo:

```swift
var minhaRua = pessoa?.endereco?.rua
```

O objeto pessoa é do tipo `Pessoa?`, e o objeto pessoa possui um atributo `endereco` do tipo `Endereco?`. A variável `minhaRua` também será do tipo `Optional`, e ela receberá um valor somente se o objeto `pessoa` e seu aributo `endereco` não forem `nil`. Caso algum deles tenha valor nulo, a variável `minhaRua` também terá valor `nil`.

### Unwrapping incondicional

<i>Unconditional unwrapping</i>, que pode ser traduzido como "desembrulhamento incondicional", é usado quando você tem certeza de que um `Optional` contém um valor. Abaixo, um exemplo:

```swift
var numero = Int("42")!
print(number)
// Saída: 42
```

No trecho acima, o inicializador de `Int` pode falhar, pois a string fornecida pode não conter um número. Porém, nós temos certeza de que `"42"` irá resultar em um número. Logo, podemos usar o <i>unconditional unwrapping</i>.

## Conclusão

Agora você já sabe como funcionam as variáveis do tipo `Optional` e as diferentes maneiras como você pode lidar com elas. Lembre-se sempre de avaliar a forma mais adequada de tratar variáveis opcionais em cada situação. Caso queira saber mais detalhes, recomendo que leia a [documentação da Apple](https://developer.apple.com/documentation/swift/optional).

Gostou deste artigo? Compartilhe e me siga para mais conteúdos como esse!

Minhas redes:

[Twitter](https://twitter.com/reisdev) | [Instagram](https://instagram.com/reisdev) | [Blog](https://blog.reisdev.com.br) | [Youtube](https://youtube.com/reisdev) | [GitHub](https://github.com/reisdev) | [LinkedIn](https://linkedin.com/in/matheus-dos-reis-de-jesus) 

Até a próxima!👋🏽