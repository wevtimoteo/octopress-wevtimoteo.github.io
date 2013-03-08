---
layout: post
title: "Abrindo arquivos alterados no Git com seu $EDITOR"
date: 2013-03-08 15:13
comments: true
categories: vim macos bash
---

Hoje cheguei no projeto que estou trabalhando na [Baby](http://www.baby.com.br) e um simples:

``git st`` (git status)

E obtenho:

```
# On branch master
# Changes not staged for commit:
#   (use "git add <file>..." to update what will be committed)
#   (use "git checkout -- <file>..." to discard changes in working directory)
#
# modified:   Gemfile
# modified:   Gemfile.lock
# modified:   app/api/company.rb
# modified:   app/helpers/authentication_helper.rb
# modified:   config/boot.rb
# modified:   config/initializers/app_config.rb
```

Pensei: seria legal, automaticamente abrir esses arquivos no meu $EDITOR.

Um simples ``git status --short`` resolveria isso, adicionado ao awk e o próprio $EDITOR:

``$EDITOR $(git status --short | awk '$1 ~ /^M$/ {print $2}')``

Isso fará com que todos os arquivos modificados sejam abertos no seu $EDITOR favorito. Se for `vim`, todos os arquivos serão abertos em buffers. Para abrir em uma abas:

``$EDITOR -p $(git status --short | awk '$1 ~ /^M$/ {print $2}')``

Depois disso pensei em usar em alias. Mas usar `gitedit` seria muito chato, então fiz essa modificação no meu [dotfiles](https://github.com/wolcanus/dotfiles/commit/4321444655acae64b05ee02faad7f463df19aade) para poder utilizar um simples:

``git edit``
