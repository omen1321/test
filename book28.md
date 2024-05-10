##  27. Сброс ветки style

Цели

Сбросить ветку style до точки перед первым слиянием.
01 Сбросьте ветку style

Давайте вернемся во времени на ветке style к точке перед тем, как мы слили ее с веткой main. Мы можем сбросить ветку к любому коммиту при помощи команды reset. По сути, это изменение указателя ветки на любую точку дерева коммитов.

В этом случае мы хотим вернуться в ветке style в точку перед слиянием с main. Нам необходимо найти последний коммит перед слиянием.

Выполните
git switch style
git log --graph
Результат
$ git switch style
Already on 'style'
$ git log --graph
*   79ac6fa 2023-11-28 | Resolved merge conflict (HEAD -> style) [Alexander Shvets]
|\  
| * 85c14e9 2023-11-28 | Added meta title (main) [Alexander Shvets]
* | a33deed 2023-11-28 | Merge branch 'main' into style [Alexander Shvets]
|\| 
| * ee16740 2023-11-28 | Added README [Alexander Shvets]
* | 0ee0113 2023-11-28 | Renamed hello.html; moved style.css [Alexander Shvets]
* | 903eb1d 2023-11-28 | Included stylesheet into hello.html [Alexander Shvets]
* | 555372e 2023-11-28 | Added css stylesheet [Alexander Shvets]
|/  
* 9288a33 2023-11-28 | Added copyright statement with email [Alexander Shvets]
* b7614c1 2023-11-28 | Added HTML header (tag: v1) [Alexander Shvets]
* 46afaff 2023-11-28 | Added standard HTML page tags (tag: v1-beta) [Alexander Shvets]
* 78433de 2023-11-28 | Added h1 tag [Alexander Shvets]
* 5836970 2023-11-28 | Initial commit [Alexander Shvets]
Это немного трудно читать, но, глядя на данные, мы видим, что коммит «Renamed hello.html; moved style.css» был последним на ветке style перед слиянием. Давайте сбросим ветку style к этому коммиту. Чтобы сослаться на этот коммит, мы либо используем его хеш, либо посчитаем, что этот коммит находится за 2 коммита до HEAD, то есть HEAD~2 в нотации Git.

Выполните
git reset --hard HEAD~2
Результат
$ git reset --hard HEAD~2
HEAD is now at 0ee0113 Renamed hello.html; moved style.css
02 Проверьте ветку

Теперь проверим историю ветки style. В истории не должно быть коммитов слияния.

Выполните
git log --graph
Результат
$ git log --graph
* 0ee0113 2023-11-28 | Renamed hello.html; moved style.css (HEAD -> style) [Alexander Shvets]
* 903eb1d 2023-11-28 | Included stylesheet into hello.html [Alexander Shvets]
* 555372e 2023-11-28 | Added css stylesheet [Alexander Shvets]
* 9288a33 2023-11-28 | Added copyright statement with email [Alexander Shvets]
* b7614c1 2023-11-28 | Added HTML header (tag: v1) [Alexander Shvets]
* 46afaff 2023-11-28 | Added standard HTML page tags (tag: v1-beta) [Alexander Shvets]
* 78433de 2023-11-28 | Added h1 tag [Alexander Shvets]
* 5836970 2023-11-28 | Initial commit [Alexander Shvets]
28. Перебазирование
---

### [Содержание](./bookgit.md)
### [Предыдущая](./book27.md)   [Следующая](./book29.md)