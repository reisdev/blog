---
title: "Operador de Nullish Coalescing (??) em Javascript"
datePublished: Mon Apr 12 2021 12:33:21 GMT+0000 (Coordinated Universal Time)
cuid: ckneku5jb00nk67s18v9r0w2m
slug: operador-de-nullish-coalescing-em-javascript
canonical: https://dev.to/reisdev/js-operador-nullish-coalescing-2g35
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1618230819020/vJeR1cjQy.jpeg
tags: javascript, learning, beginners

---


Capa por <a href="https://unsplash.com/@evan__bray?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Evan Dennis</a> no <a href="https://unsplash.com/s/photos/question-mark?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Unsplash</a>

# Sumário

- [Introdução](#introdução)
- [O operador ??](#o-operador-raw-endraw-)
- [Caso de uso](#caso-de-uso)
- [Considerações](#considerações)

# Introdução

Talvez em algum momento você tenha se deparado com um trecho de código em Javascript da seguinte maneira:

```js
const valor = valorReal || "valorPadrão";
```

O operador `||` usado acima é chamado de OU lógico, e funciona da seguinte maneira: Se o valor à esquerda do operador for verdadeiro, seu valor será atribuído à variável `valor`. Se o seu valor for falso, a variável `valor` receberá o valor à direta, "valorPadrão".

Se você já está habituado com Javascript, deve saber que existem vários problemas com relação a falsidade ou veracidade de valores na linguagem. Exemplo: "" e 0 são considerados valores falsos. Logo, se em um algoritmo "" ou 0 forem valores válidos, o operador `||` não iria fornecer o resultado necessário. É aí que entra o operador de Coalescência Nula(ou <i>Nullish Coalescing</i>).

# O operador `??`

Agora que você já entendeu o problema, vêm a solução. O operador de Coalescência Nula é representado por `??` e utilizado da seguinte forma:

```js
const valor = valorReal ?? "valorPadrão";
```

Nesse caso, se o valor da variável `valorReal` for `null` ou `undefined`, a variável `valor` receberá `"valorPadrão"`. Caso contrário, ela receberá o valor de `valorReal`.

# Caso de Uso

Pense no seguinte cenário: Você está fazendo um cálculo que utiliza um coeficiente. Se o coeficiente não for fornecido, ele irá receber um valor padrão, sendo `0` um valor válido. Como comentei, o operador `||` iria impedir que o `0` fosse utilizado. Nesse caso, o operador `??` se torna muito útil. Confira a representação desse problema abaixo:

```js
function calcularResultado(x,y,coeficiente) { ;
    const c = coeficiente ?? 0.5;
    return x + y * c;
}

const resultado = calculaResultado(2,3);
console.log(resultado) // Saída: 3.5 ( 2 + 3 * 0,5 )
```

A função `calculaResultado` usa o `??` para verificar se o parâmetro `coeficiente` foi passado para a função. Caso tenha sido, seu valor será usado. Se não, o coeficiente padrão será `0.5`.

# Considerações

O caso que citei for um exemplo simples, mas o operador `??` pode ser útil em muitas situações e garantir uma maior confiabilidade no seu código.

Gostou deste artigo? Me siga para mais conteúdos como esse!

Minhas redes sociais:

[Twitter](https://twitter.com/reisdev) | [Instagram](https://instagram.com/reisdev) | [Youtube](https://youtube.com/reisdev). 

Até o próximo artigo!👋🏽
