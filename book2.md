## 1. Финальные приготовления

Цели

Полная готовность к работе с Git.
01 Установка имени и электронной почты

Если вы никогда ранее не использовали Git, для начала вам необходимо осуществить установку. Выполните следующие команды, чтобы Git узнал ваше имя и электронную почту. Эти данные используются для подписи изменений сделанных вами, что позволит отслеживать, кто и когда сделал изменения в файле.

Выполните
git config --global user.name "Your Name"
git config --global user.email "your_email@whatever.com"
02 Имя ветки по умолчанию

Мы будем использовать main в качестве имени ветки по умолчанию. Чтобы установить его, выполните следующую команду:

Выполните
git config --global init.defaultBranch main
03 Корректная обработка окончаний строк

Для пользователей Unix/Mac:

Выполните
git config --global core.autocrlf input
git config --global core.safecrlf warn
Для пользователей Windows:

Выполните
git config --global core.autocrlf true
git config --global core.safecrlf warn
---

### [Содержание](./bookgit.md)
### [Предыдущая](./book1.md)   [Следующая](./book3.md)