##  32. Что такое origin?

Цели

Узнать об именах удаленных репозиториев.
Выполните
git remote
Результат
$ git remote
origin
Мы видим, что клонированный репозиторий знает об имени по умолчанию удаленного репозитория. Давайте посмотрим, можем ли мы получить более подробную информацию об имени по умолчанию:

Выполните
git remote show origin
Результат
$ git remote show origin
* remote origin
  Fetch URL: /home/alex/githowto/repositories/work
  Push  URL: /home/alex/githowto/repositories/work
  HEAD branch: main
  Remote branches:
    main  tracked
    style tracked
  Local branch configured for 'git pull':
    main merges with remote main
  Local ref configured for 'git push':
    main pushes to main (up to date)
Мы видим, что имя по умолчанию (origin) удаленного репозитория — изначальное work. Удаленные репозитории обычно размещаются на отдельной машине, возможно, централизованном сервере. Однако, как мы видим здесь, они могут с тем же успехом указывать на репозиторий на той же машине. Нет ничего особенного в имени origin, однако существует традиция использовать origin в качестве имени первичного централизованного репозитория (если таковой имеется).
---

### [Содержание](./bookgit.md)
### [Предыдущая](./book33.md)   [Следующая](./book35.md)