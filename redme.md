## Инструкция для работы с Git

## Что такое Git
Git — это распределенная система контроля версий нашего кода. Зачем она нам? Для распределенных команд нужна какая-то система управления работы. Нужна, чтобы отслеживать изменения, которые происходят со временем.

## создание репозитария 
Для создания репозитария надо выполнить команду *git init* в папке с репозитарием

Для добавления изменений используется команда *git add* 

Для просмотра состояния репозитария используется команда *git status*



## создание коммита
Для создания коммита используем команду *git commit -m "text"* Флажок -m задаст commit message - комментарий разработчика. Он необходим для описания закоммиченных изменений. 

Для просмотра всех выполненных фиксаций можно воспользоваться историей коммитов. Она содержит сведения о каждом проведенном коммите проекта. Запросить ее можно при помощи команды: *git log*


# инструкция для работы с MArkdown

## выделение текста

чтобы выделить текст курсивом необходимо обрамить его звездочками (*) или знаком нижнего подчеркивания(_). Напеимер : *вот так* или _вот так_.

Чтобы выделить текст полужирным, необходимо обрамить его двойными звездочками (**) или двойным знаком нижнего подчеркивания (__). Например: **вот так** или __вот так__.

Альтернативные способы выделения текста жирным или курсивом нужны для того, чтобы мы могли совмешать оба этих способа. Например; _текст может быть курсивом и при этом быть **полужирным**_.

## списки

чтобы добавить ненумерованные списки,необходимо пункты выделить звездочкой (*) или знаком +. Например; вот так:
* элемент 1 
* элемент 2 
* элемент 3
+ элемент 4

Чтобы добавить нумерованные списки, необходимо пункты просто пронумеровать. Например, вот так:
1. Первый пункт
2. Второй пункт

## работа с изображениями

чтобы вставить изображение в текст, достаточно написать следуюшее:
![привет, это лунный камень!](i.jpeg)


# Ветвление

Во время разработки новой функциональности считается хорошей практикой работать с копией оригинального проекта, которую называют веткой. Ветви имеют свою собственную историю и изолированные друг от друга изменения до тех пор, пока вы не решаете слить изменения вместе. Это происходит по набору причин:

Уже рабочая, стабильная версия кода сохраняется.
Различные новые функции могут разрабатываться параллельно разными программистами.
Разработчики могут работать с собственными ветками без риска, что кодовая база поменяется из-за чужих изменений.
В случае сомнений, различные реализации одной и той же идеи могут быть разработаны в разных ветках и затем сравниваться.

## Создание новой ветки

 то что хочу поменять!!!

## Переключение между ветками

Сейчас, если мы запустим branch, мы увидим две доступные опции: 
{name},
*master

master — это активная ветка, она помечена звездочкой. Но мы хотим работать с нашей “новой потрясающей фичей”, так что нам понадобится переключиться на другую ветку. Для этого воспользуемся командой checkout, она принимает один параметр — имя ветки, на которую необходимо переключиться.

git checkout {name}

В Git ветка — это отдельная линия разработки. Git checkout позволяет нам переключаться как между удаленными, так и между локальными ветками. Это один из способов получить доступ к работе коллеги или соавтора, обеспечивающий более высокую продуктивность совместной работы. Однако тут надо помнить, что пока вы не закомитили изменения, вы не сможете переключиться на другую ветку. В такой ситуации нужно либо сделать коммит, либо отложить его, при помощи команды git stash, добавляющей текущие незакоммиченные изменения в стек изменений и сбрасывающей рабочую копию до HEAD'а репозитория.


## слияние веток

Наша “потрясающая новая фича” будет еще одним текстовым файлом под названием <feature.txt.> Мы создадим его, добавим и закоммитим:

git add feature.txt

git commit -m "New feature complete.”

Изменения завершены, теперь мы можем переключиться обратно на ветку master.

git checkout master

Теперь, если мы откроем наш проект в файловом менеджере, мы не увидим файла feature.txt, потому что мы переключились обратно на ветку master, в которой такого файла не существует. Чтобы он появился, нужно воспользоваться merge для объединения веток (применения изменений из ветки amazing_new_feature к основной версии проекта).

git merge amazing_new_feature

Теперь ветка master актуальна. Ветка amazing_new_feature больше не нужна, и ее можно удалить.

git branch -d awesome_new_feature

Если хотите создать копию удаленного репозитория - используйте git clone. Однако если вам нужна только определенная его ветка, а не все хранилище - после git clone выполните следующую команду в соответствующем репозитории:

git checkout -b <имя ветки> origin/<имя ветки>

После этого, новая ветка создается на машине автоматически.

## Удаленные репозитории

Сейчас наш коммит является локальным — существует только в директории .git на нашей файловой системе. Несмотря на то, что сам по себе локальный репозиторий полезен, в большинстве случаев мы хотим поделиться нашей работой или доставить код на сервер, где он будет выполняться.

1. Что такое удаленный репозиторий

Репозиторий, хранящийся в облаке, на стороннем сервисе, специально созданном для работы с git имеет ряд преимуществ. Во-первых - это своего рода резервная копия вашего проекта, предоставляющая возможность безболезненной работы в команде. А еще в таком репозитории можно пользоваться дополнительными возможностями хостинга. К примеру -визуализацией истории или возможностью разрабатывать вашу программу непосредственно в веб-интерфейсе.
Клонирование
Клонирование - это когда вы копируете удаленный репозиторий к себе на локальный ПК. Это то, с чего обычно начинается любой проект. При этом вы переносите себе все файлы и папки проекта, а также всю его историю с момента его создания. Чтобы склонировать проект, сперва, необходимо узнать где он расположен и скопировать ссылку на него. В нашем руководстве мы будем использовать адрес https://github.com/tutorialzine/awesome-project, но вам посоветуем, попробовать создать свой репозиторий в GitHub, BitBucket или любом другом сервисе:

git clone https://github.com/tutorialzine/awesome-project

При клонировании в текущий каталог, там будет создана папка, в которую поместятся все проектные файлы и скрытая директория .git, с самим репозиторием, или с необходимой информацией о нем. В такой ситуации, для клонируемого репозитория, по умолчанию, будет создана папка с одноименным названием, но его можно залить и в другую директорию, например:

git clone https://github.com/tutorialzine/awesome-project new-folder

2. Подключение к удаленному репозиторию
Чтобы загрузить что-нибудь в удаленный репозиторий, сначала нужно к нему подключиться. Регистрация и установка может занять время, но все подобные сервисы предоставляют хорошую документацию.
Чтобы связать наш локальный репозиторий с репозиторием на GitHub, выполним следующую команду в терминале. Обратите внимание, что нужно обязательно изменить URI репозитория на свой.

git remote add origin https://github.com/tutorialzine/awesome-project.git

Проект может иметь несколько удаленных репозиториев одновременно. Чтобы их различать, мы дадим им разные имена. Обычно главный репозиторий называется origin.

3. Отправка изменений на сервер

Сейчас самое время переслать наш локальный коммит на сервер. Этот процесс происходит каждый раз, когда мы хотим обновить данные в удаленном репозитории.
Команда, предназначенная для этого - push. Она принимает два параметра: имя удаленного репозитория (мы назвали наш origin) и ветку, в которую необходимо внести изменения (master — это ветка по умолчанию для всех репозиториев).

$ git push origin master

Counting objects: 3, done.
Writing objects: 100% (3/3), 212 bytes | 0 bytes/s, done.
Total 3 (delta 0), reused 0 (delta 0)
To https://github.com/tutorialzine/awesome-project.git
* [new branch] master -> master

Эта команда немного похожа на git fetch, с той лишь разницей, что при помощи fetch мы импортируем коммиты в локальную ветку, а применив push, мы экспортируем их из локальной в удаленную. Если вам необходимо настроить удаленную ветку используйте git remote. Однако пушить надо осторожно, ведь рассматриваемая команда перезаписывает безвозвратно все изменения. В большинстве случаев, ее используют, чтобы опубликовать выгружаемые локальные изменения в центральный репозиторий. А еще ее применяют для того, чтобы поделиться, внесенными в локальный репозиторий, нововведениями, с коллегами или другими удаленными участниками разработки проекта. Подытожив сказанное, можно назвать git push - командой выгрузки, а git pull и git fetch - командами загрузки или скачивания. После того как вы успешно запушили измененные данные, их необходимо внедрить или интегрировать, при помощи команды слияния git merge.
В зависимости от сервиса, который вы используете, вам может потребоваться аутентифицироваться, чтобы изменения отправились. Если все сделано правильно, то когда вы посмотрите в удаленный репозиторий при помощи браузера, вы увидите файл hello.txt

4. Запрос изменений с сервера

Если вы сделали изменения в вашем удаленном репозитории, другие пользователи могут скачать изменения при помощи команды pull.

$ git pull origin master
From https://github.com/tutorialzine/awesome-project
* branch master -> FETCH_HEAD
Already up-to-date.

Так как новых коммитов с тех пор, как мы склонировали себе проект, не было, никаких изменений доступных для скачивания нет.