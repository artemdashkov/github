# Теория
Источники:
Документация по подключению github через SSH:
https://docs.github.com/en/authentication/connecting-to-github-with-ssh

о системе контроля версий
https://git-scm.com/book/ru/v2/%D0%92%D0%B2%D0%B5%D0%B4%D0%B5%D0%BD%D0%B8%D0%B5-%D0%9E-%D1%81%D0%B8%D1%81%D1%82%D0%B5%D0%BC%D0%B5-%D0%BA%D0%BE%D0%BD%D1%82%D1%80%D0%BE%D0%BB%D1%8F-%D0%B2%D0%B5%D1%80%D1%81%D0%B8%D0%B9


# Комманды:
### =======файл .gitconfig=======
-данные из файла нужны для отображения данных о пользователя, который внес изменения в репозиторий

copy NUL .gitconfig		-копирование файла gitconfig в папке C:\Users\Admin после установки Git Bash

можно добавить данные о пользователя в файл вручную, открыв в текстовом редакторе и добавив информацию
[user]
	email=artemdashkov@gmail.com
	name=artemdashkov

git config --global user.name name_from_git
	-имя пользователя будет указано в коммите. name_from_git имя пользователя из Git, можно использовать любое имя, в том числе не привязанное к Git. 

git config --global user.email last_name@gmail.com
	-e-mail будет указан в коммите.

git config --list --global	-показать данные о пользователе
user.email=artemdashkov@gmail.com
user.namr=artemdashkov

### git init
	-инициализация репозитория. создает на ПК скрытые папки и файлы для работы с Git.

### git clone https://github.com/artemdashkov/github_homework.git
	-клонирование удаленного репозитория на локальный ПК

### git status
	- показывает все файлы, которые несоответствует файлам на локальном репозитории (на ПК более свежие), например:
	
	Untracked files:
		(use "git add <file>..." to include in what will be committed)
        file_1.txt						-означает что в системе отсутствует файл

	Changes to be committed:
		(use "git rm --cached <file>..." to unstage)		- означает убрать из отслеживания в гит
        new file:   file_1.txt			-означает что файл внесен в систему

	No commits yet
	Changes to be committed:
		(use "git rm --cached <file>..." to unstage)
        new file:   file_1.txt
	Changes not staged for commit:
		(use "git add <file>..." to update what will be committed)
		(use "git restore <file>..." to discard changes in working directory)
        modified:   file_1.txt

### git add
git add conftest.py
	- добавление отдельных файлов в область подготовленных файлов.

git add .
	- команда для добавления всех файлов из выбранной папки

### git commit	
git commit -m 'update conftest.py and test_items.py'
	-создание коммита после добавления файлов в область подготовленных файлов.
	
git commit -a -m 'new commit'
	-создание коммита для всех файлов локального репозитория

### git push
git push

git push origin main
	- отправка изменений в удаленный репозиторий
	
git push -u origin new_branch
	- добавить новые ветки на внешний репозиторий

git push -u origin first_branch
	-используется для создания новой ветки в удаленном репозитории и добавлении изменений в удаленный репозиторий.

git push origin :second_name
	-удалить ветку с удаленного репозитория

### git fetch
git fetch
	- Эта команда загружает изменения из удаленного репозитория (например, origin) без их слияния с вашей текущей веткой. Вы получаете обновления о новых коммитах, ветках и тегах, которые были добавлены на удаленный сервер.

git fetch origin second_branch
	-восстановить на локальном репозитории удаленную ветку из удаленного репозитория. чтобы ветка появилась на локальном репозитории необходимо перейти в ветку git checkout second_branch

### git pull
git pull origin master
	- Эта команда объединяет две операции — git fetch и git merge. Она загружает изменения из удаленной ветки master и сразу же сливает их с вашей текущей веткой. При выполнении этой команды изменения из origin/master (удаленная ветка) будут загружены и автоматически объединены с вашей текущей веткой. Если есть конфликты, вам будет предложено их разрешить.

### git log
git log
	-показывает все коммиты
	
git log --author artemdashkov
	-показывает все коммиты по выбранному автору
	
git log --oneline --graph --all 
	-графически показывает изменение веток и коммитов
	
git log -S test --oneline
	-если интересует не место расположение строки, а время изменения

### git show
git show
	-показывает последний коммит
	
git show dcb48e4a899e58450c72816f87dd9f72911d6f0d
	-показать расширенную информацию по выбранному коммиту
	
### git blame
git blame file_1.txt
	^dcb48e4 (artemdashkov  2023-11-05 10:07:23 +0300 1) 123
	^dcb48e4 (artemdashkov  2023-11-05 10:07:23 +0300 2)
	227e2675 (Artem Dashkov 2023-11-05 10:18:58 +0300 3) 456
	227e2675 (Artem Dashkov 2023-11-05 10:18:58 +0300 4) 789.
	f1297d17 (Artem Dashkov 2023-11-05 10:43:30 +0300 5) 10 11 12
	-показывает авторов строк

git blame file_1.txt | grep 123
	^dcb48e4 (artemdashkov  2023-11-05 10:07:23 +0300 1) 123
	-показать информацию о выбранной строке

### git grep
git grep — ищет строку или регулярное выражение в репозитории и его истории изменений.

git grep test  -найти все файлы со строкой

echo "Any line" >> file_1.txt
	-добавить строку "Any line" в файл file_1.txt

### git diff
git diff
	-показывает какие изменения были выполнены в файле
	
### git reset
git reset HEAD~1
	-вернуться на один коммит назад
	
git reset HEAD~2
	-вернуться на два коммита назад

### git restore
git restore — отменяет незафиксированные изменения

### git revert
git revert — отменяет коммит в любом месте истории изменений.
	
### git checkout
git checkout file_1.txt
	-откатиться до предыдущего изменения в файле file_1.txt
	
git checkout .
	-откатиться до предыдущего изменения для всех файлов

git checkout first_branch
	-переключиться на ветку first_branch

git checkout -
git checkout -main
	-переключиться на основную ветку

git checkout -b card_pay
	- создать ветку card_pay и сразу в нее перейти

### git stach
git stash
	-откатиться до предыдущего изменения при этом изменения хранятся во временном хранилище

git stash pop
	-отменить откат до предыдущей версии и вернуть временные
	
git stash clear
	-очистить временное хранилище

### git branch
git branch
	-показывает только локальные ветки вашего репозитория. Вы увидите список всех веток, которые существуют в вашем локальном репозитории, и текущую ветку, на которой вы находитесь (она будет отмечена звездочкой *).

git branch -a
	- Эта команда показывает все ветки, как локальные, так и удаленные. Вы увидите список локальных веток, а также веток, которые существуют на удаленных репозиториях (например, на GitHub). Удаленные ветки будут отображаться с префиксом remotes/.

git branch -m first_name second_name
	-переименовать ветку first_name в second_name

git branch card_pay
	-перейти на ветку "card_pay" если она существует. в случае отсутствия ветки создаст новую.

git branch --merged
	-показывает какие ветки были слиты

git branch -d second_branch
	-удалить ветку с локального репозитория
	
git branch -D testing
	-удалить ветку с локального репозитория в случае, если ветка не была слита в мастер ветку

	
	
git rebase - перебазирование 

git reset --soft HEAD1
	отменить последний коммит в Git без удаления сделанных изменений в файлах?


# Синтаксис 

## level 2
### level 3
#### level 4
##### level 5
###### level 6

alternative

level 1
===========
**bold text**
*italic text*

> blockquotes_1
>
> blockquotes_2

list:
- any text 1
- any text 2

lis_2
1. any text 1
2. any text 2

list_3
- ferst string
    - second string

text_1

---

text_2

***

text_3

_________________


~~The world is flat.~~

- [x] Write the press release
- [ ] Update the website
- [ ] Contact the media

That is so funny! :joy:

## [Center](#center)

```
any code 2
```
### Table №1
| Syntax | Description |
| ----------- | ----------- |
| Header | Title |
| Paragraph | Text |

#### Table of Contents

- [Underline](#underline)
- [Indent](#indent)
- [Center](#center)
- [Color](#color)