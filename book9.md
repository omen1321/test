##  8. Изменения, а не файлы

Цели

Понять, что Git работает с изменениями, а не файлами.
Большинство систем контроля версий работает с файлами: вы добавляете файл в систему, и она отслеживает изменения файла с этого момента.

Git фокусируется на изменениях в файле, а не самом файле. Когда вы осуществляете команду git add file, вы не говорите Git добавить файл в репозиторий. Скорее вы говорите, что Git надо отметить текущее состояние файла, коммит которого будет произведен позже.

Мы попытаемся исследовать эту разницу в данном уроке.

01 Первое изменение: Добавьте стандартные теги страницы

Измените страницу «Hello, World», чтобы она содержала стандартные теги <html> и <body>.

Файл: hello.html
<html>
  <body>
    <h1>Hello, World!</h1>
  </body>
</html>
02 Добавьте это изменение

Теперь добавьте это изменение в индекс Git.

Выполните
git add hello.html
03 Второе изменение: Добавьте заголовки HTML

Теперь добавьте заголовки HTML (секцию <head>) к странице «Hello, World».

Файл: hello.html
<html>
  <head>
  </head>
  <body>
    <h1>Hello, World!</h1>
  </body>
</html>
04 Проверьте текущий статус

Выполните
git status
Вы увидите:

Результат
$ git status
On branch main
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
	modified:   hello.html

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	modified:   hello.html

Обратите внимание на то, что hello.html указан дважды в состоянии. Первое изменение (добавление стандартных тегов) проиндексировано и готово к коммиту. Второе изменение (добавление заголовков HTML) является непроиндексированным. Если бы вы делали коммит сейчас, заголовки не были бы сохранены в репозиторий.

Давайте проверим.

05 Коммит

Произведите коммит проиндексированного изменения (значение по умолчанию), а затем еще раз проверьте состояние.

Выполните
git commit -m "Added standard HTML page tags"
git status
Вы увидите:

Результат
$ git commit -m "Added standard HTML page tags"
[main 46afaff] Added standard HTML page tags
 1 file changed, 5 insertions(+), 1 deletion(-)
$ git status
On branch main
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	modified:   hello.html

no changes added to commit (use "git add" and/or "git commit -a")
Команда status показывает, что в файле hello.html ещё есть незаписанные изменения, но область подготовки уже пуста.

06 Добавьте второе изменение

Теперь добавьте второе изменение в индекс, а затем проверьте состояние с помощью команды git status.

Выполните
git add .
git status
Мы использовали текущую директорию (.) в качестве аргумента для добавления. Это самый короткий и удобный способ добавления всех изменений в текущей директории. Но поскольку Git добавляет в индекс всё, то не лишним будет проверить состояние репозитория перед запуском add, просто чтобы убедиться, что вы не добавили какой-то файл, который не следовало бы добавлять.

Я просто хотел показать вам трюк с add ., в дальнейшем мы будем добавлять все файлы явно.
Вы увидите:

Результат
$ git add .
$ git status
On branch main
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
	modified:   hello.html

Второе изменение было проиндексировано и готово к коммиту.

07 Сделайте коммит второго изменения

Выполните
git commit -m "Added HTML header"
Результат
$ git commit -m "Added HTML header"
[main b7614c1] Added HTML header
 1 file changed, 2 insertions(+)
 ---

 ### [Содержание](./bookgit.md)
 ### [Предыдущая](./book8.md)   [Следующая](./book10.md)