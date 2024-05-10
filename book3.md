## 2. Создание проекта

Цели

Научиться создавать Git-репозиторий с нуля.
01 Создайте страницу «Hello, World»

Начните работу в пустой директории (например, respositories, если вы скачали архив с предыдущего шага) с создания пустой поддиректории work, затем войдите в неё и создайте там файл hello.html с таким содержанием:

Выполните
mkdir work
cd work
touch hello.html
Файл: hello.html
Hello, World
02 Создайте репозиторий

Теперь у вас есть директория с одним файлом. Чтобы создать Git-репозиторий из этой директории, выполните команду git init.

Выполните
git init
Результат
Initialized empty Git repository in /home/alex/githowto/repositories/work/.git/
03 Добавьте страницу в репозиторий

Теперь давайте добавим в репозиторий страницу «Hello, World».

Выполните
git add hello.html
git commit -m "Initial Commit"
Вы увидите...

Результат
$ git add hello.html
$ git commit -m "Initial commit"
[main (root-commit) 5836970] Initial commit
 1 file changed, 1 insertion(+)
 create mode 100644 hello.html
 ---

 ### [Содержание](./bookgit.md)
 ### [Предыдущая](./book2.md)   [Следующая](./book4.md)