---
layout: post
title: "O que é Teste de Regressão?"
date: 2013-03-11 10:47
comments: true
categories: development testing software regression
---

Há um tempo já me pego lendo e ouvindo esse termo e nunca tinha entendido exatamente quais eram os momentos que eu deveria fazê-lo, então aproveitei para fazer um review completo sobre 'O que é Teste de Regressão?'.

###Qual o objetivo do teste de software?

> Identificar suas falhas para que a correção seja feita antes da entrega do produto ao usuário final.

###Como um teste de regressão surge?

> Um componente novo ou modificado pode falhar quando usado com componentes inalterados, causando defeito
> nos componentes inalterados pela geração de efeitos colaterais ou pelas características de interação.

Quando isso ocorre, diz-se que o sisteme sobre testes regrediu, por isso esses testes são chamados de testes de regressão.

Em poucas palavras, você quebrou o teste de uma outra funcionalidade por conta dessa nova _feature_ ou _correção de bug_.

###Quando um teste de regressão é utilizado?

> * durante o desenvolvimento iterativo
> * depois da depuração
> * no primeiro passo de uma integração
> * na manutenção de software

####E dentro do escopo de Orientação a Objetos?

> * quando uma subclasse é desenvolvida
> * quando uma super-classe é alterada
> * quando uma classe servidora (classe que você estendeu, por exemplo)
> * quando uma correção de falha é realizada
> * quando uma classe é reusada em um novo contexto

Isso é apenas um resumo, todas informações que citei podem ser consultadas com maiores detalhes nos links abaixo.


###Fontes:

* [Slideshare @csilvas - Testes de regressão automatizados](http://www.slideshare.net/csilvas/testes-de-regresso-automatizados)
* [Teste Funcional e Regressão](http://www.testar.me/pages/testar_me_teste_funcional_regressao.html)
* [Testes de Regressão - R.Anido (Unicamp)](http://www.ic.unicamp.br/~ranido/mc626/Regressao.pdf)
* [Thoughts on regression testing - Praticing Ruby](https://practicingruby.com/articles/shared/afshdqdholth)
