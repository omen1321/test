##  23. Слияние

Цели

Научиться сливать две отличающиеся ветки для переноса изменений обратно в одну ветку.
01 Слияние веток

Слияние переносит изменения из двух веток в одну. Давайте вернемся к ветке style и сольем main со style.

Выполните
git switch style
git merge main
git log --all --graph
Результат
$ git switch style
Switched to branch 'style'
$ git merge main
Merge made by the 'ort' strategy.
 README | 1 +
 1 file changed, 1 insertion(+)
 create mode 100644 README
$ git log --all --graph
*   a33deed 2023-11-28 | Merge branch 'main' into style (HEAD -> style) [Alexander Shvets]
|\  
| * ee16740 2023-11-28 | Added README (main) [Alexander Shvets]
* | 0ee0113 2023-11-28 | Renamed hello.html; moved style.css [Alexander Shvets]
* | 903eb1d 2023-11-28 | Included stylesheet into hello.html [Alexander Shvets]
* | 555372e 2023-11-28 | Added css stylesheet [Alexander Shvets]
|/  
* 9288a33 2023-11-28 | Added copyright statement with email [Alexander Shvets]
* b7614c1 2023-11-28 | Added HTML header (tag: v1) [Alexander Shvets]
* 46afaff 2023-11-28 | Added standard HTML page tags (tag: v1-beta) [Alexander Shvets]
* 78433de 2023-11-28 | Added h1 tag [Alexander Shvets]
* 5836970 2023-11-28 | Initial commit [Alexander Shvets]
Путем периодического слияния ветки main с веткой style вы можете переносить из main любые изменения и поддерживать совместимость изменений style с изменениями в основной ветке.

Однако, это делает графики коммитов действительно уродливыми. Позже мы рассмотрим возможность перебазирования, как альтернативы слиянию.

02 Далее

Но что если изменения в ветке main конфликтуют с изменениями в style?
---

### [Содержание](./bookgit.md)
### [Предыдущая](./book23.md)   [Следующая](./book25.md)