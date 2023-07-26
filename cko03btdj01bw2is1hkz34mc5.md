---
title: "Tratamento de Exceção com erros customizados em Swift"
datePublished: Tue Apr 27 2021 13:54:08 GMT+0000 (Coordinated Universal Time)
cuid: cko03btdj01bw2is1hkz34mc5
slug: tratamento-de-excecao-com-erros-customizados-em-swift
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1619531580214/lI-17-ywC.jpeg
tags: swift, ios, error-handling

---

Capa por <a href="https://unsplash.com/@sigmund?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Sigmund</a> no <a href="https://unsplash.com/s/photos/error?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Unsplash</a>

# Criação 

Primeiro, precisamos pensar em um contexto para criar nossos erros. Vamos supor que existe um serviço que consome uma API que fornece dados sobre filmes, e iremos tratar os possíveis erros. Os erros mais comuns são: 

- Recurso não encontrado(404)
- Proibido(403)
- Erro interno(500)
- Serviço Indisponível(503)

Os números associados aos erros são conhecidos como "Código de Status HTTP"(<i>HTTP Status Code</i>).

No trecho de código abaixo, iremos criar nossos erros customizados:

```swift
enum APIError: Error {
    case NotFound           // Recurso não encontrado
    case Forbidden          // Proibido
    case InternalError      // Erro interno
    case ServiceUnavailable // Indisponível
}
```

Usamos uma estrutura do tipo `enum` para definir o conjunto de erros que temos. Para dar continuidade, iremos supor que nosso serviço dispara exceções com os tipos definidos acima quando os respectivos códigos de status HTTP são recebidos.

# Tratamento de Exceção

Agora que já temos um conjunto definido de erros, vamos ver como tratar nossas exceções. A linguagem Swift usa, para tratamento de exceções, uma estrutura conhecida como `do-try-catch`, que é escrita da seguinte forma:

```swift
do {
    try execute()
} catch(let exception){
    // Tratamento da exceção
}
```

Adequando o código acima para nosso cenário do serviço de filmes, e supondo que o serviço já está implementado, teríamos o seguinte:

```swift
do {
    // Tenta obter os dados do filme de id 5201
    try MovieService.getById(5201)
} catch(let exception){
    // Trata os erros
}
```

Podemos ir um pouco além do que já vimos. A estrutura <i>do-try-catch</i> permite que tratemos diferentes tipos de exceções, como se fosse um <i>switch-case</i>, da seguinte forma:

```swift
do {
    // Tenta obter os dados do filme de id 5201
    try MovieService.getById(5201)
} catch APIError.NotFound {
    // Trata o erro de "Recurso não encontrado
} catch APIError.Forbidden {
    // Trata o erro de "Proibido"
} catch APIError.InternalError {
    // Trata o erro de "Erro interno
} catch APIError.ServiceUnavailable {
    // Trata o erro de "Serviço Indisponível"
}
```

Com a estrutura acima, conseguimos tratar alguns dos erros mais comuns que podem ocorrer ao fazer uma requisição a um servidor. Vale destacar que não necessariamente essa é a melhor abordagem, mas ela é um bom exemplo de como tratar erros customizados usando a linguagem Swift.

# Considerações

Caso você tenha interesse em descobrir mais sobre tratamento de exceções em Swift, você pode ler a [documentação](https://docs.swift.org/swift-book/LanguageGuide/ErrorHandling.html). Espero que essa explicação tenha te ajudado!

Gostou deste artigo? Me siga para mais conteúdos como esse!

Minhas redes sociais:

[Twitter](https://twitter.com/reisdev) | [Instagram](https://instagram.com/reisdev) | [Youtube](https://youtube.com/reisdev). 

Até a próxima!👋🏽

