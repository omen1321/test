##  37. Добавление ветки наблюдения

Цели

Научиться добавлять локальную ветку, которая отслеживает изменения удаленной ветки.
Ветки, которые начинаются с remotes/origin являются ветками оригинального репозитория. Обратите внимание, что у вас больше нет ветки под названием style, но система контроля версий знает, что в оригинальном репозитории ветка style была.

01 Добавьте локальную ветку, которая отслеживает удаленную ветку

Выполните
git branch --track style origin/style
git branch -a
git log --max-count=2
Результат
$ git branch --track style origin/style
Branch 'style' set up to track remote branch 'style' from 'origin'.
$ git branch -a
* main
  style
  remotes/origin/HEAD -> origin/main
  remotes/origin/main
  remotes/origin/style
$ git log --all --graph --max-count=2
* 71df43a 2023-11-28 | Changed README in original repo (HEAD -> main, origin/main, origin/HEAD) [Alexander Shvets]
* 39a1e0f 2023-11-28 | Renamed hello.html; moved style.css (origin/style, style) [Alexander Shvets]
Теперь мы можем видеть ветку style в списке веток и логе.
---

### [Содержание](./bookgit.md)
### [Предыдущая](./book38.md)   [Следующая](./book40.md)