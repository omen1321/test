##  24. Создание конфликта

Цели

Создание конфликтующих изменений в ветке main.
При слиянии двух веток Git пытается перенести изменения из одной ветки в другую. Если в обеих ветках была изменена одна и та же часть файла, Git может не справиться с автоматическим слиянием изменений. В этом случае Git сообщит о конфликте и попросит разрешить его вручную. В этом уроке мы смоделируем конфликт, а затем научимся его разрешать.

В реальной жизни конфликты слияния регулярно возникают при работе в команде. Например, вы и ваш коллега начали работать над двумя разными фичами, затрагивающими одни и те же файлы. Ваш коллега закончил работу первым и слил свои изменения в ветку main. Теперь вы хотите слить свои изменения в ветку main. Но ветка main теперь отличается от той, с которой вы начинали работать в начале — в ней появился новый код, присланный вашим коллегой. Вероятно, Git не сможет автоматически объединить ваши изменения и попросит помощи человека.

01 Вернитесь в main и создайте конфликт

Помните, что в нашей ветке main страница по-прежнему называется hello.html? Переключитесь обратно на ветку main и внесите следующие изменения:

git switch main
Файл: hello.html
<!-- Author: Alexander Shvets (alex@githowto.com) -->
<html>
  <head>
    <title>Hello World Page</title>
  </head>
  <body>
    <h1>Hello, World!</h1>
    <p>Let's learn Git together.</p>
  </body>
</html>
Выполните
git add hello.html
git commit -m "Added meta title"
02 Просмотр веток

Выполните
git log --all --graph
Результат
$ git log --all --graph
* 85c14e9 2023-11-28 | Added meta title (HEAD -> main) [Alexander Shvets]
| *   a33deed 2023-11-28 | Merge branch 'main' into style (style) [Alexander Shvets]
| |\  
| |/  
|/|   
* | ee16740 2023-11-28 | Added README [Alexander Shvets]
| * 0ee0113 2023-11-28 | Renamed hello.html; moved style.css [Alexander Shvets]
| * 903eb1d 2023-11-28 | Included stylesheet into hello.html [Alexander Shvets]
| * 555372e 2023-11-28 | Added css stylesheet [Alexander Shvets]
|/  
* 9288a33 2023-11-28 | Added copyright statement with email [Alexander Shvets]
* b7614c1 2023-11-28 | Added HTML header (tag: v1) [Alexander Shvets]
* 46afaff 2023-11-28 | Added standard HTML page tags (tag: v1-beta) [Alexander Shvets]
* 78433de 2023-11-28 | Added h1 tag [Alexander Shvets]
* 5836970 2023-11-28 | Initial commit [Alexander Shvets]
После коммита «Added README» ветка main была объединена с веткой style, но в настоящее время в main есть дополнительный коммит, который не был слит с style.

03 Далее

Последнее изменение в main конфликтует с некоторыми изменениями в style. На следующем шаге мы решим этот конфликт.
---

### [Содержание](./bookgit.md)
### [Предыдущая](./book24.md)   [Следующая](./book26.md)