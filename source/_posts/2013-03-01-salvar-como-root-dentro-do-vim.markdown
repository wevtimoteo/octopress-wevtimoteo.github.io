---
layout: post
title: "Salvando um arquivo como root sem fechar e abrir o Vim"
date: 2013-03-01 11:29
comments: true
categories: vim
---

Seguindo a dica do [Lucas Catón](http://blog.lucascaton.com.br/): algumas vezes abrimos um arquivo que não temos permissão de escrita.

Mas já alteramos seu conteúdo =/

Ao invés de sair do Vim e abrir o arquivo como sudo/sudo -u, podemos executar:

``:w !sudo tee %``

Pronto! Nada de sair e entrar no vim por problemas de permissão de escrita!
