##  5. Индексация изменений

Цели

Научиться индексировать изменения для последующих коммитов.
01 Добавьте изменения

Теперь дайте команду Git проиндексировать изменения. Проверьте состояние:

Выполните
git add hello.html
git status
Вы увидите:

Результат
$ git add hello.html
$ git status
On branch main
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
	modified:   hello.html

Изменения файла hello.html были проиндексированы. Это означает, что Git теперь знает об изменении, но изменение пока не перманентно (читай, навсегда) записано в репозиторий. Следующий коммит будет включать в себя проиндексированные изменения.

Если вы решили, что не хотите коммитить изменения, команда состояния напомнит вам о том, что с помощью команды git reset можно снять индексацию этих изменений.
---

### [Содержание](./bookgit.md)
### [Предыдущая](./book5.md)   [Следующая](./book7.md)