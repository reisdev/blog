---
title: "Como usar variáveis de ambiente sem biblioteca em React"
datePublished: Tue Apr 20 2021 11:02:19 GMT+0000 (Coordinated Universal Time)
cuid: cknpx3wrh0t57lps16sq4hjqw
slug: como-usar-variaveis-de-ambiente-sem-biblioteca-em-react
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1618915931972/rV5KTNAAz.jpeg
tags: cloud, security, reactjs, devops

---

Capa por <a href="https://unsplash.com/@flyd2069?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">FLY:D</a> no <a href="https://unsplash.com/s/photos/key-security?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Unsplash</a>

Já deixou vazar alguma chave de segurança porque subiu alguma alteração e esqueceu de apagar o conteúdo sensível? Usar variáveis de ambiente evita que coisas assim aconteçam. Mas, como elas funcionam no React? Vem comigo!

# Sumário

- [O que são Variáveis de ambiente](o-que-s%C3%A3o-vari%C3%A1veis-de-ambiente)
- [Como funcionam](#como-funcionam)
- [Como utilizar](#como-utilizar)

# O que são Variáveis de Ambiente

Variáveis de ambiente são um conjunto de valores que geralmente são definidos para configurações de uma aplicação. Exemplos: Dados de conexão com um banco, a URL de uma API e etc.

O termo "Ambientes" se refere à diferentes cenários em que uma aplicação pode estar sendo executada. Os mais comuns são: desenvolvimento, teste, homologação, e produção. Cada um deles pode exigir diferentes configurações, e por isso é feita essa divisão. Você uma variável na aplicação que, em diferentes ambientes, terá valores específicos para aquele cenário.

# Como funcionam

Para configurar variáveis de ambiente em uma aplicação React você precisa criar um arquivo na raiz da aplicação com o nome `.env`. Primeiro, certifique-se de que está na pasta-raiz do seu projeto, onde ficam os arquivos `package.json`, `.gitignore` e etc. Se preferir criar por linha de comando, utilize um dos comandos abaixo, de acordo com seu sistema operacional:

```bash
# MacOS ou Linux
touch .env

# Windows
type NUL > .env
```

Agora, você verá o arquivo vazio na pasta-raiz do seu projeto. Para criar uma variável de ambiente, você deve utilizar o prefixo `REACT_APP_`. Por exemplo: Se você deseja criar uma variável `API_URL`, ela deve ser nomeada como `REACT_APP_API_URL`, pois a `react-scripts` só faz a leitura das variáveis que usam esse prefixo.

# Como utilizar
 
Vamos supor uma aplicação que precise de variáveis de ambiente para usar uma API para usar com o Axios. Não se preocupe com o que é axios e o que API, foque em entender a parte das variáveis. Será preciso configurar a porta, a url base e a versão de uma API. Logo, nosso arquivo `.env` ficaria da seguinte forma:

```bash
# Arquivo .env
REACT_APP_API_BASEURL = https://mydomain.com
REACT_APP_API_PORT = 8888
REACT_APP_API_VERSION = v2
```

E agora, para configurar nossa instância do Axios, podemos utilizar nossas variáveis de ambiente:

```js
// Arquivo axios.js, apenas um exemplo
const url = process.env.REACT_APP_API_BASEURL
const port = process.env.REACT_APP_API_PORT
const version = process.env.REACT_APP_API_VERSION

const api = axios.create({
    baseURL: `${url}:${port}/${version}/`
})

export default api;
```

E pronto. Nossas variáveis de ambiente estão configuradas e prontas para serem utilizadas em toda a aplicação. Porém, ainda temos dois pontos importantes:

Para evitar que seu arquivo `.env` seja enviado para um repositório remoto, é importante adicioná-lo ao `.gitignore`,dessa forma:

```bash
# Arquivo .gitignore
# ... outros valores
.env
```

 E, para garantir que outras pessoas saberão configurar as variáveis de ambiente, crie um arquivo `.env.example`, com as variáveis sem valor definido, dessa forma:

```bash
# Arquivo .env.example
REACT_APP_API_BASEURL = https://mydomain.com
REACT_APP_API_PORT = 8888
REACT_APP_API_VERSION = v2
```

# Considerações

É importante lembrar que variáveis de ambiente configuradas em containers e ambientes cloud(Heroku, Vercel, Netlify, etc) também são reconhecidas, em tempo de build. Agora que você já sabe disso, não vai mais precisar se preocupar em apagar valore sensíveis toda vez que for fazer algum commit.

Gostou deste artigo? Me siga para mais conteúdos como esse!

Minhas redes sociais:

[Twitter](https://twitter.com/reisdev) | [Instagram](https://instagram.com/reisdev) | [Youtube](https://youtube.com/reisdev). 

Até o próximo artigo!👋🏽