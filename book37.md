##  35. Подтягивание изменений

Цели

Научиться подтягивать изменения из удаленного репозитория.
Выполните
cd ../home
git fetch
git log --all
Сейчас мы находимся в репозитории home.

Результат
$ cd ../home
$ git fetch
From /home/alex/githowto/repositories/work
   39a1e0f..71df43a  main       -> origin/main
$ git log --all --graph
* 71df43a 2023-11-28 | Changed README in original repo (origin/main, origin/HEAD) [Alexander Shvets]
* 39a1e0f 2023-11-28 | Renamed hello.html; moved style.css (HEAD -> main, origin/style) [Alexander Shvets]
* 23149b5 2023-11-28 | Included stylesheet into hello.html [Alexander Shvets]
* b9e6de1 2023-11-28 | Added css stylesheet [Alexander Shvets]
* 85c14e9 2023-11-28 | Added meta title [Alexander Shvets]
* ee16740 2023-11-28 | Added README [Alexander Shvets]
* 9288a33 2023-11-28 | Added copyright statement with email [Alexander Shvets]
* b7614c1 2023-11-28 | Added HTML header (tag: v1) [Alexander Shvets]
* 46afaff 2023-11-28 | Added standard HTML page tags (tag: v1-beta) [Alexander Shvets]
* 78433de 2023-11-28 | Added h1 tag [Alexander Shvets]
* 5836970 2023-11-28 | Initial commit [Alexander Shvets]
На данный момент в репозитории есть все коммиты из оригинального репозитория, но они не интегрированы в локальные ветки клонированного репозитория.

В истории выше найдите коммит «Changed README in original repo». Обратите внимание, что коммит включает в себя коммиты origin/main и origin/HEAD.

Теперь давайте посмотрим на коммит «Renamed hello.html; moved style.css». Вы увидите, что локальная ветка main указывает на этот коммит, а не на новый коммит, который мы только что подтянули.

Выводом является то, что команда git fetch будет подтягивать новые коммиты из удаленного репозитория, но не будет сливать их с вашими наработками в локальных ветках.

01 Проверьте README

Мы можем продемонстрировать, что клонированный файл README не изменился.

Выполните
cat README
Результат
$ cat README
This is the Hello World example from the GitHowTo tutorial.
Как видите, никаких изменений.
---

### [Содержание](./bookgit.md)
### [Предыдущая](./book36.md)   [Следующая](./book38.md)