##  9. История

Цели

Научиться просматривать историю проекта.
Получение списка произведенных изменений — функция команды git log.

Выполните
git log
Вы увидите:

Результат
$ git log
commit b7614c1aea1ffbc46400fe1a163842d6ec620a43
Author: Alexander Shvets <alex@githowto.com>
Date:   Tue Nov 28 05:51:38 2023 -0600

    Added HTML header

commit 46afaff2232fc3d564c40f65cb82e7e94839a1bb
Author: Alexander Shvets <alex@githowto.com>
Date:   Tue Nov 28 05:51:38 2023 -0600

    Added standard HTML page tags

commit 78433de967102f2b59d0a8a60eb397b2663ed282
Author: Alexander Shvets <alex@githowto.com>
Date:   Tue Nov 28 05:51:38 2023 -0600

    Added h1 tag

commit 58369706affbc1c27fa03a65fc7a05847278045f
Author: Alexander Shvets <alex@githowto.com>
Date:   Tue Nov 28 05:51:38 2023 -0600

    Initial commit
Вот список всех четырех коммитов в репозиторий, которые мы успели совершить.

01 Однострочная история

Вы полностью контролируете то, что отображает log. Мне, например, нравится однострочный формат:

Выполните
git log --pretty=oneline
Вы увидите:

Результат
$ git log --oneline
b7614c1 Added HTML header
46afaff Added standard HTML page tags
78433de Added h1 tag
5836970 Initial commit
02 Контроль отображения записей

Вот еще интересные варианты просмотра истории:

git log --oneline --max-count=2
git log --oneline --since="5 minutes ago"
git log --oneline --until="5 minutes ago"
git log --oneline --author="Your Name"
git log --oneline --all
Существует огромное количество вариантов просмотра истории, вы можете порыться на странице руководства git-log, чтобы увидеть их все.

03 Изощряемся

Вот что я использую для просмотра изменений, сделанных за последнюю неделю. Я добавлю --author=Alexander, если я хочу увидеть только изменения, которые сделал я.

git log --all --pretty=format:"%h %cd %s (%an)" --since="7 days ago"
04 Конечный формат лога

Со временем, я решил, что для большей части моей работы мне подходит следующий формат лога.

Выполните
git log --pretty=format:"%h %ad | %s%d [%an]" --date=short
Выглядит это примерно так:

Результат
$ git log --pretty=format:"%h %ad | %s%d [%an]" --date=short
b7614c1 2023-11-28 | Added HTML header (HEAD -> main) [Alexander Shvets]
46afaff 2023-11-28 | Added standard HTML page tags [Alexander Shvets]
78433de 2023-11-28 | Added h1 tag [Alexander Shvets]
5836970 2023-11-28 | Initial commit [Alexander Shvets]
Давайте рассмотрим его в деталях:

--pretty="..." — определяет формат вывода.
%h — укороченный хеш коммита.
%ad — дата коммита.
| — просто визуальный разделитель.
%s — комментарий.
%d — дополнения коммита («головы» веток или теги).
%an — имя автора.
--date=short — сохраняет формат даты коротким и симпатичным.
Таким образом, каждый раз, когда вы захотите посмотреть лог, вам придется много печатать. К счастью, существует несколько опций конфигурации Git, позволяющих настроить формат вывода истории по умолчанию:

Выполните
git config --global format.pretty '%h %ad | %s%d [%an]'
git config --global log.date short
05 Другие инструменты

Оба gitx (для Mac) и gitk (для любой платформы) полезны в изучении истории изменений.
---

### [Содержание](./bookgit.md)
### [Предыдущая](./book9.md)   [Следующая](./book11.md)