---
layout: post
title: "MnM Dev: Adicionando overlay e tooltip nas imagens"
date: 2013-01-16 15:44
comments: true
categories: [Ruby, FrontEnd, MnM Dev]
---

Toda quarta-feira irei fazer um post sobre algo que foi desenvolvido no [Mangá no Mori](http://www.manganomori.com.br) já que nossas reuniões acontecem toda terça à noite. E para estrear a coluna, esse post explicará como fazer um overlay de uma imagemcomo no exemplo abaixo:

{% img /images/posts/mnm_dev_unavailable_cover.png [Capa indisponível[Capa indisponível]] %}

Quando o usuário clica com o botão direito não aparecerá a opção de salvar a imagem.
<!-- more -->

Para fazer isso criamos um helper do Rails:

