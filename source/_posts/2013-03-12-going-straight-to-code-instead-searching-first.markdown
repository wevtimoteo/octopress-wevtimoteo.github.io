---
layout: post
title: "Vá direto pro código antes de pesquisar"
date: 2013-03-12 14:13
comments: true
categories: development debugging
---

No começo desse mês recebi uma newsletter do [Jesse Storimer](http://jstorimer.com) que achei muito interessante e resolvi fazer uma réplica.

Como o texto foi transmitido via newsletter não encontrei nenhum link direto pro artigo. Então irei tentar repassar a experiência nesse post, ao invés de copiar e colar o post dele em algum lugar.

## Batendo na parede

Uma situação bem comum: estamos desenvolvendo e esbarramos em algum problema/bug que não conseguimos resolver. O que fazemos? Pesquisamos no Google.

Mas isso não é uma boa prática. Ok, muitas vezes você vai cair certinho naquele link no [StackOverflow](http://www.stackoverflow.com) falando o que você precisa fazer e até muitas vezes o próprio mantenedor responde determinada questão. Mas, outras vezes, nem que um '42' apareça na sua frente você encontra a resposta.

Essa resposta que você tanto procura, sempre esteve em um único lugar: **no código**.

<!-- more -->

## Encontrando a solução

Algumas vezes nem no código você precisa olhar, uma simples lida na documentação (ponto que o [@darthmv](http://twitter.com/darthmv) sempre fala) resolva seu problema ou te dê uma luz.

Agora quando isso não resolve, vá direto ao código!

## Maneiras de buscar no código/Ou como chegar até ele

### bundle open <nomedagem>

Claro, se você está usando [Bundler](http://www.gembundler.com) isso faz toda diferença. Esse comando irá abrir o código da Gem no seu `$EDITOR`.

Combinando o `bundle open` com um ack/grep ou até [The Silver Searcher](https://github.com/ggreer/the_silver_searcher) são ótimos aliados para entender e encontrar o que está relacionado com o seu problema.

### qwandry

qwandry é uma gem que permite você abrir o código fonte de qualquer coisa da standard lib do Ruby.

Para instalar: ``gem install qwandry`` e para usar ``qw nome_da_classe_na_standard_lib``. Isso também abrirá o código fonte no seu $EDITOR.

Por exemplo, tenho dúvidas de como renderizar um arquivo ERB, qual método devo utilizar? Basta usar:

``qw erb``

E então explorar o código fonte :)

### gem_readme

Essa gem é bem útil quando você não quer ficar procurando a documentação no [GitHub](http://www.github.com) ou no [RubyGems](http://www.rubygems.org). Ela abre o README da gem que você deseja com um simples comando.

``gem install gem_readme``

Para usar:

``gem readme activeadmin``

### ctags

Você já deve ter ouvido falar de [Ctags](http://ctags.sourceforge.net/ctags.html), ou até usar. Se você ainda não usa de uma testada.

O Ctags é bem útil para navegar entre o código, principalmente código desconhecido.

Uma boa combinação é a [gem-ctags do @tpope](https://github.com/tpope/gem-ctags) e [AutoTag](http://www.vim.org/scripts/script.php?script_id=1343) (só não esqueça de colocar o ctags no seu gitignore global).

O Jesse aproveitou para dar [umas dicas de usar o **RI** ao invés do **Rdoc**](http://www.jstorimer.com/ri.html).

## O que você ganha fazendo tudo isso?

### Documentação não conta toda a história

Nessa parte, o Jesse deu um exemplo bem bacana que eu vou simplesmente citar aqui:

> ActiveRecord is a great example of this. When I'm trying to figure out what touch or reload or some other ActiveRecord::Base method does, I could look at the documentation. It would tell me how the method is intended to be used, what parameters it takes, and what it returns.
>
> In most cases, this is all you need. But if you've got a weird bug, or you want to know how a given method interacts with the database, you've got to go to the code. Once you do, you'll see that the reload method is defined several times in different modules that call each other, tacking on different behaviours. This is something that the documentation didn't make clear.
>
> If you want the whole story, go to the source.

### Testes são as melhores documentações

Como a comunidade Ruby ama testes, nada melhor do que olhar os testes para entender como usar determinado método ou até mesmo uma API.

### O melhor motivo: você aprende coisas novas

Outras pessoas pensam de outra forma, têm outro estilo de código e approaches diferentes dos nossos. Lendo o código dessas pessoas irá inspirar você a ter uma nova ideia.


## E se tudo falhar?

Aí sim você vai atrás de ajuda online. Mas pelo menos você já tentou de tudo e realmente aprendeu muito com isso!

## Créditos

Eu apenas traduzi e expliquei de uma forma diferente, todos os créditos vão para o [Jesse Storimer](http://jstorimer.com) pelo grande artigo.
