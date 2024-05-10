##  38. Чистые репозитории

Цели

Научиться создавать чистые репозитории.
Чистый репозиторий — это репозиторий, не имеющий рабочей директории. Он содержит только директорию .git, в которой Git хранит все свои внутренние данные. Основное предназначение таких репозиториев — быть центральным хранилищем, в которое разработчики могут отправлять и из которого могут получать данные. Поэтому в них нет смысла создавать рабочие файлы, они будут только впустую занимать место на диске. Чистые репозитории также используются в сервисах Git-хостинга таких, как GitHub и GitLab. В следующих уроках мы узнаем, как создать чистый репозиторий и как отправлять в него изменения.

01 Создайте чистый репозиторий

Выполните
cd ..
git clone --bare work work.git
ls work.git
Сейчас мы находимся в директории repositories.

Результат
$ git clone --bare work work.git
Cloning into bare repository 'work.git'...
done.
$ ls work.git
branches
config
description
HEAD
hooks
info
objects
packed-refs
refs
Принято считать, что репозитории, заканчивающиеся на .git, являются чистыми репозиториями. Мы видим, что в репозитории work.git нет рабочей директории. По сути, это просто директория .git из обычного репозитория.
---

### [Содержание](./bookgit.md)
### [Предыдущая](./book39.md)   [Следующая](./book41.md)