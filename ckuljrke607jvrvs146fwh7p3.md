---
title: "Como escrever códigos mais padronizados?"
datePublished: Sun Oct 10 2021 18:15:25 GMT+0000 (Coordinated Universal Time)
cuid: ckuljrke607jvrvs146fwh7p3
slug: como-escrever-codigos-mais-padronizados
canonical: https://dev.to/reisdev/como-escrever-codigos-mais-padronizados-5hm0
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1633889478884/xSaQrs6Ct.jpeg
tags: styleguide, learning, beginners, programming-languages

---

Capa por <a href="https://unsplash.com/@timgraf99?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Tim Graf</a> no <a href="https://unsplash.com/s/photos/guide?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Unsplash</a>

## Sumário

- [Introdução](#introducao)
- [O que é Style Guide?](#o-que-e-style-guide)
- [Quem define um guia de estilo?](#quem-define-um-guia-de-estilo)
- [No que isso vai me ajudar?](#no-que-isso-vai-me-ajudar)
- [Exemplos](#exemplos)
  
## Introdução

Quem me acompanha nas redes sociais sabe que, recentemente(junho de 2019), eu mudei o rumo da minha carreira. Estava trabalhando com Data Science e decidi focar no desenvolvimento mobile iOS. A partir disso, tive que me dedicar a aprender Swift, linguagem lançada pela Apple em 2014.

Para aprender novas linguagens, é necessário conhecer padrões: sintaxe, comandos, paradigmas e por aí vai. Um detalhe muito importante é: Qual o padrão para se escrever códigos na linguagem que estou aprendendo? Para isso existem os style guides.

## O que é Style Guide?

Em português, Guia de Estilo, é um conjunto de regras que definem como devem ser escritas as mais variadas instruções em uma determinada linguagem. Essas regras envolvem preferências sobre, por exemplo, iniciar ou não uma nova linha antes de das chaves de um comando `if`. Um exemplo de regra a seguir: 

```js
// Preferido
if(condition) {
   //code
}
// Não preferido (lógico, um crime)
if(condition)
{
   //code
}
```
Os style guides são criados para (tentar) garantir que o código terá um mesmo formato, independentemente de quem escreveu, tornando mais fácil sua leitura por qualquer pessoa.

## Quem define um guia de estilo?

Os guias de estilo podem ser definidos por um projeto, empresa, comunidade, etc. Por exemplo, dentro de uma empresa, é possível que diferentes projetos sigam diferentes guias, cada um adequado às suas necessidades.

## No que isso vai me ajudar?

Conhecer um guia de estilo pode tirar muitas dúvidas sobre como um "bom código" deve ser escrito. Você irá conhecer e entender como formatar determinados comandos, como escrever expressões, onde colocar ou não espaços, etc.

## Exemplos

Abaixo estão listados alguns exemplos de guias de estilo para você conhecer:

- [PEP-8: Style Guide oficial de Python](https://www.python.org/dev/peps/pep-0008/)
- [PSR-12: Coding Style Guide de PHP](https://www.php-fig.org/psr/psr-12/)
- [Java Style Guide da Google](https://google.github.io/styleguide/javaguide.html)
- [C# Style Guide da Google](https://google.github.io/styleguide/csharp-style.html)
- [Javascript Style Guide da AirBnb](https://github.com/airbnb/javascript)
- [Dart Style Guide](https://dart.dev/guides/language/effective-dart/style)
- [Swift Style Guide da comunidade Ray wenderlich](https://github.com/raywenderlich/swift-style-guide)