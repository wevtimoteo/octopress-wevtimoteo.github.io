---
layout: post
title: "Instalando uma versão específica de uma fórmula no Homebrew"
date: 2013-03-18 17:51
comments: true
categories: brew macosx
---

Fiquei brincando um pouco com os comandos do `brew` e surgiu uma dúvida: como instalar versões específicas no [Homebrew](http://mxcl.github.com/homebrew/)?

### Atualize

Antes de mais nada, atualize suas fórmulas com o seguinte comando:

``brew update``

### Instalando uma versão específica

Para listar as versões disponíveis para uma fórmula, utilize:

``brew versions phantomjs``

Você terá uma lista parecida com essa:

```bash
1.8.1    git checkout 1a69283 /usr/local/Library/Formula/phantomjs.rb
1.8.0    git checkout 7b4df06 /usr/local/Library/Formula/phantomjs.rb
1.7.0    git checkout d37d922 /usr/local/Library/Formula/phantomjs.rb
1.6.1    git checkout 6b8d25f /usr/local/Library/Formula/phantomjs.rb
1.6.0    git checkout 9c7885b /usr/local/Library/Formula/phantomjs.rb
1.5.0    git checkout dbcbe16 /usr/local/Library/Formula/phantomjs.rb
1.4.1    git checkout cfbdf22 /usr/local/Library/Formula/phantomjs.rb
1.3.0    git checkout 5848860 /usr/local/Library/Formula/phantomjs.rb
1.2.0    git checkout c50bbb8 /usr/local/Library/Formula/phantomjs.rb
1.1.0    git checkout 4e7c332 /usr/local/Library/Formula/phantomjs.rb
1.0.0    git checkout 0476235 /usr/local/Library/Formula/phantomjs.rb
```

<!-- more -->

Agora, vamos instalar a versão 1.7.0. Para isso, acesse o diretório das fórmulas:

``cd /usr/local/Library/Formula/``

E use o próprio comando do output do ``brew versions phantomjs``:

``git checkout d37d922 /usr/local/Library/Formula/phantomjs.rb``

Isso fará com que a fórmula do [PhantomJS](http://phantomjs.org/) volte para versão do SHA utilizado.

Agora use:

``brew install phantomjs``

Se tudo ocorreu bem, você deve obter um resultado parecido com este:

``/usr/local/Cellar/phantomjs/1.7.0: 4 files, 10M, built in 2 seconds``

## Instalando outras versões

Agora que você já sabe como instalar uma versão, vamos instalar a mais recente, no meu caso é `1.8.1`:

``git checkout 1a69283 /usr/local/Library/Formula/phantomjs.rb``

Como você já possui a fórmula do PhantomJS 1.7.0 instalada, você vai precisar "desativá-la" primeiro:

``brew unlink phantomjs``

Agora é só instalar:

``brew install phantomjs``

O resultado será como este:

``/usr/local/Cellar/phantomjs/1.8.1: 96 files, 9.2M, built in 2 seconds``

## Trocando entre versões

Agora que você está trabalhando com várias versões instaladas, nada mais justo você poder alternar entre elas.

Primeiro vamos listar as versões que você possui na sua máquina:

``brew info phantomjs``

Eu tenho instalado:

```
phantomjs: stable 1.8.2
http://www.phantomjs.org/
/usr/local/Cellar/phantomjs/1.7.0 (4 files, 10M)
/usr/local/Cellar/phantomjs/1.8.1 (96 files, 11M)
/usr/local/Cellar/phantomjs/1.8.2 (96 files, 9.2M) *
https://github.com/mxcl/homebrew/commits/master/Library/Formula/phantomjs.rb
```

A versão que está com _*_ é a que está ativada.
Agora vamos ir para 1.7.0:

``brew switch phantomjs 1.7.0``

Dê um ``brew info phantomjs`` para confirmar se deu tudo certo:

```
phantomjs: stable 1.8.2
http://www.phantomjs.org/
/usr/local/Cellar/phantomjs/1.7.0 (4 files, 10M) *
/usr/local/Cellar/phantomjs/1.8.1 (96 files, 11M)
/usr/local/Cellar/phantomjs/1.8.2 (96 files, 9.2M)
https://github.com/mxcl/homebrew/commits/master/Library/Formula/phantomjs.rb
```

Pronto! Se quiser desinstalar é só ir utilizando ``brew uninstall phantomjs`` entre as versões.
Ou se preferir, você pode remover tudo de uma vez:

``brew uninstall -f phantomjs``

Se der ``brew info phantomjs`` verá que nenhuma fórmula está instalada:

```
phantomjs: stable 1.8.2
http://www.phantomjs.org/
Not installed
https://github.com/mxcl/homebrew/commits/master/Library/Formula/phantomjs.rb
```
