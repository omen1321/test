##  4. Внесение изменений

Цели

Научиться отслеживать состояние рабочей директории.
01 Измените страницу «Hello, World»

Добавим кое-какие HTML-теги к нашему приветствию. Измените содержимое файла на:

Файл: hello.html
<h1>Hello, World!</h1>
02 Проверьте состояние

Теперь проверьте состояние рабочей директории.

Выполните
git status
Вы увидите...

Результат
$ git status
On branch main
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	modified:   hello.html

no changes added to commit (use "git add" and/or "git commit -a")
Первое, что нужно заметить, это то, что Git знает, что файл hello.html был изменен, но при этом эти изменения еще не зафиксированы в репозитории.

Также обратите внимание на то, что сообщение о состоянии дает вам подсказку о том, что нужно делать дальше. Если вы хотите добавить эти изменения в репозиторий, используйте команду git add. В противном случае используйте команду git сheckout для отмены изменений.
---

### [Содержание](./bookgit.md)
### [Предыдущая](./book4.md)   [Следующая](./book6.md)