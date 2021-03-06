![Git_log](git_log.jpg)
# Работа с Git


## 1. Проверка наличия установленного Git
В терминале выполнить команду:
 `git version`.
Если Git установлен появется собщение с информацией о версий программы. Иначе появется сообщение об ошибке.


## 2. Установка Git
Загружаем последнюю версию **Git** с сайта: https://git-scm.com/. 
Устанавливаем с настройками по умолчанию.


## 3. Натройка Git
Необходимо представится в **Git**. Для этого нужно 2 команды:
```
git config --global user.name <<Ваше имя>>

git config --global user.emil <<Ваше почта>>
```


## 4. Инициализация репозитория
В терминале переходим к папке, в которой хотим создать репозиторий. Выполняем команду: `git init`.
В исодной папке появится скрытая папка *.git* 


## 5. Запись изменений в репозиторий 

### ***Пометка. После любых измененией в файле на забывайте сохранять файл (Ctrl+S)***.

1. `git add` - добавляет содержимое рабочего каталога в индекс для последующего коммита. По умолчанию `git commit` использует лишь этот индекс, так что вы можете использовать `git add` для сборки слепка вашего следующего коммита.

Пример: `git add [имя файла с расширением]`


2. `git commit` - берёт все данные добавленные в индекс с помощью `git add`, и сохраняет их слепок во внутренней базе данных. 
- Опция `(-a)` добавляет все изменения в индекс без использования `git add`, что может быть удобным в повседневном использовании.
- Опция `(-m)` для передачи сообщения коммита без запуска полноценного редактора.
- Опция `(--amend)`, используется для изменения последнего совершённого коммита.

Пример: `git commit -m "ваш комментарии о проделоной работе"`

Пример без предворительного написания команды `git add ` : `git commit -a -m "ваш комментарии о проделоной работе"`

3. `git status` - показывает состояния файлов в рабочем каталоге и индексе: какие файлы изменены, но не добавлены в индекс; какие ожидают коммита в индексе. Вдобавок к этому выводятся подсказки о том, как изменить состояние файлов.


4. `git diff` - показывает изменене в вашем файле (добавленные или удаленные строки или символы, пробелы). Добавленные помечаются (+), удаленные (-) и крассным цветом.


## 6. История commit

Для просмотра истории коммитов используется команда 
```
git log
```
Данная команда перечесляет коммиты с их хеш-кодами, именем и электронной почтой автора, датай создания и сообщение коммита.
По умолчанию последний коммит находится вверху.

--**Извените забежал в перед и добавил сторку "По умолчанию последний коммит находится вверху." раньше чем надо((**

Для выхода из просмотра истории используется клавиша `Q`

Опция `(--groph)` лог с отображением всех коммитов и ветвей.

Опция `(--oneline)` сокращает вывод (в одну строку). 

Пример: `git log --oneline`
```
mr.Di@DESKTOP-GPJMCVI MINGW64 /f/Ucoba/Git_Praktika/1_dz (master)
$ git log --oneline
fb33878 (HEAD -> master) Дбавили альтернативные способы выделения текста
d2e8d48 Запись изменений в репозиторий
a260aea Примерно накидал план
8c3ab33 начал с того где остановился
```


## 7. Перемещение между сохранениями (коммитами)

Для переключения на нужный коммит используется команда:
```
git checkout <хеш-номер коммита>
```
Хеш-номер - это (обозначение, имя) коммита, причем можно указывать не весь хеш, а несколько начальных символов хеша.
Все хеш-номеры коммитов есть в `log`.
Пример как узнвть хеш-номер коммита:
```
$ git log
commit c98350749666d6a48256e6cdfcc2f219aecbdcee (history)
Author: Daulet <moni_i@mail.ru>
Date:   Thu Apr 7 03:17:12 2022 +0600

    Добавил строку в раздел 6
```
Где после слова `commit` идет длинный хеш-номер. 


-- ***Строка специально для создания конфликта*** -- (создана в master)



## 8. Игнор файлов

Для того, чтобы исключить из отслеживания в репозитории определенные файлы или папки необходимо создать там файл ***.gitignore*** и записать в него их названия и шаблоны, соответствующие таким файлам или папкам.


## 9. Создание веток в Git

Ветка в Git - это простой перемещаемый указатель на один из коммитов, обычно последни в цепочке коммитов.
По умолчанию имя основной ветки master.

Список веток можно посмотреть через команду `git branch`. Текущая ветка будет отмечена звездочкой: **\*master**

Создать ветку можно командой:
```
git branch <name branch>
```
В результате создается новый указатель на текущий коммит.
Список веток можно посмотреть через команду `git branch`.
Для переключения между ветками используется команда `git checkout <имя ветки>`.
Для создания сразу и перехода в ветку можно использовать команды:
```
git checkout -b <name branch>
```
или
```
git switch <name branch>
```


## 10. Слияние веток и разришение конфликтов

Для слияния веток нужно нужно выполнить команду:

    git merge <name new branch>

Если была изменена одна и та же часть в обеих ветках то может возикнуть конфликт, который потребует участие пользователя. Git прелагает варианты ришения.
Чтобы разрешить конфликт, нужно вырать один из вариантов, либо объединить содержимое по-своему. 
```
git merge <название выбранной ветки>
```
Если была изменена одна и та же часть в обеих ветках то может возикнуть конфликт, который потребует участие пользователя. Git прелагает варианты ришения.
Чтобы разрешить конфликт, нужно вырать один из вариантов, либо объединить содержимое по-своему.


## 11. Удаление веток

-- ***Строка специально для создания конфликта*** -- (создана в master)
Для удаления ветки используется команда:
```
git branch -d <имя ветки>
```
При попытке удалить еще не слитую ветку, командой:

`git branch -d` 

приведёт к ошибке:
```
$ git branch -d testing
error: The branch 'testing' is not fully merged.
If you are sure you want to delete it, run 'git branch -D testing'.
```
Если вы действительно хотите удалить ветку вместе со всеми наработками, используйте опцию `-D`, как указано в подсказке.
После выполнения слияния ненужную ветку можно удалить команой:
```
git branch -d <название ветки>
```



## 12. Работа с удалёнными репозиториями !!

Чтобы иметь возможность совместной работы над каким-либо Git-проектом, необходимо знать как управлять удалёнными репозиториями. Удалённые репозитории — это модификации проекта, которые хранятся в интернете или ещё где-то в сети. Их может быть несколько, каждый из которых как правило доступен для вас либо только на чтение, либо на чтение и запись. Совместная работа включает в себя управление удалёнными репозиториями и помещение (push) и получение (pull) данных в и из них тогда, когда нужно обменяться результатами работы. 

1. ***Как подключиться к удаленному репозитарию?***

Для загрузки данных в удаленный репозитарию сначала нужно к нему подключиться. В нашем примере мы используем адрес  ``https://github.com/AndreyBulgakov19/SCV_Git_0704.git``, однако пользователь может создать собственный удаленный репозитарий на GitHub или другом подобном сервисе. 

Для того, чтобы связать созданный нами локальный репозитарий с удаленным, выполним такую команду:

```
# This is only an example. Replace the URI with your own repository address.
$ git remote add origin https://github.com/AndreyBulgakov19/SCV_Git_0704.git
```

Первая строка напоминает нам, что URI репозитария, который приведен в примере, нужно изменить на свой.

Иногда бывает так, что проект имеет несколько удаленных репозитариев – в таком случае каждому из них присваивается собственное имя. Главный репозитарий принято называть origin.

2. ***Как клонировать удаленный репозитарий?***

Если у других пользователей возникла необходимость клонировать удаленный репозитарий, они могут получить полностью работоспособную копию при помощи команды ``clone:``

```
$ git clone https://github.com/AndreyBulgakov19/SCV_Git_0704.git
```

``GitHub`` автоматически создаст новый локальный репозитарий в виде удаленного на собственном сервере.

3. ***Как отправить изменения в удаленный репозитарий?***

Теперь, когда у нас в локальном репозитарии создан коммит и мы подключились к удаленному, можем отправить его на сервер. Мы это будем делать каждый раз, когда хотим обновить данные в удаленном репозитарии.

Отправка коммита осуществляется с помощью команды ``push``, которая имеет два параметра - имя удаленного репозитория (в нашем случае origin) и ветку, в которую необходимо внести изменения (master — это ветка по умолчанию для всех репозиториев).

```
$ git push origin master
Counting objects: 3, done.
Writing objects: 100% (3/3), 212 bytes | 0 bytes/s, done.
Total 3 (delta 0), reused 0 (delta 0)
To https://github.com/AndreyBulgakov19/SCV_Git_0704.git
* [new branch] master -> master
```

Если мы все сделали правильно, то отправленный файл ``hello.txt`` на удаленном сервере мы можем увидеть с помощью браузера. *Важный момент – некоторые сервисы для отправки изменений могут требовать дополнительной аутентификации.*

4. ***Как запросить изменения с удаленного репозитария?***

В случае, если другим пользователям нет необходимости делать клон удаленного репозитария, а нужно просто получить информацию об изменениях, это можно сделать с помощью команды ``pull``:

```
 git pull origin master
From https://github.com/AndreyBulgakov19/SCV_Git_0704.git
* branch master -> FETCH_HEAD
Already up-to-date.
```
Она скачивает новые изменения. Так как мы ничего нового не вносили с тех пор, как клонировали проект, изменений, доступных к скачиванию, нет.

5. ***Запрос на вливание вашей ветки в основную ветку исходного репозитория (удаленныи репозитори)***

Для отправке запроса на вливание изменений из вашей ветки в основную ветку исходного репозитория используется команда: `pull request`

- Делаем `fork` репозитория
- Делаем `clone` СВОЕЙ версии репозитория
- Создаем новую ветку и в НЕЕ вносим свои изменения
- Фиксируем изменения (делаем коммиты)
- Отправляем свою версию в свой `GitHub`
- На сайте `GitHub` нажимаем кнопку `pull request`

6. ***Добавление своей работы в GitHub***

Чтобы залить свою работу в GitHub, нужно создать свой акаунт на GitHub.
Потом *"подружить"* GitHub с вашим репозиторием:

```
git remote add origin https://github.com/AndreyBulgakov19/SCV_Git_0704.git
git branch -M main
git push -u origin main
```

В `git remote` указываете имя и ссылку на репозитори и связываем акаунт с локальным файлом.

В `git branch -M main` сливаем ветку `main` с основной.

В `git push -u origin main` отправляем изменение в репозитори.



----------------------------------------------------------------------


### Пункты для создания веток и слияния. Попутно решая конфликты.


1. Вариант

***-- Строка для конфликта и слияния --***
***-- Строка добавленая в ветке OneVariant --***

***-- Строка добавленая в ветке OneVariant --***

2. Вариант

***-- Строка для конфликта и слияния --***

***-- Строка добавленая в ветке OneVariant --***

***-- Строка добавленая в ветке OneVariant --***


3. Вариант

***-- Строка для конфликта и слияния --***



***-- Строка добавленая в ветке OneVariant --***

***-- Строка добавленая в ветке OneVariant --***

4. Вариант

***-- Строка добавленая в ветке OneVariant --***

***-- Строка добавленая в ветке OneVariant --***
