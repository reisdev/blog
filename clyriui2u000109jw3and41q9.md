---
title: "Como programar em Swift no Linux"
datePublished: Thu Jul 18 2024 17:04:48 GMT+0000 (Coordinated Universal Time)
cuid: clyriui2u000109jw3and41q9
slug: como-programar-em-swift-no-linux
canonical: https://dev.to/reisdev/como-programar-em-swift-no-linux-52j5
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1721321546991/8038a3ce-2df6-4770-bba7-5435689f6a5a.png
tags: tutorial, linux, swift, beginners

---

Aprender a programar em Swift, para quem não tem um dispositivo da Apple, parece impossível. Porém, muita gente não sabe que a linguagem Swift é de código-aberto e pode ser usada no macOS, Windows e Linux. Hoje, veremos o passo-a-passo para os SOs Linux, mais especificamente, o Ubuntu.

> **NOTA:** Não é possível criar apps para os dispositivos da Apple usando os sistemas operacionais Linux. Para isso, é preciso usar o macOS ou iPadOS. Porém, é possível aprender e programar em Swift, o que já é um ótimo começo.

## 1\. Obtendo a Toolchain

Primeiramente, vamos realizar o download do arquivo compactado contendo a toolchain de Swift, que dá suporte à compilação e execução de código em Swift. Para isso, acesse a página a seguir:

[https://www.swift.org/install](https://www.swift.org/install)

Nela, é possível escolher o sistema operacional desejado para obter os arquivos de instalação:

![Captura de tela da página de instalação de Swift com 3 opções listadas: macOS, Linux e Windows](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/pmfhgqxurnotj5apwiz5.png align="left")

Como vamos utilizar como base o Ubuntu Linux como base para esse tutorial, basta selecionar a opção `Linux`, e em seguida a opção da plataforma `Ubuntu`. Após isso, é possível selecionar a versão do Ubuntu em que será realizada a instalação. No meu caso, é a `22.04`.

**Escolha a opção correspondente à sua instalação do Ubuntu:**

![Captura de tela com as opções Linux, plataforma Ubuntu e versão Ubuntu 22.04 selecionadas](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/tt8wubn5b2ftewxm0161.png align="left")

Feito isso, iremos realizar o download do tarball contendo a toolchain. Para isso, primeiro, é necessário saber qual a arquitetura do seu processador: `x86_64` ou `arm64`. Para isso, execute o comando abaixo no seu terminal de preferência:

```sh
uname -m
```

Se a saída for `x86_64`, clique na opção abaixo:

![Captura de tela com o botão "Download (x86_64)" em destaque](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/cu0nk2l4sd12m113c2oc.png align="left")

Se for `aarch64` ou `arm64`, clique na opção abaixo:

![Captura de tela com o botão "Download (aarch64)" em destaque](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/jxliigqurg66mgfae1qi.png align="left")

Feito isso, o download de um arquivo `.tar.gz` será realizado. Agora, você pode acessar o link a seguir para acompanhar o processo de instalação:

[https://www.swift.org/install/linux/tarball/](https://www.swift.org/install/linux/tarball/)

## 2\. Instalando as Dependências

Antes de instalarmos a toolchain em si, é necessário garantir a instalação de todas as dependências da linguagem. O link anterior possui algumas seções contendo as dependências para cada SO Linux:

![Captura de tela com as opções de sistemas operacionais baseados no Linux e suas respectivas dependências](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/fkyygfutfe7tyzk2g31g.png align="left")

Estranhamente, não há uma opção para o Ubuntu 22.04, então usei as mesmas dependências do 20.04. Antes de instalar as dependências, é importante executar o comando para atualizar os pacotes já existentes na sua máquina:

```sh
$ apt-get update
```

> Permissões de administrador podem ser necessárias para executar os comandos no terminal. Para isso, basta adicionar o `sudo` antes dos comandos.

Feito isso, basta instalar as dependências:

```sh
$ apt-get install \
          binutils \
          git \
          gnupg2 \
          libc6-dev \
          libcurl4 \
          libedit2 \
          libgcc-9-dev \
          libpython2.7 \
          libsqlite3-0 \
          libstdc++-9-dev \
          libxml2 \
          libz3-dev \
          pkg-config \
          tzdata \
          uuid-dev \
          zlib1g-dev
```

Após instalar as dependências, podemos finalmente realizar a instalação da toolchain. Vamos acessar a pasta downloads para extrair o arquivo que baixamos anteriormente:

```sh
$ cd ~/Downloads
```

Agora, podemos extrair o conteúdo do arquivo comprimido. O nome será parecido com:

`swift-<versao>-RELEASE-<plataforma>-<arquitetura>.tar.gz`

```plaintext
$ tar xzf <nome-do-arquivo>.tar.gz
```

> **Atenção**: O nome do arquivo .tar.gz pode variar de acordo com a versão da toolchain que for obtida no site. Você pode começar digitando `~/.Downloads/swift-` e apertar tab para que o terminal complete o restante.

Os arquivo comprimido será extraído para uma pasta de mesmo nome. Agora, iremos mover esta para um novo destino:

Agora, vamos criar uma pasta para onde iremos extrair a toolchain:

```sh
$ mv <nome-da-pasta> ~/.swift-toolchain
```

Pronto, agora já temos a toolchain no lugar correto. O próximo passo é torná-la acessível pelo terminal, modificando a variável `PATH`.

É preciso adicionar o seguinte caminho:

```sh
export PATH="~/.swift-toolchain/usr/bin:$PATH"
```

Use seu arquivo de preferência para inserir essa modificação (`.bashrc`, `.zshrc`, `.bash_profile`, `.zprofile` ou outro):

```sh
$ export PATH="~/.swift-toolchain/usr/bin:$PATH" > ~/.bashrc
```

Para confirmar que a instalação foi um sucesso, você pode executar o seguinte comando no terminal:

```sh
$ swift --version
```

O resultado deverá ser similar a esse(a depender do seu SO e arquitetura)

```sh
Swift version 5.10.1 (swift-5.10.1-RELEASE)
Target: aarch64-unknown-Linux-gnu
```

Pronto, já é possível executar código Swift na sua máquina.

## 3\. Como executar código em Swift

Agora que já temos a toolchain instalada, podemos criar código em Swift.

> **ATENÇÃO**: Como dito anteriormente, não é possível criar apps para iOS/iPad/macOS/tvOS em ambiente Linux. Frameworks específicos como `UIKit`, `SwiftUI` e outros não estão disponíveis.

Primeiro, vamos criar um arquivo:

```sh
$ touch exemplo.swift
```

Arquivo criado, podemos abrí-lo com nosso editor de preferência. Pode ser o Visual Studio Code, nano, o que preferir. Eu usei o `vim`:

```sh
$ vim exemplo.swift
```

![Captura de tela do arquivo exemplo.swift aberto no editor vim. O arquivo diz print("Hello, world!")](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/785nac42dt9jzujri3h6.png align="left")

Agora, podemos executar o código no terminal e ver o resultado:

```sh
$ swift exemplo.swift 
Hello, world!
```