---
title: "Como decodificar JSON em Swift"
datePublished: Thu Jul 13 2023 17:12:33 GMT+0000 (Coordinated Universal Time)
cuid: clk1erfy3000409l5dv1qaj7j
slug: como-decodificar-json-em-swift
canonical: https://dev.to/reisdev/como-decodificar-json-em-swift-2dpe
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1681906256557/ad9507da-9e53-4509-bd9e-ca2e3e8deefa.jpeg
tags: tutorial, swift, ios, beginners

---

## Contexto

Para quem está iniciando, talvez esteja se perguntando: porque preciso saber decodificar um conteúdo em JSON?

O formato JSON é amplamente utilizando em diversas linguagens para armazenar e transferir informações de maneira estruturada. Abaixo, alguns exemplos de cenários comuns:

* Arquivo JSON que armazena de configurações
    
* Consumir uma RESTFUL API que responda no formato JSON.
    
* String contendo informações no formato JSON.
    

Neste artigos iremos ver como ler e decodificar o formato JSON usando a linguagem Swift.

## Leitura do conteúdo JSON

O primeiro passo para ler um JSON em Swift é converter o seu conteúdo no formato `Data`, um tipo da linguagem Swift, que será usado para decodificar a informação em um tipo que iremos definir mais à frente. Abaixo, temos os exemplos de conversão para cada cenário:

### String

Abaixo, temos um exemplo de uma string contendo uma lista de posts no formato JSON:

```swift
let jsonContent = """
[
  {
    "id":1,
    "title":"Como se tornar um programador",
    "content":"Para se tornar um programador, é necessário estudar linguagens de programação e desenvolver habilidades de resolução de problemas.",
    "created_at":"2023-04-18T14:00:00Z"
  },
  {
    "id":2,
    "title":"Os benefícios da meditação",
    "content":"A meditação pode ajudar a reduzir o estresse, melhorar a qualidade do sono e aumentar a sensação de bem-estar.",
    "created_at":"2023-04-18T14:00:00Z"
  },
  {
    "id":3,
    "title":"Receita de bolo de chocolate",
    "content":"Para fazer um delicioso bolo de chocolate, você vai precisar de farinha de trigo, açúcar, ovos, óleo, cacau em pó e fermento em pó.",
    "created_at":"2023-04-18T14:00:00Z"
  }
]
"""
```

Dessa forma, usando as 3 aspas(`"""`), podemos declarar uma string com múltiplas linhas. Agora, podemos fazer a conversão da nossa string para o formato `Data`:

```swift
// Usamos o .utf8 para converter a string
// para um padrão que permita acentuação
let data = Data(jsonContent.utf8)
```

### Arquivo

Supondo que tenhamos um arquivo `.json` que contenha uma lista de artigos:

```json
[
  {
    "id":1,
    "title":"Como se tornar um programador",
    "content":"Para se tornar um programador, é necessário estudar linguagens de programação e desenvolver habilidades de resolução de problemas.",
    "created_at":"2023-04-18T14:00:00Z"
  },
  {
    "id":2,
    "title":"Os benefícios da meditação",
    "content":"A meditação pode ajudar a reduzir o estresse, melhorar a qualidade do sono e aumentar a sensação de bem-estar.",
    "created_at":"2023-04-18T14:00:00Z"
  },
  {
    "id":3,
    "title":"Receita de bolo de chocolate",
    "content":"Para fazer um delicioso bolo de chocolate, você vai precisar de farinha de trigo, açúcar, ovos, óleo, cacau em pó e fermento em pó.",
    "created_at":"2023-04-18T14:00:00Z"
  }
]
```

Considerando que o nome do nosso arquivo é `artigos.json`, ele pode ser lido da seguinte forma:

```swift
// Caminho para um arquivo
let filePath = Bundle.main.path(forResource: “artigos”, ofType: "json")

// Transforma o conteúdo do arquivo em Data
let data = try? Data(contentsOf: filePath)
```

Usamos o `try?` antes do inicializador do Data porque a conversão do nosso arquivo para `Data` pode falhar e causar uma exceção. Para não termos que lidar com exceções, usamos o `try?`, que irá fazer com que o `Data(contentsOf:)` retorne `nil` caso um erro ocorra.

### Requisição em API

Para fazer uma requisição em uma API, usaremos o método mais tradicional, `URLSession.shared.dataTask(for:)`. Considerando uma URL fictícia que poderia nos fornecer a lista de artigos que desejamos obter, temos o seguinte código:

```swift
URLSession.shared.dataTask(with: url) { (data, response, error) in
    // Verificamos se um objeto data recebido não é nulo
    guard let data else { return }

    // A partir daqui, executamos o passo de decodificação
    // ...
}.resume()
```

## Criação do tipo em Swift

Precisamos definir a estrutura dos objetos contida no nosso JSON, para qual os dados serão decodificados. Para isso, vamos criar um `struct` que conforme com o protocolo `Decodable`. Esse protocolo está disponível no framework `Foundation` e é usado para definição de objetos que sejam decodificáveis. A seguir, temos a declaração do nosso tipo `Post`:

```swift
struct Post: Decodable {
    let id: Int
    let title: String
    let content: String
    let createdAt: String

    /* 
    *  Definição dos atributos que possuem
    *  uma chave num formato diferente no JSON
    *  ex.: Nomes em snake_case
    */
    enum CodingKeys: String, CodingKey {
        case id, title, content
        case createdAt = "created_at"
    }
}
```

Cada atributo do objeto contido no nosso JSON é definido como uma propriedade do nosso `struct`. Através do `enum` `CodingKeys` podemos definir uma associação entre chaves a serem "renomeadas" do JSON para atributos do nosso objeto. Acima, por exemplo, convertemos o `created_at`(em *snake-case*) para `createdAt`(em *camel-case*). Esse mesmo comportamento pode ser obtido atribuindo à propriedade `keyDecodingStrategy` do `JSONDecoder` o valor `.convertFromSnakeCase`, que será visto no próximo tópico. O uso dessa propriedade elimina a necessidade de definirmos as associações para cada propriedade que esteja no formato *snake-case*.

Com nosso *struct* definido, poderemos fazer a decodificações de outras estruturas para ele, como um JSON, que é o nosso objetivo.

## Decodificação

Agora que já temos um objeto `Data` e um tipo definido podemos usá-los para decodificar nosso conteúdo JSON. Para isso, o *framework* `Foundation` fornece uma classe `JSONDecoder` criada exatamente com esse objetivo. Abaixo, temos um exemplo do processo de decodificação:

```swift
let decoder = JSONDecoder()
decoder.keyDecodingStrategy = .convertFromSnakeCase
let artigos = try? decoder.decode([Post].self, from: data)

print(artigos)
```

O método `decode` da classe `JSONDecoder` recebe dois parâmetros. O primeiro é o tipo do objeto a ser decodificado e o segundo é o objeto `Data` que contém os dados obtidos anteriormente.

No exemplo deste artigo, o tipo a ser decodificado é uma lista do tipo `Post`. O `self` é usado para obter o tipo esperado, que é `[Post]`(um *array* de `Post`).

Vale ressaltar que o `Data` esperado não pode ser nulo, então certifique-se de que seu objeto `data` não é `nil` antes de passá-lo para o `decode`.

## Conclusão

Conhecer essas 3 formas básicas de decodificar um JSON em Swift já te dá uma base suficiente para aplicar o conceito em diversos contextos. Abaixo, a documentação de alguns dos recursos utilizados nesse artigo:

* [JSONDecoder](https://developer.apple.com/documentation/foundation/jsondecoder)
    
* [Data](https://developer.apple.com/documentation/foundation/data)
    
* [URLSession](https://developer.apple.com/documentation/foundation/urlsession)
    

Gostou deste artigo? Compartilhe e me siga para mais conteúdos como esse!

Capa por [Ferenc Almasi](https://unsplash.com/@flowforfrank?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText) na [Unsplash](https://unsplash.com/pt-br/fotografias/HfFoo4d061A?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText)