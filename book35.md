##  33. Удаленные ветки

Цели

Узнать о локальных и удаленных ветках.
Давайте посмотрим на ветки, доступные в нашем клонированном репозитории.

Выполните
git branch
Результат
$ git branch
* main
Как мы видим, в списке только ветка main. Где ветка style? Команда git branch выводит только список локальных веток по умолчанию.

01 Список удаленных веток

Для того чтобы увидеть все ветки, попробуйте следующую команду:

Выполните
git branch -a
Результат
$ git branch -a
* main
  remotes/origin/HEAD -> origin/main
  remotes/origin/style
  remotes/origin/main
Git выводит все коммиты в оригинальный репозиторий, но ветки в удаленном репозитории не рассматриваются как локальные. Если мы хотим иметь собственную ветку style, мы должны сами ее создать. Через минуту вы увидите, как это делается.
---

### [Содержание](./bookgit.md)
### [Предыдущая](./book34.md)   [Следующая](./book36.md)