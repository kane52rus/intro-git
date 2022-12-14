# Инструкция для работы с git

## Глоссарий git
+ **Терминал** - *terminal* - программа для взаимодействия с приложениями/операционной системой через текстовые команды
+ **Консоль** - *console* - аналогично терминалу
+ **Команда** - *command* - набор действий для исполнения в терминале
+ **Локальный репозиторий** - *local repository* - это какой-то проект/папка/хранилище на компьютере, в котором ведется история изменений файлов в проекте.
+ **Удаленный репозиторий** - *remote repository* - это какой-то проект/папка/хранилище на сервере (к примеру https://github.com), в котором ведется история изменений файлов в проекте.
+ **Коммит** - *commit* - это набор файлов, которые были изменены с целью применить/зафиксировать изменения в файлах/проекте или создании новых файлов в проекте.
+ **Сообщение коммита** - *commit message* - это подпись наших изменений. Мы описываем то, что изменили в рамках новой версии нашего проекта/файла
+ **Ветка** - *branch* - это ответвление от основной ветки (к примеру master/main). Ветвление означает, что вы отклоняетесь от основной линии разработки и продолжаете работу, не вмешиваясь в основную линию. Полезная вещь в командной разработке, принцип "каждой задаче - своя ветка". Ответвленные ветки можно подвергнуть слиянию. 
+ **Пуш** - *push* - отправка изменений на удаленный репозиторий
+ **Пулл** - *pull* - получение изменений с удаленного репозитория
+ **Мерж** - *merge* - слияние веток на локальном репозитории
+ **Лог** - *log* - журнал/история коммитов 
+ **Неотслеживаемый** - *untracked* - состояние файла/папки, когда он не добавлен к отслеживанию в репозитории git. В visual studio code рядом с файлом пишется ***буква U*** и файл выделяется ***зеленым цветом***
+ **Модифицированный** - *modified* - состояние файла/папки, когда файл был ранее добавлен к отслеживанию, просто был изменен относительно прошлого коммита. В visual studio code рядом с файлом пишется ***буква M*** и файл выделяется ***желтым цветом***
+ **Добавленный** - *Added* - состояние файла/папки, когда git знает об изменениях/добавлении файлов в репозитории. В visual studio code рядом с файлом пишется ***буква A*** и файл выделяется ***зеленым цветом***

## Что такое git и для чего нужен
**Git - это консольная/терминальная программа**, для отслеживания и ведения истории изменения файлов, в вашем проекте. Чаще всего его используют для кода, но можно и для других файлов. Например, для картинок - полезно для дизайнеров.

## Основные команды и методы их применения
### Создание/удаление локального репозитория в проекте/папке
1. **Создание репозитория в проекте/папке**
```bash
git init
```
В результате создается скрытая от людских глаз папка в проекте .git

2. **Удаление репозитория в проекте/папке**
```powershell
Remove-Item -Path .git -Recurse -Force
```
В результате будет удалена папка .git и репозиторий будет удален вместе со всеми коммитами. Останутся только последние изменения.

### Добавление нового/измененного файла/файлов к отслеживанию в репозитории
1. **Добавление одного файла/папки к отслеживанию в репозитории**
```powershell
git add <имя файла>
```
или
```powershell
git add <имя папки>
```
В результате будет добавлен один файл/папка к отслеживанию. Он будет готов к коммиту.

2. **Добавление нескольких файлов/папок к отслеживанию в репозитории**
```powershell
git add <имя файла 1> <имя папки 1> <имя файла 2> <имя папки 2>... <имя файла N> <имя папки N>
```
В результате будут добавлены несколько перечисленных файлов/папки к отслеживанию. Они будут готовы к коммиту

3. **Добавление *ВСЕХ* файлов/папок к отслеживанию в репозитории**
```powershell
git add .
```
или
```powershell
git add -A
```
В результате будут добавлены *ВСЕ* файлы/папки к отслеживанию в репозитории

### Применение изменений/создание коммита
1. **Создание коммита в текстовом редакторе vim (не рекомендуется)**
```powershell
git commit
```
В результате откроется текстовый редактор vim с целью написания сообщения коммита. Выйти из него, нужно ввести комбинацию клавиш *Escape* и написать *:wq*. Написание последнего действия будет в нижней строке терминала

2. **Создание коммита с сообщением коммита**
```powershell
git commit -m '<текст коммита>'
```
В результате будет выполнен коммит с добавленными к отслеживанию файлами.

3. **Создание коммита с сообщением и добавление всех *модифицированных* файлов**
```powershell
git commit -m '<текст коммита>' -a
```

4. **Дополнительная информация по ключам**
* ```-m/--message '<имя сообщения>'``` - пишется в обязательной последовательности, так как мы передаем ключ и после него ожидается текстовое значение.
* ```-a/--all``` - добавление к коммиту.
Порядок в указании ключей не важен. Главное, чтобы после ```git commit -m``` шло какое-то сообщение.
Есть еще много разных ключей, но они не нужны для стандартного пользования

### Клонирование удаленного репозитория
1. **Клонирование удаленного репозитория**
```powershell
git clone <ссылка до удаленного репозитория (URL)>
```
В результате будет создана новая папка с нужным репозиторием.
2. **Клонирование удаленного репозитория в текущую папку**
```powershell
git clone <ссылка до удаленного репозитория (URL)> .
```
Нужно обратить внимание на точку в конце команды. Она и определяет, куда проект будет скачан
В результате репозиторий будет склонирован в текущую папку без создания новой.

### Подключение/удаление/управление удаленного репозитория
1. **Подключение удаленного репозитория к проекту "по стандарту"**
```powershell
git remote add origin <ссылка на репозиторий (https/ssh)>
```
Как итог, подключается удаленный репозиторий.

2. **Просмотр статуса подключенных удаленных репозиториев к проекту**
```powershell
git remote -v
```
Данная команда покажет вывод всех подключенных удаленных репозиториев. Если результатом оказалась пустота, то он не подключен.

3. **Удаление подключенного удаленного репозитория от проекта**
```powershell
git remote remove origin
```
Для проверки можно выполнить ```git remote -v ```, чтобы убедиться, что репозиторий был удален

4. **Отправка(push) изменений в удаленный репозиторий**
```powershell
git push origin <имя ветки>
```
Выполнять данную команду необходимо после коммита. После чего все коммиты будут отправлены в удаленный репозиторий

5. **Получение(pull) изменений из удаленного репозитория**
```powershell
git pull origin <имя ветки>
```
В результате изменения из удаленного репозитория будут подтянуты в локальный.

### Работа с ветками/ветвлением
1. **Создание веток**
```powershell
git branch <имя ветки>
```
После исполнения данной команды, произойдет создание новой ветки, но в результате мы в нее не переключимся на нее.

2. **Просмотр существующих веток**
```powershell
git branch
```
Покажет все ветки в локальном репозитории
Можно просмотреть все ветки включая удаленный репозиторий
```powershell
git branch -A
```
Покажет все ветки в локальном репозитории. Зеленым выделяются ветки в локальном репозитории, красным в удаленном.

3. **Переключение на новую/существующую ветку**
```powershell
git checkout <имя ветки>
```
После этого увидим информацию, что мы переключились на другую ветку. Для достоверности переключения можно ввести команду ```git branch```

4. **Создание новой ветки и переключение в нее одной командой**
```powershell
git checkout -b <имя ветки>
```

5. **Слияние веток**
К примеру, были соверешены какие-то изменения в новой ветке и наступила пора, когда необходимо изменения добавить в основную ветку. Для начала нужно закоммитить изменения в своей ветке при помощи ```git commit -m '<сообщение коммита>' -a``` и переместиться в ветку, в которую мы собираемся производить слияние (как пример: ```git checkout master```). Исполнить следующую команду:
```powershell
git merge <имя ветки с которой мы хотим получить изменения>
```
Если конфликтов не обнаружено, то произойдет слияние веток.

6. **Мерж конфликты (merge conflicts)**
Бывает, когда слияние веток завершается ошибкой. Такое случается, когда в одном и том же файле применялось несколько изменений, которые могли бы пересекаться. В любом случае, сдвиг по строчкам происходит и git зачастую видит в этом проблему.
Чтобы решить проблему можно не прибегать к сложным устройствам команд git, а выполнить разрешение этого конфликта через Visual Studio Code или другую среду разработки (IDE). Данные редакторы кода/среды разработки показывают наглядно в чем и где проблема и предлагают решение: 
    1. Принять входящее состояние
    2. Принять исходное состояние
    3. Принять оба (может быть чревато, нужно хорошо убедиться в том, что делаешь)
    4. Исправить вручную
    После разрешения конфликта необходимо сделать коммит. Тогда конфликт разрешится.

### Вспомогательные команды
1. **Просмотр статуса изменений.**
```powershell
git status
```
В результате исполнения терминал покажет информацию о измененных файлах, в каком они статусе находятся, являются ли они новыми, являются ли измененными и т.д.

2. **Вывод списка коммитов**
```powershell
git log
```
Данная команда покажет информацию о всех коммитах в локальном репозитории

3. **Просмотр конкретных изменений кода/текста перед коммитом**
```powershell
git diff
```
В результате получим информацию о том, какие строчки были добавлены, какие удалены.


### Часто встречаемые наборы команд
1. **Создать репозиторий в существующем проекте**
```powershell
git init
git add .
git commit -m 'имя сообщения' -a
```
В результате все файлы в проекте будут добавлены и зафиксированы в репозитории

2. **Подключить удаленный репозиторий и отправить данные в него**
```powershell
git remote add origin <ссылка на удаленный репозиторий>
git push origin <имя ветки>
```
Команда выполнит подключение удаленного репозитория и отправит данные в него.

3. **Выполнить стандартную процедуру коммита**
```powershell
git add <имя файла> или git add -A
git commit -m 'имя сообщения' -a
```

