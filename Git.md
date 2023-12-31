**VCS** (version control system) или **SCM** (source control management) - это ПО, которое помогает отслеживать изменения в программах. **Версия** или **ревизия** - одно изменение или группа изменений. Основные функции:
- хранит историю изменений в виде отдельной ревизии;
- позволяет манипулировать историей изменений;
- помогает анализировать историю изменений.
`pwd` - путь к текущей директории
`cd ~` - переход к домашней директории
`ls` - отобразить содержимое директории
`ls` - отобразить содержимое директории со скрытыми файлами
`cd имя_директории` - переход к конкретной директории
`cd ..` - переход на директорию выше
`touch имя_файла.расширение` - создать файл
`mkdir имя_директории` - создать директорию
`mkdir -p dir1/dir-inside/dir-deeper-inside` - создать структуру директорий
`cp что_копируем куда_копируем` - копировать файл
`mv что_переместить куда_переместить` - переместить файл
`cat имя_файла` - прочитать файл 
`rm имя_файла` - удалить файл
`rmdir имя_директории`- удалить директорию, если она пустая
`rm -r имя_директории` - удалить директорию со всеми файлами
`&&` - выполнение нескольких команд
`git init` - сделать папку git-репозиторием
`rm -rf .git` - "разгитить" папку (удалить папку .git)
`git status` - посмотреть статус git-репозитория
#### Подготовка к сохранению
Состояние `untracked` значит, что git еще не хранит информацию о версиях файлов и не может отследить, как он изменялся.
`git add --all` - подготовка к сохранению всех файлов в репозитории
`git add todo.txt` - подготовка к сохранению отдельного файла
`git add .` - подготовка к сохранению всей папки
`git add` не сохраняет содержимое файлов в репозитории. Если отредактировать какие-либо файлы после `git add` , то они перейдут в состояние `modified` (измененный).
#### Выполнение коммита
`git commit -m "message"` - выполнить коммит с сообщением в кавычках
#### Просмотр истории коммитов
`git log` - просмотреть все сделанные коммиты
### Создание нового удаленного репозитория
На [github](https://github.com/cos-tel) перейти в репозитории и создать новый репозиторий.

### SSH-ключи 
SSH-протокол обеспечивает безопасный обмен данными в сети.
- **Приватный** ключи хранится только на вашем компьютере и не должен передаваться кому-либо еще, используется для шифрования данных
- **Публичный** ключ доступен всем и используется для расшифровки данных, которые были зашифрованы приватным
Только вы можете зашифровать данные с помощью приватного ключа, но любой пользователь, имеющий публичный ключ, может эти данные расшифровать. Таким образом образуется пара SSH-ключей.
### Проверка наличия ключа
`cd ~` - переход в домашнюю директорию
`ls -la .ssh` - вывод всех созданных ключей
### Генерация ключей
`ssh-keygen -t ed25519 -C "email"` - генерация ключа (ed25519 - алгоритм шифрования) ==после генерации будет создано два ключа, без расширения -приватный ключ, с расширением .pub - приватный== 
`ssh-keygen -t rsa -C "email"` - генерация ключа с алгоритмом шифрования rsa
Затем выведется путь где расположить ключи и предложения для создания пароля при использовании ключа.

### Привязка ключа к аккаунту в GitHub
1. `pbcopy < ~/.ssh/id_ed25519.pub` - копирование содержимого публичного ключа в буфер обмена (для привязки, например, в github)
2. На GitHub перейти в Settings
3. Перейти в пункт SSH and GPG Keys
4. В открывшейся вкладке выбрать New SSH key
5. Дать название ключу в поле Title
6. В поле key type выбрать **Authentication Key** 
7. В поле Key вставить содержимое из буфера обмена (пункт 1)
8. Нажать Add SSH key
9. Проверить подлинность ключа с помощью `ssh -T git@github.com.`
### Привязка удаленного репозитория к локальному
- Создать репозиторий на GitHub
- Скопировать URL репозитория
- Выполнить привязку с помощью `git remote add origin git@github.com:cos-tel/notes.git` 
==При привязке необходимо передать два параметра: первый - имя удаленного репозитория (origin), второй - URL удаленного репозитория==
`git remote -v` - проверка, что репозитории привязаны, если они привязаны, то в терминале отразится
```
$ git remote -v
origin    git@github.com:%ИМЯ_АККАУНТА%/%ИМЯ-ПРОЕКТА%.git (fetch)
origin    git@github.com:%ИМЯ_АККАУНТА%/%ИМЯ-ПРОЕКТА%.git (push)
```






