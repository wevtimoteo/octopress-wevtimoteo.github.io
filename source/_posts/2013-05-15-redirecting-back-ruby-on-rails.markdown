---
layout: post
title: "Redirecionando de volta no Rails"
date: 2013-05-15 13:47
comments: true
categories: ruby rails
---

Queria só fazer um post rápido de um truque que eu não conhecia =P

O comando `redirect_to :back` faz exatamente o ele diz (óbvio): redireciona o usuário de volta para página que o mesmo estava.

Esse comando é similar ao `redirect_to request.env["HTTP_REFERER"]`, por isso não se esqueça de setar o HTTP_REFERER no seu teste de controller.

Algo bacana desse redirect é que ele leva os `params` também, então se o usuário estava em página de busca cheia de filtros, nada será perdido.

