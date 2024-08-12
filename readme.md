## Шпаргалка по Git

---

* Система контроля версий, или VCS (SCM), — программа, позволяющая контролировать изменения в проекте.
* Git — один из примеров системы контроля версий: он позволяет хранить, изменять и анализировать историю проекта.
* Git — незаменимый в команде инструмент, ведь он помогает объединять результаты работы нескольких человек.

---

### Инициализция

* Инициализировать репозиторий можно с помощью команды _git init_
* Проверить статус, или состояние, репозитория поможет команда _git status_
* Если вы ошиблись и случайно инициализировали не ту папку, можно «разгитить» её — удалить скрытую подпапку **.git**

### Добавление файлов

* Команда _git add_ позволяет подготовить файл к сохранению.
* Команда _git add --all_ подготовит к сохранению сразу все файлы.
* С помощью _git add ._ можно добавить в репозиторий текущую папку со всеми файлами.

### Коммит

* Коммит можно сделать с помощью команды _git commit_
* Ключ _-m_ позволяет присвоить коммиту сообщение. Помните, что такие сообщения должны быть информативными: чётко описывать изменения.
* В коммит попадает то, что было предварительно добавлено перед коммитом.

---

### Хеш

* Git преобразует информацию о коммитах с помощью алгоритма SHA-1 и для каждого из них рассчитывает уникальный идентификатор — хеш.
* Хеш — основной идентификатор коммита и позволяет узнать его автора, дату и содержимое закоммиченных файлов.
* Все хеши, а также таблицу соответствий хеш → информация о коммите Git хранит в папке **.git**

### Лог

* Можно вызвать не только полный лог, но и сокращённый — это делается командой _git log --oneline_
* В сокращённом логе выводятся сокращённые хеши — их можно использовать точно так же, как и полные.

### HEAD

* В числе прочих файлов в папке **.git** есть служебный файл _HEAD_. Он указывает на самый свежий коммит.
* Вместо хеша последнего коммита можно написать слово _HEAD_ — Git вас поймёт.

### Статусы файлов в Git

```mermaid

graph LR;
  untracked -- "git add" --> staged;
  staged    -- "git commit" --> tracked/comitted;
  staged    -- "изменения" --> modified;
  modified  -- "git add" --> staged;
  tracked/comitted -- "изменения" --> modified;

``` 

* Статусом _untracked_ помечается файл, о существовании которого Git знает, но не следит за изменениями в нём. Этот статус — противоположность _tracked_, в который попадают все файлы, отслеживаемые Git.
* Файл переходит в статус _staged_ после выполнения _git add_
* Статус _modified_ означает, что файл был изменён.
* Большинство файлов в проектах «шагает» по следующему циклу: «изменён» → «добавлен в список на коммит» → «закоммичен» → «изменён» → и так далее.