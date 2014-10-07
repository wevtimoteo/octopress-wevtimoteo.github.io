---
layout: post
title: "O que significa 'Class Cluster' no iOS"
date: 2014-10-06 23:10
comments: true
categories: ios, foundation, objective-c, class cluster, design pattern
---

`Class Cluster` é um design pattern usado no framework Foundation.

O objetivo desse pattern é agrupar subclasses privadas a partir de uma superclasse pública abstrata.

## Sem Class Cluster

Imagine o seguinte cenário: você precisa armazenar diversas medidas, milímetros, centímetros, metros, quilômetros.

O que todas essas medidas possuem em comum? Elas podem ser convertidas (ex.: metros => centímetros) e podem ser representadas por uma única classe.
No entanto, o armazenamento de cada uma delas pode ser diferente.

Para lidar com este cenário poderíamos implementar da seguinte maneira:

* Comprimento (superclasse)
  * Milímetro
  * Centímetro
  * Metro
  * Quilômetro

`Comprimento` é nossa superclasse que declara os métodos principais de operações que todas as outras subclasses terão em comum.

Neste exemplo as subclasses são públicas, ou seja, você pode instanciá-las diretamente.

O conceito é simples mas a interface começa a ficar complexa de acordo com a quantidade de subclasses.

## Com Class Cluster

Com o mesmo cenário, vamos imaginar uma solução diferente: ao invés das subclasses públicas teremos apenas nossa superclasse pública. E como iremos instanciar uma subclasse irá depender do que nossa superclasse `Comprimento` suporta.

Agora é responsabilidade da superclasse dizer qual objeto deve ser criado a partir do método de classe que for chamado.

Exemplo:

``WWLength *aMeter = [WWLength lengthWithMeter:1];``

Cada objeto retornado pelo seu método de factory pode pertencer a um tipo de instância da subclasse. Mas não se esqueça, neste caso a subclasse está oculta, você não a conhece, então nossa instância `aMeter` é do tipo `WWLength`.

Esse é o conceito do Class Cluster, que é utilizado intensamente no framework Foundation.

Dê uma olhada na documentação para obter mais informações de classes do Foundation que seguem esta abordagem: [Cocoa Core Class Cluters](https://developer.apple.com/library/ios/documentation/general/conceptual/DevPedia-CocoaCore/ClassCluster.html)
