##  16. Удаление тега oops

Цели

Удаление тега oops.
01 Удаление тега oops

Тег oops свою функцию выполнил, давайте удалим его. Это позволит внутреннему механизму Git убрать остаточные коммиты, на которые теперь не ссылаются никакие ветки или теги.

Выполните
git tag -d oops
git log --all
Результат
$ git tag -d oops
Deleted tag 'oops' (was 86364a1)
$ git log --all
b7614c1 2023-11-28 | Added HTML header (HEAD -> main, tag: v1) [Alexander Shvets]
46afaff 2023-11-28 | Added standard HTML page tags (tag: v1-beta) [Alexander Shvets]
78433de 2023-11-28 | Added h1 tag [Alexander Shvets]
5836970 2023-11-28 | Initial commit [Alexander Shvets]
Тег oops больше не будет отображаться в репозитории.
---

### [Содержание](./bookgit.md)
### [Предыдущая](./book16.md)   [Следующая](./book18.md)